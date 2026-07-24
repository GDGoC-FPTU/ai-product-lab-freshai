03 — Nhật ký AI Log
Họ và tên: Nguyễn Đình Phúc MSSV: 2A202601835

# 03-ai-log.md

# AI Log – Nhật ký sử dụng AI trong buổi học

## 1. AI đã giúp tôi những gì?

Trong buổi học, tôi sử dụng ChatGPT làm trợ lý để hỗ trợ quá trình phân tích và phát triển ý tưởng thay vì chỉ yêu cầu AI đưa ra đáp án hoàn chỉnh.

Đầu tiên, AI giúp tôi brainstorm các pain point trong hoạt động của các công ty thành viên Vingroup như VinFast, Xanh SM, Vinhomes và Vinmec theo bốn góc nhìn (Repetitive, Time-consuming, AI-upgrade và Stakeholder Pain). Từ nhiều ý tưởng ban đầu, tôi lựa chọn bài toán "AI phát hiện tài xế mất tập trung" của Xanh SM vì đây là bài toán có tác động trực tiếp đến an toàn giao thông và có thể ứng dụng Computer Vision.

Tiếp theo, tôi sử dụng AI để xây dựng Quick Problem Card, phân tích quy trình vận hành hiện tại, xác định bottleneck, actor, workflow và đề xuất kiến trúc AI phù hợp. AI cũng hỗ trợ tôi xây dựng sơ đồ Current-State Workflow trước khi có AI, xác định các điểm handoff, thời gian xử lý và các nút thắt cổ chai theo đúng yêu cầu của bài tập.

Ngoài ra, AI còn giúp tôi phản biện ý tưởng bằng cách đánh giá xem bài toán có thực sự cần AI hay chỉ cần rule-based, từ đó giúp tôi hiểu rõ hơn giá trị mà AI mang lại trong từng tình huống.

## 2. AI đã sai ở đâu?

Trong quá trình làm việc, AI có một số câu trả lời chưa chính xác hoặc còn mang tính suy diễn.

Ví dụ, khi đề xuất quy trình "AI phát hiện tài xế mất tập trung", AI ban đầu xây dựng workflow có cả bước AI phát hiện và cảnh báo tài xế ngay trong sơ đồ Current-State. Tuy nhiên, sau khi đối chiếu với yêu cầu của đề bài, tôi nhận ra sơ đồ cần mô tả quy trình hiện tại trước khi có AI (Current-State Workflow), không phải quy trình sau khi triển khai AI. Nếu sử dụng ngay nội dung AI đưa ra thì sẽ không đúng yêu cầu.

Ngoài ra, ở một số bài toán khác, AI cũng đưa ra các số liệu thời gian và tỷ lệ cải thiện chỉ mang tính ước lượng, không dựa trên dữ liệu thực tế của doanh nghiệp. Vì vậy, các con số này chỉ nên được xem là giả định để minh họa, không nên trình bày như số liệu đã được kiểm chứng.

## 3. Tôi đã điều chỉnh như thế nào?

Để cải thiện kết quả, tôi thay đổi cách đặt prompt theo hướng cụ thể hơn.

Thay vì chỉ hỏi:

> "Hãy thiết kế workflow cho bài toán phát hiện tài xế mất tập trung."

Tôi bổ sung thêm các ràng buộc như:

> "Chỉ mô tả quy trình hiện tại trước khi có AI (Current-State Workflow). Không đưa bất kỳ thành phần AI nào vào quy trình. Đánh dấu rõ các handoff, bottleneck và thời gian xử lý."

Sau khi bổ sung các điều kiện này, AI tạo ra workflow đúng với yêu cầu của bài tập.

Bên cạnh đó, khi AI đưa ra các số liệu ước lượng, tôi chủ động kiểm tra lại tính hợp lý và chỉ sử dụng các giá trị mang tính minh họa thay vì xem đó là số liệu chính thức.

## 4. Bài học rút ra

Qua buổi học, tôi nhận thấy AI là một trợ lý hỗ trợ rất hiệu quả trong việc brainstorm ý tưởng, phân tích quy trình và xây dựng tài liệu. Tuy nhiên, AI không phải lúc nào cũng hiểu đúng ngữ cảnh hoặc yêu cầu của đề bài. Chất lượng kết quả phụ thuộc rất nhiều vào cách đặt prompt và khả năng kiểm chứng của người sử dụng.

Vì vậy, tôi xem AI như một "thought-partner" để gợi ý, phản biện và tăng tốc quá trình làm việc, còn việc đánh giá, chọn lọc và xác minh thông tin vẫn là trách nhiệm của người sử dụng.
