---
title : "Create Search API"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2. </b> "
---
In this step, we will create an interactive API with a lambda function for document search by user id, keyword, and attribute.

1. Back to the AWS CloudFormation console. Select the **Resources** tab then click the ID of **DocApi**.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-1.png?featherlight=false&width=90pc)

2. Create a new resource:
- Select **/{id}**
- Click **Actions**, then select **Create Resource**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-2.png?featherlight=false&width=90pc)

3. Enter resource name: `search`. Then click **Create Resource**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-3.png?featherlight=false&width=90pc)

4. Next, click **Actions** and select **Create Method**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-4.png?featherlight=false&width=90pc)

5. Select **GET** method and click **✓** symbol.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-5.png?featherlight=false&width=90pc)

6. The **Integration type**, select **Lambda function**.
- Check to **Use Lambda Proxy integration**.
- Enter function name: `search_docs`.
- Click **Save**.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-6.png?featherlight=false&width=90pc)

7. Click **OK**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-7.png?featherlight=false&width=90pc)

8. Select **Method Request**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-8.png?featherlight=false&width=90pc)

9. Expand **URL Query String Parameters** section and click **Add query string** to add a parameter for method

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-9.png?featherlight=false&width=90pc)

10. Select `key` and click **✓** symbol.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-10.png?featherlight=false&width=90pc)

11. Click **Add query string**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-11.png?featherlight=false&width=90pc)

12. Select `field` and click **✓** symbol.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-12.png?featherlight=false&width=90pc)

13. Select **/search** and click **Actions**. Then select  **Enable CORS**.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-13.png?featherlight=false&width=90pc)

13. Click **Enable CORS and replace existing CORS headers**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-14.png?featherlight=false&width=90pc)

14. Click **Yes, replace existing values**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-15.png?featherlight=false&width=90pc)

15. Next, click **Actions** and select **Deploy API**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-16.png?featherlight=false&width=90pc)

16. Select **dev** stage and click **Deploy**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-17.png?featherlight=false&width=90pc)

You have finished creating the API and integrating it with the lambda function. In the next section, we will create an OpenSearch domain.
