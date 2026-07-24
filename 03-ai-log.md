# 03 — AI Log (Cá nhân)
# Lab 02: AI Product Scoping — Vin Smart Future

> **Họ và tên:** Nguyễn Ngọc Sơn
> **MSSV:** 2A202601948
> **Ngày:** 24/07/2026
> **Công cụ AI dùng:** Antigravity (Claude Sonnet) tích hợp trong VS Code

---

## AI giúp gì?

Trong buổi lab mình dùng AI khá nhiều, chủ yếu là:

- Đọc file README và các tài liệu đề bài rồi nhờ AI tóm tắt lại nhóm cần làm gì, theo thứ tự nào — đỡ mất công đọc hết từng chữ.
- Brainstorm pain points cho Phase 1. Mình cho AI biết bối cảnh Vingroup rồi nhờ gợi ý, AI đưa ra cả danh sách với con số ước tính, mình chỉ cần chọn cái nào phù hợp.
- Viết 3 Quick Problem Cards theo template. Sau khi mình chọn bài toán, AI điền đủ các trường (Actor, Workflow, Bottleneck, Metric, Architecture) — tiết kiệm nhiều thời gian so với tự gõ từng cái.
- Phân tích diagram nhóm vẽ tay. Mình chụp ảnh sơ đồ rồi đưa cho AI, AI đọc được và phân tích các bước, bottleneck, handoff — từ đó viết luôn phần deep-dive report.
- Làm mấy lệnh git (tạo branch, commit, push) vì mình hay quên cú pháp.

---

## AI sai gì?

**Lỗi đáng chú ý nhất:** Khi nhờ AI gợi ý pain points, AI đưa vào danh sách bài toán "Xanh SM sự cố sạc pin" — đúng cái case mẫu đã có sẵn trong file `02-deliverable-example.md`. AI còn tự ghi chú là "nên tránh chọn cái này" nhưng vẫn để nó trong danh sách thay vì bỏ hẳn ra.

Nếu mình không đọc kỹ và chọn nhầm thì bài nộp sẽ giống y chang ví dụ mẫu, chắc chắn bị điểm thấp.

**Lỗi thứ 2:** Khi viết file báo cáo nhóm, AI không hỏi tên nhóm và thành viên trước, tự điền placeholder vào rồi để mình sửa lại. Nhỏ thôi nhưng hơi mất công.

---

## Sửa đổi ra sao?

Với case mẫu bị lẫn vào danh sách — mình phát hiện ra khi đọc lại và không chọn nó. Lần sau sẽ nói rõ hơn trong prompt, ví dụ thêm câu "không được gợi ý bài toán nào đã có trong file example".

Với thông tin nhóm — mình tự điền thẳng vào file thay vì nhờ AI, vì thông tin đó AI không thể biết được.

Bài học chung là AI viết nhanh nhưng vẫn cần người đọc lại và kiểm tra. Không nên copy thẳng output mà không review, đặc biệt khi AI có thể "biết" thông tin nhưng vẫn áp dụng sai ngữ cảnh.
