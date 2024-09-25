# 1. AWS storage data protection services introduction
- Sự tăng trưởng nhanh chóng của dữ liệu trên toàn thế giới đã khiến việc quản lý bảo vệ dữ liệu trở nên khó khăn hơn bao giờ hết. Với các phương pháp sao lưu truyền thống, chẳng hạn như thư viện băng từ và các trang web, bị tụt lại phía sau, nhiều tổ chức sẵn sàng mở rộng mục tiêu sao lưu lên đám mây.
- AWS cung cấp các dịch vụ lưu trữ, phương thức truyền dữ liệu và tùy chọn kết nối mạng để xây dựng các giải pháp bảo vệ dữ liệu của bạn một cách bền vững, bảo mật và chi phí phù hợp.
## Data protection methods
- AWS cung cấp ba loại dịch vụ bảo vệ dữ liệu để đáp ứng các yêu cầu về recovery point objectives (RPO), recovery time objectives (RTO), và compliance.
- Mỗi dịch vụ lưu trữ chính bao gồm một cơ chế bảo vệ dữ liệu, cho dù đó là ảnh chụp nhanh, sao chép dữ liệu hay sao lưu gốc, để giúp bảo vệ dữ liệu của bạn.
### Data backup
- Sao lưu dữ liệu là phương pháp kết hợp các giải pháp sao lưu với cài đặt có thể quản lý để tạo bản sao dữ liệu hiệu quả và tiết kiệm chi phí. Dữ liệu có thể được sao chép đến một hoặc nhiều vị trí, ở số lần lặp lại định trước và ở các dung lượng khác nhau. Bạn có thể thiết lập thao tác sao lưu dữ liệu linh hoạt bằng kiến ​​trúc của riêng mình, sử dụng các dịch vụ lưu trữ sao lưu có sẵn hoặc kết hợp cả hai. 
- Sao lưu dữ liệu bao gồm việc sao chép dữ liệu từ vị trí chính sang vị trí phụ để bảo vệ dữ liệu trong trường hợp xảy ra thảm họa, tai nạn hoặc hành động độc hại.
- Đối với các tổ chức hiện đại, dữ liệu của họ rất cần thiết cho hoạt động liên tục. Mất dữ liệu có thể gây ra thiệt hại không thể khắc phục và làm gián đoạn các hoạt động đang diễn ra.
- AWS Backup cung cấp dịch vụ sao lưu trên Đám mây AWS. Dữ liệu của bạn được bảo vệ trong các nhóm Amazon Simple Storage Service (Amazon S3) do AWS quản lý với độ bền 99,999999999 phần trăm (11 số).
### Snapshots
- Snapshots là bản sao tăng dần, theo thời gian của dữ liệu được lưu trữ của bạn.
- Snapshots giúp bạn bảo vệ dữ liệu của mình về mặt địa lý và đạt được tính liên tục trong kinh doanh.
- Snapshots thường được tích hợp trong một ứng dụng hoặc dịch vụ lưu trữ. Với sự tích hợp chặt chẽ này, snapshots có thể hoạt động mà không làm ảnh hưởng đến dịch vụ chính. Snapshots là bản gốc và được tích hợp chặt chẽ với các dịch vụ lưu trữ AWS hỗ trợ chúng. Dữ liệu ảnh chụp nhanh của bạn được bảo vệ trong nhóm S3 do AWS quản lý với độ bền 99,999999999 phần trăm (11 giây)
### Disaster recovery services
AWS Elastic Disaster Recovery lưu giữ bản sao cập nhật của các máy chủ ứng dụng tại chỗ của bạn để sẵn sàng chuyển đổi dự phòng.
# 2. AWS Backup
## 2.1. Introduction
- AWS Backup is a fully managed data protection service that makes it convenient to centralize and automate across AWS services, in the cloud, and on premises.
- Bạn có thể sử dụng AWS Backup cùng với AWS Organizations để triển khai tập trung các chính sách bảo vệ dữ liệu. Bạn có thể sử dụng các chính sách này để đặt cấu hình, quản lý và quản lý hoạt động sao lưu của mình trên các tài khoản và tài nguyên AWS của tổ chức.
- AWS Backup giải quyết những thách thức khi backup trên môi trường on-primises:
  - Complexity: AWS Backup cung cấp một dịch vụ ứng dụng sao lưu duy nhất hỗ trợ nhiều dịch vụ AWS. Bạn không cần quản lý tập lệnh tùy chỉnh cho các dịch vụ khác nhau. Việc tích hợp với IAM, Amazon CloudWatch và AWS CloudTrail cung cấp khả năng giám sát, kiểm tra và quản lý quyền truy cập mà tổ chức của bạn cần.
  - Compliance: Có các tùy chọn và chính sách tích hợp để đáp ứng các yêu cầu tuân thủ của bạn, bao gồm nhật ký và báo cáo kiểm tra thuận tiện. Tất cả quyền truy cập IAM đều được ghi lại và bạn có thể tạo chính sách IAM để giới hạn quyền truy cập dựa trên người dùng, nhóm hoặc vai trò.
  - Cost: AWS Backup helps reduce management and support costs spent on custom applications or services. You pay for the backup data that you have stored in cost-effective storage.
- AWS resources supported by AWS Backup:

  ![image](https://github.com/user-attachments/assets/d6c3182d-ad0a-4669-8c13-512b455ec0e0)

## 2.2. AWS Backup Features
- Foundational features:
  - Centralized backup management: console, APIs, CLI.
  - Policy-based backup
  - Tag-based backup policies: organize and classify your AWS resources, helps you quickly apply a backup plan to a group of AWS resources.
  - Automated backup scheduling
  - Automated retention management
  - Lifecycle management policies
  - Incremental backups: Bản sao lưu đầu tiên của tài nguyên AWS sẽ sao lưu bản sao đầy đủ dữ liệu của bạn. Đối với mỗi bản sao lưu gia tăng liên tiếp, chỉ những thay đổi đối với tài nguyên AWS của bạn mới được sao lưu.
  - Cross-Region backup
- Technical features:
  - Cross-account management and backup: Tính năng sao lưu nhiều tài khoản cung cấp cho bạn lớp bảo vệ bổ sung nếu tài khoản nguồn gặp phải sự gián đoạn do vô tình hoặc cố tình xóa, thiên tai hoặc phần mềm tống tiền.
  - Full AWS Backup management
  - Backup activity monitoring: AWS Backup tích hợp với CloudTrail => cung cấp cái nhìn tổng hợp về nhật ký hoạt động sao lưu giúp kiểm tra nội dung và cách thức tài nguyên của bạn được sao lưu nhanh chóng và thuận tiện. AWS Backup + Dịch vụ thông báo đơn giản của Amazon (Amazon SNS) => tự động thông báo cho bạn về hoạt động sao lưu, chẳng hạn như khi sao lưu thành công hoặc khi quá trình khôi phục được bắt đầu.
  - Secure data: cung cấp các chính sách truy cập dựa trên tài nguyên cho kho dự phòng của bạn để xác định ai có quyền truy cập vào các bản sao lưu của bạn.
  - Compliance: FedRAMP High; General Data Protection Regulation (GDPR); SOC 1, 2, and 3; payment card industry; and Health Insurance Portability and Accountability Act of 1996 (HIPAA).
  - Auditing and reporting with AWS Backup Audit Manager: help streamline data governance and compliance management.
- Pricing basics: Giá lưu trữ Sao lưu AWS dựa trên dung lượng lưu trữ mà dữ liệu sao lưu của bạn tiêu thụ. Đối với bản sao lưu đầu tiên của tài nguyên AWS, bản sao đầy đủ dữ liệu của bạn sẽ được lưu. Đối với mỗi bản sao lưu gia tăng, chỉ phần tài nguyên AWS đã thay đổi của bạn mới được lưu. Giá cả khác nhau tùy theo dịch vụ được sao lưu và Khu vực.
## 2.3. AWS Backup Architecture and Use Cases
- AWS Backup architecture:

  ![image](https://github.com/user-attachments/assets/e28c5122-cb13-444f-a134-20800b866c3d)

  AWS Backup vault:

  ![image](https://github.com/user-attachments/assets/098df5d6-c1cd-4b55-87bc-5767dc927c76)

- Use cases:
  - AWS Backup and cloud-centered protection: Using AWS Backup with cross-account management (CAM), cross-region copy (CRC), and cross-account backup (CAB), you can expand what you can do with your workloads. 
  - AWS Backup and DR: DR có thể là một cách nhanh chóng nhưng tốn kém để khôi phục hệ thống và dữ liệu của bạn. Do tính chất dư thừa của DR nên thường đòi hỏi chi phí cao hơn so với việc khôi phục sao lưu thông thường. Tuy nhiên, có nhiều cách khác để sử dụng bản sao lưu cho DR có thể phù hợp với mục tiêu kinh doanh của bạn. Bên cạnh các hệ thống dự phòng thông thường và khả năng phục hồi nhanh chóng của các giải pháp DR như Elastic Disaster Recovery, bạn có thể cần các giải pháp khôi phục ở các Khu vực khác.
  - AWS Backup and compliance: bạn cần theo dõi, kiểm tra và báo cáo về hoạt động sao lưu để đảm bảo đáp ứng các yêu cầu về tổ chức và quy định.
  - AWS Backup and ransomware mitigation: Vault lock - A powerful function of AWS Backup is that when you create a backup vault, you can use a different AWS KMS key (protect against bad actors modifying critical data for ransomware attacks).

## 3. Service Native Snapshots
## 4. AWS Elastic Disaster Recovery
