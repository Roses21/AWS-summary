AWS Transit Gateway là dịch vụ mạng của Amazon giúp bạn kết nối nhiều mạng VPCs, VPNs, và On-premises networks với nhau, tất cả qua một gateway duy nhất. Transit Gateway hoạt động như một trung tâm (hub) trong mô hình hub-and-spoke, giúp đơn giản hóa và tăng cường khả năng mở rộng của mạng trên AWS.
# 1. Tổng quan về workshop
- Workshop sẽ sử dụng các dịch vụ sau: AWS Transit Gateway, AWS Network Firewall, VPC Interface Endpoints.
- Kết quả mong đợi: Sau khi hoàn thành hội thảo, bạn sẽ hiểu rõ hơn về các trường hợp sử dụng khác nhau liên quan đến chuyển đổi mạng.
## Connectivity within AWS
- VPC-to-VPC connectivity using AWS Transit Gateway , VPC peering, and AWS PrivateLink.
- Transit between AWS Regions with spoke networks using AWS Transit Gateway.
## Connectivity to/from the internet
- Centralized ingress and egress architecture pattern for access to/from the internet.
- Organizations often consolidate network security controls and traffic inspection, as opposed to having distributed internet ingress and egress points, each with their own security controls.
## Connectivity to data centers
- Interconnecting AWS and remote location with hybrid connectivity.
- This workshop will focus on integration between Site-to-Site VPN with AWS Transit Gateway, using TGW VPN attachment.
## Network Security
- Workload segmentation, ingress and egress security, traffic filtering, intrusion prevention system (IPS) and encryption.
- AWS Network Firewall secures network traffic and provides network security control points within AWS.
# 2. Getting Started
## 2.1. Kiến trúc ban đầu
Đây là kiến trúc đơn giản và còn nhiều vấn đề. Sau từng use case chúng ta phân tích, chúng ta sẽ biển đổi kiến trúc dưới đây để tối ưu hơn.

<img src="https://github.com/user-attachments/assets/4abf5396-e2ac-4573-bae5-ea7f10c9c404" width="70%"/>

- Kiến trúc gồm các thành phần:
  - 2 Spoke VPCs (DEV and PROD)
  - Shared Services VPC, which will be responsible for egress connectivity and centralizing access to VPC private endpoints
- This architecture allows you to:
  - Connect to the internet from each EC2 instance.
  - Establish VPC to VPC connectivity (DEV <-> Prod) via VPC Peering
  - Access each instance using AWS SSM Session Manager.
## 2.2. Use Cases

<img src="https://github.com/user-attachments/assets/296d1a9b-d408-4176-b15d-a9cfc12810e7" width="50%"/>

<img src="https://github.com/user-attachments/assets/2dc1f9c8-9de1-4920-aa95-f257b83622b8" width="50%"/>

<img src="https://github.com/user-attachments/assets/fcfacf62-e364-4863-a864-b61af32a0fe2" width="50%"/>

<img src="https://github.com/user-attachments/assets/8727d079-3fab-4dc8-8d2a-625fe3d5ab6f" width="50%"/>

<img src="https://github.com/user-attachments/assets/2be629db-1f85-4410-9411-2f8e2e9c3e0a" width="50%"/>

# 3. Enable Transitive Routing
Ở phần này, chúng ta sẽ đi sâu vào từng use case cụ thể.
## 3.1. Usecase 1: Any VPC <--> Any VPC with Centralized connectivity
### Phân tích
- Kiến trúc hiện tại của chúng ta tận dụng tính năng của VPC peering và cho phép DEV và PROD kết nối với nhau. Tình huống phát sinh là:
  - Điều gì sẽ xảy ra nếu cơ sở hạ tầng của chúng ta phát triển và nhiều VPC được triển khai - chúng yêu cầu kết nối với nhau hơn?
  - Chúng ta giới thiệu chuỗi dịch vụ và kiểm tra chúng như thế nào?
- Giải quyết:
  - Option 1: Sử dụng kiến ​​trúc hiện có và tận dụng VPC Peering. Khi mở rộng số lượng VPC trong môi trường của bạn, điều này có thể dẫn đến những thách thức về khả năng quản lý và tăng độ phức tạp
  - Option 2: Enable transitive routing by introducing AWS Transit Gateway.
    
    <img src="https://github.com/user-attachments/assets/697a7ca0-d162-4448-aaf3-d527c9a07da9" width="80%"/>

**Option 2 tối ưu hơn.** Để hỗ trợ *định tuyến bắc cầu* (transitive routing) và mở rộng quy mô kết nối cho hàng trăm VPC, bạn có thể sử dụng AWS Transit Gateway. Transit Gateway hoạt động như một khối kết nối cho nhiều mạng và tùy chọn kết nối, đồng thời mở ra nhiều kiến ​​trúc có thể tiết kiệm chi phí và cải thiện tình trạng bảo mật của bạn.
- Sau khi giải quyết được use case 1, chúng ta có kiến trúc tối ưu hơn như sau (thay thế VPC Peering bằng Transit Gateway): 

  ![{A192566C-3B64-4688-A03A-B7B3ED78E0DD}](https://github.com/user-attachments/assets/9ddbe7f7-72bc-498a-a80f-5619bc15892d)

### Deploy
- Prepare VPC connectivity to Transit Gateway:

    <img src="https://github.com/user-attachments/assets/20ad9b03-d609-4b30-8347-7307fa0b3115" width="50%"/>

 - Create Transit Gateway: To create Transit Gateway infrastructure, you'll need to perform the following steps:
   - Create TGW:
     
     <img src="https://github.com/user-attachments/assets/d82536e0-457a-475c-b4aa-c1ae93d547ad" width="100%"/>

     ASN (Autonomous System Number): Hệ thống tự trị (AS) là một nhóm các mạng dưới sự kiểm soát quản trị duy nhất duy trì một chính sách định tuyến được xác định rõ ràng. Để nhiều hệ thống tự trị tương tác với nhau, mỗi hệ thống cần có một mã định danh duy nhất (number).
     
   - Create TGW Attachments
     - Transit Gateway Attachment là một "kết nối" hay "liên kết" giữa Transit Gateway và các tài nguyên mạng của bạn, như VPC, VPN, Direct Connect, hoặc TGW peering.
       
       ![{2A12572A-282B-4446-A621-4CF9227F3A1A}](https://github.com/user-attachments/assets/e746664b-202c-4b9b-9bcd-a4117bf3e7b3)

   - Create TGW Route Table and associate VPC Attachments
   - Create TGW Propagations
   - Verify Routes in TGW
  
<img src="" width="50%"/>

