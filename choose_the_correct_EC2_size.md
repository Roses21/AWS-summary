- Để lựa chọn kích cỡ EC2 phù hợp, cần theo dõi và phân tích việc sử dụng dịch vụ hiện tại để hiểu rõ về hiệu suất của các máy ảo và các kiểu mẫu đang được sử dụng (nên quan sát ít nhất 2 tuần, lý tưởng nhất là 1 tháng).
- Có thể dùng CloudWatch để xem log. Amazon CloudWatch là một dịch vụ giám sát, quản lý các tài nguyên AWS của người dùng, cũng như các ứng dụng vận hành trên AWS. Những thông số cần quan tâm:
  - CPU Utilization: Phần trăm thời gian CPU vật lý mà Amazon EC2 sử dụng để chạy instance EC2, bao gồm thời gian dành để chạy cả mã của người dùng và mã của Amazon EC2 (%).
  - Network In: xác định khối lượng lưu lượng truy cập mạng đến một instance (bytes).
  - Network Out: xác định khối lượng lưu lượng truy cập mạng đi ra từ một instance (bytes).

(Xem thêm tại https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/viewing_metrics_with_cloudwatch.html )

- Cài đặt và đặt cấu hình CloudWatch agent để truy cập vào EC2 (instance ở trạng thái running):
  - Tạo IAM role với Policy là CloudWatchAgentServerPolicy (Enables an instance to use the CloudWatch agent to write data to CloudWatch) 
  - Gắn IAM role vào EC2 instance: Trong giao diện EC2, Chọn Actions -> Chọn Security -> Chọn Modify IAM role.
  - Cài đặt CloudWatch agent: Kết nối đến instance bằng browser. Tải gói "Amazon CloudWatch Agent" theo hướng dẫn https://000032.awsstudygroup.com/vi/4-install-cloudwatch-agent/
- Tối ưu hóa tài nguyên EC2:
  - AWS phân tích mức sử dụng tài nguyên EC2 trong quá khứ (14 ngày qua sử dụng Amazon CloudWatch) và dấu vết đặt trước hiện có để xác định các cơ hội tiết kiệm chi phí. Có hai loại hành động được khuyến nghị: Chấm dứt nếu phiên bản được coi là không hoạt động ( mức sử dụng CPU tối đa là bằng hoặc dưới 1% ) hoặc Downsize nếu phiên bản đó được sử dụng không đầy đủ (mức sử dụng CPU tối đa là từ 1% đến 40% ).
  - Chọn Billing and Cost Management -> Chọn Savings Plans -> Chọn Recommendations:
    
    ![image](https://github.com/user-attachments/assets/1b903a71-7185-4446-922e-60594aa744e0)

    Tại ô Recommendations:

      Optimization opportunities: Số lượng đề xuất có sẵn dựa trên tài nguyên và cách sử dụng của bạn.

      Estimated monthly savings: Tổng số tiền tiết kiệm hàng tháng dự kiến ​​được liên kết với từng đề xuất được cung cấp.

      Estimated savings (%): Các tiết kiệm khả dụng so với chi phí Amazon EC2 trực tiếp (On-demand) được liên kết với các trường hợp trong danh sách đề xuất. Bạn cũng có thể lọc các đề xuất của mình theo loại hành động (Không sử dụng và không được sử dụng), Tài khoản được liên kết, Khu vực và Thẻ.

- AWS Compute Optimizer: là dịch vụ phân tích việc sử dụng tài nguyên điện toán AWS và miễn phí. Dựa trên những phát hiện của mình, nó đưa ra các đề xuất cho tài nguyên của bạn để giảm chi phí và cải thiện hiệu suất.
  - Việc tối ưu chi phí khi sử dụng compute (EC2, Lambda, Fargate) cần làm theo thứ tự sau:
    - Tối ưu instance type, cấu hình.
    - Khi đã chắc chắn instance type, cấu hình đảm bảo được khối lượng công việc, tiến hành mua compute saving plans để nhận được chiết khấu lên đến 66% so với việc chi trả theo hình thức on-demand.
  - Lưu ý:
    - Việc có đầy đủ metric (như Memory utilization, CPU Utilization,... được thu thập bằng CloudWatch trong khoảng thời gian 14 ngày) sẽ giúp đưa ra các đề xuất chính xác trên mức độ sử dụng thật tế, giúp việc tiết kiệm đạt hiệu quả cao nhất.
    - AWS Compute Optimizer không đề xuất cho Spot Instances.
    - Đối với Auto Scaling group, EC2, EBS, Lambda, Fargate: AWS Compute Optimizer sẽ có các yêu cầu khác nhau cần thỏa mãn trước khi đề xuất tối ưu chi phí. Để đảm bảo nhận được hỗ trợ, cần check kỹ điều kiện cho từng service.
