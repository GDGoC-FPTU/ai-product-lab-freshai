# 03-ai-log.md

# AI Log – Nhật ký sử dụng AI trong buổi học

## 1. AI đã hỗ trợ tôi những gì

Trong buổi học, tôi sử dụng ChatGPT như một trợ lý để brainstorm ý tưởng và hoàn thiện bài tập về ứng dụng AI trong VinFast.

Ban đầu, AI gợi ý nhiều bài toán khác nhau trong hệ sinh thái Vingroup như điều phối xe, xử lý ticket chăm sóc khách hàng và kiểm tra hư hỏng phương tiện. Sau khi thảo luận với nhóm, chúng tôi quyết định chọn bài toán **"Rà soát video Driver Monitoring để xác nhận tài xế đang mất tập trung"** vì phù hợp với lĩnh vực Computer Vision và có tính ứng dụng cao tại VinFast.

Sau đó, tôi tiếp tục sử dụng AI để:

* Phân tích quy trình vận hành hiện tại (Current Workflow).
* Xác định Bottleneck trong quá trình rà soát video.
* Xây dựng Problem Statement theo 6 trường của đề bài.
* Thiết kế Future-State Flow có AI, Human-in-the-loop và Fallback.
* Đề xuất các chỉ số đánh giá như thời gian review, tỷ lệ cảnh báo sai (False Positive), Precision và Recall.

AI giúp tôi tiết kiệm nhiều thời gian trong việc tổng hợp ý tưởng và trình bày báo cáo theo đúng cấu trúc yêu cầu.

---

## 2. AI đã trả lời sai hoặc chưa phù hợp

Trong quá trình sử dụng, AI có một số câu trả lời chưa phù hợp với yêu cầu thực tế.

Ví dụ, ban đầu AI đề xuất bài toán về Xanh SM hoặc kết hợp cả VinFast và Xanh SM trong cùng một báo cáo, trong khi nhóm tôi chỉ lựa chọn một bài toán của VinFast.

Ngoài ra, AI cũng đưa ra một số số liệu như thời gian xử lý, số lượng video hoặc tỷ lệ cải thiện hiệu suất. Các số liệu này chỉ mang tính tham khảo và không phải dữ liệu nội bộ của VinFast, vì vậy cần ghi rõ đây là các giá trị ước tính hoặc thay thế bằng số liệu thực tế nếu doanh nghiệp cung cấp.

Một số đề xuất ban đầu cũng tập trung vào việc để AI tự động đưa ra kết luận cuối cùng. Sau khi xem xét, nhóm thống nhất rằng AI chỉ nên đóng vai trò hỗ trợ, còn quyết định cuối cùng vẫn phải do kỹ sư hoặc nhóm đánh giá xác nhận.

---

## 3. Tôi đã điều chỉnh Prompt như thế nào

Để AI trả lời đúng với bài toán của nhóm, tôi bổ sung thêm các ràng buộc trong prompt.

Cụ thể:

* Chỉ tập trung vào **VinFast**.
* Chỉ phân tích bài toán **Driver Monitoring System (DMS)**.
* AI chỉ hỗ trợ rà soát video để xác nhận tài xế mất tập trung, không tự động đưa ra quyết định cuối cùng.
* Báo cáo phải bám sát cấu trúc của đề bài gồm Current Workflow, Problem Statement, Future-State Flow và Evaluate.
* Các số liệu phải được ghi rõ là ước tính nếu không có nguồn xác thực.

Sau khi bổ sung các điều kiện này, AI đưa ra câu trả lời sát với yêu cầu hơn và phù hợp để nhóm sử dụng trong báo cáo.

---

## 4. Bài học rút ra

Qua buổi học, tôi nhận thấy AI là một công cụ hỗ trợ rất hiệu quả trong việc phân tích bài toán, xây dựng quy trình và đề xuất giải pháp. Tuy nhiên, AI không hiểu đầy đủ bối cảnh nếu prompt chưa đủ chi tiết và đôi khi đưa ra các giả định hoặc số liệu chưa được kiểm chứng.

Để sử dụng AI hiệu quả, cần mô tả rõ phạm vi bài toán, vai trò của AI và các giới hạn của hệ thống. Đồng thời, người dùng phải kiểm tra lại các thông tin quan trọng trước khi đưa vào báo cáo hoặc áp dụng trong thực tế. AI nên được xem là một **trợ lý hỗ trợ ra quyết định**, còn việc đánh giá và chịu trách nhiệm cuối cùng vẫn thuộc về con người.
