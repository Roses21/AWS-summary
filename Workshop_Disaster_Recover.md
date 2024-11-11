# 1. Introduction to AWS Elastic Disaster Recovery
- Các thảm họa CNTT như lỗi trung tâm dữ liệu, hỏng máy chủ hoặc tấn công mạng không chỉ có thể làm gián đoạn hoạt động kinh doanh của bạn mà còn gây mất dữ liệu, ảnh hưởng đến doanh thu và gây tổn hại đến danh tiếng của bạn.
- AWS Elastic Disaster Recovery (thường được gọi là DRS) giảm thiểu thời gian ngừng hoạt động và mất dữ liệu bằng cách cung cấp **khả năng khôi phục nhanh chóng, đáng tin cậy** cho các máy chủ vật lý, ảo và dựa trên đám mây vào Đám mây AWS.
- DRS **liên tục sao chép các máy của bạn** (bao gồm hệ điều hành, cấu hình trạng thái hệ thống, cơ sở dữ liệu, ứng dụng và tệp) vào khu vực tổ chức với chi phí thấp trong tài khoản AWS mục tiêu và Khu vực ưu tiên của bạn.
- Trong trường hợp xảy ra thảm họa, bạn có thể hướng dẫn DRS tự động khởi chạy tất cả các máy cần thiết ở trạng thái được cung cấp đầy đủ **trong vài phút**.
# 2. Thực hành
- Kiến trúc:
  
  ![{CAED35E6-EC0A-4DE6-B165-7CE300718C7C}](https://github.com/user-attachments/assets/57364da6-911c-4670-9873-1dc5a37ec2b3)

## 2.1. Module 1 - Environment Setup
