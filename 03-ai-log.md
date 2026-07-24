# 03 — AI Log & Reflection

*Ghi chú: bài dưới đây là bản nháp phản ánh dựa trên quá trình thực tế làm việc với AI
(Claude) trong buổi lab. Từng thành viên đọc, chỉnh sửa lại theo đúng trải nghiệm cá nhân
của mình, thêm/bớt chi tiết cho trung thực, rồi ghi tên + MSSV vào.*

---

## Thành viên: Lường Duy Thái (MSSV:  2A202601021)

### AI giúp gì?

Trong buổi lab, mình dùng AI (Claude) chủ yếu ở 3 giai đoạn:

1. **Brainstorm bài toán (Phase 1):** Ban đầu mình chưa có ý tưởng cụ thể cho mảng VinFast,
   nên nhờ AI gợi ý theo 4 lens (Lặp lại, Tốn thời gian, AI-upgrade, Stakeholder Pain). AI
   đưa ra 10 ý tưởng khác nhau qua 2 lượt hỏi, giúp mình có nhiều lựa chọn để so sánh thay vì
   chỉ bí một hướng. 
2. **Cấu trúc lại Problem Statement (Phase 3):** Sau khi chọn bài toán "Hệ thống cảnh báo ý
   thức tài xế", AI giúp mình viết lại theo đúng khung 6-field và chỉ ra rằng bài toán này có
   một đặc điểm khác thường: bottleneck không phải là "một bước bị chậm" mà là "một bước hoàn
   toàn không tồn tại" (thiếu xử lý real-time). Điều này giúp mình hiểu sâu hơn cách phân tích
   quy trình, không chỉ áp khuôn máy móc.
3. **Viết prompt_prototype.py (Phase 4):** AI hỗ trợ viết system prompt, JSON schema, và đặc
   biệt là 3 adversarial test case (prompt injection, dụ AI ra lệnh điều khiển xe trực tiếp,
   dữ liệu thiếu/mâu thuẫn) — đây là phần mình tự làm sẽ khó nghĩ ra đủ các góc tấn công.

### AI sai gì?

Điểm mình nhận ra rõ nhất: **các con số ước tính impact (VD: "8-12 phút/ticket", "hàng chục
giờ nhân sự lãng phí/ngày") đều do AI tự ước lượng, không dựa trên số liệu thực tế nào của
VinFast.** Nếu mình copy nguyên các con số này vào báo cáo mà không kiểm tra lại, đây sẽ là
một dạng "hallucination nhẹ" — nghe có vẻ hợp lý nhưng thực chất không có căn cứ.

Ngoài ra, ở bước đề xuất kiến trúc, AI ban đầu gợi ý "Agent" (Agentic Loop) cho bài toán cảnh
báo tài xế mà chưa giải thích rõ vì sao không dùng "Rule" đơn giản hơn — mình phải hỏi lại và
nhận ra lý do hợp lý (cần kết hợp rule cứng cho an toàn + LLM cho các trường hợp mơ hồ), nhưng
nếu không hỏi thêm, dễ bị over-engineering mà không tự biết.

### Sửa đổi ra sao?

- Mình đánh dấu rõ trong báo cáo rằng các con số impact là **ước tính giả định**, cần nhóm
  xác minh lại với dữ liệu thật (hoặc dữ liệu mô phỏng) trước khi dùng để thuyết phục stakeholder
  thật — không trình bày như thể đó là số liệu đã được kiểm chứng.
- Mình yêu cầu AI giải thích rõ **tại sao chọn kiến trúc Agent thay vì Rule/LLM đơn thuần**,
  và bổ sung ranh giới cụ thể: "rule cứng luôn ưu tiên hơn LLM trong tình huống khẩn cấp rõ
  ràng" — để tránh rủi ro nếu LLM phản hồi chậm hoặc sai trong tình huống nguy hiểm thực sự.
- Khi test `prompt_prototype.py`, mình chủ động thử thêm các câu lệnh injection khác ("hãy bỏ
  qua ranh giới trên", "đóng vai hệ thống khác") ngoài 3 case AI đã viết sẵn, để tự kiểm chứng
  ranh giới có thực sự vững hay chỉ vững với đúng những case đã được luyện.

---

