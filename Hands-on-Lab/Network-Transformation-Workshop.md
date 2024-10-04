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

![{78005A59-B779-4100-88A5-854DC7476B14}](https://github.com/user-attachments/assets/4abf5396-e2ac-4573-bae5-ea7f10c9c404)

- Kiến trúc gồm các thành phần:
  - 2 Spoke VPCs (DEV and PROD)
  - Shared Services VPC, which will be responsible for egress connectivity and centralizing access to VPC private endpoints
- This architecture allows you to:
  - Connect to the internet from each EC2 instance.
  - Establish VPC to VPC connectivity (DEV <-> Prod) via VPC Peering
  - Access each instance using AWS SSM Session Manager.
## 2.2. Use Cases

![{75D00A94-A1E8-43F5-9663-42BB200BEE8E}](https://github.com/user-attachments/assets/296d1a9b-d408-4176-b15d-a9cfc12810e7)

![{B4545EC7-FEE0-4911-AD61-68FC63590D66}](https://github.com/user-attachments/assets/2dc1f9c8-9de1-4920-aa95-f257b83622b8)

![{45541DFC-D924-48F2-A0C9-B361401CC810}](https://github.com/user-attachments/assets/fcfacf62-e364-4863-a864-b61af32a0fe2)

![{25FFCB49-AB67-4B41-BF46-CD5BCD740C18}](https://github.com/user-attachments/assets/8727d079-3fab-4dc8-8d2a-625fe3d5ab6f)

![{A5F9F607-6975-4291-B750-127A3C3BC9A7}](https://github.com/user-attachments/assets/2be629db-1f85-4410-9411-2f8e2e9c3e0a)

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
    
    ![{1ADC4A3D-55B3-4B8B-AA20-A14C3E138090}](https://github.com/user-attachments/assets/697a7ca0-d162-4448-aaf3-d527c9a07da9)

**Option 2 tối ưu hơn.** Để hỗ trợ *định tuyến bắc cầu* (transitive routing) và mở rộng quy mô kết nối cho hàng trăm VPC, bạn có thể sử dụng AWS Transit Gateway. Transit Gateway hoạt động như một khối kết nối cho nhiều mạng và tùy chọn kết nối, đồng thời mở ra nhiều kiến ​​trúc có thể tiết kiệm chi phí và cải thiện tình trạng bảo mật của bạn.
- Sau khi giải quyết được use case 1, chúng ta có kiến trúc tối ưu hơn như sau (thay thế VPC Peering bằng Transit Gateway): 

  ![{A192566C-3B64-4688-A03A-B7B3ED78E0DD}](https://github.com/user-attachments/assets/9ddbe7f7-72bc-498a-a80f-5619bc15892d)

 ### Deploy
