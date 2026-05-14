---
title : "Serverless - Tích hợp Amazon OpenSearch với DynamoDB Stream"
date: 2024-01-01
weight : 1 
chapter : false
---
# Serverless - Tích hợp Amazon OpenSearch với DynamoDB Stream

#### Tổng quan

Trong bài số 6 của series này, chúng ta sẽ xây dựng tính năng tìm kiếm cho ứng dụng với Amazon OpenSearch tích hợp với DynamoDB stream.

Kiến trúc của ứng dụng web sẽ như sau:

![SeverlessExample](/images/serverless-diagram.png?featherlight=false&width=50pc)

Chúng ta sẽ tạo một mới 1 hàm Lambda để load streaming data từ DynamoDB với OpenSearch instance và 1 hàm để tìm kiếm tệp trong OpenSearch instance. Và chúng ta cũng ssẽ tạo một API dùng để tìm kiếm tương tác với hàm Lambda.

#### Amazon OpenSearch
Amazon OpenSearch Service là dịch vụ được quản lý giúp bạn dễ dàng thực hiện phân tích nhật ký tương tác, giám sát ứng dụng theo thời gian thực, tìm kiếm trang web, v.v. OpenSearch là một bộ phân tích và tìm kiếm phân tán, mã nguồn mở có nguồn gốc từ Elaticsearch. Amazon OpenSearch Service cung cấp các phiên bản OpenSearch mới nhất, hỗ trợ 19 phiên bản Elaticsearch (phiên bản 1.5 đến 7.10), cũng như khả năng trực quan hóa được cung cấp bởi OpenSearch Dashboards và Kibana (phiên bản 1.5 đến 7.10).

Amazon OpenSearch Service quản lý công việc liên quan đến thiết lập miền, từ việc cung cấp dung lượng cơ sở hạ tầng trong môi trường mạng mà bạn yêu cầu đến cài đặt phần mềm OpenSearch hoặc Elaticsearch. Sau khi miền của bạn đang chạy, Amazon OpenSearch Service sẽ tự động hóa các tác vụ quản trị phổ biến, chẳng hạn như thực hiện sao lưu, giám sát các phiên bản và vá lỗi phần mềm.

Các tính năng của Dịch vụ tìm kiếm mở của Amazon:
- **Scale**: Nhiều cấu hình CPU, bộ nhớ và dung lượng lưu trữ được gọi là các loại phiên bản, bao gồm các phiên bản Graviton tiết kiệm chi phí
- **Security**: Kiểm soát truy cập AWS Identity and Access Management (IAM), tích hợp dễ dàng với các nhóm bảo mật VPC và Amazon VPC, Mã hóa dữ liệu ở rest và mã hóa giữa các nút
- **Stability**: Nhiều vị trí địa lý cho tài nguyên của bạn, Multi-AZ, các nút chính chuyên dụng để giảm tải các nhiệm vụ quản lý cụm, ảnh chụp nhanh tự động để sao lưu và khôi phục miền OpenSearch Service.
- **Flexibility**: Hỗ trợ SQL để tích hợp với các ứng dụng kinh doanh thông minh (BI), gói tùy chỉnh để cải thiện kết quả tìm kiếm

- **Tích hợp với các dịch vụ phổ biến**: Tích hợp với Amazon CloudWatch để theo dõi số liệu miền của Dịch vụ tìm kiếm mở và đặt cảnh báo, với AWS CloudTrail để kiểm tra lệnh gọi API cấu hình tới các miền Dịch vụ OpenSearch, với Amazon S3, Amazon Kinesis và Amazon DynamoDB để tải dữ liệu truyền trực tuyến vào OpenSearch Service,...

#### DynamoDB Stream
DynamoDB Stream ghi lại chuỗi sửa đổi cấp mục theo thứ tự thời gian trong bất kỳ bảng DynamoDB nào và lưu trữ thông tin này trong nhật ký trong tối đa 24 giờ. Các ứng dụng có thể truy cập nhật ký này và xem các mục dữ liệu khi chúng xuất hiện trước và sau khi chúng được sửa đổi, trong thời gian gần như thực.

Một DynamoDB stream là một luồng thông tin được sắp xếp theo thứ tự về các thay đổi đối với các mục trong bảng DynamoDB. Khi bạn bật luồng trên bảng, DynamoDB sẽ ghi lại thông tin về mọi sửa đổi đối với các mục dữ liệu trong bảng. Bất cứ khi nào một ứng dụng tạo, cập nhật hoặc xóa các mục trong bảng, DynamoDB stream sẽ ghi một bản ghi luồng với các thuộc tính khóa chính của các mục đã được sửa đổi. Bản ghi luồng chứa thông tin về việc sửa đổi dữ liệu đối với một mục trong bảng DynamoDB.


#### Nội dung

1. [Chuẩn Bị](1-preparation/)
2. [Tạo API và Lambda Function](2-create-api-and-lambda-functions/)
3. [Tạo OpenSearch Instance](3-create-opensearch-instance/)
4. [Kiểm Tra Hoạt Động](4-test-operation/)
5. [Dọn Dẹp Tài Nguyên](5-cleanup)
