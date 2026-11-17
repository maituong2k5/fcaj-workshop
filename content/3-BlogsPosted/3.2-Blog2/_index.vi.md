---
title: "Blog 2: Giám sát nâng cao trong AWS AppSync"
date: 2025-10-09
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

Trong các ứng dụng hiện đại, API đóng vai trò quan trọng trong việc kết nối ứng dụng Frontend với các dịch vụ Backend. Tuy nhiên, khi ứng dụng ngày càng phức tạp, việc giám sát hiệu năng API và xác định nguyên nhân gốc rễ của các lỗi có thể trở nên khó khăn.

AWS AppSync là dịch vụ được quản lý hoàn toàn, giúp đơn giản hóa quá trình phát triển GraphQL API và Pub/Sub API. Với tính năng Enhanced Monitoring, nhà phát triển có thể truy cập các chỉ số chi tiết hơn để theo dõi hiệu năng API ở cấp độ Resolver, Data Source và Operation.

**Những điểm quan trọng cần biết:**

- AWS AppSync là dịch vụ được quản lý hoàn toàn để xây dựng GraphQL API và Pub/Sub API.
- Enhanced Monitoring cung cấp thông tin chi tiết hơn về hiệu năng API.
- Resolver-Level Metrics giúp xác định các Resolver hoạt động chậm hoặc gặp sự cố.
- Data Source Metrics cung cấp khả năng giám sát các dịch vụ như Amazon DynamoDB, AWS Lambda và Amazon RDS.
- Operation-Level Metrics theo dõi các thao tác GraphQL như Queries và Mutations.
- Amazon CloudWatch cung cấp Dashboard và Metrics để phân tích hiệu năng API.
- Enhanced Monitoring có thể được kích hoạt thông qua AWS Management Console, AWS CLI hoặc Terraform.
- Các CloudWatch Metrics bổ sung có thể làm tăng chi phí giám sát.

Tính năng này đặc biệt hữu ích đối với những ứng dụng có nhiều Resolver và Data Source, khi nhà phát triển cần xác định các điểm nghẽn hiệu năng và cải thiện độ tin cậy của API.

#### Tại sao việc giám sát API lại quan trọng?

Giám sát là một phần thiết yếu trong quá trình quản lý API. Nếu không có hệ thống giám sát đầy đủ, nhà phát triển có thể gặp khó khăn trong việc phát hiện các vấn đề về hiệu năng, thời gian phản hồi tăng cao và những lỗi phát sinh ngoài dự kiến.

Bằng cách theo dõi các chỉ số như độ trễ yêu cầu (Request Latency), số lượng yêu cầu (Request Count) và tỷ lệ lỗi (Error Rate), đội ngũ phát triển có thể sớm phát hiện những dấu hiệu bất thường và tìm ra nguyên nhân trước khi chúng ảnh hưởng đến người dùng.

#### Enhanced Monitoring trong AWS AppSync hoạt động như thế nào?

Enhanced Monitoring cung cấp các chỉ số chi tiết hơn so với phương pháp giám sát API cơ bản.

Tính năng này bổ sung ba khả năng giám sát quan trọng:

1. **Resolver-Level Metrics:** Theo dõi từng Resolver riêng lẻ để xác định thời gian thực thi chậm và các lỗi phát sinh.
2. **Data Source Metrics:** Giám sát hiệu năng của các nguồn dữ liệu được kết nối như DynamoDB, Lambda và RDS.
3. **Operation-Level Metrics:** Theo dõi các thao tác GraphQL, bao gồm Queries và Mutations.

Những chỉ số này giúp nhà phát triển hiểu rõ thành phần nào trong quá trình xử lý API đang gây ra vấn đề về hiệu năng.

#### Làm thế nào để kích hoạt Enhanced Monitoring?

AWS AppSync hỗ trợ nhiều phương pháp để kích hoạt Enhanced Monitoring:

- **AWS Management Console:** Truy cập phần cài đặt của GraphQL API và bật các chỉ số giám sát nâng cao cần thiết.
- **AWS CLI:** Cập nhật cấu hình GraphQL API thông qua lệnh `update-graphql-api`.
- **Terraform:** Cấu hình khối `enhanced_metrics_config` bên trong tài nguyên `aws_appsync_graphql_api`.

![AWS architecture diagram](/images/3-BlogsPosted/3.2-Blog2/picture1-1.png)

#### Amazon CloudWatch hỗ trợ tối ưu hiệu năng API như thế nào?

Sau khi kích hoạt Enhanced Monitoring, nhà phát triển có thể xem các chỉ số chi tiết thông qua Amazon CloudWatch.

Ví dụ, nếu truy vấn `searchUsers` có độ trễ cao, nhà phát triển có thể kiểm tra xem nguyên nhân đến từ AWS Lambda Resolver hay nguồn dữ liệu Amazon OpenSearch Service.

CloudWatch Dashboard có thể hiển thị những chỉ số quan trọng như:

- Số lượng yêu cầu và thời gian thực thi của Resolver.
- Thời gian phản hồi của Data Source.
- Tỷ lệ lỗi của API.
- Các chỉ số theo từng GraphQL Operation.

Thông qua việc phân tích những chỉ số này, nhà phát triển có thể đưa ra các biện pháp phù hợp:

- Kích hoạt cơ chế Caching để giảm các yêu cầu lặp lại.
- Tối ưu logic Resolver và các truy vấn cơ sở dữ liệu.
- Cải thiện hiệu năng của các hàm Lambda.
- Kiểm tra lỗi và triển khai cơ chế Retry.
- Áp dụng Rate Limiting để hạn chế tình trạng bị giới hạn lưu lượng (Throttling).

#### Chi phí giám sát được tính như thế nào?

Enhanced Monitoring tạo thêm các Custom Metrics trong Amazon CloudWatch, do đó có thể làm tăng chi phí hàng tháng.

Trong ví dụ API được AWS trình bày, hệ thống có ba Queries, hai Mutations và bốn Data Sources. Bài viết ước tính có thêm 37 Metrics, với chi phí minh họa là 11,10 USD mỗi tháng, dựa trên mức giá 0,30 USD cho mỗi Custom Metric.

Chi phí thực tế phụ thuộc vào bảng giá CloudWatch áp dụng, AWS Region và số lượng Metrics được sử dụng.

Vì vậy, nhà phát triển nên lựa chọn những Metrics thực sự cần thiết và thường xuyên kiểm tra chi phí giám sát.

#### Tại sao giải pháp này quan trọng?

Enhanced Monitoring giúp nhà phát triển có cái nhìn chi tiết hơn về hiệu năng API thay vì chỉ dựa vào các chỉ số tổng quan.

Bằng cách kết hợp AWS AppSync với Amazon CloudWatch, đội ngũ phát triển có thể xác định điểm nghẽn, xử lý lỗi và tối ưu hoạt động của API hiệu quả hơn.

Đây là kiến thức hữu ích đối với Backend Developer, Cloud Engineer và DevOps Engineer trong quá trình xây dựng các ứng dụng có độ tin cậy cao, khả năng mở rộng tốt và được giám sát chặt chẽ.

#### Tài liệu tham khảo

- Bài viết gốc AWS Blog: https://aws.amazon.com/vi/blogs/mobile/unlocking-deeper-insights-with-enhanced-monitoring-in-aws-appsync/
- Tài liệu AWS AppSync: https://docs.aws.amazon.com/appsync/
- Tài liệu Amazon CloudWatch: https://docs.aws.amazon.com/cloudwatch/
