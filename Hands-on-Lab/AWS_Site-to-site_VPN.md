## 1. Kiến trúc

![{958395C0-80EF-4D21-9A77-BF4DA617EA8C}](https://github.com/user-attachments/assets/d220ac1d-adfd-4afe-a355-6e19cf70284e)

## 2. Thực hiện
- Để tạo kết nối site-to-site VPN, cần có các thành phần:
  - Transit gateway hoặc Virtual Private Gateway.
  - Customer Gateway.
  - Customer Gateway Device.

Lưu ý: Khi tạo Site-to-site VPN sử dụng TGW, mặc định AWS sẽ tạo sẵn cho chúng ta 1 TGW Attachment loại VPN (được sử dụng để kết nối Transit Gateway với các mạng on-premises thông qua một VPN) như hình. Do đó chúng ta cần tạo thêm 1 TGW Attachment cho Cloud VPC trong bài lab này:

![{5C618883-0932-4759-9052-B8CDF1C86C71}](https://github.com/user-attachments/assets/4359a143-4c2a-48e9-bf97-d030dbb0b9d9)

- Các bước triển khai cần thiết:

![{D04B5155-FB32-41BF-8186-D6E73F390FE4}](https://github.com/user-attachments/assets/b9bfae4f-7ff3-4322-864b-646b931d6006)

![{9D3A04A4-5789-4D36-889F-0D18EDF42D26}](https://github.com/user-attachments/assets/7746aec6-501c-49ba-b072-684779c1bd20)

![{BCF6E25C-5A16-4876-A3BD-231C4A88E5FF}](https://github.com/user-attachments/assets/3dcb1bea-617f-407d-b3fd-e0a55bc0c845)

![{2652BE1D-8C6B-4437-BF84-29769E6990F8}](https://github.com/user-attachments/assets/449fc4d8-275f-481f-a5e4-71b9b9612854)

  



