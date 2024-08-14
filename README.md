## Mục lục:
1. [Lưu ý về vẽ kiến trúc trên draw.io](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#1-l%C6%B0u-%C3%BD-v%E1%BB%81-v%E1%BA%BD-ki%E1%BA%BFn-tr%C3%BAc-tr%C3%AAn-drawio)

2. [Three tier architecture](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#2-three-tier-architecture)

3. [AWS Well-Architected Framework](https://github.com/Roses21/AWS-summary?tab=readme-ov-file#3-aws-well-architected-framework)
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

## 4. Auto Scaling
- Auto Scaling có 3 components:
  - Group (Nhóm co giãn tự động) là một nhóm các EC2 Instance hoặc RDS Instance. Nhóm này có khả năng co giãn số lượng các EC2 Instance thành viên dựa trên các chính sách co giãn mà bạn thiết lập.
  - Configuration Templates: là một tính năng giúp bạn tạo mẫu cho việc khởi tạo các EC2 Instance. Điều này giúp tự động hóa và đơn giản hóa việc khởi tạo các EC2 Instance cho dịch vụ Auto Scaling.
  - Scaling Options: Cung cấp một số cách để scale ASG (scale khi đáp ứng một điều kiện cụ thể hay theo lịch trình).
- Triển khai ứng dụng sử dụng Auto Scaling Group để đảm bảo khả năng mở rộng linh hoạt theo nhu cầu của người dùng, tăng tính sẵn sàng và đảm bảo khả năng chịu lỗi.
- Khi thiết kế HA cho Auto Scaling, hãy ưu tiên sử dụng nhiều AZ và nhiều Region.
- Auto Scaling cho phép bạn tạm dừng và sau đó tiếp tục một hoặc nhiều quy trình này, điều này có lợi cho bạn khi muốn điều tra sự cố trong ứng dụng của mình mà không kích hoạt quy trình Auto Scaling.
- Bạn không thể sửa đổi cấu hình khởi chạy sau khi đã tạo nó. Nếu muốn thay đổi cấu hình khởi chạy cho nhóm Auto Scaling, bạn phải tạo cấu hình khởi chạy mới và cập nhật nhóm Auto Scaling của mình để kế thừa cấu hình khởi chạy mới này.
### Nguồn tham khảo
- Mindmap: https://github.com/notcuder/aws-mindmap?tab=readme-ov-file
- https://github.com/keenanromain/AWS-SAA-C02-Study-Guide?tab=readme-ov-file
