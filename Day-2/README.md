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

# Application Deployment on Elastic Beanstalk

### To install the Elastic Beanstalk. Use the following command:
 
```
pip install awsebcli
```
### To Instiate the Project. Use the following command:

```
$ eb init -p node.js my-middleware-app
```
### Now we have to create the environment

To create the environment use the following command:
```
$ eb create production
```
The output will look like:
```
$ eb create production
Creating application version archive "app-231007_222215385100".
Uploading: [##################################################] 100% Done...
Environment details for: production
  Application name: my-middleware-app
  Region: us-west-2
  Deployed Version: app-231007_222215385100
  Environment ID: e-kkpfkd8uzj
  Platform: arn:aws:elasticbeanstalk:us-west-2::platform/Node.js 18 running on 64bit Amazon Linux 2023/6.0.1
  Tier: WebServer-Standard-1.0
  CNAME: UNKNOWN
  Updated: 2023-10-07 16:54:18.314000+00:00
Printing Status:
2023-10-07 16:54:16    INFO    createEnvironment is starting.
2023-10-07 16:54:18    INFO    Using elasticbeanstalk-us-west-2-789502026025 as Amazon S3 storage bucket for environment data.
2023-10-07 16:54:40    INFO    Created security group named: sg-06eb8aa51cf1fe2b1
2023-10-07 16:54:40    INFO    Created security group named: awseb-e-kkpfkd8uzj-stack-AWSEBSecurityGroup-13WDTESGTG7X9
2023-10-07 16:54:55    INFO    Created Auto Scaling launch configuration named: awseb-e-kkpfkd8uzj-stack-AWSEBAutoScalingLaunchConfiguration-8IeU6hpUHxnQ
2023-10-07 16:54:55    INFO    Created target group named: arn:aws:elasticloadbalancing:us-west-2:789502026025:targetgroup/awseb-AWSEB-PNCRNXIHUHB3/70ccfbe210d04665
2023-10-07 16:55:11    INFO    Created Auto Scaling group named: awseb-e-kkpfkd8uzj-stack-AWSEBAutoScalingGroup-2sxKhn8Scbrj
2023-10-07 16:55:11    INFO    Waiting for EC2 instances to launch. This may take a few minutes.
2023-10-07 16:55:26    INFO    Created Auto Scaling group policy named: arn:aws:autoscaling:us-west-2:789502026025:scalingPolicy:7d975a2a-9d0c-452b-b7dd-6679dc0805cf:autoScalingGroupName/awseb-e-kkpfkd8uzj-stack-AWSEBAutoScalingGroup-2sxKhn8Scbrj:policyName/awseb-e-kkpfkd8uzj-stack-AWSEBAutoScalingScaleUpPolicy-RI2sBcTT24X8
2023-10-07 16:55:26    INFO    Created Auto Scaling group policy named: arn:aws:autoscaling:us-west-2:789502026025:scalingPolicy:2738e3a1-c33c-49c1-afd8-3173c89c786c:autoScalingGroupName/awseb-e-kkpfkd8uzj-stack-AWSEBAutoScalingGroup-2sxKhn8Scbrj:policyName/awseb-e-kkpfkd8uzj-stack-AWSEBAutoScalingScaleDownPolicy-m0WrPhlAqyMP
2023-10-07 16:55:26    INFO    Created CloudWatch alarm named: awseb-e-kkpfkd8uzj-stack-AWSEBCloudwatchAlarmLow-oKeDQodmdo9w
2023-10-07 16:55:26    INFO    Created CloudWatch alarm named: awseb-e-kkpfkd8uzj-stack-AWSEBCloudwatchAlarmHigh-7wwXPn8rQe05
2023-10-07 16:56:46    INFO    Created load balancer named: arn:aws:elasticloadbalancing:us-west-2:789502026025:loadbalancer/app/awseb--AWSEB-ULBgjprjirzn/52697a10271ac8a0
2023-10-07 16:56:46    INFO    Created Load Balancer listener named: arn:aws:elasticloadbalancing:us-west-2:789502026025:listener/app/awseb--AWSEB-ULBgjprjirzn/52697a10271ac8a0/da400053530e3167
2023-10-07 16:57:02    INFO    Instance deployment completed successfully.
2023-10-07 16:58:07    INFO    Successfully launched environment: production
```

### Now Deploy the application

To deploy the application you need to run the following command:
```dotnetcli
$ eb deploy
```
The output will be:
```
$ eb deploy
Creating application version archive "app-231007_223703345967".
Uploading: [##################################################] 100% Done...
2023-10-07 17:09:08    INFO    Environment update is starting.      
2023-10-07 17:09:13    INFO    Deploying new version to instance(s).
2023-10-07 17:09:33    INFO    Instance deployment completed successfully.
2023-10-07 17:09:39    INFO    New application version was deployed to running EC2 instances.
2023-10-07 17:09:39    INFO    Environment update completed successfully.
```