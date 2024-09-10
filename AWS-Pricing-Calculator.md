## 1. Khái niệm
- AWS Pricing Calculator: là công cụ miễn phí cho phép bạn khám phá các dịch vụ AWS và tạo ước tính chi phí (không bao gồm thuế) cho các trường hợp sử dụng của bạn trên AWS. Bạn không cần có tài khoản AWS hoặc kiến ​​thức chuyên sâu về AWS để sử dụng AWS Pricing Calculator.
- AWS Pricing Calculator giả định rằng bạn không sử dụng Free tier và không bao gồm bất kỳ Free tier nào sắp hết hạn trong estimates của bạn.
## 2. Features
  - Xem giá rõ ràng: có thể xem ước tính giá theo dịch vụ hoặc theo nhóm dịch vụ để phân tích chi phí kiến ​​trúc của mình. Khi cấu hình, bạn có thể xem thông tin chi tiết về giá của từng dịch vụ:

    ![image](https://github.com/user-attachments/assets/8e2a4698-6d8d-493b-b22f-973b841e6711)

  - Sử dụng các nhóm để ước tính theo cấp bậc: Sắp xếp các ước tính của bạn thành các nhóm để phù hợp với kiến ​​trúc của bạn nhằm phân tích chi phí dịch vụ rõ ràng.
  - Lưu ước tính: Lưu liên kết đến từng ước tính để chia sẻ với người khác hoặc dùng để sau này xem lại. Ước tính được lưu vào máy chủ công cộng AWS.
  - Xuất ước tính: định dạng CSV hoặc PDF để chia sẻ cục bộ với các bên liên quan.
## 3. Best practice

Để tận dụng ước tính một cách tốt nhất, hãy đảm bảo bạn hiểu rõ về các yêu cầu cơ bản của mình.

- Using groups to organize your estimates: Bạn cũng có thể sử dụng các nhóm để sắp xếp ước tính của mình theo nhiều cách khác nhau. Ví dụ: bạn có thể sắp xếp ước tính của mình theo trung tâm chi phí, nhóm dịch vụ, kiến ​​trúc sản phẩm hoặc khách hàng. Một estimate có thể có nhiều group và trong mỗi group, có thể tạo nhiều group con.
    
    ![image](https://github.com/user-attachments/assets/6a969033-24e4-4713-be8b-448a4c1ac7a8)

- Add AWS Support costs to your estimates:
  
  ![image](https://github.com/user-attachments/assets/8cfeb4ae-6835-4a0b-9973-ee4a3c01d7d6)

- Sharing your estimate: Estimate links created on or after May 31, 2023, remain valid for **one year**. Estimate links created before this date remain valid for three years.
- Exporting your estimates: CSV, JSON hoặc PDF. Trong file sẽ gồm các thông tin như: ngày export, estimate link, chi phí ước tính theo tháng và theo năm, Groups (nếu có), chi tiết ước tính (gồm các thông tin liên quan đến cấu hình của từng service).
## 4. Thực hành
  - Version 1 - chỉ estimate EC2: https://calculator.aws/#/estimate?id=78ee48d44fa4f7d519a98ad1614f184aab54e957
  - Version 2 - xóa EC2: https://calculator.aws/#/estimate?id=e930bebfb774aceb1ec0f18e84673b061303cb4f
  - Version 3: https://calculator.aws/#/estimate?id=4d25dc8ee387fbf328137fbdd69e5c51976b2641 

    Có thể thấy, khi update estimate nhưng link của version cũ vẫn sẽ được giữ lại. Ban đầu truy cập link thì chỉ có thể xem, nhưng load lại trang web sẽ có thể chỉnh sửa được estimate.
  


