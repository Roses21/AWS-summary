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

# 3. Service Native Snapshots
- Snapshots có tính nhất quán cao trên nhiều ổ lưu trữ. Điều này có nghĩa là nhiều Snapshots có thể được chụp cùng một lúc. Điều này rất quan trọng khi dữ liệu có thể được phân phối trên nhiều thiết bị lưu trữ. Nếu bạn cần khôi phục hoặc sao chép dữ liệu, tất cả các nguồn dữ liệu sẽ được khớp với cùng một thời điểm.
- Snapshots are stored in a protected part of Amazon S3 as part of the managed service. Storing snapshots on Amazon S3 protects your data with 99.999999999 percent (11 9s) of durability and provides you Regional access and availability.
- Bốn dịch vụ AWS Storage cốt lõi hỗ trợ snapshort: Amazon EBS, Amazon FSx for NetApp ONTAP, Amazon FSx for OpenZFS và Amazon FSx for Lustre.
## 3.1. Amazon EBS snapshots
- Each snapshot contains all of the information for that point in time that is needed to restore your data to a new Amazon EBS volume.
- Khi bạn tạo ổ đĩa (volume) Amazon EBS mới dựa trên một snapshort, ổ đĩa mới sẽ giống y chang ổ đĩa gốc - cái mà được dùng để tạo ra snapshort đó. Dữ liệu của bạn được tải vào ổ đĩa mới ở chế độ nền. Bạn có thể bắt đầu sử dụng ổ đĩa mới ngay lập tức trong khi tải dữ liệu lên Amazon EBS. Nếu bạn truy cập vào dữ liệu chưa được tải, ổ đĩa sẽ tải xuống ngay dữ liệu được yêu cầu từ Amazon S3. Sau đó, snapshort của Amazon EBS sẽ tiếp tục tải phần dữ liệu còn lại của ổ đĩa ở chế độ nền.
- When you delete a snapshot, only the data unique to that snapshot is removed. Any information contained in that snapshot that is required by other snapshots remains available and is not deleted.
- Amazon EBS snapshot events are tracked through CloudWatch events.
- Bạn có thể tạo bản sao lưu của khối lượng công việc quan trọng, chẳng hạn như cơ sở dữ liệu lớn hoặc hệ thống tệp trải rộng trên nhiều ổ đĩa Amazon EBS.
## 3.2. Amazon FSx for NetApp ONTAP 
- A snapshot is a read-only image of an Amazon FSx for NetApp ONTAP volume at a point in time.
- Snapshort được lưu trữ cùng với dữ liệu hệ thống file của bạn. Chúng tiêu tốn dung lượng lưu trữ sẵn có của hệ thống tập tin. Tuy nhiên, snapshort chỉ tiêu tốn dung lượng lưu trữ gia tăng cho các phần đã thay đổi của tệp kể từ snapshort cuối cùng. Các snapshort được lưu trữ trong hệ thống tệp của bạn sẽ không được đưa vào bản sao lưu của các ổ đĩa hệ thống tệp của bạn.
- Với FSx for ONTAP, bạn có thể sử dụng ảnh chụp nhanh để tạo các ổ đĩa mới, khôi phục các ổ đĩa cũng như khôi phục các tệp và thư mục riêng lẻ.
## 3.3. Amazon FSx for OpenZFS
- A snapshot is a read-only image of an FSx for OpenZFS volume at a point in time.
- Cung cấp khả năng bảo vệ chống lại việc vô tình xóa hoặc sửa đổi các tệp trong ổ đĩa; khôi phục thuận tiện; người dùng có thể hoàn tác các thay đổi và so sánh các phiên bản tệp.
- Các snapshorts được lưu trữ cùng với dữ liệu của hệ thống tệp nên chúng tiêu tốn dung lượng lưu trữ của hệ thống tệp.
## 3.4. Amazon FSx for Lustre
- Là hệ thống tệp nhất quán, có độ bền cao và tăng dần.
- Bạn có thể kết hợp cả snapshort thủ công và tự động trên cùng một hệ thống tệp. Tuy nhiên, chỉ có một snapshort có thể xảy ra tại một thời điểm.
- Snapshort chỉ khả dụng với các hệ thống tệp liên tục mà không được liên kết với kho dữ liệu Amazon S3.
# 4. AWS Elastic Disaster Recovery
## 4.1. Introduction
- AWS DRS sao chép ứng dụng của bạn sang Amazon EC2 instance và bộ lưu trữ Amazon EBS tiết kiệm chi phí. Trong trường hợp cần thiết sẽ được nâng lên thành các tài nguyên có khả năng xử lý toàn bộ khối lượng công việc của ứng dụng.
- AWS DRS works with your on-premises applications servers, applications in other cloud providers, or with Amazon EC2 and Amazon EBS between AWS Regions.
- Using AWS DRS to protect your most critical databases, including Oracle, MySQL, and SQL Server, and enterprise applications such as SAP.
- AWS DRS liên tục sao chép máy của bạn vào khu vực tổ chức có chi phí thấp trong tài khoản AWS mục tiêu và Khu vực ưa thích của bạn. Bản sao bao gồm hệ điều hành, cấu hình trạng thái hệ thống, cơ sở dữ liệu, ứng dụng và tệp.
- Trong trường hợp xảy ra thảm họa, bạn có thể hướng dẫn AWS DRS tự động khởi chạy hàng nghìn máy ở trạng thái được cung cấp đầy đủ trong vài phút.
## 4.2. AWS DRS Features
- Continuous replication: khả năng sao chép liên tục, không đồng bộ, ở cấp block của máy nguồn của bạn vào khu vực tổ chức. Bạn có thể đạt được Mục tiêu điểm khôi phục (RPO) dưới giây vì các ứng dụng cập nhật luôn sẵn sàng khởi động trên AWS nếu thảm họa xảy ra.
- Low-cost staging area: Dữ liệu liên tục được đồng bộ hóa trong khu vực tổ chức gọn nhẹ. Khu vực tổ chức chứa các tài nguyên chi phí thấp mà AWS DRS tự động cung cấp và quản lý. Điều này làm giảm nhu cầu về các tài nguyên trùng lặp và giảm đáng kể tổng chi phí sở hữu (TCO) để khắc phục thảm họa.
- Automated machine conversion and orchestration: AWS DRS sao chép toàn bộ máy, bao gồm hệ điều hành, cấu hình trạng thái hệ thống, ổ đĩa hệ thống, cơ sở dữ liệu, ứng dụng và tệp. Do đó, bạn không cần phải cài đặt lại mọi thứ hoặc duy trì các bản sao trùng lặp của hệ điều hành, cấu hình trạng thái hệ thống hoặc phần mềm.
- Point-in-time recovery: bạn có thể khôi phục các ứng dụng và môi trường CNTT đã bị hỏng do vô tình thay đổi hệ thống, phần mềm tống tiền hoặc các cuộc tấn công độc hại khác.
- Non-disruptive disaster recovery testing: có thể tiến hành diễn tập khắc phục thảm họa mà không làm gián đoạn môi trường nguồn hoặc gặp rủi ro mất dữ liệu.
- Wide application and infrastructure support.
## 4.3. AWS DRS Use Cases
- On premises to AWS: Nhanh chóng khôi phục hoạt động sau các sự kiện không mong muốn như sự cố phần mềm hoặc lỗi phần cứng trung tâm dữ liệu. AWS DRS có RPO tính bằng giây và RTO tính bằng phút.
- Cloud to AWS: Giúp tăng khả năng phục hồi và đáp ứng các yêu cầu tuân thủ bằng cách sử dụng AWS làm trang khôi phục của bạn. AWS DRS chuyển đổi các ứng dụng dựa trên đám mây của bạn để chạy tự nhiên trên AWS.
- Region to Region: Tăng khả năng phục hồi của ứng dụng và giúp đáp ứng các mục tiêu về tính khả dụng cho ứng dụng AWS của bạn bằng cách sử dụng AWS DRS để khôi phục các ứng dụng ở Khu vực AWS khác.
