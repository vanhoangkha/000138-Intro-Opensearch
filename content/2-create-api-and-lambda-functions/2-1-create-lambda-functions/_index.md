---
title : "Create Lambda Functions"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 2.1. </b> "
---
Download the source code below:

{{%attachments title="Source code" pattern=".*\.(zip)$"/%}}

1. Open [AWS Lambda console](https://ap-southeast-1.console.aws.amazon.com/lambda/home?region=ap-southeast-1#/functions)

2. Click **Create function**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-1.png?featherlight=false&width=90pc)

3. Enter function name: `search_docs`
- Selecting **Runtime** is **Python 3.9**
- Click **Create function**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-2.png?featherlight=false&width=90pc)

4. Click **Upload from**, then select **.zip file**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-3.png?featherlight=false&width=90pc)

5. Click **Upload** and choose **search_docs.zip** file you just downloaded. Next click **Save**.

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-4.png?featherlight=false&width=90pc)

6. Scroll down to bottom, in **Runtime settings** section, click **Edit**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-5.png?featherlight=false&width=90pc)

7. Repalce **lambda_function** with `search_docs`, then click **Save**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-6.png?featherlight=false&width=90pc)

8. Next, we will update the permissions for Lambda to be able to access the OpenSearch domain.
- Select **Configuration** tab and select **Permission** on the left menu.
- Select the execution role of this function

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-7.png?featherlight=false&width=90pc)

9. Expand policy and click **Edit**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-8.png?featherlight=false&width=90pc)

10. Copy the below script and paste to **JSON** tab. Then click **Review policy**
```json
,
        {
            "Effect": "Allow",
            "Action": "es:*",
            "Resource": "*"
        }
```

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-9.png?featherlight=false&width=90pc)

11. Click **Save changes**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-10.png?featherlight=false&width=90pc)

12. Similarly, we will create a function to load streaming data from the DynamoDB into the OpenSearch instance.
13. Back to AWS Lambda console, click **Create function**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-11.png?featherlight=false&width=90pc)

14. Enter the function name: `load_stream`
- Selecting **Runtime** is **Python 3.9**
- Click **Create function**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-12.png?featherlight=false&width=90pc)

15. Click **Upload from**, then select **.zip file**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-13.png?featherlight=false&width=90pc)

16. Click **Upload** and choose **search_docs.zip** file you just downloaded. Next click **Save**.

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-14.png?featherlight=false&width=90pc)

17. Scroll down to bottom, in **Runtime settings** section, click **Edit**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-15.png?featherlight=false&width=90pc)

18. Repalce **lambda_function** with `load_stream_data`, then click **Save**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-16.png?featherlight=false&width=90pc)

19. Next, we will update the permissions for Lambda to be able to access the OpenSearch domain and DynamoDB.
- Select **Configuration** tab and select **Permission** on the left menu.
- Select the execution role of this function

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-17.png?featherlight=false&width=90pc)

20. Click **Add permissions** and select **Attach policies**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-18.png?featherlight=false&width=90pc)

21. Enter `AmazonOpenSearchServiceFullAccess` and select that policy


![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-19.png?featherlight=false&width=90pc)

22. Enter `AWSLambdaDynamoDBExecutionRole` and select that policy. Then click **Add permissions**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-20.png?featherlight=false&width=90pc)

23. Open [Amazon DynamoDB console](https://ap-southeast-1.console.aws.amazon.com/dynamodbv2/home?region=ap-southeast-1#service)
24. Select **Tables | Update settings** on the left menu, then select **Documents** table
25. Click **Exports and streams** tab

![CreateStream](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-21.png?featherlight=false&width=90pc)

26. Scroll down to bottom, in **DynamoDB stream details** section, click **Create trigger**

![CreateStream](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-22.png?featherlight=false&width=90pc)

23. Enter the lambda function: `load_stream`
    - Enter `1` for batch size
    - Click **Create trigger**
    
![CreateStream](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-23.png?featherlight=false&width=90pc)