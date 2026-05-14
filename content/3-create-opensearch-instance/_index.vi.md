---
title : "Tạo OpenSearch Instance"
date: 2024-01-01
weight : 3
chapter : false
pre : " <b> 3. </b> "
---
1. Mở bảng điều khiển của [Amazon OpenSearch Service](https://ap-southeast-1.console.aws.amazon.com/aos/home?region=ap-southeast-1#opensearch/dashboard)

2. Ấn **Create domain**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-1.png?featherlight=false&width=90pc)

3. Nhập tên cho domain: `fcjdms`
    - Chọn kiểu triển khai là **Development and testing**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-2.png?featherlight=false&width=90pc)

4. Tại phần **Data nodes**:
    - Chọn 1 availability zone
    - Chọn **t3.small.search** cho kiểu instance
    - Nhập `2` là số lượng nodes
    - Chọn **General Purpose (SSD) - gp2** cho **kiểu EC2 volume**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-3.png?featherlight=false&width=90pc)

5. Mở rộng phần **Dedicated master nodes** và tích vào **Enbale dedicated master nodes**
    - Chọn kiểu instance là **t3.small.search**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-4.png?featherlight=false&width=90pc)

6. Chọn **Public access** cho **Network**
    - Chọn **Create master user** 
    - Nhập username, password và confirm password

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-5.png?featherlight=false&width=90pc)

7. Tại mục **Access policy**, chọn **Only use fine-grained access control**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-6.png?featherlight=false&width=90pc)

8. Kéo xuống cuối và ấn **Create**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-7.png?featherlight=false&width=90pc)

9. Đợi một vài phút để domain khởi tạo

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-8.png?featherlight=false&width=90pc)

10. Sau khi domain đã sẵn sàng, ghi lại domain endpoint và ấn vào OpenSearch Dashboards URL.

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-9.png?featherlight=false&width=90pc)

11. Mở bảng điều khiển của AWS Lambda. Chọn hàm **search_docs**
    - Chọn tab **Configuration**
    - Chọn **Environment variables** ở menu phía bên trái
    - Ấn **Edit**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-10.png?featherlight=false&width=90pc)

12. Ấn **Add environment variable**
    - Nhập `SEARCH_DOMAIN` cho Key
    - Dán OpenSearch domain endpoint vào ô Value và xoá **https://**
    - Ấn **Save**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-11.png?featherlight=false&width=90pc)

13. Lặp lại bước 11 và 12 cho hàm **load_stream**
14. Quay lại với tab của OpenSearch Dashboards, nhập thông tin user mà bạn đã tạo. Sau đó ấn **Log in**.

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-12.png?featherlight=false&width=90pc)

15. Mở menu ở góc trên bên trái và chọn **Security**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-13.png?featherlight=false&width=90pc)

16. Chọn **Roles** ở menu phía bên trái 
    - Chọn **all_access**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-14.png?featherlight=false&width=90pc)

17. Chọn tab **Mapped users** và ấn **Manage mapping**.

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-15.png?featherlight=false&width=90pc)

18. Ở phần **Backend roles**:
    - Nhập Role ARN của role mà hàm **search_docs** đang thực thi.
    - Ấn **Add another backend role**
    - Nhập Role ARN của role mà hàm **load_stream** đang thực thi.
    - Ấn **Map**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-16.png?featherlight=false&width=90pc)

19. Bạn đã hoàn thành việc map role của các hàm Lambda cho người dùng.

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-17.png?featherlight=false&width=90pc)
