Link lab: https://000020.awsstudygroup.com/1-introduce/
## 0. Kiến trúc 

 <img src="https://github.com/user-attachments/assets/49f37ff8-62fb-4564-b736-6613e60c7491" width="50%"/>
 
## 1. Các bước chuẩn bị
- Tài nguyên:
  - First EC2 Host ở VPC1 và Third EC2 Host ở VPC3 có thể kết nối Internet.
  - Second EC2 Host ở VPC2 và Fourth EC2 Host ở VPC4 không thể kết nối Internet.
- Đẩy key từ máy tính local lên EC2 instance:

![{0FA47161-85F8-4F10-A2D5-17F63ED08534}](https://github.com/user-attachments/assets/9abc8968-accf-49b3-abb4-a6510772bc00)

## 2. Tạo TGW và tạo TGW Attachments
- Tạo TGW: Vào VPC -> Transit gateway -> Create và điền thông tin cần thiết:
  
  ![{6ED02BE2-296D-4F15-95A9-55DE2E3C8F82}](https://github.com/user-attachments/assets/cc2ba5ad-fe1b-4c33-aa4b-91bb25979f97)

- Tạo TGW Attachments:
  
  ![{502C8731-A17A-4C14-8D89-458A837B6382}](https://github.com/user-attachments/assets/b17506c3-48f9-4472-82f6-cb236feb9449)

- Kết nối SSH đến các instance ở VPC1, sau đó ping đến IP private của instance khác:

  ![{5746E834-C3FD-4747-9CCD-E30FAB635297}](https://github.com/user-attachments/assets/facee8d8-8ce1-42de-9920-3ac55fb708d9)

  Kết quả là không được bởi vì việc gán các VPC vào Transit Gateway không tự tạo các các trúc liên kết routing trong trường hợp này bởi vì cấu hình Default route table association và Default route table propagation đã bị vô hiệu hoá ở phần tạo Transit Gateway trước.

## 3. Tạo Transit Gateway Route Tables
- Tạo TGW route table:
  
  ![{B401B7D8-B94A-44C0-A6B7-1D3D003AA875}](https://github.com/user-attachments/assets/44c788b6-ca14-472f-8f7a-03a10b59cdd5)

- Tab Associations (Liên kết): Gán một TGW attachment với một Route Table duy nhất, kiểm soát toàn bộ lưu lượng từ attachment đó. Thực hiện đính cả 4 VPC:

  ![{C4D62B64-65A5-457D-ADDD-3EEE9F3C127B}](https://github.com/user-attachments/assets/cfc2110c-5118-4772-9ae2-7746ef7442c7)

- Tab Propagations (Lan truyền): Tự động thêm các route của TGW attachment vào Route TablAn attachment, giúp đơn giản hóa việc quản lý route trong môi trường phức tạp:

  ![{D8F7DACC-08A9-4699-A963-86DC6C09A8DF}](https://github.com/user-attachments/assets/d12c64e7-1e9e-45d5-8f49-15a93a534c65)

## 4. Thêm Transit Gateway Routes vào VPC Route Tables

Ở phần này, bạn sẽ cấu hình route table ở từng VPC để route traffic tới các VPC còn lại thông qua Transit Gateway.

- Tại Route Table của VPC1 và VPC3, edit route để thêm rule:

  ![{66FB5EA9-19B6-42C9-813C-F739BFC26E8A}](https://github.com/user-attachments/assets/9e709352-5439-4968-bc5e-ef7d22929694)

Điều này cho VPC1 biết rằng tất cả packet cho bất kỳ mạng 172.16.x.x nào đều thông qua Transit Gateway.

- Ở VPC2 và VPC4: Destination: 0.0.0.0/0, Target: chọn Transit Gateway bạn đã tạo:

  ![{725DA2A6-0952-4534-9345-1C381F04AD69}](https://github.com/user-attachments/assets/3588cd93-9ff3-4040-9911-7fd6eff26f48)

- Kiểm tra: ping các EC2 instance ở các VPC, nếu ping được là ok.
