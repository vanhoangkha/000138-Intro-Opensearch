---
title : "Tạo API Tìm Kiếm"
date: 2024-01-01
weight : 2
chapter : false
pre : " <b> 2.2. </b> "
---
Trong bước này chúng ta sẽ tạo một API tương tác với hàm lambda để sử dụng cho tính năng tìm kiếm tài liệu theo user id, keyword và thuộc tính.

1. Quay lại với bảng điều khiển của AWS CloudFormation. Chọn tab **Resources** sau đó ấn vào ID của **DocApi**.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-1.png?featherlight=false&width=90pc)

2. Tạo một resource mới:
- Chọn **/{id}**
- Ấn **Actions**, sau đó chọn **Create Resource**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-2.png?featherlight=false&width=90pc)

3. Nhập tên cho resource: `search`. Sau đó ấn **Create Resource**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-3.png?featherlight=false&width=90pc)

4. Tiếp theo ấn **Actions** và chọn **Create Method**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-4.png?featherlight=false&width=90pc)

5. Chọn method **GET** và ấn biểu tượng **✓**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-5.png?featherlight=false&width=90pc)

6. Với **Integration type**, chọn **Lambda function**.
- Tích vào **Use Lambda Proxy integration**.
- Nhập tên function: `search_docs`.
- Ấn **Save**.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-6.png?featherlight=false&width=90pc)

7. Ấn **OK**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-7.png?featherlight=false&width=90pc)

8. Chọn **Method Request**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-8.png?featherlight=false&width=90pc)

9. Mở rộng phần **URL Query String Parameters** và ấn **Add query string** để thêm parameter cho method

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-9.png?featherlight=false&width=90pc)

10. Nhập `key` và ấn biểu tượng **✓**.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-10.png?featherlight=false&width=90pc)

11. Ấn **Add query string**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-11.png?featherlight=false&width=90pc)

12. Nhập `field` và ấn biểu tượng **✓**.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-12.png?featherlight=false&width=90pc)

13. Chọn **/search** và ấn **Actions**. Tiếp theo chọn **Enable CORS**.

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-13.png?featherlight=false&width=90pc)

13. Ấn **Enable CORS and replace existing CORS headers**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-14.png?featherlight=false&width=90pc)

14. Ấn **Yes, replace existing values**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-15.png?featherlight=false&width=90pc)

15. Tiếp theo chúng ta ấn **Actions** và chọn **Deploy API**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-16.png?featherlight=false&width=90pc)

16. Chọn stage **dev** và ấn **Deploy**

![CreateAPI](/images/2-create-api-and-lambda-functions/2-2-create-api-17.png?featherlight=false&width=90pc)

Bạn đã hoàn thành việc tạo API và tích hợp với hàm lambda. Trong phần tiếp chúng ta sẽ tạo OpenSearch domain.

