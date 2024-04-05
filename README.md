# Build a Realtime Web Chat and deploy to AWS - TypeScript, Node, React & TailwindCSS - Frontend

This repository has been created as a part of the YouTube video:
[Build a Realtime Web Chat and deploy to AWS - TypeScript, Node, React & TailwindCSS](https://youtu.be/82Geq2Jq0pg)

It is a frontend part of a simple web chat application using API Gateway Webosockets with Serverless Framework Infrastructure as a Code
to easily deploy it to AWS.

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Prerequisites

- AWS CLI installed and configured
- [`serverless-framework`](https://github.com/serverless/serverless)
- [`node.js`](https://nodejs.org)

## Installation

Run:

```bash
npm install
```

or

```
yarn install
```

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

## Deployment

Follow the instructions on the video to create and configure AWS S3 Bucket.

To synchronize changes with S3 bucket run:

```bash
npm run build && aws s3 sync ./build s3://your_bucket_name/
```

where `your_bucket_name` is the name of the S3 bucket created and configured to serve content as static web server.

## Licence

MIT.

## Steps
1.Run:

```bash
npm install
```
or
```
yarn install
```
2. ### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

3. Now change the websocket endpoint from /src/App.tsx file to ```WS_URL = "Your Api endpoint"```

4. Check if the frontend is working properly or not refer console for error fixing.

5.```npm run build```

6. Create an s3 bucket using ```aws s3api create-bucket --bucket your-bucket-name```  the bucket name must be unique.

7. List the aws bucket that we just created ```aws s3 ls```

8. Now attack the bucket policy to your s3 bucket using ```aws s3api put-bucket-policy --bucket your-bucket-name --policy file://D:/Downloads/CC_Proj/serverless-chat-ui-main/bucket_policy.json```
    the bucket policy is attached in the root folder.
9. Sync your build with aws s3 using ```aws s3 sync ./build s3://your_bucket_name/```

10. Now make the s3 bucket a static website ```aws s3 website s3://your-bucket-name/ --index-document index.html --error-document index.html```

11. Your bucket is now live hosted on web example link ```http://your-bucket-name.s3-website-us-east-1.amazonaws.com```

If error occur make sure the make your bucket public from aws s3 console

## IMP NOTE
```Make sure to close all instance from aws console after using the app to avoid any unnecessary bills in your account```