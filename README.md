## Mục lục:
1. [Lưu ý về vẽ kiến trúc trên draw.io](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#1-l%C6%B0u-%C3%BD-v%E1%BB%81-v%E1%BA%BD-ki%E1%BA%BFn-tr%C3%BAc-tr%C3%AAn-drawio)
2. [Three tier architecture](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#2-three-tier-architecture)
3. [AWS Well-Architected Framework](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#3-aws-well-architected-framework)
4. [Auto Scaling](https://github.com/Roses21/AWS-summary/blob/main/README.md#4-ec2-auto-scaling)
5. [AWS Networking](https://github.com/Roses21/AWS-summary/blob/main/README.md#5-aws-network)

   5.1. [VPC]()
   
6. [AWS Compute](https://github.com/Roses21/AWS-summary/blob/main/README.md#6-compute)

   6.1. [Elastic Compute Cloud (EC2)](https://github.com/Roses21/AWS-summary/tree/main#61-elastic-compute-cloud-ec2)
      
   6.2. [AWS Fargate - Severless]()

   6.3. [AWS Lambda - Severless]()
   
7. [Storage](https://github.com/Roses21/AWS-summary/blob/main/README.md#7-storage)
8. [Database](https://github.com/Roses21/AWS-summary/blob/main/README.md#8-database)
9. [AWS Management Tools](https://github.com/Roses21/AWS-summary/blob/main/README.md#9-aws-management-tools)

   9.1. [IAM](https://github.com/Roses21/AWS-summary/blob/main/README.md#91-iam)

   9.2. [CloudWatch (Application)](https://github.com/Roses21/AWS-summary/blob/main/README.md#92-cloudwatch-application)

   9.3. [CloudTrail (AWS Account)](https://github.com/Roses21/AWS-summary/blob/main/README.md#93-cloudtrail-aws-account)
10. [Nguồn tham khảo](https://github.com/Roses21/AWS-summary/blob/main/README.md#ngu%E1%BB%93n-tham-kh%E1%BA%A3o)
## 1. Lưu ý về vẽ kiến trúc trên draw.io
- Tỉ lệ khung ngoài cùng của kiến trúc AWS: 1.618, ví dụ Height = 500 => Width = 500 x 1.618 = 809.
- Khung tên của service AWS nên là màu cam (FF8000).
- Size icon: 60x60.
## 2. Three tier architecture
- Web/Presentation Tier: Houses the user-facing elements of the application, such as web servers and the interface/frontend.
- Application Tier: Houses the backend and application source code needed to process data and run functions.
- Data Tier: Houses and manages the application data. Often where the databases are stored.

![image](https://github.com/user-attachments/assets/31b4a426-bc54-43cd-a527-4a27a8a866a8)

## 3. AWS Well-Architected Framework
Gồm 6 trụ cột chính:
### 3.1. Operational Excellence Pillar
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
### 3.2. Security 
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
### 3.3. Reliability 
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
### 3.4. Performance Efficiency
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
### 3.5. Cost Optimization
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
### 3.6. Sustainability 
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

## 4. EC2 Auto Scaling
- Auto Scaling có 3 components:
  - Group (Nhóm co giãn tự động) là một nhóm các EC2 Instance hoặc RDS Instance. Nhóm này có khả năng co giãn số lượng các EC2 Instance thành viên dựa trên các chính sách co giãn mà bạn thiết lập.
  - Configuration Templates: là một tính năng giúp bạn tạo mẫu cho việc khởi tạo các EC2 Instance. Điều này giúp tự động hóa và đơn giản hóa việc khởi tạo các EC2 Instance cho dịch vụ Auto Scaling.
  - Scaling Options: Cung cấp một số cách để scale ASG (scale khi đáp ứng một điều kiện cụ thể hay theo lịch trình).
- Triển khai ứng dụng sử dụng Auto Scaling Group để đảm bảo khả năng mở rộng linh hoạt theo nhu cầu của người dùng, tăng tính sẵn sàng và đảm bảo khả năng chịu lỗi.
- Khi thiết kế HA cho Auto Scaling, hãy ưu tiên sử dụng nhiều AZ và nhiều Region.
- Auto Scaling cho phép bạn tạm dừng và sau đó tiếp tục một hoặc nhiều quy trình này, điều này có lợi cho bạn khi muốn điều tra sự cố trong ứng dụng của mình mà không kích hoạt quy trình Auto Scaling.
- Bạn không thể sửa đổi cấu hình khởi chạy sau khi đã tạo nó. Nếu muốn thay đổi cấu hình khởi chạy cho nhóm Auto Scaling, bạn phải tạo cấu hình khởi chạy mới và cập nhật nhóm Auto Scaling của mình để kế thừa cấu hình khởi chạy mới này.

![image](https://github.com/user-attachments/assets/41cdb655-d8de-4c1f-b0c8-c12f90d4205a)

### Scaling policies
- Gồm 3 loại:
#### Simple scaling policy
- Hoạt động dựa trên một điều kiện duy nhất: Simple Scaling chỉ có một ngưỡng đơn lẻ và thực hiện một hành động duy nhất khi điều kiện đó được đáp ứng.
- Thay đổi đơn giản và ngay lập tức: Khi điều kiện (chẳng hạn như CPU vượt quá một mức cụ thể) được kích hoạt, Simple Scaling thực hiện ngay lập tức hành động mở rộng hoặc thu nhỏ số lượng instances theo một số lượng cố định.
- Ví dụ: Nếu CPU > 70%, tăng thêm 1 instance. Nếu CPU < 30%, giảm 1 instance.
#### Step scaling
- Hoạt động dựa trên các ngưỡng cụ thể: Step Scaling cho phép bạn thiết lập nhiều ngưỡng khác nhau cho một chỉ số (như CPU, Network In/Out, v.v.), và tương ứng với mỗi ngưỡng, bạn có thể cấu hình một hành động mở rộng hoặc thu nhỏ cụ thể.
- Thay đổi theo từng bước: Số lượng instances tăng hoặc giảm sẽ phụ thuộc vào mức độ mà chỉ số vượt qua các ngưỡng đã thiết lập. Điều này có nghĩa là khi chỉ số vượt qua ngưỡng cao hơn, số lượng instances được thay đổi sẽ lớn hơn so với khi chỉ số chỉ vượt qua ngưỡng thấp hơn.
- Ví dụ: Nếu CPU > 70%, tăng thêm 2 instances. Nếu CPU > 90%, tăng thêm 4 instances. Nếu CPU < 30%, giảm 1 instance.
#### Target Tracking
- Tự động điều chỉnh số lượng instances dựa trên một chỉ số mục tiêu đã được xác định, chẳng hạn như mức sử dụng CPU. AWS sẽ liên tục theo dõi chỉ số này và tăng hoặc giảm số lượng instances để duy trì chỉ số gần với mục tiêu.
- Ví dụ: Bạn có thể tạo một policy để tự động thêm hoặc bớt EC2 instances trong một Auto Scaling group nhằm duy trì mức sử dụng CPU trung bình là 50%.
## 5. AWS Network
### 5.1. VPC
### 5.2. Elastic Load Balancing (ELB)

![image](https://github.com/user-attachments/assets/a8a9d511-a02d-4308-a506-515c48db4869)

### 5.3. ENB
### 5.4. Route 53
## 6. Compute

Gồm 3 loại: virtual machines (VMs), containers, và serverless.

### 6.1. Virtual machines (VMs): Elastic Compute Cloud (EC2)
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

### 6.2. Containers
- Container: đóng gói mã ứng dụng và các phần phụ thuộc của nó, tạo ra môi trường độc lập của riêng container đó; giúp workload có thể được chuyển từ nơi này sang nơi khác, chẳng hạn như từ quá trình phát triển đến production hoặc từ môi trường tại chỗ lên đám mây. Một ví dụ về nền tảng container là Docker.
- Sự khác biệt giữa VM và container:
  
![image](https://github.com/user-attachments/assets/995224c1-c3a1-4b5a-bd43-0cff7c41011a)

   - Các containers chia sẻ cùng hệ điều hành và kernel với máy chủ mà chúng tồn tại trên đó. Nhưng máy ảo có hệ điều hành riêng. Mỗi máy ảo phải duy trì một bản sao của hệ điều hành, điều này dẫn đến lãng phí tài nguyên ở mức độ nào đó.
   - Container nhẹ hơn, khởi động nhanh hơn, có ưu thế về tốc độ. Còn máy ảo cung cấp toàn bộ sức mạnh của hệ điều hành và nhiều tài nguyên, như cài đặt gói, hạt nhân chuyên dụng, v.v.
- Tổ chức các containers:
  - Trong AWS, containers có thể chạy trên EC2 instances. Hầu hết các công ty và tổ chức đều chạy nhiều containers trên nhiều EC2 instances trên một vài AZ.
  - AWS cung cấp 2 dịch vụ container orchestration: Amazon Elastic Container Service (Amazon ECS) và Amazon Elastic Kubernetes Service (Amazon EKS):
    - ECS:  là dịch vụ quản lý container với khả năng mở rộng cao cho phép đơn giản hóa việc chạy, ngừng chạy và quản lý các container trong cluster; tích hợp được với Docker. Gồm 3 layers:
      - Capacity: Cơ sở hạ tầng nơi container của bạn chạy (gồm EC2 instance, Fargate, on-premises compute).
      - Controller: Triển khai và quản lý các ứng dụng chạy trên container của bạn (ECS scheduler - là phần mềm quản lý các ứng dụng của bạn).
      - Provisioning: Các công cụ mà bạn có thể sử dụng để giao tiếp với scheduler nhằm triển khai và quản lý các ứng dụng cũng như container của mình (Console, CLI, SDK, copilot, CDK).
     
        Các khái niệm trong ECS:
         - Images: là một plaintext file chứa các hướng dẫn xây dựng container.
         - Registry: là nơi lưu trữ images. AWS Elastic Container Registry (ECR) là một loại registry được quản lý hoàn toàn bởi AWS nhằm đơn giản hóa việc lưu trữ, quản lý và triển khai các Docker container image. 
         - Task definition: là một tệp văn bản ở định dạng JSON mô tả các tham số và một hoặc nhiều vùng chứa tạo thành ứng dụng của bạn. Ví dụ: bạn có thể sử dụng nó để chỉ định hình ảnh và tham số cho hệ điều hành, bộ chứa nào sẽ sử dụng, cổng nào sẽ mở cho ứng dụng của bạn và khối lượng dữ liệu nào sẽ sử dụng với bộ chứa trong tác vụ.
         - Amazon ECS Services: là một cấu hình cho phép chạy một hoặc nhiều các task liên tiếp nhau trong cluster và tự động duy trì chúng. Các task và các dịch vụ có thể được chạy trên các hạ tầng serverless (quản lý bởi AWS Fargate) hoặc thông quan hạ tầng do bạn quản lý như EC2 cluster.
         - Cluster: là một nhóm logical tasks hoặc service chạy trên Capacity.
    - EKS: là một dịch vụ được quản lý mà bạn có thể sử dụng để chạy Kubernetes trên AWS mà không cần cài đặt, vận hành và bảo trì.
- ECS khác EKS:
  - An ECS container is called a task. An EKS container is called a pod.
  - Amazon ECS chạy trên công nghệ gốc của AWS. Amazon EKS chạy trên Kubernetes.
  - In Amazon ECS, the machine that runs the containers is an EC2 instance that has an ECS agent installed and configured to run and manage your containers. This instance is called a container instance. In Amazon EKS, the machine that runs the containers is called a worker node or Kubernetes node. 
### 6.3. Serverless 
## 7. Storage 
### 7.1. CloudFront
### 7.2. S3
### 7.3. EBS
## 8. Database
### 8.1.
## 9. AWS Management Tools
### 9.1. IAM
- AWS Identity and Access Management (IAM) is an AWS service that helps you manage access to your AWS account and resources. It also provides a centralized view of who and what are allowed inside your AWS account (authentication), and who and what have permissions to use and work with your AWS resources (authorization).
- Với IAM, bạn có thể chia sẻ quyền truy cập vào tài khoản và tài nguyên AWS mà không cần chia sẻ bộ khóa truy cập hoặc mật khẩu. Bạn cũng có thể cung cấp quyền truy cập chi tiết cho những người làm việc trong tài khoản của mình để mọi người và dịch vụ chỉ có quyền đối với những tài nguyên họ cần.
#### IAM features
- Global: IAM mang tính toàn cầu và không dành riêng cho bất kỳ Region nào. Bạn có thể xem và sử dụng cấu hình IAM của mình từ bất kỳ Khu vực nào trong AWS Management Console.
- Free to use.
#### IAM user
- 
#### IAM groups
- Là một tập hợp người dùng. Tất cả người dùng trong nhóm sẽ kế thừa các quyền được gán cho nhóm. Điều này cho phép ta cấp quyền cho nhiều người dùng cùng một lúc. 
- Bạn không thể lồng các IAM group. Người dùng IAM riêng lẻ có thể thuộc nhiều nhóm, nhưng không thể tạo nhóm con trong một IAM group khác.
- Lợi ích: Cung cấp một cách để xem ai có quyền gì trong tổ chức. Nó cũng giúp mở rộng quy mô khi có người mới tham gia, rời đi hay thay đổi vai trò trong tổ chức.
#### IAM policies
- Để quản lý quyền truy cập và cấp quyền cho các dịch vụ và tài nguyên AWS.
- Hầu hết các chính sách đều được lưu trữ trong AWS dưới dạng tài liệu JSON với một số thông tin cơ bản như Version, Effect, Action, và Resource.
- Ví dụ:
  
  ![image](https://github.com/user-attachments/assets/1256b014-290d-483a-b2e2-6c4bbf80c976)

#### IAM role
- Phân quyền truy cập tạm thời: Thay vì gán quyền trực tiếp cho người dùng hoặc dịch vụ, bạn có thể tạo một IAM Role với các quyền cụ thể và sau đó gán role này cho người dùng, dịch vụ hoặc ứng dụng khi họ cần truy cập.
- Tăng cường bảo mật: IAM Role giúp giảm rủi ro bảo mật bằng cách cung cấp quyền truy cập chỉ khi cần thiết và không cần sử dụng thông tin đăng nhập tĩnh (như Access Keys) cho các dịch vụ AWS.
- Linh hoạt trong quản lý: Bạn có thể gán, thu hồi hoặc thay đổi IAM Role một cách dễ dàng mà không cần phải thay đổi cấu hình hoặc quyền hạn của người dùng hoặc dịch vụ.
- Ví dụ: Truy cập dịch vụ khác từ EC2: Giả sử bạn có một ứng dụng chạy trên một EC2 instance cần truy cập vào một S3 bucket để lưu trữ hoặc đọc dữ liệu. Thay vì gán trực tiếp Access Key và Secret Key cho ứng dụng, bạn có thể tạo một IAM Role với quyền truy cập S3 và gán role này cho EC2 instance. Điều này cho phép ứng dụng truy cập S3 mà không cần quản lý thông tin đăng nhập.
#### Best practices
- Lock down the AWS root user.
- Follow the principle of least privilege
- Use IAM appropriately
- Use IAM roles when possible
- Consider using an identity provider
- Regularly review and remove unused users, roles, and other credentials
  
### 9.2. CloudWatch (Application)
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
  
#### CloudWatch alarms
- Gửi thông báo hoặc tự động thực hiện thay đổi khi vượt giá trị ngưỡng đối với tài nguyên bạn đang theo dõi dựa trên các quy tắc bạn xác định.
- Có 3 trạng thái:
  - OK: Số liệu nằm trong ngưỡng được xác định. Mọi thứ dường như đang hoạt động như bình thường.
  - ALARM: Số liệu nằm ngoài ngưỡng được xác định. Đây có thể là một vấn đề hoạt động.
  - INSUFFICIENT_DATA: Cảnh báo vừa mới bắt đầu, metric không có sẵn hoặc không có đủ dữ liệu cho metric để xác định trạng thái cảnh báo.
#### Amazon CloudWatch Logs
- Là nơi tập trung để lưu trữ và phân tích nhật ký. Với dịch vụ này, bạn có thể giám sát, lưu trữ và truy cập các tệp nhật ký của mình từ các ứng dụng chạy trên phiên bản EC2, hàm AWS Lambda và các nguồn khác.
- Cách sắp xếp dữ liệu trong CloudWatch Logs:
  - Event logs: là bản ghi hoạt động được ghi lại bởi ứng dụng hoặc tài nguyên đang được giám sát. Nó có dấu thời gian và thông báo sự kiện.
  - Stream logs: Các event logs được nhóm thành stream logs - là chuỗi các sự kiện nhật ký thuộc về cùng một tài nguyên đang được theo dõi.
  - Group logs: bao gồm các stream logs đều có chung cài đặt quyền và lưu giữ.
    
  ![image](https://github.com/user-attachments/assets/4f768068-64c3-4b98-af7c-59451e09065e)
 
#### CloudWatch Dashboards:
- Là các trang chủ có thể tùy chỉnh trong bảng điều khiển CloudWatch mà bạn có thể sử dụng để giám sát tài nguyên của mình trong một chế độ xem duy nhất.
- CloudWatch Dashboards tích hợp với CloudWatch Metrics và CloudWatch Alarms để tạo chế độ xem tùy chỉnh về số liệu và cảnh báo cho tài nguyên AWS của bạn.
### 9.3. CloudTrail (AWS Account)

![image](https://github.com/user-attachments/assets/ad53f89b-f7ec-472a-83a5-fa140a316b34)

- AWS CloudTrail AWS CloudTrail: là một dịch vụ audit cho tài khoản AWS. Actions taken by a user, role, or an AWS service are recorded as events in CloudTrail. Các events bao gồm các hành động được thực hiện trong AWS Management Console, AWS Command Line Interface, và AWS SDKs và APIs. Event được lưu lại tối đa 90 ngày trên CloudTrail (enabled by default and is no additional cost).
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
## 10. CloudFormation
- 
### Nguồn tham khảo
- Mindmap: https://github.com/notcuder/aws-mindmap?tab=readme-ov-file
- Tổng hợp kiến thức ôn thi SAA: https://github.com/keenanromain/AWS-SAA-C02-Study-Guide?tab=readme-ov-file
- Note lý thuyết cơ bản về AWS: https://github.com/skulltech/aws-solutions-architect-associate-notes?tab=readme-ov-file
- Khóa học cơ bản Practitioner Essentials: https://explore.skillbuilder.aws/learn/course/134/play/136404/aws-cloud-practitioner-essentials
- Technical Essentials: https://explore.skillbuilder.aws/learn/course/internal/view/elearning/1851/aws-technical-essentials
- Youtube: Be A Better Dev
- Tối ưu chi phí cho AWS EC2: https://blog.daovanhung.com/post/toi-uu-chi-phi-cho-aws-ec2# 
