---
title : "Kiểm Tra Hoạt Động"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---
1. Trở lại với bảng điều khiển của CloudFormation, chọn stack **fcjdms**. Sau đó chọn tab **Outputs**
    - Ghi lại giá trị của CloudFront distribution

![UpdateSource](/images/4-test-operation/4-test-operation-1.png?featherlight=false&width=90pc)

2. Dán distribution vào một tab mới trong trình duyệt của bạn. Sau đó ấn **Sign up**

![UpdateSource](/images/4-test-operation/4-test-operation-2.png?featherlight=false&width=90pc)

3. Nhập thông tin đăng ký: user name, email của bạn và mật khẩu.
- Ấn **Sign up**

![AccessWeb](/images/4-test-operation/4-test-operation-3.png?featherlight=false&width=90pc)

4. Mở email của bạn để lấy code và nhập code vào ứng dụng. Sau đó ấn **Submit**
5. Nhập lại thông tin vừa đăng ký. 
    - Ấn **Sign in**

![AccessWeb](/images/4-test-operation/4-test-operation-4.png?featherlight=false&width=90pc)

6. Ấn **Upload**

![Login](/images/4-test-operation/4-test-operation-5.png?featherlight=false&width=90pc)

7. Ấn **Add files**
8. Chọn các tệp mà bạn muốn tải lên
    - Thêm tag cho các tệp hoặc bỏ qua
    - Ấn **Upload**

![AddData](/images/4-test-operation/4-test-operation-6.png?featherlight=false&width=90pc)

9. Sau khi upload các tệp xong, chọn **My Document** ở menu phía bên trái.

![AddData](/images/4-test-operation/4-test-operation-7.png?featherlight=false&width=90pc)

10. Nhập từ khoá tìm kiếm, bạn sẽ thấy kết quả hiện ra.

![AddData](/images/4-test-operation/4-test-operation-8.png?featherlight=false&width=90pc)

11. Chọn **Tag** và nhập từ khoá mới để tìm tệp theo tag

![AddData](/images/4-test-operation/4-test-operation-9.png?featherlight=false&width=90pc)

12. Chọn **Type** và nhập từ khoá mới để tìm tệp theo kiểu tệp.

![AddData](/images/4-test-operation/4-test-operation-10.png?featherlight=false&width=90pc)

Chúng ta đã hoàn thành workshop, đã biết cách tạo và tìm kiếm với Amazon OpenSearch Service. Workshop tiếp theo chúng ta sẽ sử dụng CodePipeline để triển khai ứng dụng.