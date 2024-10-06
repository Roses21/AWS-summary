<p align="center">
  <img src="https://github.com/user-attachments/assets/b2bfe96c-ef08-4668-b4b6-612cf9ba08f9" width="20%">
</p>

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
<p align="center">
<img src="https://github.com/user-attachments/assets/296d1a9b-d408-4176-b15d-a9cfc12810e7" width="50%"/>

<img src="https://github.com/user-attachments/assets/2dc1f9c8-9de1-4920-aa95-f257b83622b8" width="50%"/>

<img src="https://github.com/user-attachments/assets/fcfacf62-e364-4863-a864-b61af32a0fe2" width="50%"/>

<img src="https://github.com/user-attachments/assets/8727d079-3fab-4dc8-8d2a-625fe3d5ab6f" width="50%"/>

<img src="https://github.com/user-attachments/assets/2be629db-1f85-4410-9411-2f8e2e9c3e0a" width="50%"/>
</p>

# 3. Enable Transitive Routing (Usecase 1: Any VPC <--> Any VPC with Centralized connectivity)
## Phân tích
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

## Deploy

1. Prepare VPC connectivity to Transit Gateway.
      - Bước này, chúng ta sẽ tạo các Transit Gateway subnet- điều này không bắt buộc. Tuy nhiên, best practice là nên có các subnet dành riêng cho Transit Gateway Attachments. Điều này sẽ hữu ích nếu bạn cần kiểm soát việc định tuyến lối vào hoặc chỉ định các NACL chuyên dụng.
    <img src="https://github.com/user-attachments/assets/20ad9b03-d609-4b30-8347-7307fa0b3115" width="50%"/>
      - Tiếp theo, liên kết các subnets với từng private route table của VPC. Ví dụ đối với SHARED SERVICES VPC: Select SHARED-SERVICES Private RT, Click on Subnet associations, Click on Edit subnet association, Select SHARED-SERVICES TGW Subnet and SHARED-SERVICES Private Subnet, Click Save associations.
2. Create Transit Gateway: To create Transit Gateway infrastructure, you'll need to perform the following steps:
   
   -  Create TGW:
     
     <img src="https://github.com/user-attachments/assets/04eb0ed1-41e5-4ade-b5a3-d801e0d65810" width="100%"/>

     ASN (Autonomous System Number): Hệ thống tự trị (AS) là một nhóm các mạng dưới sự kiểm soát quản trị duy nhất duy trì một chính sách định tuyến được xác định rõ ràng. Để nhiều hệ thống tự trị tương tác với nhau, mỗi hệ thống cần có một mã định danh duy nhất (number).
     
   - Create TGW Attachments

     Transit Gateway Attachment là một "kết nối" hay "liên kết" giữa Transit Gateway và các tài nguyên mạng, như VPC, VPN, Direct Connect, hoặc TGW peering. Mỗi Transit Gateway Attachment phải được gắn với một Transit Gateway duy nhất.

     Trong VPC, khi một subnet ở một AZ có Transit Gateway Attachment với một TGW, các subnet khác trong cùng AZ đều có thể kết nối tới TGW đó.

     Trong workshop này, attachment type của chúng ta là VPC:
     
     <img src="https://github.com/user-attachments/assets/3ccdebed-e66a-4b16-8ae7-bacc24ba76e8" width="60%"/>

     ![{2A12572A-282B-4446-A621-4CF9227F3A1A}](https://github.com/user-attachments/assets/e746664b-202c-4b9b-9bcd-a4117bf3e7b3)

   - Create TGW Route Table and associate VPC Attachments:
     
       ![{54FDC050-AA92-4822-B647-0D263831202E}](https://github.com/user-attachments/assets/18c88a8f-f791-41c3-9d1d-dfcb52319dd4)

   - Create TGW Propagations
  
     Transit Gateway Propagations là một tính năng trong AWS Transit Gateway giúp **tự động cập nhật bảng định tuyến (route tables) của Transit Gateway** với thông tin định tuyến từ các kết nối mạng đã được liên kết với nó. Điều này giúp việc quản lý và định tuyến lưu lượng giữa các VPC, VPN, hoặc Direct Connect dễ dàng hơn mà không cần phải thêm các route thủ công.
     
       ![{B464722A-1A34-4C5B-B875-A94F77623A7C}](https://github.com/user-attachments/assets/08d7405a-5af7-401e-9cc8-10461b3c809a)

   - Verify Routes in TGW: cả 3 VPC CIDRs của 3 VPC đã xuất hiện trong TGW Route Table:

     <img src="https://github.com/user-attachments/assets/20fe5baf-f01c-4ed6-ba32-611bf27bff75" width="70%"/>

     Điều này có nghĩa là từ góc độ Transit Gateway, Transit Gateway có khả năng định tuyến giữa các VPC, nhưng để VPC có thể gửi lưu lượng đi, bạn phải cấu hình route trong bảng định tuyến của từng VPC để chỉ rõ lưu lượng nào cần đi qua Transit Gateway. Nếu không có các route này trong bảng định tuyến của từng VPC, mặc dù Transit Gateway có thể định tuyến, các VPC sẽ không biết cách gửi lưu lượng đến Transit Gateway. Chúng ta sẽ tiếp tục khắc phục vấn đề này ở bước 3.
     
3. Switch Traffic to Transit Gateway

    Ở giai đoạn này, chúng ta sẽ thiết lập Transit Gateway với tất cả cấu trúc cần thiết để kích hoạt kết nối giữa các VPC.
      
  - Kịch bản: Traffic chỉ truyền qua lại được giữa các spoke VPCs (DEV and PROD) thông qua VPC Peering.  

    <img src="https://github.com/user-attachments/assets/03805d82-88d7-4905-8ded-2c7ce71d80cf" width="50%"/>
    
  - Kết quả mong đợi cuối cùng: cả 3 EC2 instance có thể giao tiếp với nhau thông qua TGW.
    
     <img src="https://github.com/user-attachments/assets/11cd6e96-4a9d-40e2-99d5-fa7cf4f0b6ac" width="50%"/>

  - Chúng ta cần cập nhật bảng định tuyến của từng VPC để traffic có thể đi qua Transit Gateway: VPC > Route Table > Select route table > Routes > Edit routes > Add an entry for CIDR 10.0.0.0/8 with TGW as the target > Remove VPC Peering.

# 4. Centralized Services (Use case 2. Any VPC --> Internet with centralized egress; Use case 3. Any VPC --> Centralized VPC interface endpoints)
## 4.1. Centralized egress to internet (Truy cập internet tập trung)
Việc triển khai một giải pháp kết nối internet riêng biệt trong mỗi VPC có thể trở nên tốn kém, vì vậy việc sử dụng mô hình kết nối internet tập trung là một lựa chọn khả thi. Để thực hiện điều này, chúng ta tạo một VPC egress trong tài khoản dịch vụ mạng và định tuyến tất cả lưu lượng egress từ các VPC con đến VPC egress bằng cách sử dụng Transit Gateway. Trong use case này, chúng ta sẽ sử dụng Shared Services VPC cho việc kết nối ra internet tập trung.

![{BFB49B5B-66A7-4B27-B51D-E88088BD0058}](https://github.com/user-attachments/assets/626705b4-9370-4039-8da8-6a4428eb7087)

- Hiện tại, các spoke VPC đang kết nối với internet cục bộ thông qua NAT Gateway -> IGW. Chúng tôi cần chỉnh VPC routes để tận dụng Transit Gateway để gửi tất cả lưu lượng truy cập trên Internet theo flow: **Spoke VPCs -> Transit Gateway -> Shared Services VPC -> Internet**
  
  ![{A8117F50-B144-4EEC-B965-89B787D672F2}](https://github.com/user-attachments/assets/52586ecb-3c91-4826-828d-73d6cbf963b6)

- Add default route in private subnet route table via Transit Gateway: Update destination 0.0.0.0/0 with target as the Transit Gateway (PROD với DEV).

  ![{47746CF6-8A1F-4A8D-80D8-26CE56AC9DB5}](https://github.com/user-attachments/assets/f4b56439-926f-4e3d-a953-69546c01420c)

- Remove default route in public subnet route table via Internet Gateway (xóa PROD với DEV).
- Create static route in TGW route table: Transit Gateways -> Transit Gateway Route Tables -> select TGW RT -> Route -> Create static route.
- Thêm route trả về cho 10.0.0.0/8 đến Transit Gateway trong Shared Services VPC. Điều này sẽ cho phép mọi lưu lượng trả về từ Internet đến các VPC DEV và PROD:

  ![{0FAFEDE0-56B3-4A2E-979E-DE47CC32E0E4}](https://github.com/user-attachments/assets/ba4360f4-6f86-4c83-8541-66d25917d169)

- Kiểm tra kết quả: network path is traversing Shared Service (10.99.x.x) VPC:

![{16E7B13F-F66A-4550-8738-0B26903B5940}](https://github.com/user-attachments/assets/0b8cbcb5-0afa-4595-88c8-f70cf482cc71)

## 4.2. Centralized access to VPC private endpoint
- Kiến trúc ban đầu:

  <img src="https://github.com/user-attachments/assets/7506b22e-b762-45eb-998c-0f5a13950a26" width="80%"/>

- Kết quả mong đợi:
  
  <img src="https://github.com/user-attachments/assets/4a2ba890-a416-40b2-9757-fe69d1234a68" width="80%"/>

- Interface Endpoint là một loại điểm cuối (endpoint) trong Amazon Web Services (AWS) cho phép bạn kết nối trực tiếp đến các dịch vụ AWS mà không cần phải đi qua Internet công cộng.
- Khi bạn cấp phát một interface endpoint, người dùng sẽ phải trả phí cho mỗi giờ endpoint đó hoạt động. Theo mặc định, bạn sẽ tạo một interface endpoint trong mỗi VPC mà bạn muốn truy cập dịch vụ AWS. Điều này có thể tốn kém và khó quản lý khi một khách hàng muốn tương tác với một dịch vụ AWS cụ thể qua nhiều VPC.
- Để tránh điều này, bạn có thể lưu trữ các interface endpoint trong một VPC trung tâm. Tất cả các VPC con sẽ sử dụng các endpoint tập trung này.

![{65671348-9542-423D-88D6-72D645E1F6EC}](https://github.com/user-attachments/assets/7a972429-ec64-43f5-969a-21b55c963849)

- Tóm lại, trong phần 4.2, chúng ta sẽ xóa các điểm cuối SSM khỏi VPC DEV và PROD và tập trung chúng vào SHARED-SERVICES VPC.
- Remove Endpoints in Spoke VPCs: Virtual Private Cloud -> Endpoints -> Chọn 3 Endpoint của DEV và PROD rồi xóa. Tuy nhiên sau khi xóa các endpoint này, bạn vẫn có thể kết nối với instance Dev và Prod EC2 bằng Session Manager. Điều này do ở các bước trước, các instance đang tiếp cận các dịch vụ SSM/EC2 thông qua Shared Services -> Internet:
  
  <img src="https://github.com/user-attachments/assets/4a44f27e-b632-41f0-ad1b-88fb428d697f" width="80%"/>

- Do đó cần thực hiện các bước sau để đảm bảo DEV và PROD đi qua interface endpoint trong SHARED-SERVICES để đến SSM và EC2 services:
  - Disable Private DNS names for the Shared Services endpoints: For following 3 service endpoints in Shared Services VPC -> Actions -> Modify Private DNS names -> Uncheck Enable Private DNS names.
  - Create Private Hosted Zone: Trong phần này, chúng ta sẽ tạo ba PHZ, một PHZ cho mỗi điểm cuối được đề cập ở trên.

    Route 53 -> Hosted zones > Create hosted zone
