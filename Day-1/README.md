# Deploy a fullstack application on AWS Amplify


## Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

### Available Scripts

In the project directory, you can run:

#### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

#### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

#### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

#### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

### Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

#### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

#### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

#### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

#### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

#### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

#### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)

# Hosting Application on S3 with AWS Amplify

## Install the Amplify CLI

The Amplify Command Line Interface (CLI) is a unified toolchain to create AWS cloud services for your app. Let's go ahead and install the Amplify CLI.
```
npm install -g @aws-amplify/cli
``` 

## Configure the Amplify CLI

To set up the Amplify CLI on your local machine, you have to configure it to connect to your AWS account.

Configure Amplify by running the following command:
```
amplify configure
```

`amplify configure` will ask you to sign into the AWS Console.

Once you're signed in, Amplify CLI will ask you to create an IAM user.
```
Specify the AWS Region
? region:  # Your preferred region
Follow the instructions at
https://docs.amplify.aws/cli/start/install/#configure-the-amplify-cli

to complete the user creation in the AWS console
https://console.aws.amazon.com/iamv2/home#/users/create
```
After you're done with the user creation download the credentials and use it.

## Initialize an Amplify project

Initialize the project using:
```
amplify init
```
After following the prompts you will get similar result like this:
```
Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project project4
The following configuration will be applied:

Project information
| Name: project4
| Environment: dev
| Default editor: Visual Studio Code
| App type: javascript
| Javascript framework: react
| Source Directory Path: src
| Distribution Directory Path: build
| Build Command: npm.cmd run-script build
| Start Command: npm.cmd run-script start

? Initialize the project with the above configuration? Yes
Using default provider  awscloudformation
? Select the authentication method you want to use: AWS profile

For more information on AWS Profiles, see:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html

? Please choose the profile you want to use default
Adding backend environment dev to AWS Amplify app: d6b894nxryrmh

Deployment completed.
Deploying root stack project4 [ ====================-------------------- ] 2/4
        amplify-project4-dev-162413    AWS::CloudFormation::Stack     CREATE_IN_PROGRESS             Sat Oct 07 2023 16:24:18…
        UnauthRole                     AWS::IAM::Role                 CREATE_COMPLETE                Sat Oct 07 2023 16:24:36…
        AuthRole                       AWS::IAM::Role                 CREATE_COMPLETE                Sat Oct 07 2023 16:24:37…
        DeploymentBucket               AWS::S3::Bucket                CREATE_IN_PROGRESS             Sat Oct 07 2023 16:24:20…

√ Help improve Amplify CLI by sharing non-sensitive project configurations on failures (y/N) · yes

    Thank you for helping us improve Amplify CLI!
Deployment state saved successfully.
✔ Initialized provider successfully.
✅ Initialized your environment successfully.
✅ Your project has been successfully initialized and connected to the cloud!
Some next steps:

"amplify status" will show you what you've added already and if it's locally configured or deployed
"amplify add <category>" will allow you to add features like user login or a backend API
"amplify push" will build all your local backend resources and provision it in the cloud
"amplify console" to open the Amplify Console and view your project status
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud


Pro tip:
Try "amplify add api" to create a backend API and then "amplify push" to deploy everything
```
## Add backend resources like authentication, API, and storage using the Amplify CLI:

```
amplify add auth
```
After running this command you will get similar output:
```
$ amplify add auth
Using service: Cognito, provided by: awscloudformation

 The current configured provider is Amazon Cognito.

 Do you want to use the default authentication and security configuration? Default configuration
 Warning: you will not be able to edit these selections.
 How do you want users to be able to sign in? Username
 Do you want to configure advanced settings? No, I am done.
✅ Successfully added auth resource project42675a3c3 locally

✅ Some next steps:
"amplify push" will build all your local backend resources and provision it in the cloud
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud
```
Then run the following command:
```
amplify add api
```
The results will be:
```
$ amplify add api
? Select from one of the below mentioned services: GraphQL
? Here is the GraphQL API that we will create. Select a setting to edit or continue Continue
? Choose a schema template: Single object with fields (e.g., “Todo” with ID, name, description)

⚠️  WARNING: your GraphQL API currently allows public create, read, update, and delete access to all models via an API Key. To configure PRODUCTION-READY authorization rules, review: https://docs.amplify.aws/cli/graphql/authorization-rules

✅ GraphQL schema compiled successfully.

Edit your schema at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema.graphql or place .graphql files in a directory at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema
√ Do you want to edit the schema now? (Y/n) · yes
Edit the file in your editor: D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema.graphql
✅ Successfully added resource project4 locally

✅ Some next steps:
"amplify push" will build all your local backend resources and provision it in the cloud
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud
```
Then you have to run this command:
```dotnetcli
amplify add storage
```
This will result something like this:
```
$ amplify add storage
? Select from one of the below mentioned services: Content (Images, audio, video, etc.)
√ Provide a friendly name for your resource that will be used to label this category in the project: · khProject
√ Provide bucket name: · khproject123
√ Who should have access: · Auth users only
√ What kind of access do you want for Authenticated users? · create/update, read, delete
√ Do you want to add a Lambda Trigger for your S3 Bucket? (y/N) · yes
✅ Successfully added resource S3Trigger23659b7a locally
√ Do you want to edit the local S3Trigger23659b7a lambda function now? (y/N) · yes
Edit the file in your editor: D:\microapp\kh-project\project-4\amplify\backend\function\S3Trigger23659b7a\src\index.js
? Press enter to continue
✅ Successfully added resource khProject locally

⚠️ If a user is part of a user pool group, run "amplify update storage" to enable IAM group policies for CRUD operations
✅ Some next steps:
"amplify push" builds all of your local backend resources and provisions them in the cloud
"amplify publish" builds all of your local backend and front-end resources (if you added hosting category) and provisions them in the cloud
```
## Push your Amplify project to the AWS cloud
Push you project to the AWS cloud using the following command:
```
amplify push
```
The result will be similar to the following:
```
$ amplify push
/ Fetching updates to backend environment: dev from the cloud.
⚠️  WARNING: your GraphQL API currently allows public create, read, update, and delete access to all models via an API Key. To configure PRODUCTION-READY authorization rules, review: https://docs.amplify.aws/cli/graphql/authorization-rules

| Fetching updates to backend environment: dev from the cloud.✅ GraphQL schema compiled successfully.

Edit your schema at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema.graphql or place .graphql files in a directory at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema
✔ Successfully pulled backend environment dev from the cloud.
/ Building resource api/project4
⚠️  WARNING: your GraphQL API currently allows public create, read, update, and delete access to all models via an API Key. To configure PRODUCTION-READY authorization rules, review: https://docs.amplify.aws/cli/graphql/authorization-rules

- Building resource api/project4✅ GraphQL schema compiled successfully.

Edit your schema at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema.graphql or place .graphql files in a directory at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema

    Current Environment: dev
    
┌──────────┬───────────────────┬───────────┬───────────────────┐
│ Category │ Resource name     │ Operation │ Provider plugin   │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Auth     │ project42675a3c3  │ Create    │ awscloudformation │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Api      │ project4          │ Create    │ awscloudformation │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Function │ S3Trigger23659b7a │ Create    │ awscloudformation │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Storage  │ khProject         │ Create    │ awscloudformation │
└──────────┴───────────────────┴───────────┴───────────────────┘
√ Are you sure you want to continue? (Y/n) · yes

⚠️  WARNING: your GraphQL API currently allows public create, read, update, and delete access to all models via an API Key. To configure PRODUCTION-READY authoriization rules, review: https://docs.amplify.aws/cli/graphql/authorization-rules

✅ GraphQL schema compiled successfully.

Edit your schema at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema.graphql or place .graphql files in a directory at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema
\ Building resource api/project4
⚠️  WARNING: your GraphQL API currently allows public create, read, update, and delete access to all models via an API Key. To configure PRODUCTION-READY authoriization rules, review: https://docs.amplify.aws/cli/graphql/authorization-rules

- Building resource api/project4✅ GraphQL schema compiled successfully.

Edit your schema at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema.graphql or place .graphql files in a directory at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema
? Do you want to generate code for your newly created GraphQL API Yes
? Choose the code generation language target javascript
? Enter the file name pattern of graphql queries, mutations and subscriptions src\graphql\**\*.js
? Do you want to generate/update all possible GraphQL operations - queries, mutations and subscriptions Yes
? Enter maximum statement depth [increase from default if your schema is deeply nested] 2

Deployment completed.
Deployed root stack project4 [ ======================================== ] 5/5
        amplify-project4-dev-162413    AWS::CloudFormation::Stack     UPDATE_COMPLETE                Sat Oct 07 2023 16:38:41…
        functionS3Trigger23659b7a      AWS::CloudFormation::Stack     CREATE_COMPLETE                Sat Oct 07 2023 16:37:36…
        apiproject4                    AWS::CloudFormation::Stack     CREATE_COMPLETE                Sat Oct 07 2023 16:38:09…
        authproject42675a3c3           AWS::CloudFormation::Stack     CREATE_COMPLETE                Sat Oct 07 2023 16:36:57…
        storagekhProject               AWS::CloudFormation::Stack     CREATE_COMPLETE                Sat Oct 07 2023 16:38:39…
Deployed auth project42675a3c3 [ ======================================== ] 6/6
        UserPool                       AWS::Cognito::UserPool         CREATE_COMPLETE                Sat Oct 07 2023 16:36:40…
        UserPoolClientRole             AWS::IAM::Role                 CREATE_COMPLETE                Sat Oct 07 2023 16:36:54…
        UserPoolClient                 AWS::Cognito::UserPoolClient   CREATE_COMPLETE                Sat Oct 07 2023 16:36:42…
        UserPoolClientWeb              AWS::Cognito::UserPoolClient   CREATE_COMPLETE                Sat Oct 07 2023 16:36:42…
        IdentityPool                   AWS::Cognito::IdentityPool     CREATE_COMPLETE                Sat Oct 07 2023 16:36:44…
        IdentityPoolRoleMap            AWS::Cognito::IdentityPoolRol… CREATE_COMPLETE                Sat Oct 07 2023 16:36:46…
Deployed api project4 [ ======================================== ] 6/6
        GraphQLAPI                     AWS::AppSync::GraphQLApi       CREATE_COMPLETE                Sat Oct 07 2023 16:36:41…
        GraphQLAPINONEDS95A13CF0       AWS::AppSync::DataSource       CREATE_COMPLETE                Sat Oct 07 2023 16:36:43…
        GraphQLAPITransformerSchema3C… AWS::AppSync::GraphQLSchema    CREATE_COMPLETE                Sat Oct 07 2023 16:36:54…
        GraphQLAPIDefaultApiKey215A6D… AWS::AppSync::ApiKey           CREATE_COMPLETE                Sat Oct 07 2023 16:36:43…
        Todo                           AWS::CloudFormation::Stack     CREATE_COMPLETE                Sat Oct 07 2023 16:37:42…
        CustomResourcesjson            AWS::CloudFormation::Stack     CREATE_IN_PROGRESS             Sat Oct 07 2023 16:37:43…
Deployed function S3Trigger23659b7a [ ======================================== ] 3/3
        LambdaExecutionRole            AWS::IAM::Role                 CREATE_COMPLETE                Sat Oct 07 2023 16:36:55…
        LambdaFunction                 AWS::Lambda::Function          CREATE_COMPLETE                Sat Oct 07 2023 16:37:04…
        lambdaexecutionpolicy          AWS::IAM::Policy               CREATE_IN_PROGRESS             Sat Oct 07 2023 16:37:04…
Deployed storage khProject [ ======================================== ] 9/9
        TriggerPermissions             AWS::Lambda::Permission        CREATE_COMPLETE                Sat Oct 07 2023 16:37:42…
        S3Bucket                       AWS::S3::Bucket                CREATE_COMPLETE                Sat Oct 07 2023 16:38:04…
        S3AuthPrivatePolicy            AWS::IAM::Policy               CREATE_IN_PROGRESS             Sat Oct 07 2023 16:38:05…
        S3AuthProtectedPolicy          AWS::IAM::Policy               CREATE_IN_PROGRESS             Sat Oct 07 2023 16:38:05…
        S3AuthPublicPolicy             AWS::IAM::Policy               CREATE_IN_PROGRESS             Sat Oct 07 2023 16:38:05…
        S3AuthReadPolicy               AWS::IAM::Policy               CREATE_IN_PROGRESS             Sat Oct 07 2023 16:38:05…
        S3TriggerBucketPolicy          AWS::IAM::Policy               CREATE_IN_PROGRESS             Sat Oct 07 2023 16:38:06…
        S3AuthUploadPolicy             AWS::IAM::Policy               CREATE_IN_PROGRESS             Sat Oct 07 2023 16:38:06…

✔ Generated GraphQL operations successfully and saved at src\graphql
Deployment state saved successfully.

GraphQL endpoint: https://f3hsexfeyvaxdisse77q4jdvyi.appsync-api.us-east-1.amazonaws.com/graphql
GraphQL API KEY: da2-fs6auzl3wzcypbabnky3337gwm

GraphQL transformer version: 2

Browserslist: caniuse-lite is outdated. Please run:
  npx update-browserslist-db@latest
  Why you should do it regularly: https://github.com/browserslist/update-db#readme
```
## Deploy Your Frontend

Deploy your frontend using the following command:
```
amplify publish
```
Results will look like:
```
$ amplify publish
/ Building resource api/project4
⚠️  WARNING: your GraphQL API currently allows public create, read, update, and delete access to all models via an API Key. To configure PRODUCTION-READY authoriization rules, review: https://docs.amplify.aws/cli/graphql/authorization-rules

- Building resource api/project4✅ GraphQL schema compiled successfully.

Edit your schema at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema.graphql or place .graphql files in a directory at D:\microapp\kh-project\project-4\amplify\backend\api\project4\schema
✔ Successfully pulled backend environment dev from the cloud.

    Current Environment: dev

┌──────────┬───────────────────┬───────────┬───────────────────┐
│ Category │ Resource name     │ Operation │ Provider plugin   │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Hosting  │ S3AndCloudFront   │ Create    │ awscloudformation │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Auth     │ project42675a3c3  │ No Change │ awscloudformation │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Api      │ project4          │ No Change │ awscloudformation │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Function │ S3Trigger23659b7a │ No Change │ awscloudformation │
├──────────┼───────────────────┼───────────┼───────────────────┤
│ Storage  │ khProject         │ No Change │ awscloudformation │
└──────────┴───────────────────┴───────────┴───────────────────┘
√ Are you sure you want to continue? (Y/n) · yes

Deployment completed.
Deployed root stack project4 [ ======================================== ] 6/6
        amplify-project4-dev-162413    AWS::CloudFormation::Stack     UPDATE_COMPLETE                Sat Oct 07 2023 16:53:20…
        hostingS3AndCloudFront         AWS::CloudFormation::Stack     CREATE_COMPLETE                Sat Oct 07 2023 16:53:07…
        functionS3Trigger23659b7a      AWS::CloudFormation::Stack     UPDATE_COMPLETE                Sat Oct 07 2023 16:48:30…
        apiproject4                    AWS::CloudFormation::Stack     UPDATE_COMPLETE                Sat Oct 07 2023 16:48:41…
        authproject42675a3c3           AWS::CloudFormation::Stack     UPDATE_COMPLETE                Sat Oct 07 2023 16:48:31…
        storagekhProject               AWS::CloudFormation::Stack     UPDATE_COMPLETE                Sat Oct 07 2023 16:48:32…
Deployed hosting S3AndCloudFront [ ======================================== ] 4/4
        S3Bucket                       AWS::S3::Bucket                CREATE_COMPLETE                Sat Oct 07 2023 16:48:55…
        OriginAccessIdentity           AWS::CloudFront::CloudFrontOr… CREATE_COMPLETE                Sat Oct 07 2023 16:48:35…
        CloudFrontDistribution         AWS::CloudFront::Distribution  CREATE_COMPLETE                Sat Oct 07 2023 16:52:35…
        PrivateBucketPolicy            AWS::S3::BucketPolicy          CREATE_COMPLETE                Sat Oct 07 2023 16:48:57…

Deployment state saved successfully.

GraphQL transformer version: 2
Hosting endpoint: https://d16vq8efb0rarj.cloudfront.net

Browserslist: caniuse-lite is outdated. Please run:
  npx update-browserslist-db@latest
  Why you should do it regularly: https://github.com/browserslist/update-db#readme

> project-4@0.1.0 build
> react-scripts build

Creating an optimized production build...
One of your dependencies, babel-preset-react-app, is importing the
"@babel/plugin-proposal-private-property-in-object" package without
declaring it in its dependencies. This is currently working because
"@babel/plugin-proposal-private-property-in-object" is already in your
node_modules folder for unrelated reasons, but it may break at any time.

babel-preset-react-app is part of the create-react-app project, which
is not maintianed anymore. It is thus unlikely that this bug will
ever be fixed. Add "@babel/plugin-proposal-private-property-in-object" to
your devDependencies to work around this error. This will make this message
go away.

Compiled successfully.

File sizes after gzip:

  46.61 kB  build\static\js\main.c7486130.js
  1.78 kB   build\static\js\787.17c6f57e.chunk.js
  541 B     build\static\css\main.073c9b0a.css

The project was built assuming it is hosted at /.
You can control this with the homepage field in your package.json.

The build folder is ready to be deployed.
You may serve it with a static server:

  serve -s build

Find out more about deployment here:

  https://cra.link/deployment

frontend build command exited with code 0
Publish started for S3AndCloudFront
✔ Uploaded files successfully.
Your app is published successfully.
https://d16vq8efb0rarj.cloudfront.net
```
## Verify the deployment

To Verify the deployment run the url given above. You will get this result:

![ReactApp](Screenshot%20(90).png "ReactApp")