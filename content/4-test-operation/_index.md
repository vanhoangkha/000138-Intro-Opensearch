---
title : "Test Web Operation"
date: 2024-01-01
weight : 4
chapter : false
pre : " <b> 4. </b> "
---
1. Back in the CloudFormation dashboard, select the **fcjdms** stack. Then select the **Outputs** tab
    - Note down CloudFront distribution value

![UpdateSource](/images/4-test-operation/4-test-operation-1.png?featherlight=false&width=90pc)

2. Paste distribution to a new tab in your browser. Then click **Sign up**

![UpdateSource](/images/4-test-operation/4-test-operation-2.png?featherlight=false&width=90pc)

3. Enter the registration information: user name, email and password.
- Click **Sign up**

![AccessWeb](/images/4-test-operation/4-test-operation-3.png?featherlight=false&width=90pc)

4. Open your email to get the code and enter the code into the app. Then click **Submit**
5. Re-enter the registered information. 
    - Click **Sign in**

![AccessWeb](/images/4-test-operation/4-test-operation-4.png?featherlight=false&width=90pc)

6. Click **Upload**

![Login](/images/4-test-operation/4-test-operation-5.png?featherlight=false&width=90pc)

7. Click **Add files**
8. Select the files you want to upload
    - Add tags to files or ignore
    - Click **Upload**

![AddData](/images/4-test-operation/4-test-operation-6.png?featherlight=false&width=90pc)

9. After uploading the files, select **My Document** on the left menu.

![AddData](/images/4-test-operation/4-test-operation-7.png?featherlight=false&width=90pc)

10. Enter the search keyword, and you will see the results appear.

![AddData](/images/4-test-operation/4-test-operation-8.png?featherlight=false&width=90pc)

11. Select **Tag** and enter a new keyword to search file by tag.

![AddData](/images/4-test-operation/4-test-operation-9.png?featherlight=false&width=90pc)

12. Select **Type** and enter a new keyword to search file by file type.

![AddData](/images/4-test-operation/4-test-operation-10.png?featherlight=false&width=90pc)

We finished the workshop, already know how to create and search with Amazon OpenSearch Service. The next workshop we will use CodePipeline to deploy the application.