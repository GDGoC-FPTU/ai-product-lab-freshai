# 01 — Problem Scan (Cá nhân)

## Thành viên: Lường Duy Thái (MSSV:  2A202601021)

**Công ty thành viên tập trung:** VinFast
**Bài toán chốt để Deep-Dive:** Hệ thống cảnh báo ý thức tài xế (Driver Attention/Drowsiness Alert)

---

## Phase 1 — SCAN: 5 bài toán tiềm năng

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | VinFast | AI-upgrade / Stakeholder Pain | **Hệ thống cảnh báo ý thức tài xế** — trợ lý AI trong xe phát hiện dấu hiệu buồn ngủ/mất tập trung từ chỉ số cảm biến (chớp mắt, hướng đầu...) và đưa ra cảnh báo real-time |
| 2 | VinFast | Tốn thời gian | Phân loại & tóm tắt ticket bảo hành pin tại trung tâm dịch vụ — nhân viên đọc thủ công log lỗi + mô tả khách hàng để xếp mức độ ưu tiên |
| 3 | VinFast | Lặp lại | Kiểm tra chất lượng hình ảnh lỗi ngoại thất/nội thất xe trên dây chuyền sản xuất — QC viên soi thủ công ảnh chụp xe |
| 4 | VinFast | AI-upgrade | Trợ lý AI nội bộ cho kỹ thuật viên tra cứu tài liệu sửa chữa (technical manual) thay vì lật thủ công hàng trăm trang |
| 5 | VinFast | Stakeholder Pain | Dự báo nhu cầu phụ tùng thay thế theo khu vực (Spare Parts Demand Forecasting) — trung tâm dịch vụ thiếu phụ tùng đúng lúc cần |

---

## Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

### QUICK PROBLEM CARD #1 (⭐ Bài toán được chọn Deep-Dive)

```
Bài toán (1 câu): Cảnh báo tài xế mất tập trung/buồn ngủ khi lái xe điện VinFast
Công ty thành viên: [x] VinFast

Ai đang đau (Actor)? Tài xế cá nhân + đội xe VinFast/Xanh SM chạy đường dài;
                      gián tiếp là bộ phận An toàn Vận hành (Safety/Fleet Ops)

Workflow thủ công hiện tại (3-5 bước):
  1. Tài xế tự nhận biết mệt/buồn ngủ (không có hỗ trợ)
  ──> 2. Camera/cảm biến trong xe ghi nhận tín hiệu nhưng không xử lý real-time
  ──> 3. Không có cảnh báo chủ động → tài xế tiếp tục lái
  ──> 4. Sự cố xảy ra (nếu có) mới được rà soát lại qua dữ liệu sau đó

Bước nào tốn thời gian/lỗi nhất? Bước 2-3 (⏱ ước tính: hiện tại thời gian phản ứng
        = 0 vì KHÔNG có cảnh báo nào xảy ra; mục tiêu sau khi có AI là phát hiện
        và cảnh báo trong dưới 3 giây kể từ khi chỉ số cảm biến vượt ngưỡng rủi ro)
AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 — suy luận real-time từ các
        chỉ số cảm biến (tần suất chớp mắt, thời gian nhắm mắt, góc đầu lệch...)
        để quyết định mức độ rủi ro và loại cảnh báo phù hợp

Đo thành công bằng gì (Metric có số)?
  "Phát hiện & cảnh báo dấu hiệu buồn ngủ/mất tập trung trong dưới 3 giây,
   độ chính xác ≥ 90%, tỷ lệ cảnh báo giả (false alarm) dưới 5%"

Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent (LLM suy luận
                     đa tín hiệu + quyết định hành động, kết hợp rule an toàn cứng)
```

### QUICK PROBLEM CARD #2

```
Bài toán (1 câu): Phân loại & tóm tắt ticket bảo hành pin tại trung tâm dịch vụ
Công ty thành viên: [x] VinFast

Ai đang đau (Actor)? Nhân viên tiếp nhận (Service Advisor)

Workflow thủ công hiện tại (3-5 bước):
  1. Khách báo lỗi qua hotline/app ──> 2. Đọc mô tả + log lỗi hệ thống
  ──> 3. Tự phân loại mức ưu tiên & loại lỗi ──> 4. Nhập tay vào hệ thống
  ──> 5. Chuyển kỹ thuật viên phù hợp

Bước nào tốn thời gian/lỗi nhất? Bước 2-3 (⏱ ~10 phút/ticket)
AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3 — tóm tắt + gợi ý phân loại

Đo thành công bằng gì (Metric có số)?
  "Giảm thời gian phân loại từ 10 phút xuống dưới 1 phút/ticket,
   độ chính xác phân loại ưu tiên ≥ 90%"

Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent
```

### QUICK PROBLEM CARD #3

```
Bài toán (1 câu): Trợ lý AI tra cứu tài liệu sửa chữa cho kỹ thuật viên
Công ty thành viên: [x] VinFast

Ai đang đau (Actor)? Kỹ thuật viên tại trung tâm dịch vụ

Workflow thủ công hiện tại (3-5 bước):
  1. Xe gặp lỗi ──> 2. KTV lật thủ công tài liệu kỹ thuật (hàng trăm trang)
  ──> 3. Tìm đúng quy trình sửa chữa ──> 4. Thực hiện sửa chữa

Bước nào tốn thời gian/lỗi nhất? Bước 2 (⏱ ~15-20 phút/lần tra cứu)
AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 — chatbot RAG tra cứu tài liệu

Đo thành công bằng gì (Metric có số)?
  "Giảm thời gian tra cứu từ 15 phút xuống dưới 2 phút,
   độ chính xác trích dẫn đúng tài liệu ≥ 95%"

Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent
```