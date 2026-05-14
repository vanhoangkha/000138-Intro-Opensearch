---
title : "Tạo Lambda Function"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 2.1. </b> "
---
Tải source code dưới đây:

{{%attachments title="Source code" pattern=".*\.(zip)$"/%}}

1. Mở bảng điều khiển của [AWS Lambda](https://ap-southeast-1.console.aws.amazon.com/lambda/home?region=ap-southeast-1#/functions)

2. Ấn **Create function**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-1.png?featherlight=false&width=90pc)

3. Nhập tên cho function: `search_docs`
- Chọn **Runtime** là **Python 3.9**
- Ấn **Create function**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-2.png?featherlight=false&width=90pc)

4. Ấn **Upload from**, sau đó chọn **.zip file**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-3.png?featherlight=false&width=90pc)

5. Ấn **Upload** và chọn tệp **search_docs.zip** bạn vừa tải về. Tiếp theo ấn **Save**.

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-4.png?featherlight=false&width=90pc)

6. Kéo xuống cuối trang, tại mục **Runtime settings** ấn **Edit**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-5.png?featherlight=false&width=90pc)

7. Thay **lambda_function** bằng `search_docs`, sau đó ấn **Save**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-6.png?featherlight=false&width=90pc)

8. Tiếp theo chúng ta sẽ cập nhật quyền cho Lambda có thể truy cập vào OpenSearch domain.
- Chọn tab **Configuration** và chọn **Permission** ở menu phía bên trái
- Chọn role mà function đang thực hiện.

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-7.png?featherlight=false&width=90pc)

9. Mở rộng policy và ấn **Edit**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-8.png?featherlight=false&width=90pc)

10. Sao chép script dưới đây và dán vào tab **JSON**. Sau đó ấn **Review policy**
```json
,
        {
            "Effect": "Allow",
            "Action": "es:*",
            "Resource": "*"
        }
```

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-9.png?featherlight=false&width=90pc)

11. Ấn **Save changes**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-10.png?featherlight=false&width=90pc)

12. Tương tự chúng ta sẽ tạo một function để load streaming data từ DynamoDB vào OpenSearch instance.
13. Trở lại với bảng điều khiển của AWS Lambda, ấn **Create function**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-11.png?featherlight=false&width=90pc)

14. Nhập tên cho function: `load_stream`
- Chọn **Runtime** là **Python 3.9**
- Ấn **Create function**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-12.png?featherlight=false&width=90pc)

15. Ấn **Upload from**, sau đó chọn **.zip file**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-13.png?featherlight=false&width=90pc)

16. Ấn **Upload** và chọn tệp **load_stream_data.zip** bạn vừa tải về. Tiếp theo ấn **Save**.

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-14.png?featherlight=false&width=90pc)

17. Kéo xuống cuối trang, tại mục **Runtime settings** ấn **Edit**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-15.png?featherlight=false&width=90pc)

18. Thay **lambda_function** bằng `load_stream_data`, sau đó ấn **Save**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-16.png?featherlight=false&width=90pc)

19. Tiếp theo chúng ta sẽ cập nhật quyền cho Lambda có thể truy cập vào OpenSearch domain và DynamoDB.
- Chọn tab **Configuration** và chọn **Permission** ở menu phía bên trái
- Chọn role mà function đang thực hiện.

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-17.png?featherlight=false&width=90pc)

20. Ấn **Add permissions** và chọn **Attach policies**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-18.png?featherlight=false&width=90pc)

21. Nhập tên policy `AmazonOpenSearchServiceFullAccess` và chọn policy đó


![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-19.png?featherlight=false&width=90pc)

22. Nhập tên policy `AWSLambdaDynamoDBExecutionRole` và chọn policy đó. Sau đó ấn **Add permissions**

![CreateSQS](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-20.png?featherlight=false&width=90pc)

23. Mở bảng điều khiển của [Amazon DynamoDB](https://ap-southeast-1.console.aws.amazon.com/dynamodbv2/home?region=ap-southeast-1#service)
24. Chọn **Tables | Update settings** ở menu phía bên trái, sau đó chọn bảng **Documents**
25. Ấn chọn tab **Exports and streams**

![CreateStream](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-21.png?featherlight=false&width=90pc)

26. Kéo xuống cuối, tại mục **DynamoDB stream details**, ấn **Create trigger**

![CreateStream](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-22.png?featherlight=false&width=90pc)

23. Nhập tên hàm Lambda: `load_stream`
    - Nhập `1` cho batch size
    - Ấn **Create trigger**
    
![CreateStream](/images/2-create-api-and-lambda-functions/2-1-create-lambda-function-23.png?featherlight=false&width=90pc)

