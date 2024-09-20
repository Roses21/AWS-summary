## 1. Tổng quan
- Elastic Beanstalk là dịch vụ giúp nhanh chóng triển khai và quản lý các ứng dụng trên Đám mây AWS mà không cần phải tìm hiểu về cơ sở hạ tầng chạy các ứng dụng đó. Nhà phát triển chỉ cần tải ứng dụng lên và Elastic Beanstalk sẽ tự động xử lý việc triển khai, từ cung cấp công suất, cân bằng tải, tự động thay đổi quy mô đến giám sát trạng thái ứng dụng.
- Elastic Beanstalk hỗ trợ các ứng dụng được phát triển bằng Go, Java, .NET, Node.js, PHP, Python và Ruby.
- Elastic Beanstalk cũng hỗ trợ nền tảng Docker. Với Docker container, bạn có thể chọn ngôn ngữ lập trình và các phần phụ thuộc ứng dụng của riêng mình thậm chí có thể dùng các platform mà Elastic Beanstalk có thể không hỗ trợ.
- Những thành phần của ứng dụng bạn có thể kiểm soát:
  - Chọn hệ điều hành phù hợp với yêu cầu ứng dụng của bạn (ví dụ: Amazon Linux hoặc Windows Server 2016)
  - Chọn từ một số Amazon EC2 instance, bao gồm On-Demand, Reserved instances, and Spot instances.
  - Chọn từ một số tùy chọn cơ sở dữ liệu và dung lượng lưu trữ hiện có
  - Cho phép truy cập vào các phiên bản Amazon EC2 để khắc phục sự cố tức thì và trực tiếp
  - Nhanh chóng cải thiện độ tin cậy của ứng dụng bằng cách chạy trên nhiều AZ
  - Tăng cường bảo mật cho ứng dụng bằng cách kích hoạt giao thức HTTPS trên bộ cân bằng tải
  - Truy cập tính năng giám sát Amazon CloudWatch tích hợp sẵn và nhận thông báo về trạng thái ứng dụng cũng như các sự kiện quan trọng khác
  - Điều chỉnh thiết lập máy chủ ứng dụng (ví dụ: thiết lập JVM) và chuyển các biến môi trường
  - Chạy các thành phần khác của ứng dụng, chẳng hạn như dịch vụ lưu vào bộ nhớ đệm, song song trên Amazon EC2
  - Truy cập tệp nhật ký mà không cần đăng nhập vào máy chủ ứng dụng
- Những tài nguyên Đám mây được cung cấp để chạy ứng dụng trên AWS Elastic Beanstalk:
  - Amazon EC2, Amazon RDS, Elastic Load Balancing, Auto Scaling, Amazon S3 và Amazon SNS => tạo ra môi trường chạy ứng dụng.
  - Phiên bản hiện tại của AWS Elastic Beanstalk sử dụng Amazon Linux AMI hoặc Windows Server 2019 R2 AMI.
## 2. Cơ sở dữ liệu và dung lượng lưu trữ
## 3. Bảo mật
## 4. 
## 5. Billing
Không tính thêm phí khi sử dụng AWS Elastic Beanstalk – bạn chỉ phải trả phí cho những tài nguyên AWS được sử dụng trên thực tế để lưu trữ và chạy ứng dụng của mình.
