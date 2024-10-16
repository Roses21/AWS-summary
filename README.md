# Mục lục:
1. [Cloud Computing](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#1-l%C6%B0u-%C3%BD-v%E1%BB%81-v%E1%BA%BD-ki%E1%BA%BFn-tr%C3%BAc-tr%C3%AAn-drawio)
2. [Three tier architecture](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#2-three-tier-architecture)
3. [AWS Well-Architected Framework](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#3-aws-well-architected-framework)
4. [Auto Scaling](https://github.com/Roses21/AWS-summary/blob/main/README.md#4-ec2-auto-scaling)
5. [AWS Networking](https://github.com/Roses21/AWS-summary/blob/main/README.md#5-aws-network)

   5.1. [VPC](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#51-vpc)

   5.2. [Elastic Load Balancing (ELB)](https://github.com/Roses21/AWS-summary/blob/main/README.md#52-elastic-load-balancing-elb)

   5.3. [ENB](https://github.com/Roses21/AWS-summary/blob/main/README.md#53-enb)

   5.4. [Route 53](https://github.com/Roses21/AWS-summary/blob/main/README.md#54-route-53)
   
6. [AWS Compute](https://github.com/Roses21/AWS-summary/blob/main/README.md#6-compute)

   6.1. [Virtual machines (VMs): Elastic Compute Cloud (EC2)](https://github.com/Roses21/AWS-summary/tree/main?tab=readme-ov-file#61-virtual-machines-vms-elastic-compute-cloud-ec2)
      
   6.2. [Containers](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#62-containers)

   6.3. [Severless](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#63-serverless)
   
7. [Storage](https://github.com/Roses21/AWS-summary/blob/main/README.md#7-storage)

   7.1. [Object, file, and block storage]()
   
      7.1.1. [Amazon File Cache]()
   
      7.1.2. [Simple Storage Service - S3](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#72-s3)

      7.1.3. [Elastic Block Storage - EBS](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#73-ebs)

      7.1.4. [Amozon FSx]()

   7.2. [Data migration]()
   
      7.2.1. [AWS DataSync]()

      7.2.2. [AWS Snow Family]()

   7.3. [Hybrid cloud storage and edge computing]()

      7.3.1. [AWS Storage Gateway]()

      7.3.2. [AWS Snow Family]()
   
   7.4. [Disaster recovery and backup]()

      7.4.1. [AWS Elastic Disaster Recovery]()

      7.4.1. [Backup]()

   7.5. [Managed file transfer]()

      [AWS Transfer Family]()

8. [Database](https://github.com/Roses21/AWS-summary/blob/main/README.md#8-database) 

   Relational:

   8.1. [Amazon Relational Database Service](https://github.com/Roses21/AWS-summary/blob/main/README.md#81-amazon-relational-database-service-rds)

   8.2. [Amazon Aurora]()

   Non-relational:
   
   8.3. [NoSQL Database Service (Key-value) - DynamoDB]()

   8.4. [Graph - Neptune]()

   8.5. [Data Warehouse - RedShift]()

   8.6. [Caching - Amazon ElastiCache]()

   8.7. [Document - DocumentDB]()

   8.8. [In-memory - MemoryDB]()

   8.9. [Time-series - Timestream]()

   8.10. [Ledger - Amazon LQDB]()

   8.11. [Wide column - Amazon Keyspace]()
   

9. [AWS Management Tools](https://github.com/Roses21/AWS-summary/blob/main/README.md#9-aws-management-tools)

   9.1. [IAM](https://github.com/Roses21/AWS-summary/blob/main/README.md#91-iam)

   9.2. [CloudWatch (Application)](https://github.com/Roses21/AWS-summary/blob/main/README.md#92-cloudwatch-application)

   9.3. [CloudTrail (AWS Account)](https://github.com/Roses21/AWS-summary/blob/main/README.md#93-cloudtrail-aws-account)

10. [CloudFormation](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#10-cloudformation)
11. [AWS Billing and Cost Management](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#11-aws-billing-and-cost-management)
12. [AWS CLI](https://github.com/Roses21/AWS-summary/blob/main/README.md#12-aws-cli)
13. [WAF](https://github.com/Roses21/AWS-summary/blob/main/README.md#13-waf-web-application-firewall) 
14. [Nguồn tham khảo](https://github.com/Roses21/AWS-summary/blob/main/README.md#ngu%E1%BB%93n-tham-kh%E1%BA%A3o)

![{085F76D4-136F-4A53-8841-04F633E24232}](https://github.com/user-attachments/assets/ec7d14c8-7030-40d7-81a6-9b0b0c9a2341)

# 1. Cloud Computing
- Là việc cung cấp các dịch vụ điện toán qua internet thay vì sử dụng các máy chủ cục bộ.
- Nó cung cấp các dịch vụ điện toán đám mây đáng tin cậy, có thể mở rộng và không tốn kém, bao gồm lưu trữ dữ liệu, cơ sở dữ liệu, ứng dụng, phân tích, học máy và thậm chí thiết lập máy chủ ảo. 
- Three types of cloud service models:
  - IaaS (Infrastructure as a Service): cung cấp cơ sở hạ tầng ảo hóa (máy chủ, lưu trữ, mạng, và các tài nguyên máy tính khác) qua internet. VD: Amazon CloudFormation, EC2, S3, ELB,...
  - PaaS (Platform as a Service): cung cấp môi trường thời gian chạy để phát triển, thử nghiệm và quản lý ứng dụng. VD:Lambda, RDS, Elastic Beanstalk
  - SaaS (Software as a Service): cung cấp phần mềm qua internet, người dùng chỉ cần truy cập và sử dụng dịch vụ mà không phải quản lý cơ sở hạ tầng hay cài đặt phần mềm. VD: Amazon WorkMail, Google Workspace, Microsoft Office 365, Dropbox.
- Lưu ý khi vẽ architect trên draw.io:
  - Tỉ lệ khung ngoài cùng của kiến trúc AWS: 1.618, ví dụ Height = 500 => Width = 500 x 1.618 = 809.
  - Khung tên của service AWS nên là màu cam (FF8000).
  - Size icon: 60x60.
# 2. Three tier architecture
- Web/Presentation Tier: Houses the user-facing elements of the application, such as web servers and the interface/frontend.
- Application Tier: Houses the backend and application source code needed to process data and run functions.
- Data Tier: Houses and manages the application data. Often where the databases are stored.

![image](https://github.com/user-attachments/assets/31b4a426-bc54-43cd-a527-4a27a8a866a8)

# 3. AWS Well-Architected Framework
Gồm 6 trụ cột chính:
## 3.1. Operational Excellence Pillar
  - K/n: focuses on running and monitoring systems, and continually improving processes and procedures: automating changes, responding to events, and defining standards to manage daily operations.
  - Design Principles
    - Perform operations as code
    - Annotate documents
    - Make frequent, small, reversible changes
    - Refine operations procedures frequently
    - Anticipate failure
    - Learn from all operational failures
  - Best practices:
    - Organization
    - Prepare
    - Operate
    - Evolve
## 3.2. Security 
  - K/n: focuses on protecting information and systems: confidentiality and integrity of data, managing user permissions, and establishing controls to detect security events.
  - Design Principles:
    - Implement a strong identity foundation: IAM
    - Maintain traceability (truy xuất nguồn gốc): AWS CloudTrail và AWS Config.
    - Apply security at all layers.
    - Automate security best practices.
    - Protect data in transit and at rest: encrypt, AWS KMS.
    - Keep people away from data: NACLs.
    - Prepare for security events: AWS WAF.
  - Best practice:
    - Identity and Access Management
    - Detective Controls
    - Infrastructure Protection
    - Data Protection
    - Incident Response
## 3.3. Reliability 
- K/n:đảm bảo workload hoạt động chính xác và như mong đợi: distributed system design, recovery planning, and adapting to changing requirements.
- Design Principles:
  - Automatically recover from failure: EC2 Auto scaling, Amazon Route 53, Load Balancer
  - Test recovery procedures
  - Scale horizontally to increase aggregate workload availability
  - Stop guessing capacity
  - Manage change through automation
- Best practices:
 - Foundations
 - Change Management
 - Failure Management
## 3.4. Performance Efficiency
- K/n: tập trung vào việc phân bổ có cấu trúc và hợp lý các tài nguyên máy tính và CNTT: chọn loại và quy mô tài nguyên được tối ưu hóa cho yêu cầu khối lượng công việc, giám sát hiệu suất và duy trì hiệu quả khi nhu cầu kinh doanh phát triển.
- Design Principles:
  - Democratize advanced technologies (cung cấp các dịch vụ dễ sử dụng, không cần phải có chuyên môn sâu để triển khai)
  - Go global in minutes: Route 53, CloudFront.
  - Use serverless architectures:  AWS Lambda
  - Experiment more often
  - Consider mechanical sympathy (chọn đúng loại tài nguyên phù hợp với công việc cụ thể):
- Best practices:
  - Selection: Compute, Storage, Database, Network
  - Review
  - Monitoring
  - Tradeoffs
## 3.5. Cost Optimization
- K/n: tránh những chi phí không cần thiết: understanding spending over time and controlling fund allocation, selecting resources of the right type and quantity, and scaling to meet business needs without overspending.
- Design Principles:
  - Implement cloud financial management: Cost Explorer.
  - Adopt a consumption model (không trả trước, dùng bao nhiêu trả bấy nhiêu): EC2 Auto Scaling, Lamda, S3.
  - Measure overall efficiency: AWS Trusted Advisor, CloudWatch.
  - Stop spending money on undifferentiated heavy lifting: Fargate, RDS.
  - Analyze and attribute expenditure: AWS Cost Anomaly Detection
- Best practices:
  - Expenditure Awareness
  - Cost-Effective Resources
  - Matching Supply and Demand
  - Optimizing Over Time
## 3.6. Sustainability 
- K/n: focuses on minimizing the environmental impacts of running cloud workloads: a shared responsibility model for sustainability, understanding impact, and maximizing utilization to minimize required resources and reduce downstream impacts. 
- Design Principles:
  - Understand your impact
  - Establish sustainability goal
  - Maximize utilization (Tối đa hóa việc sử dụng)
  - Anticipate and adopt new, more efficient hardware and software offerings
  - Use managed services
  - Reduce the downstream impact of your cloud workloads
- Best practices:
  - Region selection
  - Alignment to demand
  - Software and architecture
  - Data management
  - Hardware and services
  - Process and culture

# 4. EC2 Auto Scaling
- Auto Scaling có 3 components:
  - Group (Nhóm co giãn tự động) là một nhóm các EC2 Instance hoặc RDS Instance. Nhóm này có khả năng co giãn số lượng các EC2 Instance thành viên dựa trên các chính sách co giãn mà bạn thiết lập.
  - Configuration Templates: là một tính năng giúp bạn tạo mẫu cho việc khởi tạo các EC2 Instance. Điều này giúp tự động hóa và đơn giản hóa việc khởi tạo các EC2 Instance cho dịch vụ Auto Scaling.
  - Scaling Options: Cung cấp một số cách để scale ASG (scale khi đáp ứng một điều kiện cụ thể hay theo lịch trình).
- Triển khai ứng dụng sử dụng Auto Scaling Group để đảm bảo khả năng mở rộng linh hoạt theo nhu cầu của người dùng, tăng tính sẵn sàng và đảm bảo khả năng chịu lỗi.
- Khi thiết kế HA cho Auto Scaling, hãy ưu tiên sử dụng nhiều AZ và nhiều Region.
- Auto Scaling cho phép bạn tạm dừng và sau đó tiếp tục một hoặc nhiều quy trình này, điều này có lợi cho bạn khi muốn điều tra sự cố trong ứng dụng của mình mà không kích hoạt quy trình Auto Scaling.
- Bạn không thể sửa đổi cấu hình khởi chạy sau khi đã tạo nó. Nếu muốn thay đổi cấu hình khởi chạy cho nhóm Auto Scaling, bạn phải tạo cấu hình khởi chạy mới và cập nhật nhóm Auto Scaling của mình để kế thừa cấu hình khởi chạy mới này.

![image](https://github.com/user-attachments/assets/41cdb655-d8de-4c1f-b0c8-c12f90d4205a)

## Scaling policies
- Gồm 3 loại:
### Simple scaling policy
- Hoạt động dựa trên một điều kiện duy nhất: Simple Scaling chỉ có một ngưỡng đơn lẻ và thực hiện một hành động duy nhất khi điều kiện đó được đáp ứng.
- Thay đổi đơn giản và ngay lập tức: Khi điều kiện (chẳng hạn như CPU vượt quá một mức cụ thể) được kích hoạt, Simple Scaling thực hiện ngay lập tức hành động mở rộng hoặc thu nhỏ số lượng instances theo một số lượng cố định.
- Ví dụ: Nếu CPU > 70%, tăng thêm 1 instance. Nếu CPU < 30%, giảm 1 instance.
### Step scaling
- Hoạt động dựa trên các ngưỡng cụ thể: Step Scaling cho phép bạn thiết lập nhiều ngưỡng khác nhau cho một chỉ số (như CPU, Network In/Out, v.v.), và tương ứng với mỗi ngưỡng, bạn có thể cấu hình một hành động mở rộng hoặc thu nhỏ cụ thể.
- Thay đổi theo từng bước: Số lượng instances tăng hoặc giảm sẽ phụ thuộc vào mức độ mà chỉ số vượt qua các ngưỡng đã thiết lập. Điều này có nghĩa là khi chỉ số vượt qua ngưỡng cao hơn, số lượng instances được thay đổi sẽ lớn hơn so với khi chỉ số chỉ vượt qua ngưỡng thấp hơn.
- Ví dụ: Nếu CPU > 70%, tăng thêm 2 instances. Nếu CPU > 90%, tăng thêm 4 instances. Nếu CPU < 30%, giảm 1 instance.
### Target Tracking
- Tự động điều chỉnh số lượng instances dựa trên một chỉ số mục tiêu đã được xác định, chẳng hạn như mức sử dụng CPU. AWS sẽ liên tục theo dõi chỉ số này và tăng hoặc giảm số lượng instances để duy trì chỉ số gần với mục tiêu.
- Ví dụ: Bạn có thể tạo một policy để tự động thêm hoặc bớt EC2 instances trong một Auto Scaling group nhằm duy trì mức sử dụng CPU trung bình là 50%.
# 5. AWS Networking
## 5.1. VPC
- Nằm trong 1 Region (1 khu vực địa lý nơi đặt cụm data center), hiện tại 1 AWS Region tối đa 5 VPC trên 1 AWS account.
- Khi tạo VPC cần khai báo 1 lớp mạng CIDR IPv4 (bắt buộc) và IPv6 (tùy chọn).
- Mục đích chính: phân tách các môi trường (dev/test/production/…) ở mức network. Còn muốn tách biệt hẳn các tài nguyên (user không thấy được tài nguyên) thì cần tạo nhiều AWS account chứ không phải tạo nhiều VPC.
- Địa chỉ IP trong VPC là IP private: 10.0.0.0 - 10.255.255.255, 172.16.0.0 - 172.31.255.255, 192.168.0.0 - 192.168.255.255.
### Firewall trong VPC - Subnet security
Dùng khi muốn public subnet connect tới private subnet thông qua 1 port.
  - Security Group (control inbound and outbound traffic for your **instances**): là 1 tường lửa ảo lưu giữ trạng thái (**stateful** - return traffic automatically allowed, regardless of any rules). Rule **chỉ cho phép rule allow**, rule sẽ hạn chế theo protocol, IP nguồn, port kết nối or 1 SG khác. Không có thứ tự xử lý quy tắc. Mặc định: chặn tất cả đến, cho tất cả đi. Mỗi Security Group có thể chứa tối đa 60 quy tắc inbound và 60 quy tắc outbound. You can associate one or more (**up to five**) security groups to an instance in your VPC.
  - NACL (Network Access Control List) - control inbound and outbound traffic for your **subnets**:
    - **stateless**, áp dụng lên các Amazon VPC subnets => ảnh hưởng đến nhiều máy chủ/ứng dụng khác khi thay đổi rule NACL.
    - NACLs xử lý các quy tắc **ưu tiên số nhỏ hơn** (1-32766). Khi một quy tắc phù hợp được tìm thấy, NACL sẽ dừng đánh giá và áp dụng quy tắc đó. AWS khuyến nghị thêm quy tắc theo mức tăng 100. Nếu không có quy tắc nào áp dụng, thì mặc định NACL sẽ chặn (DENY) gói tin.
    - Can associate a network ACL with multiple subnets; however, a subnet can be associated with only one network ACL at a time.
    - Mỗi NACL có thể chứa tối đa 20 quy tắc inbound và 20 quy tắc outbound.
    - Default NACL không thể modify, nó cho phép toàn bộ lưu lượng vào/ra.
    - Custom NACL mặc định sẽ chặn toàn bộ lưu lượng vào/ra cho đến khi bạn thêm các quy tắc cho phép. For custom ACLs, you need to add a rule for ephemeral ports, usually with the range of 32768-65535. If you have a NAT Gateway, ELB or a Lambda function in a VPC, you need to enable 1024-65535 port range.
  - VPC Flow logs: cho phép nắm bắt **thông tin về lưu lượng IP đến và đi từ giao diện mạng** (ELB, RDS, ElastiCache, Redshift,WorkSpaces, NATGW, TGW,...) trong VPC. Các file logs để thể xuất lên Amazon CloudWatch, Kinesis Data Firehose và S3. Không capture được nội dung gói tin. => Theo dõi lưu lượng bất thường trong mạng.
    
    ![{F7241509-69F9-4A8B-A41A-0A485D9B2283}](https://github.com/user-attachments/assets/f55a6082-ebc8-4808-9934-87af6358b4d8)

### Subnet
- VPC cho phép tạo nhiều mạng ảo và chia các mạng ảo này thành các mạng con. VPC Subnet sẽ nằm trong 1 AZ cụ thể. Khi tạo subnet, cần chỉ định CIDR cho mạng con đó và đây là một tập hợp con của khối VPC CIDR.
  - CIDR (Classless Inter-Domain Routing): Định nghĩa 1 dải địa chỉ IP. Tối đa 5 CIDR/VPC.
  - A CIDR consists of two components: IP và subnet mask. Ví dụ: 192.168.0.0/24
  - Your VPC CIDR should NOT overlap with your other networks.
- AWS giữ 4 địa chỉ IP đầu và 1 IP cuối của mỗi subnet để kết nối mạng. Subnet nhỏ nhất là /28 ~ 16 địa chỉ IP. Subnet lớn nhất là /16 ~ 65536 địa chỉ IP.
 - Public subnet: được ra ngoài internet.
 - Private subnet: giao tiếp với internet qua NAT gateway.
 - VPN-only subnet: This subnet has a route table that directs traffic to Amazon VPC’s Virtual Private Gateway
   
### Route table
- Khi tạo VPC, AWS sẽ tự tạo 1 Default Route Table - không thể bị xóa và chỉ chứa 1 route duy nhất cho phép tất cả các subnet trong VPC liên lạc với nhau.
- 1 router-table có thể có nhiều subnets, nhưng 1 subnet chỉ có 1 route-table.
- You cannot delete the main route table, but you can replace the main route table with a custom table that you’ve created.
  
### Connect to VPC
- **Internet gateways**:
  - Có quy mô theo chiều ngang, dự phòng và có tính khả dụng cao cho phép giao tiếp giữa VPC và Internet. Nó hỗ trợ lưu lượng IPv4 và IPv6.
  - Một VPC chỉ có thể được gắn vào một IGW và ngược lại.
  - Sử dụng Internet gateway thì miễn phí, nhưng sẽ tính phí truyền dữ liệu đối với các EC2 instances sử dụng internet gateway.
    
- **Bastion Host**:
  - Là public EC2 instance, use a Bastion Host to **SSH into our private EC2 instances**.
  - Bastion host nằm trong public subnet nhưng SSH được đến instance trong private subnet.
  - Bastion Host security group must allow inbound from the internet on port 22 from restricted CIDR, for example the **public CIDR** of your corporation.
  - Security Group of the EC2 Instances must allow the Security Group of the Bastion Host, or the **private IP** of the Bastion host.
  - Trước tiên, bạn SSH vào Bastion Host, sau đó từ đó, bạn có thể SSH vào các máy chủ khác trong private subnet. Điều này hạn chế quyền truy cập trực tiếp vào máy chủ trong private subnet từ internet, cải thiện tính bảo mật.
- **NAT**: Đặt ở public subnet. Cho phép các instance trong private subnet kết nối với Internet hoặc các dịch vụ AWS khác nhưng ngăn Internet kết nối với các instances.
  - NAT Instance (outdated):
    - Manage by you.
    - Must disable EC2 setting: Source/destination Check
    - Must have Elastic IP attached to it
    - Route Tables must be configured to route traffic from private subnets to the NAT Instance

      ![{B6AEED66-28E1-452A-93A4-EEF5A7FD2031}](https://github.com/user-attachments/assets/823214c0-9016-468f-b5a4-b61fdb30c8ae)

   - NAT gateway:
     - Các phiên bản trong private subnet có thể sử dụng cổng NAT để truy cập Internet để cập nhật phần mềm, tìm nạp các phần phụ thuộc, v.v. mà không để lộ địa chỉ IP riêng tư của chúng trên Internet.
     - HA. **AWS-managed** NAT => **Không cần Security Group**. Nhưng có thể kiểm soát lưu lượng đi ra và vào thông qua Route Tables và Network ACLs.
     - Higher bandwidth, high availability, no administration.
     - Cần **phải có IGW**: private subnet -> NATGW -> IGW.
     - NAT Gateway bắt buộc **phải có một EIP** để hoạt động.
     - Trong từng AZ, NAT Gateway có khả năng chịu lỗi nội bộ. Điều này có nghĩa là trong mỗi AZ, nếu hạ tầng bên trong AZ đó vẫn hoạt động, NAT Gateway sẽ tự đảm bảo tính sẵn sàng và hoạt động ổn định cho các tài nguyên trong cùng AZ. Nhưng để tránh sự cố toàn cục khi một AZ ngừng hoạt động, bạn cần triển khai NAT Gateway ở nhiều AZ để đảm bảo dịch vụ hoạt động liên tục trong các AZ còn lại.
     - Các tài nguyên trong mỗi AZ cần sử dụng NAT Gateway trong chính AZ của mình.

![image](https://github.com/user-attachments/assets/4b84ee6e-caa8-45c2-b474-dddf74f37cb0)

- **Elastic IP (EIP)**: là **địa chỉ IP công cộng, tĩnh** và băng thông có thể mở rộng, cho phép tài nguyên đám mây của bạn giao tiếp với Internet. Nếu một tài nguyên được gán EIP, nó có khả năng truy cập Internet trực tiếp. Mỗi EIP chỉ có thể được liên kết với một tài nguyên đám mây và chúng phải ở cùng một khu vực. Tính năng:
  - Uyển chuyển: có thể liên kết linh hoạt EIP với hoặc hủy liên kết EIP khỏi bất kỳ EC, GPU, cổng NAT, bộ cân bằng tải và địa chỉ IP ảo nào.
  - Băng thông tốc độ cao.
  - Chi phí thấp.
  - Quản lý dễ dàng


- **Direct Connect (DX)**:
  - Cung cấp kết nối riêng biệt và bảo mật từ mạng từ xa của bạn đến VPC.
  - Cần thiết lập kết nối chuyên dụng giữa trung tâm dữ liệu (Data Center - DC) của bạn và các vị trí của AWS Direct Connect.
  - Bạn cần thiết lập Virtual Private Gateway trên VPC của mình.
  - Có thể truy cập cả tài nguyên công cộng (như S3) và tài nguyên riêng (như EC2) trên cùng một kết nối.
  - Các trường hợp sử dụng:
    - Tăng băng thông truyền tải: Phù hợp với việc xử lý các bộ dữ liệu lớn – chi phí thấp hơn.
    - Trải nghiệm mạng nhất quán hơn: Thích hợp cho các ứng dụng sử dụng luồng dữ liệu thời gian thực.
    - Môi trường kết hợp: Phối hợp giữa hệ thống tại chỗ (on-premise) và đám mây.
    - Hỗ trợ cả IPv4 và IPv6.
   - Direct Connect Gateway: dùng trong trường hợp cần thiết lập DX trên 1 hoặc nhiều VPC ở nhiều Regions (cùng account).
   - Data trên đường truyền sẽ không được mã hóa nhưng nó private => DX + VPN để có IPsec-encrypted private connection.
   - Connection Types:
     - Dedicated Connections: Cung cấp dung lượng 1Gbps, 10Gbps, và 100Gbps qua cổng ethernet vật lý dành riêng cho khách hàng, yêu cầu qua AWS và được hoàn thành bởi AWS Direct Connect Partners.
     - Hosted Connections: Dung lượng từ 50Mbps đến 10Gbps, **có thể điều chỉnh linh hoạt**, yêu cầu qua AWS Direct Connect Partners. Các mức 1Gbps, 2Gbps, 5Gbps, và 10Gbps có sẵn tại một số đối tác.
   - In case Direct Connect fails, you can set up a backup Direct Connect connection (expensive), or a Site-to-Site VPN connection.
   
- **Transit Gateway**:
  
  ![image](https://github.com/user-attachments/assets/b7f6f0fb-a971-4682-aa98-35bbdebc9737)

  - Lợi ích chính: khả năng tập trung và đơn giản hóa việc quản lý kết nối giữa VPC và mạng tại chỗ thông qua một gateway trung tâm duy nhất.
  - Dùng kết nối các VPC và mạng tại chỗ, cổng này hoạt động như một trung tâm định tuyến lưu lượng giữa các VPC, kết nối VPN và kết nối AWS Direct Connect.
  - Pricing: dựa trên lượng dữ liệu truyền qua cổng và thời gian sử dụng.
  - Transit Gateway Attachment là công cụ dùng để gán các subnet của từng VPC cần kết nối với nhau vào một Transit Gateway đã được khởi tạo, hoạt động ở phạm vi toàn bộ AZ.
  - You can use AWS Resource Access Manager (RAM) to share Transit Gateway with other accounts.
    
- **AWS Virtual Private Network (VPN)**: kết nối VPC của mình với các mạng và người dùng remote. VPN connectivity option:
  - AWS Site-to-Site VPN: create an IPsec VPN connection between your VPC and your remote network. On the AWS side of the Site-to-Site VPN connection, a virtual private gateway or transit gateway provides two VPN endpoints (tunnels) for automatic failover. Customer Gateway (On-premises) is Software application or physical device on customer side of the VPN connection.
  - AWS Client VPN
  - AWS VPN CloudHub
  - Third party software VPN appliance
    
- **VPC peering connections**: 
  
  ![image](https://github.com/user-attachments/assets/569b4519-c6ca-4bb5-97bf-75f0ab81ce68)

  - VPC Peering: giúp kết nối 2 VPC, để các tài nguyên trong 2 VPC có thể liên lạc trực tiếp với nhau mà không thông qua Internet. Kết nối 1:1 giữa 2 VPC. Không hỗ trợ khi 2 VPC bị overlap CIDR.
  - Phải cấu hình bảng định tuyến, chỉ ra rằng phải kết nối với VPC Peering để đến được IP đích. IP đích có thể là IP của VPC/máy ảo/subnet.
  - Có khả năng **kết nối các VPC trên các tài khoản AWS/Regions khác nhau**.
  - Đảm bảo rằng tất cả lưu lượng dữ liệu giữa các VPC ngang hàng vẫn nằm trong mạng AWS mà không bao giờ truyền qua Internet công cộng.
  - Use cases: 
    - Cho phép liên lạc an toàn giữa các tầng khác nhau của ứng dụng (chẳng hạn như máy chủ web và máy chủ cơ sở dữ liệu).
    - Hỗ trợ chia sẻ tài nguyên giữa nhiều nhóm hoặc đơn vị kinh doanh.
    - Cho phép kiến ​​trúc đám mây lai bằng cách kết nối mạng tại chỗ với VPC AWS.
   
- **VPC Endpoint**:
  - Mọi service của AWS đều public (có URL để connect).
  - VPC Endpoint provide private access to AWS Services (S3, DynamoDB, CloudFormation, SSM) within a VPC.
  - Endpoints are virtual devices.
  - Use case:
    - Check DNS Setting Resolution in your VPC.
    - Check Route Tables.
  - Gồm 2 loại:
    - Interface Endpoints (powered by PrivateLink): Cung cấp ENI (elastic network interface) với private IP làm điểm vào (phải đính kèm SG), hỗ trợ hầu hết các dịch vụ AWS. Chi phí gồm $ mỗi giờ + $ mỗi GB dữ liệu được xử lý
    - Gateway Endpoints: Provisions a gateway and must be used as a target in a route table (does not use security groups); Supports both S3 and DynamoDB; Free.

- Egress-only Internet Gateway: like a NAT Gateway, but for IPv6 targets.
- Traffic Mirroring: copy network traffic from ENIs for further analysis.
  
## 5.2. Elastic Load Balancing (ELB)
- **Automated distributes incoming application or network traffic** across multiple targets, such as EC2 instances, containers (ECS), Lambda functions, and IP addresses, in multiple Availability Zones.
- When you create a load balancer, you must specify one public subnet from at least two Availability Zones.
- **Cross Zone Load Balancing** – when enabled, each load balancer node distributes traffic across the registered targets in all enabled AZs.
- Benefits:
  - Load balancers phân phối khối lượng công việc giữa các tài nguyên tính toán như máy chủ ảo, giúp tăng cường tính sẵn sàng và khả năng chịu lỗi của ứng dụng. Bạn có thể thêm hoặc gỡ bỏ tài nguyên mà không làm gián đoạn luồng yêu cầu.
  - Load balancers cũng có thể cấu hình kiểm tra sức khỏe để đảm bảo chỉ gửi yêu cầu đến các tài nguyên hoạt động tốt.
  - Chúng có thể xử lý việc mã hóa và giải mã để giảm tải cho tài nguyên tính toán, giúp chúng tập trung vào công việc chính.
- ELB gồm 4 loại:
  - Application Load Balancers

    ![{E85D97C2-1062-4C51-B455-5087FD7BA4A7}](https://github.com/user-attachments/assets/dfdec2ac-562d-4149-b83d-8cd2dcbd3811)

  - Network Load Balancers

    ![{C3142AB5-B989-4B5D-B624-144548DADD6F}](https://github.com/user-attachments/assets/81a9587a-e47b-48ca-906c-891f57131be2)

  - Gateway Load Balancers
  - Classic Load Balancers

## 5.3. ENB
## 5.4. Route 53

![image](https://github.com/user-attachments/assets/c5660d3e-fa00-410e-890c-60dac47d9ef7)

# 6. Compute

Gồm 3 loại: virtual machines (VMs), containers, và serverless.

## 6.1. Virtual machines (VMs): Elastic Compute Cloud (EC2)
- EC2 instance lifecycle
  
  ![image](https://github.com/user-attachments/assets/d40c58fa-b292-4f4a-b5e7-cf0292bf3f35)

   - Pending (billing has not started): AWS performs all actions needed to set up an instance, such as copying the AMI content to the root device and allocating the necessary networking components.
   - Running (billing begins): you can take other actions on the instance, such as reboot, terminate, stop, and stop-hibernate.
   - Rebooting: equivalent to rebooting an operating system. The instance keeps its public DNS name (IPv4) and private and public IPv4 addresses. An IPv6 address (if applicable) remains on the same host computer and maintains its public and private IP address, in addition to any data on its instance store volumes.
   - Stopping: is similar to when you shut down your laptop; retains its private IPv4 addresses and IPv6 address. 2 options:
     - Stop (storage for any Amazon EBS volumes is charged): Giống như tắt nguồn máy tính, mất dữ liệu trong RAM. Bạn luôn có thể bật lại và nó sẽ trải qua trình tự khởi động thông thường, chuyển qua trạng thái chờ xử lý và quay lại trạng thái đang chạy.
     - Stop-hibernate: Giống với cách bạn lock máy tính xách tay và đóng nắp lại, nhưng khi bạn mở lại, mọi thứ vẫn ở nguyên vị trí nơi bạn để nó. Dữ liệu trong RAM được lưu vào ổ đĩa EBS gốc.
   - Terminate (stop incurring charges): xóa vĩnh viễn instance.
- Pricing: gồm 5 loại:
  - On-Demand Instances: dùng bao nhiêu trả bấy nhiêu (tính trên giờ or giây chạy instance). Phù hợp cho các trường hợp:
    - Người dùng thích chi phí thấp và tính linh hoạt của Amazon EC2 mà không cần trả trước hoặc cam kết sử dụng dài hạn.
    - Ứng dụng có khối lượng công việc ngắn hạn, thường xuyên biến động hoặc có khả năng bị gián đoạn.
    - Ứng dụng đang được phát triển hoặc thử nghiệm trên Amazon EC2 lần đầu tiên.
  - Spot Instances: giảm tới 90% so với giá của On-Demand Instances. Use cases:
    - Các ứng dụng có thời gian bắt đầu và kết thúc thay đổi liên tục như là chạy CI/CD, data analysis, batch jobs, background processing.
    - Người dùng có khối lượng công việc có khả năng chịu lỗi hoặc không có trạng thái.
    - Các ứng dụng chỉ khả thi ở mức giá rất thấp.
  - Reserved Instances: tiết kiệm tới 72% so với giá của On-Demand Instances, phải ký hợp đồng sử dụng. Bạn có thể chọn giữa ba tùy chọn thanh toán: Trả trước toàn bộ, Trả trước một phần hoặc Không trả trước. Bạn có thể chọn thời hạn 1 năm hoặc 3 năm cho mỗi tùy chọn này. Có 3 options:
    - Standard Reserved Instances: giảm nhiều nhất (lên tới 72% so với On-Demand Instances), phù hợp với ứng dụng cố định.
    - Convertible Reserved Instances: rẻ hơn đến 54% so với On-Demand Instance, cung cấp khả năng thay đổi các thuộc tính của Reserved Instances như có thể lấy tài nguyên của nhiều loại instance khác nhau, ví dụ lấy vCPU của loại này và lấy memory của loại khác.
    - Scheduled Reserved Instances:  là loại có thể cố định thời gian bật và tắt instance, chỉ tính tiền trong thời gian bật instance. Loại này phù hợp với các job chạy trong một khoảng thời gian cố định biết trước (VD như batch chạy vào 3h sáng tới 4h sáng mỗi cuối tuần).
  - Savings Plans: phải ký hợp đồng nhưng bạn lại có thể quy định số tiền mình trả để sử dụng hết hoặc một phần giá rẻ của hợp đồng. Ví dụ Reserved Instances hợp đồng 1 năm bạn phải trả phí là 20 đô/giờ để tiết kiệm được 70% so với on-demand Instances, thì Saving Plans bạn có thể chỉ muốn trả 10 đô/giờ để chỉ sử dụng phần giá rẻ đó trong nửa năm, nếu sau nửa năm hết tiền giá rẻ mà bạn không tạo Saving Plans mới thì sẽ tính theo on-demand như bình thường. Use cases:
    - Khối lượng công việc với mức sử dụng nhất quán và ổn định.
    - Khách hàng muốn sử dụng các loại instance và giải pháp điện toán khác nhau ở nhiều địa điểm khác nhau.
    - Khách hàng có thể cam kết tài chính để sử dụng Amazon EC2 trong thời hạn 1 năm hoặc 3 năm.
  - Dedicated Hosts (máy chủ chuyên dụng): là máy chủ Amazon EC2 vật lý được dành riêng cho bạn sử dụng, giúp bạn giảm chi phí vì bạn có thể sử dụng các giấy phép phần mềm gắn với máy chủ hiện có của mình, chẳng hạn như giấy phép Windows Server, SQL Server và Oracle. Dedicated Hosts có thể được mua theo yêu cầu (tính theo giờ) với ưu đãi giảm tới 70% nếu đặt trước.

## 6.2. Containers
- Container: đóng gói mã ứng dụng và các phần phụ thuộc của nó, tạo ra môi trường độc lập của riêng container đó; giúp workload có thể được chuyển từ nơi này sang nơi khác, chẳng hạn như từ quá trình phát triển đến production hoặc từ môi trường tại chỗ lên đám mây. Một ví dụ về nền tảng container là Docker.
- Sự khác biệt giữa VM và container:
  
![image](https://github.com/user-attachments/assets/995224c1-c3a1-4b5a-bd43-0cff7c41011a)

   - Các containers chia sẻ cùng hệ điều hành và kernel với máy chủ mà chúng tồn tại trên đó. Nhưng máy ảo có hệ điều hành riêng. Mỗi máy ảo phải duy trì một bản sao của hệ điều hành, điều này dẫn đến lãng phí tài nguyên ở mức độ nào đó.
   - Container nhẹ hơn, khởi động nhanh hơn, có ưu thế về tốc độ. Còn máy ảo cung cấp toàn bộ sức mạnh của hệ điều hành và nhiều tài nguyên, như cài đặt gói, hạt nhân chuyên dụng, v.v.
- Tổ chức các containers:
  - Trong AWS, containers có thể chạy trên EC2 instances. Hầu hết các công ty và tổ chức đều chạy nhiều containers trên nhiều EC2 instances trên một vài AZ.
  - AWS cung cấp 2 dịch vụ container orchestration: Amazon Elastic Container Service (Amazon ECS) và Amazon Elastic Kubernetes Service (Amazon EKS):
    - ECS:
      
  ![image](https://github.com/user-attachments/assets/02587539-8d63-417b-84db-3e7a1bd03045)

    - EKS: là một dịch vụ được quản lý mà bạn có thể sử dụng để chạy Kubernetes trên AWS mà không cần cài đặt, vận hành và bảo trì.
- ECS khác EKS:
  - An ECS container is called a task. An EKS container is called a pod.
  - Amazon ECS chạy trên công nghệ gốc của AWS. Amazon EKS chạy trên Kubernetes.
  - In Amazon ECS, the machine that runs the containers is an EC2 instance that has an ECS agent installed and configured to run and manage your containers. This instance is called a container instance. In Amazon EKS, the machine that runs the containers is called a worker node or Kubernetes node. 
## 6.3. Serverless 
- Serverless có nghĩa là bạn không thể xem hoặc truy cập vào cơ sở hạ tầng hoặc instance cơ bản đang lưu trữ giải pháp của bạn. Thay vào đó, tất cả việc quản lý môi trường cơ bản từ góc độ cung cấp, mở rộng quy mô, khả năng chịu lỗi và bảo trì đều được AWS đảm bảo. Tất cả những gì bạn cần làm là tập trung vào ứng dụng của mình.
- Tự động mở rộng theo mức sử dụng.
- Serverless services on AWS:
  - Compute: Fargate, Lambda.
  - Data store: Aurora, Redshift, DynamoDB, S3, EFS, RDS Proxy, Neptune, ElastiCache, OpenSearch.
  - Application integration: EventBridge, Step Functions, SQS, SNS, API Gateway, AppSync.
    
### Fargate

![image](https://github.com/user-attachments/assets/fca29408-95c0-4d14-b1ed-04bb722ba950)

- AWS Fargate là nền tảng điện toán serverless dành cho container mà bạn có thể sử dụng với ECS hoặc EKS.
- Fargate allocates the right amount of compute. This eliminates the need to choose and manage EC2 instances, cluster capacity, and scaling.
### Lambda

![image](https://github.com/user-attachments/assets/4e03985d-027a-460d-b2ee-ecd2345e1711)

### Amazon API Gateway

![image](https://github.com/user-attachments/assets/b41f1fbb-34b7-407f-8d8e-2300e131bdcf)

- APIs hoạt động như "cửa trước" để các ứng dụng truy cập dữ liệu, business logic hoặc chức năng từ các dịch vụ backend.
- Bằng cách sử dụng API Gateway, bạn có thể tạo các API RESTful và API WebSocket để kích hoạt các ứng dụng giao tiếp hai chiều theo thời gian thực. API Gateway hỗ trợ các khối lượng công việc có trong container và serverless, cũng như các ứng dụng web.
- API Gateway xử lý tất cả các nhiệm vụ liên quan đến việc chấp nhận và xử lý lên tới hàng trăm nghìn lệnh gọi API đồng thời, bao gồm quản lý lưu lượng, hỗ trợ CORS (Cross-Origin Resource Sharing), kiểm soát ủy quyền và truy cập, điều tiết, giám sát và quản lý phiên bản API.
- API Gateway không có phí tối thiểu hoặc chi phí khởi động. Bạn trả tiền cho các lệnh gọi API mà bạn nhận được cũng như lượng dữ liệu được truyền đi và với mô hình định giá theo bậc của API Gateway, bạn có thể giảm chi phí khi mức sử dụng API của bạn tăng lên.
- Loại API: gồm WEBSOCKET APIs và RESTful APIs, mục đích là xây dựng giao tiếp giữa máy chủ và client.
  
    ![image](https://github.com/user-attachments/assets/3361e04f-9aeb-4233-9ade-e897ef231ad8)

# 7. Storage 
- Có 3 loại lưu trữ:
  
   ![image](https://github.com/user-attachments/assets/7519d070-17d0-4b9c-8c06-b078d172fe2f)

### File storage
- Dữ liệu được lưu trữ dưới dạng tệp theo cấu trúc phân cấp. Mỗi tệp có siêu dữ liệu như tên tệp, kích thước tệp và ngày tạo tệp. Tệp cũng có đường dẫn. Khi bạn cần truy xuất một tệp, hệ thống của bạn có thể sử dụng đường dẫn để tìm tệp đó trong hệ thống phân cấp tệp. File storage là giải pháp lý tưởng khi bạn yêu cầu quyền truy cập tập trung vào các tệp phải được chia sẻ và quản lý dễ dàng bởi nhiều máy tính chủ.
- AWS có 2 dịch vụ:
  - EFS (Elastic File System): một hệ thống tệp cài đặt và quên, tự động tăng và thu nhỏ khi bạn thêm và xóa tệp. Không cần cung cấp hoặc quản lý dung lượng và hiệu suất lưu trữ. Cho phép tạo ra NFSv4 network volume và gán vào nhiều EC2 cùng lúc, chỉ support Linux. Có thể được cấu hình để gắn vào môi trường on-premise qua direct connect hoặc VPN.
  - FSx: là một dịch vụ được quản lý toàn phần mang lại độ tin cậy, bảo mật, khả năng mở rộng và một loạt chức năng giúp việc khởi chạy, chạy và mở rộng quy mô các hệ thống tệp hiệu suất cao trên đám mây trở nên thuận tiện và tiết kiệm chi phí. Support cả windows và linux. Hỗ trợ deduplication. Gán vào nhiều EC2 thông qua giao thức SMB (server message block).
### Block storage

![image](https://github.com/user-attachments/assets/b28c44a6-2537-4dd7-b9fe-7865296fa6f4)

- Volume types:
  - SSD (solid-state drives): được sử dụng cho khối lượng công việc giao dịch có thao tác đọc/ghi thường xuyên với kích thước I/O nhỏ.
    
    ![image](https://github.com/user-attachments/assets/2e80587f-1a20-4f73-ae72-68d95b7a45bf)

  - HDD (hard-disk drives): sử dụng cho streaming workload lớn, cần hiệu suất thông lượng cao.

    ![image](https://github.com/user-attachments/assets/bbae45c8-83bc-4979-9865-f3cb2221cff9)

### Object storage 
- Dữ liệu được lưu trữ dưới dạng object trong bucket, thích hợp để lưu dữ liệu phi cấu trúc và ít thay đổi. 
## 7.1. CloudFront
- Amazon CloudFront là một dịch vụ web giúp tăng tốc độ phân phối nội dung web tĩnh và động, chẳng hạn như các tệp .html, .css, .js và hình ảnh tới người dùng. CloudFront cung cấp nội dung của bạn thông qua mạng lưới trung tâm dữ liệu trên toàn thế giới được gọi là edge locations. Khi người dùng yêu cầu nội dung mà bạn đang phân phát bằng CloudFront, yêu cầu đó sẽ được chuyển đến vị trí biên có độ trễ thấp nhất, để nội dung đó được phân phối với hiệu suất tốt nhất có thể.
  - Nếu nội dung đã ở vị trí biên có độ trễ thấp nhất thì CloudFront sẽ phân phối nội dung đó ngay lập tức.
  - Ngược lại, nó sẽ truy xuất nội dung từ nguồn mà bạn đã chỉ định (S3, MediaPackage channel hoặc máy chủ HTTP). 
- Higher performance: CloudFront đảm bảo rằng các yêu cầu của người dùng cuối được phân phát ở vị trí biên gần nhất; tăng tốc độ phân phối nội dung của bạn bằng cách định tuyến từng yêu cầu của người dùng thông qua **AWS backbone network** để đến vị trí biên. Đồng thời, lưu vào bộ nhớ đệm biên thuộc region các bản sao nội dung của bạn. CloudFront sẽ duy trì các kết nối liên tục với máy chủ gốc để có thể tìm nạp những tệp đó từ máy chủ gốc nhanh nhất có thể.
  
## 7.2. S3

![image](https://github.com/user-attachments/assets/fe87eaa3-8683-400f-8be4-b2fb9701e7bd)

### Storage classes
S3 Standard, S3 Standard-IA, S3 Intelligent-Tiering, S3 Glacier Instant Retrieval, S3 Glacier Flexible Retrieval, và S3 Glacier Deep Archive: các đối tượng sẽ tự động được lưu trữ trên nhiều thiết bị, trải rộng ít nhất là ba Vùng Sẵn Sàng (Availability Zones - AZs). Các AZs này được tách biệt về mặt vật lý với một khoảng cách đáng kể, nhưng so với bất kỳ 1 AZ nào khác, tất cả đều **nằm trong phạm vi 100 km** (60 dặm).

- (1) S3 Intelligent-Tiering: được thiết kế để tối ưu hóa chi phí lưu trữ ở cấp độ object bằng cách tự động di chuyển dữ liệu sang lớp truy cập tiết kiệm chi phí nhất khi tần suất truy cập dữ liệu thay đổi. Chi phí thấp bao gồm việc tự động hóa di chuyển data và giám sát object hàng tháng. 
  - Các đối tượng chưa được truy cập trong 30 ngày liên tiếp: di chuyển sang Infrequent Access tier => tiết kiệm 40% chi phí.
  - Sau 90 ngày liên tục không truy cập: các đối tượng sẽ được chuyển sang bậc Archive Instant Access tier => tiết kiệm tới 68% chi phí lưu trữ.
  - Không yêu cầu kích thước tối thiểu cho các object, nhưng các object **nhỏ hơn 128KB sẽ không auto-tiering**. Những objects này vẫn có thể được lưu tại lớp này nhưng sẽ luôn bị tính phí theo lớp truy cập thường xuyên và không bị tính phí giám sát và tự động hóa.
  - Use case: dành cho dữ liệu có kiểu truy cập không xác định hoặc đang thay đổi, đặc biệt data lakes, data analytics, machine learning, new applications, and user-generated content.
- (2) Amazon S3 Standard: khả năng lưu trữ lâu dài với độ trễ truy cập tính bằng mili giây và hiệu suất thông lượng cao cho dữ liệu được truy cập thường xuyên, thường là nhiều hơn 1 lần/tháng. Use case:  lý tưởng nhất cho dữ liệu được **truy cập hoặc sửa đổi thường xuyên**; data lakes, cloud native applications, dynamic websites, content distribution, mobile and gaming applications, and analytics.
- (3) S3 Express One Zone: có độ trễ thấp nhất, với tốc độ truy cập dữ liệu nhanh hơn tới 10 lần và chi phí yêu cầu thấp hơn 50% so với Amazon S3 Standard; thích hợp cho: machine learning (ML) training and inference, interactive analytics, and media content creation (edit video).
- (4) S3 Standard-Infrequent Access (S3 Standard-IA): dành cho dữ liệu được truy cập ít thường xuyên hơn nhưng yêu cầu truy cập nhanh khi cần. Lý tưởng cho dữ liệu được lưu giữ trong ít nhất một tháng và được truy cập một hoặc hai tháng một lần.
- (5) S3 One Zone-Infrequent Access (S3 One Zone-IA)
- (6) Amazon S3 Glacier:
  - Instant Retrieval: cung cấp bộ lưu trữ có chi phí thấp nhất cho dữ liệu có thời gian tồn tại lâu, **ít truy cập** (mỗi quý một lần); cung cấp khả năng **truy cập nhanh nhất** vào kho lưu trữ; thời gian lưu trữ tối thiểu là 90 ngày.
  - Amazon S3 Glacier Flexible Retrieval: dành cho dữ liệu lưu trữ được truy cập 1-2 lần mỗi năm, không yêu cầu truy cập ngay lập tức nhưng muốn **truy xuất các bộ dữ liệu lớn mà không mất phí**. (sao lưu hoặc khắc phục thảm họa)
  - Amazon S3 Glacier Deep Archive: lưu giữ lâu dài những dữ liệu được truy cập 1-2 lần trong một năm. Chỉ từ 0,00099 USD mỗi GB-tháng, cung cấp bộ lưu trữ có **chi phí thấp nhất trên đám mây, truy xuất lâu (12 tiếng cho Standard retrieval tier)**. Phù hợp cho mục đích bảo vệ tài sản trí tuệ cốt lõi, hồ sơ tài chính và y tế, kết quả nghiên cứu, tài liệu pháp lý, nghiên cứu thăm dò địa chấn và sao lưu dài hạn, đặc biệt là trong các ngành được quản lý chặt chẽ như Dịch vụ tài chính, Chăm sóc sức khỏe , Dầu khí và Khu vực công. Thời gian lưu trữ tối thiểu là 180 ngày.
- (7) S3 on Outposts: cung cấp khả năng lưu trữ đối tượng trong môi trường tại chỗ.
    
![image](https://github.com/user-attachments/assets/fe4326f9-6090-45b4-8e83-b5e868bd664b)

### General purpose bucket and directory bucket
- General purpose bucket: are the **original S3 bucket type**, and a single general purpose bucket can contain objects stored across all storage classes except S3 Express One Zone. They are recommended for most use cases and access patterns.
- Directory bucket: only allow objects stored in the **S3 Express One Zone** storage class, which provides faster data processing within a **single Availability Zone**. They are recommended for **low-latency** use cases. Each S3 directory bucket can support hundreds of thousands of transactions per second (TPS), independent of the number of directories within the bucket.
  
### Amazon S3 Transfer Acceleration
- Amazon S3 Transfer Acceleration cho phép **truyền tập tin một cách nhanh chóng, dễ dàng và bảo mật qua khoảng cách lớn** giữa máy client và Amazon S3 bucket.
- S3 Transfer Acceleration tận dụng AWS Edge Location được phân phối toàn cầu của Amazon CloudFront. Khi dữ liệu đến một AWS Edge Location, dữ liệu được định tuyến tới Amazon S3 bucket của bạn qua một đường dẫn qua mạng đã được tối ưu hóa.
- Mỗi lần bạn sử dụng S3 Transfer Acceleration để tải lên một đối tượng, AWS sẽ kiểm tra xem S3 Transfer Acceleration có nhanh hơn tốc độ truyền thông thường của Amazon S3 hay không. Nếu không, thì AWS sẽ không tính phí sử dụng S3 Transfer Acceleration cho lần truyền đó và có thể bỏ qua Hệ thống S3 Transfer Acceleration cho quá trình tải lên đó.

### Security
- Data: Amazon S3 tự động mã hóa server-side (SSE - S3) tất cả các đối tượng được tải lên bucket (kể từ ngày 5 tháng 1 năm 2023). Ngoài ra, bạn có thể sử dụng thư viện mã hóa của riêng mình để mã hóa dữ liệu trước khi lưu trữ trên Amazon S3.
- Control access to data stored on Amazon S3:
  - IAM (bucket or objects)
  - Bucket and access point policies
  - ACLs (cấp các quyền cụ thể (ví dụ: ĐỌC, VIẾT, FULL_Control) cho những người dùng cụ thể cho một bucket hoặc object riêng lẻ)
  - Query String Authentication (tạo URL tới object, URL này chỉ có hiệu lực trong một khoảng thời gian giới hạn)
  - Service control policies
  - VPC endpoint: đính kèm endpoint policies vào để kiểm soát quyền truy cập vào tài nguyên Amazon S3 mà họ đang kết nối. Có 2 loại VPC endpoints cho S3:
    - Gateway VPC endpoints: là một cổng mà bạn chỉ định trong route table để truy cập S3 từ VPC qua mạng AWS.
    - Interface VPC endpoints: sử dụng private IPs để định tuyến các yêu cầu đến S3 từ VPC, tại chỗ hoặc từ Region khác.
  - S3 Block Public Access.
- AWS PrivateLink for Amazon S3: cung cấp kết nối riêng tư giữa Amazon S3 và on-premise.
- Amazon Macie: là dịch vụ bảo mật được **hỗ trợ bởi AI (cụ thể là ML)** giúp bạn ngăn ngừa mất dữ liệu bằng cách tự động phát hiện, phân loại và bảo vệ dữ liệu nhạy cảm được lưu trữ trong Amazon S3.
  
### Amazon Athena (truy vấn tại chỗ)
- Amazon Athena is an interactive query service that makes it **easy to analyze data** in Amazon S3 using **standard SQL queries**.
- Athena is serverless, so there is no infrastructure to set up or manage, and you can start analyzing data immediately. You don’t even need to load your data into Athena; it works directly with data stored in any S3 storage class.
- To get started, just log into the Athena Management Console, define your schema, and start querying. Amazon Athena uses Presto with full standard SQL support and works with a variety of standard data formats, including CSV, JSON, ORC, Apache Parquet and Avro. While Athena is ideal for quick, ad-hoc querying and integrates with Amazon QuickSight for easy visualization, it can also handle complex analysis, including large joins, window functions, and arrays.

## 7.3. EBS


## 7.4. Glacier

## 7.5. Storage Gateway

# 8. Database

![{84756FCC-0C90-426B-B7F9-2B4141CFF712}](https://github.com/user-attachments/assets/a621e3cc-4ace-4488-a9d5-f8f2e290c56d)

**Relational/SQL/OLTP**

## 8.1. Relational Database Management System (RDMS):
### Relational Database
- Cơ sở dữ liệu quan hệ **tổ chức dữ liệu thành các bảng**. Dữ liệu trong các bảng có thể liên kết với nhau để tạo mối quan hệ.
- Một bảng lưu trữ dữ liệu theo hàng và cột. Một hàng, thường được gọi là bản ghi (record), chứa tất cả thông tin về một mục cụ thể. Các cột mô tả các thuộc tính của một mục.
- Lợi ích khi dùng RD: dùng câu **truy vấn SQL phức tạp**, giảm dư thừa (lưu data vào 1 bảng và các bảng khác truy vấn đến thay vì lưu trong nhiều bảng), quen thuộc (ra đời 1970s), accuracy (đảm bảo rằng dữ liệu có tính toàn vẹn cao và tuân thủ nguyên tắc).
- Use cases:
  - Những ứng dụng có lược đồ cố định và **không thay đổi thường xuyên**.
  - Những ứng dụng **cần lưu trữ liên tục** và tuân theo nguyên tắc **ACID** (Atomicity, Consistency, Isolation, and Durability), chẳng hạn như: Ứng dụng hoạch định nguồn lực doanh nghiệp (ERP) Ứng dụng quản lý quan hệ khách hàng (CRM).
### Amazon Relational Database Service
- Là một dịch vụ quản lý cho phép bạn triển khai và quản lý các cơ sở dữ liệu quan hệ trên AWS. 
- Storage in the RDS:
   - EBS: MySQL, MariaDB, PostgreSQL, Oracle, and SQL Server. 
   - Cluster volumes: Aurora - lưu trữ dữ liệu trong một tầng lưu trữ riêng biệt, phân tán, và được quản lý bởi AWS.
   - Có 3 loại lưu trữ: General Purpose SSD (also called gp2 and gp3 - nhu cầu I/O trung bình, hiệu quả về chi phí), Provisioned IOPS SSD (also called io1 - yêu cầu I/O cao, độ trễ thấp), and Magnetic (also called standard).
- RDS **tự động xử lý các nhiệm vụ** như sao lưu dữ liệu, sao chép dữ liệu cho độ tin cậy cao, thiết lập môi trường mạng bảo mật, quản lý các phiên bản cơ sở dữ liệu và cung cấp khả năng mở rộng linh hoạt. Việc mở rộng, sao chép và tính sẵn có chỉ cần một nút nhấn.
- Use case: Build web and mobile applications, Move to managed databases, break free from legacy databases
- Mặc định, khách hàng được phép có tối đa 40 DB instances Amazon RDS (chỉ có 10 trong số này có thể là Oracle hoặc MS SQL trừ khi bạn có giấy phép riêng của mình).
- Sự kiện và thông báo: RDS sử dụng AWS SNS để gửi sự kiện RDS qua thông báo SNS. Bạn có thể sử dụng API calls đến dịch vụ Amazon RDS để liệt kê các sự kiện RDS trong 14 ngày qua (API DescribeEvents). Bạn có thể xem các sự kiện trong 14 ngày qua bằng dòng lệnh CLI. Sử dụng AWS Console, bạn chỉ có thể xem các sự kiện RDS trong 1 ngày qua.
- Các yêu cầu không phù hợp cho RDS:
  
![image](https://github.com/user-attachments/assets/1e442d59-2f8f-41ec-ad5b-45e5b020420a)

- Hỗ trợ **Read Replicas** => có khả năng mở rộng khả năng read hiệu quả.
- **Automated Backup with Point** in time restore feature (up to **35** days)
- **Manual DB Snapshot** for longer-term recovery
- Managed and Scheduled maintenance (with downtime)
- **Amazon RDS Multi-AZ**: creates a redundant copy of your database in another Availability Zone. Bạn không thể chọn AZ nào trong AZ sẽ được chọn để tạo bản sao DB dự phòng.

![image](https://github.com/user-attachments/assets/d10ce159-beaf-4e8f-8206-eb68c08bad7e)

- Amazon RDS security:
  - SSL/TLS: Use Secure Sockets Layer (SSL) or Transport Layer Security (TLS) connections with DB instances running the MySQL, MariaDB, PostgreSQL, Oracle, or SQL Server database engines.
  - RDS encryption: to secure your DB instances and snapshots at rest.
  - IAM: to assign permissions that determine who can manage Amazon RDS resources.
  - Security Group: to control which IP addresses or Amazon EC2 instances can connect to your databases on a DB instance.

![image](https://github.com/user-attachments/assets/e1df3cde-9445-4fbe-b898-5fc9a287fa24)

![image](https://github.com/user-attachments/assets/8a462c72-0754-4f0c-8e10-3276c3c9253b)

## 8.2. Amazon Aurora

![{E52EEC45-FFA8-464D-A999-51D90EBD4427}](https://github.com/user-attachments/assets/602d8480-17df-4db5-9836-d4a84b7f7d70)

![{6C31027D-1C9B-42E6-954E-33D73107B2E2}](https://github.com/user-attachments/assets/7092993d-577d-41a0-a4ea-855cb574f8d5)

**Non-relational/NoSQL database:**

## Sumary

![{C32E72EB-42CD-4D49-AFD7-057848AD1887}](https://github.com/user-attachments/assets/33d253f1-234b-4df3-8bf7-5ba667712209)

- Cách chọn loại db theo mục đích sử dụng:
  - Amazon DynamoDB: fully managed NoSQL database, phù hợp high-scale applications and serverless applications. High concurrency and connections for millions of users and millions of requests per second
  - Amazon ElastiCache: fully managed, in-memory caching solution. It provides support for two open-source, in-memory cache engines: Redis and Memcached. Lưu trữ tạm thời nhanh cho lượng dữ liệu nhỏ, dữ liệu biến động cao.
  - Amazon MemoryDB for Redis: hiệu suất cực nhanh, độ trễ đọc micro giây, độ trễ ghi mili giây một chữ số, thông lượng cao và độ bền Multi-AZ cho các ứng dụng hiện đại.
  - Amazon DocumentDB (with MongoDB compatibility): fully managed document database, có khả năng tương thích API với MongoDB.
  - Amazon Neptune: fully managed graph database, use for recommendation engines, fraud detection, and knowledge graphs.
  - Amazon Timestream: Dữ liệu chuỗi thời gian là một chuỗi các điểm dữ liệu được ghi lại trong một khoảng thời gian. Nó được sử dụng để đo lường các sự kiện thay đổi theo thời gian, chẳng hạn như giá cổ phiếu theo thời gian hoặc đo nhiệt độ theo thời gian. Nhanh, rẻ, có thể mở rộng và không cần máy chủ dành cho Internet of Things (IoT) và các ứng dụng vận hành.
  - Amazon Quantum Ledger Database (Amazon QLDB): được xây dựng với mục đích cung cấp lịch sử đầy đủ và có thể xác minh bằng mật mã về tất cả các thay đổi được thực hiện đối với dữ liệu ứng dụng của bạn.
  - Amazon Keyspaces (for Apache Cassandra): tương thích với Apache Cassandra có khả năng mở rộng, có tính sẵn sàng cao và được quản lý, phổ biến cho các ứng dụng quy mô cao cần hiệu năng cao nhất.
- Database Types:
  - RDBMS (= SQL / OLTP): RDS, Aurora – great for joins
  - NoSQL database – no joins, no SQL : DynamoDB (~JSON), ElastiCache (key/value pairs), Neptune (graphs), DocumentDB (for MongoDB), Keyspaces (for Apache Cassandra)
  - Object Store: S3 (for big objects) / Glacier (for backups / archives)
  - Data Warehouse (= SQL Analytics / BI): Redshift (OLAP), Athena, EMR
  - Search: OpenSearch (JSON) – free text, unstructured searches
  - Graphs: Amazon Neptune – displays relationships between data
  - Ledger: Amazon Quantum Ledger Database
  - Time series: Amazon Timestream
  
# 9. AWS Management Tools
## 9.1. IAM
- AWS Identity and Access Management (IAM) is an AWS service that helps you manage access to your AWS account and resources. It also provides a centralized view of who and what are allowed inside your AWS account (authentication), and who and what have permissions to use and work with your AWS resources (authorization).
- Với IAM, bạn có thể chia sẻ quyền truy cập vào tài khoản và tài nguyên AWS mà không cần chia sẻ bộ khóa truy cập hoặc mật khẩu. Bạn cũng có thể cung cấp quyền truy cập chi tiết cho những người làm việc trong tài khoản của mình để mọi người và dịch vụ chỉ có quyền đối với những tài nguyên họ cần.
### IAM features
- Global: IAM mang tính toàn cầu và không dành riêng cho bất kỳ Region nào. Bạn có thể xem và sử dụng cấu hình IAM của mình từ bất kỳ Khu vực nào trong AWS Management Console.
- Free to use.
### IAM user
- Là một chủ thể được người dùng tạo trong aws và được sử dụng để đại diện cho một người hoặc một service tương tác với AWS.
- When to create an IAM user (instead of a role)?
  - Workloads that cannot use IAM roles.
  - Third-party AWS clients: không host trên AWS được nên không dùng IAM role để phân quyền được.
  - AWS CodeCommit (dùng để lưu trữ code) access.
  - Amazon Keyspaces (for Apache Cassandra) access.
  - Emergency access.
### IAM groups
- Là một tập hợp người dùng. Tất cả người dùng trong nhóm sẽ kế thừa các quyền được gán cho nhóm. Điều này cho phép ta cấp quyền cho nhiều người dùng cùng một lúc. 
- Bạn không thể lồng các IAM group. Người dùng IAM riêng lẻ có thể thuộc nhiều nhóm, nhưng không thể tạo nhóm con trong một IAM group khác.
- Lợi ích: Cung cấp một cách để xem ai có quyền gì trong tổ chức. Nó cũng giúp mở rộng quy mô khi có người mới tham gia, rời đi hay thay đổi vai trò trong tổ chức.
### IAM policies
- Để quản lý quyền truy cập và cấp quyền cho các dịch vụ và tài nguyên AWS. AWS cũng có cung cấp những policies có sẵn cho user, ví dụ như AmazonEC2FullAccess,...
- Hầu hết các chính sách đều được lưu trữ trong AWS dưới dạng tài liệu JSON với một số thông tin cơ bản như Version, Effect, Action, và Resource.
- Ví dụ:
  
  ![image](https://github.com/user-attachments/assets/1256b014-290d-483a-b2e2-6c4bbf80c976)
   #### IAM Permission Boundary
  - AWS hỗ trợ Permission Boundary cho các thực thể IAM (users or roles). Permission Boundary là một tính năng nâng cao để sử dụng chính sách được quản lý nhằm đặt các quyền tối đa mà chính sách dựa trên danh tính có thể cấp cho thực thể IAM. Quyền hạn có hiệu lực (effective permissions) của thực thể sẽ bao gồm những quyền được cho phép bởi cả Permission Boundary và chính sách quyền dựa trên danh tính của thực thể đó (Identity-based policy).

    ![image](https://github.com/user-attachments/assets/0c0609e5-a1e5-4b89-b2cb-972898248424)

  - Tại sao sử dụng IAM Permission Boundary?

    Hữu ích khi số lượng user tăng lên và những thay đổi liên tục trong vai trò công việc của các user yêu cầu bạn phải tạo ra thêm nhiều chính sách quyền mới. Để đơn giản hóa công tác quản lý quyền, thay vì bạn phải chỉnh sửa từng chính sách quyền, bạn có thể áp dụng Permission Boundary một cách nhanh chóng và đồng loạt để giúp bạn đóng những lỗ hổng về privilege escalation.
  - Ví dụ về policy giới hạn quyền: Đoạn JSON có ý nghĩa rằng mọi hành động đối với tất cả dịch vụ EC2 từ mọi tài nguyên đều được cho phép với điều kiện rằng dịch vụ EC2 đó phải ở region ap-southeast-1 (Singapore).
    
    ![image](https://github.com/user-attachments/assets/970f95f1-c874-403d-8a82-4e2fe5a1bd03)
  
### IAM role
- Phân quyền truy cập tạm thời: Thay vì gán quyền trực tiếp cho người dùng hoặc dịch vụ, bạn có thể tạo một IAM Role với các quyền cụ thể và sau đó gán role này cho người dùng, dịch vụ hoặc ứng dụng khi họ cần truy cập.
- Tăng cường bảo mật: IAM Role giúp giảm rủi ro bảo mật bằng cách cung cấp quyền truy cập chỉ khi cần thiết và không cần sử dụng thông tin đăng nhập tĩnh (như Access Keys) cho các dịch vụ AWS.
- Linh hoạt trong quản lý: Bạn có thể gán, thu hồi hoặc thay đổi IAM Role một cách dễ dàng mà không cần phải thay đổi cấu hình hoặc quyền hạn của người dùng hoặc dịch vụ.
- Ví dụ: Truy cập dịch vụ khác từ EC2: Giả sử bạn có một ứng dụng chạy trên một EC2 instance cần truy cập vào một S3 bucket để lưu trữ hoặc đọc dữ liệu. Thay vì gán trực tiếp Access Key và Secret Key cho ứng dụng, bạn có thể tạo một IAM Role với quyền truy cập S3 và gán role này cho EC2 instance. Điều này cho phép ứng dụng truy cập S3 mà không cần quản lý thông tin đăng nhập.
#### Role condition
- Tham khảo: https://000044.awsstudygroup.com/
- AWS STS (Security Token Service) là dịch vụ web cho phép người dùng yêu cầu thông tin xác thực tạm thời, có đặc quyền hạn chế để người dùng truy cập tài nguyên AWS mà không cần tạo danh tính AWS. AWS Temporary Credentials được tạo ra bởi Assume Role có thời hạn hiệu lực trong vòng 3600s (1 tiếng) để kéo dài thời gian này cần dùng thêm options *--duration-seconds* với giá trị từ 900s (15 phút) tới 43200s (12 giờ).
- Quá trình assume role (có thể hiểu nôm na là "Ủy thác Vai trò"): 

   ![image](https://github.com/user-attachments/assets/d02a9d7d-2013-430f-92a7-c259f90b9605)

  - IAM user sẽ có thông tin chứng thực dài hạn ( password / acccesskey & secretaccesskey ) và sẽ dùng thông tin chứng thực dài hạn đó để request tới AWS Security Token Service ( AWS STS ) và thực hiện action sts:AssumeRole.
  - STS sẽ thực hiện kiểm tra xem IAM user có quyền để thực hiện action này hay không thông qua kiểm tra Trust Relationship ( gán vào Role ) và Identity Policy ( gán vào IAM User ). Nếu quá trình STS kiểm tra thành công, STS sẽ trả về thông tin chứng thực tạm thời.
  - IAM user sẽ sử dụng thông tin chứng thực tạm thời để thực hiện các request (API call) tới các dịch vụ của AWS. (IAM User ở thời điểm này sẽ có các quyền hạn được gán vào IAM role mà IAM User đã assume).
- Trusted entity là thực thể (service, account, custom trust policy,...) được phép assume role.
- Thực hành: Lab 000044:
  - Tạo 1 IAM Group có quyền truy cập admin tới cả hai dịch vụ EC2 và RDS: *ec2-rds-admin-group*
  - Thực hiện tạo 4 IAM user: *EC2-admin-user*, *RDS-admin-user*, *Group-user* (user được gán quyền quản trị thông qua IAM User Group được tạo ở trên), *No-permission-user* (user không có quyền gì cả, sẽ được dùng để tiếp nhận IAM role có quyền Admin).
  - Tạo IAM Role: *lab44-RoleFullAccess* có quyền Admin.
  - Cấu hình Switch role: cấu hình role *lab44-RoleFullAccess* để cho phép user *No-permission-user* sử dụng được role này.
    - Sao chép thông tin User ARN của *No-permission-user*.
    - Edit trust relationship của role *lab44-RoleFullAccess*: nhằm mục đích siết chặt khả năng sử dụng role này - chỉ sử dụng role khi thỏa các condition. Thêm thông tin:
      
      ![image](https://github.com/user-attachments/assets/a6368baa-5386-4788-bd76-4697ac455fa4)

    - Log in user *No-permission-user* -> Switch Role -> nhập các thông tin gồm ID của role và tên role.
    - Edit trust relationship để bổ sung thêm condition (như IP, thời gian,...) tùy thuộc vào mục đích sử dụng role.
### Best practices
- Lock down the AWS root user.
- Follow the principle of least privilege
- Use IAM appropriately
- Use IAM roles when possible
- Consider using an identity provider
- Regularly review and remove unused users, roles, and other credentials

## 9.2. CloudWatch (Application)
- CloudWatch là một dịch vụ thu thập, giám sát và phân tích dữ liệu, nguồn tài nguyên của ứng dụng; cung cấp thông tin để định hướng hành động, gửi thông báo, hỗ trợ việc tối ưu hóa hiệu năng ứng dụng, quản lý sử dụng tài nguyên và hiểu rõ tình trạng hoạt động của toàn hệ thống.

  ![image](https://github.com/user-attachments/assets/859bb721-bf25-4b37-b3a9-f39174a3d01b)

- CloudWatch sử dụng metrics - là dữ liệu về hiệu suất của hệ thống của bạn.
  
![image](https://github.com/user-attachments/assets/a155fe6f-c8e5-44f6-9009-6bbdffc80b34)

- Các loại metrics:
  
  ![image](https://github.com/user-attachments/assets/8725b74d-e6ac-44cc-9b8c-ea1622d1997e)

- CloudWatch hiển thị dữ liệu số liệu và nhật ký chi tiết đến từng giây, duy trì dữ liệu trong 15 tháng và cho phép tính toán trên số liệu.
- Có thể truy cập Amazon CloudWatch thông qua API, CLI, các AWS SDK và AWS Management Console.
- Trong compute domain, CloudWatch có thể thông báo cho bạn về tình trạng của EC2 intances, Autoscaling Groups, Elastic Load Balancers, and Route53 Health Checks. Trong storage and content delivery domains, CloudWatch có thể thông báo cho bạn về tình trạng của EBS Volumes, Storage Gateways, và CloudFront.
- Liên quan đến EC2, CloudWatch chỉ có thể giám sát các số liệu ở cấp độ máy chủ như CPU, mạng, ổ đĩa và kiểm tra trạng thái để biết thông tin chi tiết như tình trạng của trình ảo hóa cơ bản.
- CloudWatch tập trung vào hiệu suất. CloudTrail chủ yếu là kiểm tra (auditing).
- Cách hoạt động:
  
  ![image](https://github.com/user-attachments/assets/2823c6ea-67d9-44a8-9519-50dbc8285239)
  
### CloudWatch alarms
- Gửi thông báo hoặc tự động thực hiện thay đổi khi vượt giá trị ngưỡng đối với tài nguyên bạn đang theo dõi dựa trên các quy tắc bạn xác định.
- Có 3 trạng thái:
  - OK: Số liệu nằm trong ngưỡng được xác định. Mọi thứ dường như đang hoạt động như bình thường.
  - ALARM: Số liệu nằm ngoài ngưỡng được xác định. Đây có thể là một vấn đề hoạt động.
  - INSUFFICIENT_DATA: Cảnh báo vừa mới bắt đầu, metric không có sẵn hoặc không có đủ dữ liệu cho metric để xác định trạng thái cảnh báo.
### Amazon CloudWatch Logs
- Là nơi tập trung để lưu trữ và phân tích nhật ký. Với dịch vụ này, bạn có thể giám sát, lưu trữ và truy cập các tệp nhật ký của mình từ các ứng dụng chạy trên phiên bản EC2, hàm AWS Lambda và các nguồn khác.
- Cách sắp xếp dữ liệu trong CloudWatch Logs:
  - Event logs: là bản ghi hoạt động được ghi lại bởi ứng dụng hoặc tài nguyên đang được giám sát. Nó có dấu thời gian và thông báo sự kiện.
  - Stream logs: Các event logs được nhóm thành stream logs - là chuỗi các sự kiện nhật ký thuộc về cùng một tài nguyên đang được theo dõi.
  - Group logs: bao gồm các stream logs đều có chung cài đặt quyền và lưu giữ.
    
  ![image](https://github.com/user-attachments/assets/4f768068-64c3-4b98-af7c-59451e09065e)
 
### CloudWatch Dashboards:
- Là các trang chủ có thể tùy chỉnh trong bảng điều khiển CloudWatch mà bạn có thể sử dụng để giám sát tài nguyên của mình trong một chế độ xem duy nhất.
- CloudWatch Dashboards tích hợp với CloudWatch Metrics và CloudWatch Alarms để tạo chế độ xem tùy chỉnh về số liệu và cảnh báo cho tài nguyên AWS của bạn.
## 9.3. CloudTrail (AWS Account)

![image](https://github.com/user-attachments/assets/ad53f89b-f7ec-472a-83a5-fa140a316b34)

- AWS CloudTrail: là một dịch vụ audit cho tài khoản AWS. Actions taken by a user, role, or an AWS service are recorded as events in CloudTrail. Các events bao gồm các hành động được thực hiện trong AWS Management Console, AWS Command Line Interface, và AWS SDKs và APIs. Event được lưu lại tối đa 90 ngày trên CloudTrail (enabled by default and is no additional cost).
- Use case:
  - Tuân thủ & kiểm toán: sử dụng CloudTrail logs để chứng minh việc tuân thủ những quy định như SOC, PCI và HIPAA.
  - Bảo mật: Cải thiện tình hình bảo mật của bạn bằng cách ghi lại các sự kiện và hoạt động của người dùng, đồng thời thiết lập quy tắc luồng công việc tự động với Amazon EventBridge.
  - Vận hành: Trả lời các câu hỏi vận hành, tạo điều kiện thuận lợi cho việc gỡ lỗi và điều tra các vấn đề.
- Các sự kiện thường được cập nhật trong CloudTrail trong 15 phút sau lệnh gọi API.
- Bạn có thể lọc các sự kiện bằng cách chỉ định ngày và giờ xảy ra lệnh gọi API, người dùng đã yêu cầu hành động, loại tài nguyên liên quan đến lệnh gọi API,...
- Các sự kiện được ghi lại có thể được lưu trữ trong Amazon S3. CloudTrail có thể được tích hợp với Amazon CloudWatch để tạo ra các cảnh báo khi có các sự kiện quan trọng, hoặc kết hợp với AWS Lambda để tự động phản hồi các sự kiện cụ thể.
- CloudTrail cung cấp 3 cách để record sự kiện:
  - Event history (free): cung cấp bản ghi có thể xem, tìm kiếm, tải xuống và không thể thay đổi về các sự kiện quản lý trong 90 ngày qua trong Region.
  - CloudTrail Lake (có phí): là managed data lake để thu thập, lưu trữ, truy cập và phân tích hoạt động của người dùng và API trên AWS nhằm mục đích kiểm tra và bảo mật. CloudTrail Lake chuyển đổi các sự kiện hiện có ở định dạng JSON dựa trên hàng sang định dạng ORC của Apache (để truy xuất dữ liệu nhanh chóng). Bạn có thể lưu giữ dữ liệu sự kiện trong kho lưu trữ dữ liệu sự kiện trong tối đa 3.653 ngày (khoảng 10 năm) tùy vào gói dịch vụ bạn chọn.
  - Trails (có tính phí lưu trữ trên S3): capture a record of AWS activities, delivering and storing these events in an Amazon S3 bucket, with optional delivery to CloudWatch Logs and Amazon EventBridge. Bạn có thể gửi miễn phí một bản sao các sự kiện quản lý đang diễn ra tới bộ chứa S3 của mình từ CloudTrail bằng cách tạo một trail, tuy nhiên, sẽ phải trả phí lưu trữ trên Amazon S3.
- CloudTrail Insights: Dùng để tự động phát hiện các hoạt động API bất thường trong tài khoản AWS của bạn. Mỗi hoạt động, bao gồm các hành động được thực hiện qua AWS Management Console, AWS SDK, Command Line Tools, và các dịch vụ AWS khác, đều được ghi lại dưới dạng "sự kiện" và lưu trữ để bạn có thể xem lại và phân tích sau này.
- Data protection in AWS CloudTrail: By default, CloudTrail event log files are encrypted using Amazon S3 server-side encryption (SSE). You can also choose to encrypt your log files with an AWS Key Management Service (AWS KMS) key.
- Types of events that can be logged in CloudTrail: management events and data events.
  - Management events: cung cấp khả năng hiển thị các hoạt động quản lý được thực hiện trên các tài nguyên trong tài khoản AWS của bạn. Ví dụ:
    - Configuring security.
    - Configuring rules for routing data.
  - Data events: provide information about the resource operations performed on or in a resource. Ví dụ:
    - Amazon S3 object-level API activity (for example, GetObject, DeleteObject, and PutObject API operations) on objects in S3 buckets.
    - AWS Lambda function execution activity (the Invoke API).
- By default, CloudTrail logs management events, but not data events.
# 10. CloudFormation
- Là dịch vụ IaC (Infrastructure as Code), giúp bạn lập mô hình và thiết lập tài nguyên AWS để bạn tiết kiệm thời gian cho việc quản lý các tài nguyên đó và có nhiều thời gian hơn để tập trung vào các ứng dụng chạy trong AWS.
- You create a template that describes all the AWS resources that you want (like Amazon EC2 instances or Amazon RDS DB instances) => CloudFormation takes care of provisioning and configuring those resources for you.
- CloudFormation is a **free** service; however, you are charged for the AWS resources you include in your stacks at the current rates for each
- Những trường hợp CloudFormation hữu ích:
  - Simplify infrastructure management: when you use that template to create a CloudFormation stack, CloudFormation provisions the Auto Scaling group, load balancer, and database for you
  - Quickly replicate your infrastructure: reuse your template
  - Easily control and track changes to your infrastructure: these templates are text files, you simply track differences in your templates to track changes to your infrastructure.
## How CloudFormation works?

![{CFE53A99-80A8-463C-BB5A-D6E5181BAACD}](https://github.com/user-attachments/assets/e10e0879-c708-478b-9867-a11268ca2c6b)

- Template:
  - Định dạng file: JSON or YAML; có thể lưu extention .json, .yaml, .template, hoặc .txt
  - Templates as blueprints for building your AWS resource
  - CloudFormation templates have additional capabilities that you can use to build complex sets of resources and reuse those templates in multiple contexts.
- Stack:
  - You create, update, and delete a collection of resources by creating, updating, and deleting stacks.
  - To create those resources, you create a stack by submitting the template that you created, and CloudFormation provisions all those resources for you.
- Change sets:
  - A summary of your proposed changes.
  - Allow you to see **how your changes might impact your running resources**, especially for critical resources, before implementing them.
  - Updates can cause interruptions.
## Security in AWS CloudFormation
- Prevent a stack from being accidentally deleted by enabling termination protection on the stack.
- Prevent stack resources from being unintentionally updated or deleted during a stack update by using a stack policy.
- Data protection:
  - Encryption at rest: AWS CloudFormation stores your data encrypted at rest. Customers are responsible for setting encryption and storage policies for data stored in their accounts.
  - Encryption at transit: CloudFormation uses encrypted channels for service communications
  - Internetwork traffic privacy: AWS CloudFormation service communications are securely encrypted by default between Regions or Availability Zones.
- Control CloudFormation access with IAM
- Logging AWS CloudFormation API calls with AWS CloudTrail
- Resilience
- Compliance validation for AWS CloudFormation
- Configuration and vulnerability analysis
- Security best practices for CloudFormation:
  - Use IAM to control access
  - Do not embed credentials in your templates
  - Use AWS CloudTrail to log CloudFormation calls
- AWS PrivateLink: use AWS PrivateLink to create a private connection between your VPC and CloudFormation. 
# 11. AWS Billing and Cost Management
### Sử dụng để làm gì?
  - Ước tính và lập kế hoạch chi phí AWS của bạn.
  - Nhận thông báo nếu chi phí của bạn vượt quá hoặc đạt đến ngưỡng.
  - Đánh giá khoản đầu tư lớn nhất của bạn vào tài nguyên AWS.
  - Tổ chức hợp lý sổ sách kế toán nếu bạn làm việc với nhiều tài khoản AWS.
### Month-to-date (MTD)

Là một khoảng thời gian bắt đầu từ đầu tháng và kết thúc ở ngày hiện tại trong tháng đó.

Ví dụ: nếu ngày hôm nay là ngày 15, bạn được sếp yêu cầu tính sales trong tháng hiện tại, bạn sẽ tính tổng sales từ ngày 1 đến ngày 14 (ngày 15 chưa kết thúc).

### AWS Cost Management Console 
- Sử dụng để tối ưu hóa chi phí trong tương lai.
- Daily unblended costs là thuật ngữ trong quản lý chi phí đám mây (cloud cost management), đề cập đến tổng chi phí mà bạn phải thanh toán cho tất cả các dịch vụ và tài nguyên cloud mà bạn đã sử dụng trong một ngày cụ thể, không phân tách ra theo từng dịch vụ hay loại tài nguyên cụ thể.
### Các dịch vụ liên quan đến chi phí
  
  ![image](https://github.com/user-attachments/assets/0510451e-1db7-4cb9-85e5-4c2c23eba502)
- Establish visibility:
  - Cost Explorer: Cost Explorer là tính năng của Cost Management mà bạn có thể sử dụng để trực quan hóa và hiểu rõ hơn về chi phí và mức sử dụng của mình. Sau khi kích hoạt dịch vụ này, bạn có thể xem lại dữ liệu chi phí lịch sử trong 12 tháng qua và Cost Explorer có thể sử dụng dữ liệu đó để dự đoán số tiền bạn có thể chi tiêu trong 12 tháng tới.
  - Cost and Usage Reports:
    - Theo dõi mức sử dụng AWS của bạn và cung cấp mức phí ước tính cho tài khoản. Các báo cáo cung cấp quyền truy cập vào dữ liệu chi tiết, giúp bạn phân tích và hiểu rõ hơn về chi phí AWS của mình, cũng như các dịch vụ sản phẩm cụ thể và lượng sử dụng làm cơ sở cho các chi phí đó. Mỗi báo cáo chứa các mục hàng cho từng tổ hợp sản phẩm AWS, loại sử dụng và hoạt động duy nhất mà bạn sử dụng trong tài khoản AWS của mình.
    - Báo cáo chi phí và mức sử dụng sẽ hữu ích nhất nếu chúng tôi muốn chạy truy vấn tùy chỉnh trên dữ liệu chi phí hoặc xây dựng ứng dụng báo cáo của riêng mình. Ngoài ra, mức độ chi tiết cao trong các báo cáo này sẽ hữu ích nếu chúng tôi phát hiện chi phí bất thường nào và chúng tôi cần điều tra
- Avoiding overspend with AWS:
  - AWS Budgets: Sử dụng để theo dõi và quản lý chi phí AWS của mình. Khi tạo ngân sách, bạn tạo một ranh giới trên một cách hiệu quả mà bạn muốn chi phí của mình duy trì trong khoảng thời gian đã định cấu hình. Bạn có thể theo dõi chi phí chuyên sâu bằng cách thêm các bộ lọc liên quan đến dịch vụ AWS, tài khoản thành viên, Khu vực AWS, thẻ, v.v. Ví dụ: bạn có thể muốn theo dõi chi tiêu hàng tháng cho môi trường phát triển có thẻ cụ thể được gắn vào từng tài nguyên.

  - AWS Cost Anomaly Detection: Phát hiện chi phí bất thường của AWS là một tính năng Quản lý chi phí AWS sử dụng ML để liên tục theo dõi chi phí và mức sử dụng của bạn nhằm phát hiện các khoản chi tiêu bất thường. Công cụ này có thể được sử dụng như một yếu tố giảm thiểu khác đối với việc nhận các hóa đơn bất ngờ vào cuối tháng. 
### Cảnh báo vượt ngưỡng của AWS

AWS Budget bao gồm 4 loại cảnh báo:

- Cost Budget: gửi cảnh báo khi tổng chi phí vượt qua ngưỡng chi phí trong ngân sách.
- Usage Budget: gửi cảnh báo khi tổng mức sử dụng theo từng dịch vụ bạn lựa chọn vượt qua ngưỡng mức sử dụng trong ngân sách.
- RI Budget: gửi cảnh báo dựa trên mức sử dụng các dịch vụ trả trước (reserve instance) của bạn.
- Savings Plans Budget: gửi cảnh báo dựa trên mức sử dụng các dịch vụ đã được quy định ở trong savings plans.
# 12. AWS CLI
## Bật tính năng tự động gợi ý (auto-prompt mode)
`aws --cli-auto-prompt`
  
  ![image](https://github.com/user-attachments/assets/52051188-d468-4e26-aa00-b9ef11f33869)

## Tương tác với S3
- Tạo S3 bucket: `aws s3 mb s3://<name_bucket>` .Do tên bucket là duy nhất trên global nên tôi đã thêm các ký tự rác.
  
  ![image](https://github.com/user-attachments/assets/895686b5-c3dc-4756-82f5-820967705846)

- Kiểm tra danh sách s3 bucket: `aws s3 ls`
  
  ![image](https://github.com/user-attachments/assets/72c1ea10-718d-43bb-a46d-fddd994086e6)
  
- Kiểm tra object trong s3 bucket: `aws s3 ls s3://<bucket-name>`
- Xóa object: `aws s3 rm s3://<bucket-name>/<object>`
- Xóa bucket: `aws s3 rb <target>`
  
  ![image](https://github.com/user-attachments/assets/c781a54c-f63f-47be-9278-45d6477e3290)

## Tương tác với VPC
- Tạo VPC: `aws ec2 create-vpc <option> <value>`
  
  ![image](https://github.com/user-attachments/assets/4df4afee-e832-4abc-b5e9-f2af3d009096)

- Tạo subnet: `aws ec2 create-subnet --vpc-id <VPC id> --cidr-block <dải IP>`

  ![image](https://github.com/user-attachments/assets/79faf861-ca18-4ac4-8509-d90aaaebbb2c)

- Tạo Internet Gateway: `aws ec2 create-internet-gateway`
- Attach internet gateway: `aws ec2 attach-internet-gateway --vpc-id <VPC-ID> --internet-gateway-id <IGW ID>`
- Tạo route table: `aws ec2 create-route-table --vpc-id <VPC-ID> --query RouteTable.RouteTableId --output text`
- Định tuyến Route table: `aws ec2 create-route --route-table-id <RTB ID> --destination-cidr-block 0.0.0.0/0 --gateway-id <IGW ID>`
- Associate route table: `aws ec2 associate-route-table  --subnet-id <subnet ID> --route-table-id <RTB ID>`
# 13. WAF (Web application firewall)
- Giúp bảo vệ các ứng dụng web ở layer 7 khỏi các cuộc tấn công bằng cách cho phép định cấu hình các quy tắc allow, block hoặc monitor (đếm) yêu cầu web dựa trên các điều kiện mà bạn xác định. Các điều kiện này bao gồm địa chỉ IP, tiêu đề HTTP, nội dung HTTP, URI string, SQL injection và cross-site scripting.
- WAF với Amazon CloudFront, Application Load Balancer (ALB), Amazon API Gateway, AWS AppSync:
  - Áp dụng AWS WAF trên Amazon CloudFront: các rules sẽ chạy ở tất cả các Vị trí biên AWS, nằm trên khắp thế giới, gần với người dùng cuối. Bảo mật không ảnh hưởng đến hiệu suất. Các yêu cầu bị chặn sẽ bị dừng trước khi chúng đến được máy chủ web.
  - Dùng AWS WAF trên regional services (như Application Load Balancer, Amazon API Gateway, AWS AppSync): rules run in region and can be used to protect internet-facing resources as well as internal resources.
- Mối quan hệ tích hợp giữa AWS WAF và API Gateway, ALB và CloudFront:
  - Mỗi WebACL chỉ có thể được gắn vào một loại dịch vụ cụ thể tại một thời điểm. 
  - Các dịch vụ regional như API Gateway, ALB, AppSync chỉ có thể gắn với 1 WAF. Ngược lại thì không đúng, AWS WAF (Web Application Firewall) có thể bảo vệ nhiều service bằng cách tạo các WebACL (Web Access Control List) khác nhau và gắn chúng với các tài nguyên tương ứng. 
# Nguồn tham khảo
- Mindmap: https://github.com/notcuder/aws-mindmap?tab=readme-ov-file
- Tổng hợp kiến thức ôn thi SAA: https://github.com/keenanromain/AWS-SAA-C02-Study-Guide?tab=readme-ov-file
- Note lý thuyết cơ bản về AWS: https://github.com/skulltech/aws-solutions-architect-associate-notes?tab=readme-ov-file
- Khóa học cơ bản Practitioner Essentials: https://explore.skillbuilder.aws/learn/course/134/play/136404/aws-cloud-practitioner-essentials
- Technical Essentials: https://explore.skillbuilder.aws/learn/course/internal/view/elearning/1851/aws-technical-essentials
- Youtube: Be A Better Dev
- Tối ưu chi phí cho AWS EC2: https://blog.daovanhung.com/post/toi-uu-chi-phi-cho-aws-ec2#
