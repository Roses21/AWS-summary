## 1. Tổng quan
- Elastic Beanstalk là dịch vụ Paas (Platform as a service) giúp nhanh chóng triển khai và quản lý các ứng dụng trên Đám mây AWS mà không cần phải tìm hiểu về cơ sở hạ tầng chạy các ứng dụng đó. Nhà phát triển chỉ cần tải ứng dụng lên và Elastic Beanstalk sẽ tự động xử lý việc triển khai, từ cung cấp công suất, cân bằng tải, tự động thay đổi quy mô đến giám sát trạng thái ứng dụng.
- Để sử dụng Elastic Beanstalk, bạn cần tạo một ứng dụng, tải phiên bản ứng dụng dưới dạng gói nguồn ứng dụng (ví dụ: tệp Java .war) lên Elastic Beanstalk, sau đó cung cấp một số thông tin về ứng dụng. Elastic Beanstalk tự động khởi chạy một môi trường, đồng thời tạo và đặt cấu hình các tài nguyên AWS cần thiết để chạy mã của bạn. Sau khi môi trường của bạn được khởi chạy, bạn có thể quản lý môi trường của mình và triển khai các phiên bản ứng dụng mới. Sơ đồ sau đây minh họa quy trình làm việc của Elastic Beanstalk:
  
  ![image](https://github.com/user-attachments/assets/45961620-c14f-4b9b-a7ce-469a5b6d0da2)

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
## 2. Các resource cần khi tạo Elastic Beanstalk
- EC2 instance - Được cấu hình để chạy các ứng dụng web trên nền tảng bạn chọn. Bao gồm application với version mà bạn đã lựa chọn và Apache hoặc NGINX như một reverse proxy để nhận request
- Instance security group - Giúp quản lý inbound, outbound của các instance
- Load balancer - Bộ cân bằng tải Elastic Load Balancing được định cấu hình để phân phối request đến ứng dụng.
- Load balancer security group - Giúp quản lý inbound, outbound của ELB
- Auto Scaling group - Được định cấu hình để thay thế một phiên bản nếu nó bị terminated hoặc không khả dụng.
- Amazon S3 bucket - Nơi lưu trữ mã nguồn, log và các artifacts được tạo ra khi sử dụng Elastic Beanstalk.
- Amazon CloudWatch alarms - Hai CloudWatch alarms giám sát tải trên các instance trong môi trường. Được kích hoạt nếu tải quá cao hoặc quá thấp. Khi một alarms được kích hoạt, Auto Scaling group sẽ scale up hoặc scale down.
- AWS CloudFormation stack - Sử dụng để khởi chạy các tài nguyên trong môi trường và apply các thay đổi cấu hình.
- Domain name - Một domain name route đến ứng dụng, ví dụ: subdomain.region.elasticbeanstalk.com.
- IAM user: phân quyền phù hợp để tương tác với AWS Elastic Beanstalk.
## 3. Bảo mật
- Theo mặc định, ứng dụng được công khai trên *myapp.elasticbeanstalk.com* để ai cũng truy cập được. Bạn có thể sử dụng Amazon VPC để cung cấp một phần riêng tư, cách ly của ứng dụng trên một mạng ảo do bạn xác lập. Có thể đặt mạng ảo này ở chế độ riêng tư bằng một số security group rules riêng, network ACLs và bảng định tuyến tùy chỉnh. Bạn cũng có thể dễ dàng kiểm soát việc lưu lượng nhận vào, chẳng hạn như SSH, có được phân phối đến máy chủ ứng dụng của bạn hay không bằng cách thay đổi thiết lập EC2 security group.
- IAM user:
  - Elastic Beanstalk cung cấp 2 policy templates: read-only access template và full-access template. Read-only access template cấp quyền truy cập đọc vào tài nguyên Elastic Beanstalk. Full-access template cấp quyền truy cập đầy đủ vào tất cả các hoạt động của Elastic Beanstalk cũng như các quyền để quản lý các tài nguyên phụ thuộc, chẳng hạn như Elastic Load Balancing, Auto Scaling và Amazon S3.
  - Có thể tạo policy tùy chỉnh.
## 4. Tính năng: Managed platform updates
- Để Elastic Beanstalk tự động quản lý các bản cập nhật của platform, bạn phải kích hoạt cập nhật nền tảng được quản lý trên Configuration tab của Elastic Beanstalk console hoặc dùng EB CLI hoặc API. Sau khi kích hoạt tính năng này, bạn có thể cấu hình cho phép những loại cập nhật nào và thời điểm thực hiện cập nhật.
- AWS Elastic Beanstalk có thể tự động thực hiện cập nhật nền tảng cho bản vá lỗi mới và các phiên bản của nền tảng phụ. Elastic Beanstalk sẽ không tự động thực hiện các cập nhật phiên bản nền tảng chính (ví dụ: từ Java 7 Tomcat 7 lên Java 8 Tomcat 8) vì chúng bao gồm những thay đổi không tương thích với quá khứ và yêu cầu phải kiểm thử bổ sung. Trong các trường hợp này, bạn phải khởi tạo cập nhật một cách thủ công.
- Cách AWS Elastic Beanstalk có thể phân biệt giữa các bản phát hành phiên bản “chính,” “phụ,” và “vá lỗi”:

  Platform AWS Elastic Beanstalk được đánh số phiên bản theo cấu trúc sau: MAJOR.MINOR.PATCH (ví dụ: 2.0.0). Mỗi phần được tăng dần như sau:

  - Phiên bản MAJOR khi có những thay đổi không tương thích.
  - Phiên bản MINOR khi bổ sung thêm tính năng theo cách tương thích với version cũ.
  - Phiên bản PATCH khi khắc phục sự cố tương thích với version cũ.
- Ứng dụng của bạn sẽ vẫn sẵn sàng trong khoảng thời gian bảo trì và người sử dụng ứng dụng không bị ảnh hưởng gì từ việc cập nhật.
- Không tính thêm phí khi sử dụng tính năng cập nhật nền tảng được quản lý. Bạn chỉ cần trả phí đối với những phiên bản EC2 bổ sung cần thiết để thực hiện cập nhật trong thời gian cập nhật.
- Khoảng thời gian bảo trì mặc định là 2 giờ hàng tuần, Elastic Beanstalk sẽ khởi tạo cập nhật nền tảng nếu chức năng cập nhật nền tảng được quản lý được bật và phiên bản mới của nền tảng đã sẵn sàng.
## 5. Billing
Không tính thêm phí khi sử dụng AWS Elastic Beanstalk – bạn chỉ phải trả phí cho những tài nguyên AWS được sử dụng trên thực tế để lưu trữ và chạy ứng dụng của mình.
## 6. Thực hành

## Tham khảo
https://aws.amazon.com/elasticbeanstalk/faqs/?nc1=h_ls

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html

https://www.youtube.com/playlist?list=PL4NoNM0L1m72JODh4efPGC-XhAJ9_uEJl
