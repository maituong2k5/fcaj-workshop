---
title: "Blog 3: Amazon Threat Intelligence theo dõi các tác nhân đe dọa đang thực hiện các chiến dịch tội phạm mạng bằng các tác nhân AI ARTEX."
date: 2026-11-17
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

Trí tuệ nhân tạo (AI) ngày càng được ứng dụng rộng rãi nhằm tự động hóa công việc và nâng cao hiệu suất. Tuy nhiên, công nghệ này cũng có thể bị tội phạm mạng lợi dụng để tự động hóa các hoạt động độc hại và thực hiện những cuộc tấn công với quy mô lớn hơn.

Vào tháng 11/2026, Amazon Threat Intelligence công bố phát hiện các tác nhân tấn công sử dụng ARTEX, một framework AI Agent mã nguồn mở phục vụ kiểm thử xâm nhập, để tổ chức các chiến dịch tội phạm mạng. Thông qua mạng lưới cảm biến an ninh MadPot của Amazon, các nhà nghiên cứu đã thu thập được thông tin về hoạt động của AI Agent liên quan đến hành vi đánh cắp thông tin xác thực và tìm cách vượt qua hệ thống xác minh danh tính.

**Những điểm quan trọng cần biết:**

- ARTEX là framework AI Agent mã nguồn mở có khả năng phối hợp nhiều tác nhân AI để thực hiện các nhiệm vụ liên quan đến bảo mật.
- Amazon MadPot sử dụng mạng lưới cảm biến đánh lừa (Decoy Sensors) phân bố trên toàn cầu để quan sát hoạt động đáng ngờ và thu thập thông tin tình báo về mối đe dọa.
- Kẻ tấn công sử dụng AI Agent để tìm kiếm thông tin xác thực và API Key bị lộ, qua đó truy cập các mô hình AI và dịch vụ đám mây.
- Một chiến dịch khác tìm cách vượt qua quy trình xác minh danh tính KYC tại các sàn giao dịch tiền điện tử bằng công nghệ Deepfake thời gian thực.
- Các ARTEX Agent chia sẻ thông tin thông qua Knowledge Graph, cho phép nhiều Agent tiếp tục những nhiệm vụ mà các Agent khác đã thực hiện.
- Những chiến dịch này cho thấy AI có thể làm tăng tốc độ, khả năng duy trì và quy mô của các cuộc tấn công mạng.
- Các tổ chức cần bảo vệ thông tin xác thực, bảo mật ứng dụng AI, cập nhật phần mềm và giám sát những hoạt động API hoặc chi phí dịch vụ bất thường.

Những phát hiện này cho thấy một thách thức an ninh quan trọng: AI Agent có thể khiến các cuộc tấn công mạng trở nên tự động và dai dẳng hơn, ngay cả khi kẻ tấn công chỉ khai thác những điểm yếu vốn đã tồn tại trong các hệ thống truyền thống.

#### Amazon Threat Intelligence phát hiện các chiến dịch này như thế nào?

Amazon sử dụng MadPot, một mạng lưới cảm biến đánh lừa (Decoy Threat Sensors) được phân bố trên toàn cầu nhằm quan sát các hoạt động đáng ngờ.

Các cảm biến này cung cấp những dịch vụ được kiểm soát, mô phỏng giao diện API suy luận của các mô hình ngôn ngữ lớn (LLM) phổ biến. Các ARTEX Agent tương tác với những giao diện này như một phần trong quy trình hoạt động của chúng.

Những yêu cầu được ghi nhận chứa các thông tin như chỉ dẫn nhiệm vụ, lịch sử hoạt động của Agent và kết quả được báo cáo. Nhờ đó, Amazon Threat Intelligence có thể phân tích cách các chiến dịch được tổ chức và mục tiêu mà những kẻ tấn công hướng đến.

Cần lưu ý rằng các phát hiện này chủ yếu dựa trên bản ghi do chính các AI Agent cung cấp. Amazon không trực tiếp quan sát mọi hoạt động được mô tả trong những bản ghi đó và không thể xác minh độc lập toàn bộ kết quả được báo cáo.

#### ARTEX AI Agent tổ chức các cuộc tấn công như thế nào?

ARTEX phân chia nhiệm vụ cho nhiều Agent chuyên biệt, bao gồm:

- **Planner Agents:** Lập kế hoạch và xác định những hành động tiếp theo.
- **Worker Agents:** Thực hiện các nhiệm vụ được giao.
- **Verification Agents:** Kiểm tra và đánh giá kết quả được báo cáo.
- **Compression Agents:** Tóm tắt thông tin để duy trì ngữ cảnh hoạt động chung.

Các Agent sử dụng Knowledge Graph làm bộ nhớ dùng chung. Mỗi Agent có thể đọc thông tin do những Agent khác thu thập và bổ sung các phát hiện mới, giúp quá trình hoạt động được tiếp tục mà không cần bắt đầu lại từ đầu.

Amazon đã ghi nhận hai chiến dịch chính.

#### Chiến dịch 1: Đánh cắp thông tin xác thực AI trên quy mô lớn

Trong chiến dịch đầu tiên, các đối tượng tấn công sử dụng AI Agent để tìm kiếm API Key và thông tin xác thực bị lộ, cho phép truy cập vào các mô hình AI.

Các Agent nhắm đến những ứng dụng AI công khai trên Internet, API Gateway và các nền tảng quản lý thông tin xác thực của nhiều nhà cung cấp AI.

Những thông tin xác thực bị đánh cắp có thể được sử dụng để truy cập các dịch vụ AI mà không phải trả chi phí sử dụng tương ứng. Thông tin xác thực trên nền tảng đám mây cũng được tìm kiếm vì chúng có thể mở rộng quyền truy cập đến các tài nguyên và dữ liệu nhạy cảm khác.

Chiến dịch này cho thấy những rủi ro đến từ:

- Để lộ API Key trong các kho mã nguồn công khai.
- Sử dụng thông tin xác thực mặc định hoặc được mã hóa cứng (Hardcoded Credentials).
- Để các giao diện quản trị có thể truy cập mà không yêu cầu xác thực.
- Sử dụng các ứng dụng lỗi thời có lỗ hổng bảo mật đã được công bố.
- Không bảo vệ đầy đủ thông tin xác thực trên nền tảng đám mây và các bí mật của ứng dụng.

#### Chiến dịch 2: Tìm cách vượt qua xác minh danh tính bằng Deepfake

Chiến dịch thứ hai nhắm vào hệ thống xác minh danh tính Know Your Customer (KYC) tại hai sàn giao dịch tiền điện tử.

Theo bản ghi của các Agent, kẻ tấn công đã thử sử dụng video Deepfake thời gian thực để vượt qua bước xác minh selfie trực tiếp và hình ảnh giấy tờ tùy thân bị chỉnh sửa để vượt qua bước kiểm tra tài liệu.

Các Agent cũng tìm cách phân tích cơ chế hoạt động của hệ thống Liveness Detection. Đây là phương pháp bảo mật nhằm xác nhận người đang thực hiện xác minh là người thật và hiện diện trực tiếp tại thời điểm kiểm tra.

Tuy nhiên, AWS cho biết hệ thống kiểm tra phía máy chủ của nhà cung cấp dịch vụ xác minh đã từ chối tất cả các lần thử Deepfake được ghi nhận trong bản báo cáo.

Chiến dịch này cho thấy những thách thức bảo mật ngày càng gia tăng liên quan đến nội dung do AI tạo ra và hệ thống xác minh danh tính kỹ thuật số.

#### Các tổ chức có thể rút ra bài học gì từ những chiến dịch này?

Amazon nhấn mạnh rằng các kỹ thuật tấn công trong những chiến dịch này không hoàn toàn mới. Điểm thay đổi lớn nhất nằm ở tốc độ, khả năng duy trì và mức độ tự động hóa mà AI Agent mang lại.

Các tổ chức cần tăng cường những biện pháp bảo mật cơ bản:

- **Bảo vệ thông tin xác thực:** Tránh để lộ API Key, mật khẩu và thông tin truy cập đám mây trong kho mã nguồn công khai hoặc các tệp ứng dụng.
- **Bảo mật ứng dụng AI:** Áp dụng cơ chế kiểm soát truy cập phù hợp cho ứng dụng AI, Model Gateway và các Inference Endpoint.
- **Loại bỏ thông tin xác thực mặc định:** Thay thế mật khẩu mặc định và thông tin bí mật được mã hóa cứng bằng các cơ chế xác thực an toàn.
- **Vá các lỗ hổng bảo mật:** Thường xuyên cập nhật ứng dụng và xử lý những điểm yếu bảo mật đã được công bố.
- **Giám sát hoạt động bất thường:** Sử dụng hệ thống giám sát để phát hiện lưu lượng API bất thường, hành vi truy cập đáng ngờ và mức tăng chi phí dịch vụ AI không mong muốn.

#### Tại sao vấn đề này quan trọng?

Việc sử dụng ARTEX cho thấy Agentic AI có thể làm thay đổi cách tội phạm mạng tổ chức các hoạt động tấn công.

Thay vì hoàn toàn dựa vào thao tác thủ công, kẻ tấn công có thể phối hợp nhiều AI Agent để thực hiện các nhiệm vụ khác nhau, chia sẻ thông tin và tiếp tục hoạt động với mức độ can thiệp của con người thấp hơn.

Đối với Cloud Engineer, DevOps Engineer và Security Engineer, đây là lời nhắc nhở về tầm quan trọng của việc bảo vệ thông tin xác thực trên nền tảng đám mây, bảo mật hạ tầng AI, giám sát hoạt động API và duy trì các cấu hình bảo mật chặt chẽ.

Khi công nghệ AI tiếp tục phát triển, các tổ chức cũng cần liên tục cải thiện những biện pháp bảo mật để thích ứng với các mối đe dọa mới.

#### Tài liệu tham khảo

- Bài viết gốc AWS Security Blog: https://aws.amazon.com/vi/blogs/security/amazon-threat-intelligence-observes-threat-actors-running-cybercrime-campaigns-with-artex-ai-agents/
- Tài liệu bảo mật AWS: https://docs.aws.amazon.com/security/
- AWS Security Blog: https://aws.amazon.com/blogs/security/
