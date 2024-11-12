# 1. Giới thiệu AWS Elastic Disaster Recovery
- Các thảm họa CNTT như lỗi trung tâm dữ liệu, hỏng máy chủ hoặc tấn công mạng không chỉ có thể làm gián đoạn hoạt động kinh doanh của bạn mà còn gây mất dữ liệu, ảnh hưởng đến doanh thu và gây tổn hại đến danh tiếng của bạn.
- AWS Elastic Disaster Recovery (thường được gọi là DRS) giảm thiểu thời gian ngừng hoạt động và mất dữ liệu bằng cách cung cấp **khả năng khôi phục nhanh chóng, đáng tin cậy** cho các máy chủ vật lý, ảo và dựa trên đám mây vào Đám mây AWS.
- DRS **liên tục sao chép các máy của bạn** (bao gồm hệ điều hành, cấu hình trạng thái hệ thống, cơ sở dữ liệu, ứng dụng và tệp) vào khu vực tổ chức với chi phí thấp trong tài khoản AWS mục tiêu và Khu vực ưu tiên của bạn.
- Trong trường hợp xảy ra thảm họa, bạn có thể hướng dẫn DRS tự động khởi chạy tất cả các máy cần thiết ở trạng thái được cung cấp đầy đủ **trong vài phút**.
- Để sử dụng dịch vụ AWS Elastic Disaster Recovery (AWS DRS), chúng ta phải đặt cấu hình dịch vụ đó trong Region nơi dự định sử dụng dịch vụ đó. Đây là Region - nơi bạn dự định sao chép và khởi chạy các instance Recovery.
## Các thành phần cơ bản
- Source server: sao chép liên tục dữ liệu từ các máy chủ nguồn trong vùng gốc (Source AWS Region) sang vùng khôi phục (Recovery AWS Region). Tạo các điểm khôi phục theo thời gian (Point-In-Time Recovery) để bảo đảm có các bản sao lưu gần nhất, phục vụ cho việc khôi phục nếu xảy ra sự cố.

  ![{0D6019AC-5D8A-4D88-A331-21AAFC657AC8}](https://github.com/user-attachments/assets/393972c3-7b47-4b5d-a2d2-ab1718c37d68)

- DRS Recovery Server: Là các EC2 instance light weigh được dùng để sao chép dữ liệu giữa máy chủ nguồn và AWS của bạn. Khi Source Instance gặp sự cố, AWS DRS sẽ khởi động DRS Recovery Server trong vùng Recovery, đảm bảo dịch vụ tiếp tục hoạt động mà không gián đoạn. Tuy nhiên, chỉ tồn tại để thực hiện failover; chúng không trực tiếp xử lý lưu lượng từ người dùng.
  
  ![{990916AD-2076-46F3-81C5-7EFAC0CC83E2}](https://github.com/user-attachments/assets/178ade5f-72ff-496a-befb-b150611c43f1)

- Recovered Instances: thực sự thay thế các Source Instance trong việc cung cấp dịch vụ cho người dùng, đảm bảo hệ thống hoạt động liên tục ngay cả khi xảy ra sự cố ở Source Region.
- Replication Agent: install the AWS Replication Agent on each source server that you want to add to AWS Application Migration Service.
  
## Best practices
- Lập kế hoạch khôi phục cẩn thận và có ghi nhận lại, nên dùng CloudFormation template.
- Thực hiện diễn tập sự cố thường xuyên.
- Theo dõi tình trạng của quá trình replication đang diễn ra bằng DRS console hoặc programmatically. Không **Ready** thì phải chú ý.
  - **stalled**: cần bạn can thiệp để giải quyết.
  - **Lag**: có thể tự giải quyết (trừ khi chúng cũng bị đình trệ).
- Bị giới hạn: số lượng máy chủ tối đa có thể được replication bằng DRS trong một tài khoản AWS bị giới hạn ở **300**. Để tăng nhiều hơn số lượng máy chủ tối đa, hãy sử dụng nhiều Tài khoản AWS hoặc nhiều Khu vực AWS mục tiêu (bạn sẽ cần thiết lập DRS riêng cho từng tài khoản/Khu vực).
- Protecting Point-In-Time snapshots.
- Controlling agent installation permissions: Nên sử dụng IAM Role để cấp quyền tạm thời.
- Recovery best practices:
  - DRS giúp thực hiện failover bằng cách duy trì replication liên tục và khởi chạy các Recovery instance theo yêu cầu. Tuy nhiên, việc chuyển hướng dữ liệu (re-routing) không được thực hiện qua DRS mà cần sử dụng các dịch vụ DNS, như Amazon Route 53. Kế hoạch khôi phục cần bao gồm các bước và điều kiện cần để thực hiện chuyển hướng này.
  - Bảo vệ chống xóa cho Recovery instance: Instance settings -> Change termination protection -> Yes, Enable
  - Chi phí khi sử dụng failover.
  - Không sử dụng tính năng "Disconnect from AWS" cho các server đã khởi chạy Recovery instance, vì điều này sẽ xóa toàn bộ tài nguyên replication và các điểm khôi phục Point-In-Time (PIT).
  - Khi sử dụng Recovery instance làm server chính, chúng sẽ không được replication và không tạo ra các PIT mới. Để đảm bảo dự phòng cho site khôi phục, có thể cấu hình Recovery instance làm server nguồn mới và replicate chúng sang khu vực khác (phát sinh thêm chi phí).
  - DRS cho phép khôi phục vào một instance đã tồn tại thay vì tạo mới, với điều kiện instance này phải có hệ điều hành giống như instance nguồn, đang dừng và có tag _AWSDRS=AllowLaunchingIntoThisInstance_.
- Failback best practices:
  - Nếu các server không xuất hiện, có thể cần cài đặt hoặc cài đặt lại AWS Replication Agent.
  - Nếu các server xuất hiện trong DRS Console nhưng không sao chép, kiểm tra các lý do như cài đặt firewall.
  - Recovery Instances: Kết thúc các Recovery instance từ trang Recovery Instances của DRS Console.
  - Source Servers: Kiểm tra trong DRS Console và đảm bảo chỉ có một source server cho mỗi server thực tế ở nguồn.
    - Nếu có bản sao, đừng ngắt kết nối hoặc xóa các source server ban đầu cho đến khi server mới tích lũy đủ các Point-In-Time recovery points (PITs) cần thiết.
    - Ngắt kết nối từ AWS với các source server không cần thiết để ngừng chi phí cho DRS và các tài nguyên sao chép khác.
    - Cleanup cho nguồn ở AWS: Nếu nguồn là AWS, có thể sẽ có thêm các tài nguyên cần được dọn dẹp để tiết kiệm chi phí.
## Elastic Disaster Recovery network diagrams
- Establish communication between the staging area subnet and AWS Elastic Disaster Recovery over TCP port 443 directly.
- Communication between the source servers and the Staging Area Subnet over TCP port 1500.

 ![image](https://github.com/user-attachments/assets/f6df32c4-87ad-41a7-8603-530f2f3eb1d0)

# 2. Failover và Failback
## 2.1. Failover
- Là quá trình chuyển hoạt động từ Source Region sang DR Region khi Source Region gặp sự cố.
- Tác vụ chính: Khởi chạy bản sao ở DR Region.

  ![{E1A47AA5-42BA-4BAD-939F-A59A834EC99B}](https://github.com/user-attachments/assets/315a45c9-af86-4222-92e1-96c0ee681464)

## 2.2. Failback
- Là quá trình chuyển hoạt động từ DR Region về lại Source Region khi Source Region đã phục hồi và sẵn sàng.
- Tác vụ chính: Đồng bộ lại dữ liệu về Source và chuyển hoạt động về đó.
- During failover, AWS DRS allows you to replace the EC2 source instance (A1) with the EC2 recovered instance (B3). After performing a recovery, your applications are running on EC2 instances in the recovery region. However, these recovered instances (marked B3 in the diagram above) are not protected against other potential outages. In order to avoid data loss, you should start a reversed replication immediately. Starting reversed replication involves copying the data from the EC2 recovered instances (B3) to the original region, an operation that takes time and incurs cross-Region data transfer costs.

  A Source server (A2) will be created in the source region.
  
![{FF2CA784-4F03-4418-A992-7B480E6DD584}](https://github.com/user-attachments/assets/f5a2c3f1-299c-4ae3-a0eb-4aa505f2787d)

- Redirect traffic to failed back instances (A4), which will now become your new primary instances. Traffic redirection is not conducted using DRS:
  
![{1137DA1A-4A20-441A-BD5D-8B4873939538}](https://github.com/user-attachments/assets/bff976ec-54ed-4edc-82b1-317a9d1aecb5)

- The newly launched failed-back instances (A4) are not protected. In order to protect them, navigate to the recovery instance (A3) in the source region. Click _Start reversed replication_. This step will replace the Instances that the Source Server (B1) protects (A4 instead of A1):

  ![{4F6B3ABA-871D-438A-B2D4-A28858CFAE85}](https://github.com/user-attachments/assets/c14cadfc-9ba1-43d9-8c06-132a1eeea9f1)

- Clean up:
  - Stop replication on the source servers (A2) of the source region.
  - Terminate the recovery instances (B2).
  - Terminate the source region EC2 instances (A1).
  - Remove the recovery instance (A3) in the source region.
  - Remove the recovery instance (A3) in the source region.Remove the source servers (A2) in the source region.

- Final diagram:

  ![{DFDB71B9-247E-4F18-BD75-BFD27B3FF524}](https://github.com/user-attachments/assets/540fee03-9ec7-4c08-8aa9-f98b6efb270d)

# 3. Thực hành
- Kiến trúc:

We have two EC2 instances that host different pages of a website, and both of these instances are behind a load balancer.

  ![{CAED35E6-EC0A-4DE6-B165-7CE300718C7C}](https://github.com/user-attachments/assets/57364da6-911c-4670-9873-1dc5a37ec2b3)

- Failover:

  ![{6431342B-8732-4E6A-88AA-E8D6D8D965E9}](https://github.com/user-attachments/assets/cb9c5639-e54d-462e-aabe-66000b89d8db)

- Failback:

  ![{E345B6C1-3148-4E57-B9C6-2BE37E785B06}](https://github.com/user-attachments/assets/a8df2d29-eb8e-418d-b38e-94dbc62225ee)
