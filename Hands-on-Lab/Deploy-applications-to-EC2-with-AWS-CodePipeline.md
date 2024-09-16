- Link lab:
  - https://000015.awsstudygroup.com/
  - https://000023.awsstudygroup.com/
- Kiến trúc:

  ![image](https://github.com/user-attachments/assets/359fee95-55bf-4c01-b914-72f1a29b03f4)

 - Developer sẽ viết mã và commit thay đổi vào CodeCommit (kho lưu trữ mã nguồn của AWS tương tự như Git) -> CodeCommit sẽ kích hoạt một sự kiện CloudWatch.
 - CloudWatch sẽ theo dõi và phát hiện sự kiện commit mới trong CodeCommit -> CloudWatch sẽ kích hoạt quá trình CI/CD (cụ thể là khởi động CodePipeline).
 - CodePipeline là dịch vụ tự động hóa các bước xây dựng và triển khai. Trong pipeline này có 2 hành động chính:
    - Build & Test: Hành động này sử dụng AWS CodeBuild để thực hiện việc xây dựng (build) và kiểm thử (test) ứng dụng.
    - Deploy: Sau khi quá trình build và test hoàn tất thành công, quá trình triển khai (deploy) sẽ được kích hoạt.
 - AWS CodeBuild: Dịch vụ biên dịch mã nguồn, chạy các bài kiểm thử và tạo ra các artifact (tập tin kết quả từ quá trình build). Các artifact này sẽ được lưu vào Amazon S3.
 - AWS CodeDeploy: triển khai artifact từ S3 vào các EC2 instances. Quá trình này được khởi động bởi CodePipeline thông qua hành động trigger deploy.
## 1. Chuẩn bị cơ sở hạ tầng
