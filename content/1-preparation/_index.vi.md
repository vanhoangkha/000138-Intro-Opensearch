---
title : "Chuẩn Bị"
date: 2024-01-01
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
Trước khi thực hiện nội dung chính của workshop này, chúng ta cần thiết lập lại ứng dụng web bằng AWS SAM.
1. Tải source code dưới đây

{{%attachments title="Source code" pattern=".*\.(zip)$"/%}}

2. Chạy các câu lệnh dưới đây
```
sam build
sam deploy --guided
```

3. Nhập nội dung như sau:

- Stack Name []: `fcjdmsapp`
- AWS Region []: `ap-southeast-1`
- Confirm changes before deploy [Y/n]: `y`
- Allow SAM CLI IAM role creation [Y/n]: `y`
- Disable rollback [y/N]: `n`
- DocsList may not have authorization defined, Is this okay? [y/N]: `y`
- DocsUpload may not have authorization defined, Is this okay? [y/N]: `y`
- DocsDelete may not have authorization defined, Is this okay? [y/N]: `y`
- GeneralInforUpload may not have authorization defined, Is this okay? [y/N]: y
- GeneralInforGet may not have authorization defined, Is this okay? [y/N]: y
- Save arguments to configuration file [Y/n]: `y`
- Deploy this changeset? [y/N]: `y`

4. Mở bảng điều khiển của [AWS CloudFormation](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/)

5. Chọn **Stacks** ở menu bên trái và chọn stack **fcjdmsapp**. Sau đó chọn tab **Outputs**
6. Sao chép URL của API

![Preparation](/images/1-preparation/1-preparation-1.png?featherlight=false&width=90pc)

7. Nếu bạn chưa tải code của ứng dụng thì chạy command dưới đây:
```
git clone https://github.com/AWS-First-Cloud-Journey/FCJ-Serverless-DMS.git
cd FCJ-Serverless-Workshop
npm install
```
8. Mở tệp **src/constant.js**, dán API URL cho giá trị của **APP_API_URL**và lưu tệp.

![Preparation](/images/1-preparation/1-preparation-2.png?featherlight=false&width=90pc)

9. Chạy câu lệnh sau tại thư mục gốc của front-end project.
```
amplify init
```
- Nhập theo các thông tin dưới đây:

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

10. Chạy các câu lệnh sau để import xác thực người dùng và storage vào project:
```
amplify import auth
```
- Chọn **Cognito User Pool and Identity Pool** cho *What type of auth resource do you want to import?*

```
amplify import storage
```
- Chọn **S3 bucket - Content (Images, audio, video, etc.)** cho *Select from one of the below mentioned services*
- Chọn bucket mà bạn đã tạo từ các bước trên

- Chạy câu lệnh: `amplify push` để cập nhật tài nguyên cloud.

11. Chạy các lệnh dưới đây để build và tải lên S3 bucket
```
yarn build
aws s3 cp build s3://fcjdmswebstore --recursive
```