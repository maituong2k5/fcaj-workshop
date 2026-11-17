---
title: "Blog 1: Triển khai Amazon S3 Files bằng Terraform"
date: 2026-11-17
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

Amazon S3 cung cấp dịch vụ lưu trữ đối tượng có khả năng mở rộng, tuy nhiên một số ứng dụng lại yêu cầu truy cập dữ liệu thông qua giao diện hệ thống tệp truyền thống. Amazon S3 Files giải quyết nhu cầu này bằng cách cho phép các tài nguyên tính toán được hỗ trợ truy cập dữ liệu S3 thông qua giao thức NFS.

Bằng cách kết hợp Amazon S3 Files với Terraform, hạ tầng AWS có thể được triển khai tự động, giảm thiểu các thao tác cấu hình thủ công đồng thời đảm bảo các yêu cầu về bảo mật và giám sát.

**Những điểm quan trọng cần biết:**

- Amazon S3 Files cung cấp giao diện NFS để truy cập dữ liệu được lưu trữ trong Amazon S3.
- Terraform tự động hóa quá trình triển khai hạ tầng thông qua phương pháp Infrastructure as Code (IaC).
- Mount Targets cho phép các tài nguyên tính toán kết nối với hệ thống tệp thông qua VPC.
- Security Groups kiểm soát lưu lượng NFS thông qua cổng TCP 2049.
- IAM Policies áp dụng nguyên tắc đặc quyền tối thiểu (Least Privilege).
- Amazon EC2, Amazon ECS và AWS Lambda có thể tích hợp với hệ thống tệp.
- Amazon CloudWatch hỗ trợ giám sát khả năng kết nối của các máy khách.
- Dữ liệu có thể được mã hóa bằng SSE-S3 hoặc khóa AWS KMS do khách hàng quản lý.

Giải pháp này đặc biệt hữu ích đối với các ứng dụng cần truy cập dữ liệu S3 thông qua giao diện hệ thống tệp, đồng thời vẫn đảm bảo khả năng tự động hóa hạ tầng và quản lý bảo mật tập trung.

#### Vấn đề cần giải quyết là gì?

Theo cách truyền thống, các ứng dụng tương tác với Amazon S3 thông qua API để tải lên, tải xuống và quản lý các đối tượng dữ liệu. Tuy nhiên, một số ứng dụng được thiết kế để làm việc với tệp và thư mục thông qua giao diện hệ thống tệp.

Điều này có thể khiến quá trình tích hợp trở nên phức tạp hơn khi ứng dụng cần truy cập dữ liệu S3 bằng các thao tác tệp quen thuộc.

Bên cạnh đó, việc cấu hình thủ công hệ thống mạng, quyền truy cập và hạ tầng lưu trữ cũng có thể trở nên khó khăn khi quy mô hệ thống ngày càng mở rộng.

#### Amazon S3 Files giải quyết vấn đề như thế nào?

Amazon S3 Files cung cấp giao diện hệ thống tệp dựa trên giao thức NFS để truy cập dữ liệu được lưu trữ trong Amazon S3.

Thay vì yêu cầu ứng dụng tương tác trực tiếp với API của S3, các tài nguyên tính toán được hỗ trợ có thể truy cập dữ liệu thông qua một hệ thống tệp được gắn kết (Mounted File System).

Terraform bổ trợ cho dịch vụ này bằng cách tự động hóa quá trình tạo và cấu hình các tài nguyên hạ tầng cần thiết.

Sự kết hợp giữa hai công nghệ giúp đơn giản hóa quá trình triển khai và giúp việc duy trì cấu hình hạ tầng trở nên thuận tiện hơn.

#### Kiến trúc hệ thống hoạt động như thế nào?

Giải pháp sử dụng một số thành phần AWS chính:

1. **Amazon S3:** Lưu trữ dữ liệu của ứng dụng.
2. **Amazon S3 Files:** Cung cấp giao diện hệ thống tệp NFS.
3. **Mount Targets:** Cung cấp các điểm kết nối mạng cho máy khách.
4. **Amazon VPC:** Cung cấp môi trường kết nối mạng riêng.
5. **Security Groups:** Kiểm soát lưu lượng NFS thông qua cổng TCP 2049.
6. **AWS IAM:** Quản lý quyền truy cập và phân quyền.
7. **Amazon CloudWatch:** Giám sát khả năng kết nối của hệ thống.

![AWS architecture diagram](/images/3-BlogsPosted/3.1-Blog1/storage-1876-1.jpg)

#### Quá trình triển khai bằng Terraform bao gồm những gì?

Giải pháp của AWS trình bày quy trình triển khai tự động bao gồm các bước quan trọng:

1. Tạo S3 File System và Mount Targets trên nhiều Availability Zones.
2. Cấu hình Security Groups để cho phép các kết nối NFS được cấp quyền.
3. Tạo IAM Policies dựa trên nguyên tắc đặc quyền tối thiểu (Least Privilege).
4. Cấu hình quá trình đồng bộ dữ liệu.
5. Kết nối các tài nguyên tính toán như EC2, ECS và Lambda.
6. Thiết lập CloudWatch Dashboards và Alarms.
7. Kiểm tra lại các cấu hình bảo mật và mã hóa dữ liệu.

Phương pháp này giúp giảm thiểu việc cấu hình hạ tầng thủ công và đảm bảo quá trình triển khai được thực hiện nhất quán hơn.

#### Tại sao giải pháp này quan trọng?

Sự kết hợp giữa Amazon S3 Files và Terraform cho thấy cách hạ tầng điện toán đám mây có thể được tự động hóa mà vẫn đảm bảo các yêu cầu về bảo mật và khả năng giám sát.

Đối với Cloud Engineer và DevOps Engineer, giải pháp này mang lại kiến thức thực tế về Infrastructure as Code, lưu trữ đám mây, hệ thống mạng, quản lý quyền IAM và giám sát hệ thống.

Đồng thời, đây cũng là một ví dụ cho thấy nhiều dịch vụ AWS có thể phối hợp với nhau để giải quyết các bài toán hạ tầng trong thực tế.

#### Tài liệu tham khảo

- Bài viết gốc AWS Blog: https://aws.amazon.com/blogs/storage/deploy-amazon-s3-files-with-terraform/
- Mã nguồn Terraform tham khảo: https://github.com/aws-samples/sample-code-for-deploying-s3-files-with-terraform
- Tài liệu AWS: https://docs.aws.amazon.com/
