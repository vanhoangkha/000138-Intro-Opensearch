---
title : "Preparation"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
Before we get to the main content of this workshop, we need to reset the web application.
1. Download the below source code

{{%attachments title="Source code" pattern=".*\.(zip)$"/%}}

2. Run the below commands
```
sam build
sam deploy --guided
```

3. Enter the following content:

- Stack Name []: `fcjdmsapp`
- AWS Region []: `ap-southeast-1`
- Confirm changes before deploy [Y/n]: y
- Allow SAM CLI IAM role creation [Y/n]: y
- Disable rollback [y/N]: n
- DocsList may not have authorization defined, Is this okay? [y/N]: y
- DocsUpload may not have authorization defined, Is this okay? [y/N]: y
- DocsDelete may not have authorization defined, Is this okay? [y/N]: y
- GeneralInforUpload may not have authorization defined, Is this okay? [y/N]: y
- GeneralInforGet may not have authorization defined, Is this okay? [y/N]: y
- Save arguments to configuration file [Y/n]: `y`
- Deploy this changeset? [y/N]: `y`

4. Open [AWS CloudFormation console](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/)


5. Select **Stacks** on the left menu and select **fcjdmsapp** stack. Then select the **Outputs** tab
6. Copy the API URL

![Preparation](/images/1-preparation/1-preparation-1.png?featherlight=false&width=90pc)

7. If you have not downloaded the application code, run the command below:
```
git clone https://github.com/AWS-First-Cloud-Journey/FCJ-Serverless-Workshop.git
cd FCJ-Serverless-Workshop
npm install
```
8. Open the **src/constant.js** file, paste the API URL for the value of **APP_API_URL** and save the file.

![Preparation](/images/1-preparation/1-preparation-2.png?featherlight=false&width=90pc)

9. Run the following command at the root of the front-end project.
```
amplify init
```
- Entering follow the below information:

    ? Enter a name for the project `fcjdms`\
    The following configuration will be applied:

    Project information\
    | Name: fcjdms\
    | Environment: dev\
    | Default editor: Visual Studio Code\
    | App type: javascript\
    | Javascript framework: react\
    | Source Directory Path: src\
    | Distribution Directory Path: build\
    | Build Command: npm run-script build\
    | Start Command: npm run-script start

    ? Initialize the project with the above configuration? `Yes`\
    Using default provider  awscloudformation\
    ? Select the authentication method you want to use: *AWS profile*

    For more information on AWS Profiles, see:\
    https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html

    ? Please choose the profile you want to use *default*\
    ? Help improve Amplify CLI by sharing non sensitive configurations on failures (y/N) › `No`

10. Run the following commands to import user authentication and storage into the project:
```
amplify import auth
```
- Select **Cognito User Pool and Identity Pool** for *What type of auth resource do you want to import?*

```
amplify import storage
```
- Select **S3 bucket - Content (Images, audio, video, etc.)** for *Select from one of the below mentioned services*
- Select the bucket you created from the above steps

- Run the command: `amplify push` to update cloud resources

11. Run the below command to build and upload to S3 bucket
```
yarn build
aws s3 cp build s3://fcjdmswebstore --recursive
```