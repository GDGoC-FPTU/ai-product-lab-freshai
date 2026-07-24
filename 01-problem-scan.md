# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | VinFast | Repetitive| Rà soát video Driver Monitoring (DMS): Hằng ngày hệ thống phát hiện hàng nghìn sự kiện như buồn ngủ, mất tập trung, dùng điện thoại. Kỹ sư phải xem lại video để xác nhận đúng/sai và gán nhãn dữ liệu, rất tốn thời gian.|
| 2 | VinFast | Time-consuming| Chẩn đoán lỗi xe từ dữ liệu telematics: Khi xe báo lỗi, kỹ thuật viên phải đọc DTC (Diagnostic Trouble Code), kiểm tra log CAN Bus và lịch sử sửa chữa trước khi đưa ra kết luận. Việc phân tích thủ công làm tăng thời gian sửa chữa và thời gian xe nằm xưởng. |
| 3 | VinFast | AI-Upgrade| Xử lý ticket chăm sóc khách hàng: Nhân viên phải đọc nội dung khiếu nại, kiểm tra GPS, lịch sử chuyến, thanh toán và ghi âm cuộc gọi để đưa ra quyết định. AI có thể tự động tóm tắt và đề xuất hướng xử lý, giúp giảm đáng kể thời gian phản hồi.|
| 4 | Xanh SM | Stakeholder Pain|Điều phối xe chưa tối ưu: Vào giờ cao điểm hoặc sau các sự kiện lớn, hệ thống có thể phân bổ xe chưa sát nhu cầu thực tế, khiến khách chờ lâu và tài xế phải chạy rỗng để đón khách. |
| 5 | Xanh SM | Time-consuming|Kiểm tra hư hỏng phương tiện bằng hình ảnh: Sau tai nạn hoặc khi bàn giao xe, nhân viên phải xem nhiều ảnh để phát hiện vết trầy, móp, nứt. AI Vision có thể tự động phát hiện và đánh dấu vị trí hư hỏng, rút ngắn thời gian giám định. |

### 3 Quick Problem Cards:
```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Rà soát video Driver Monitoring để xác nhận tài xế đang mất tập trung  │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? AI Engineer, Các bài báo cáo TNGT │     
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Camera trên xe ghi nhận video và AI tạo cảnh báo.      |
|     ──> 2. Kỹ sư mở từng video để xem lại.                  |
|     ──> 3. Đánh giá cảnh báo đúng/sai, xác định nguyên nhân. |
|     ──> 4. Gán nhãn dữ liệu và cập nhật dataset để huấn luyện. │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?Bước 2 & 3   
|  Khoảng 2–5 phút/video (tùy độ dài và độ phức tạp).      │
│ AI có thể nhảy vào hỗ trợ ở bước nào?
|    → Sau khi AI phát hiện sự kiện:                      │
│   • Tự đánh giá confidence.                                 │
│   • Tự phân loại đúng/sai với các trường hợp dễ.  │
│   • Chỉ chuyển các video có confidence thấp cho kỹ sư. │
│   • Tự cắt đoạn video liên quan và tạo tóm tắt sự kiện.      
│                                                             │
│ Đo thành công bằng gì (Metric có số)? │
│ • Giảm thời gian review từ 3 phút xuống dưới 1 phút/video. │
│ • Giảm ≥50% số video cần review thủ công.   │
│ • Precision của cảnh báo >95%.  │
│ • False Positive Rate giảm ≥30%. │
│ • Tăng số video được review mỗi kỹ sư/ngày từ khoảng 150 lên trên 300 video.│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```


```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Điều phối xe chưa tối ưu vào giờ cao điểm |
|hoặc sau các sự kiện lớn, khiến khách chờ lâu                │
│ và tài xế phải chạy rỗng để đón khách.                      |
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ • Khách hàng                                                │
│ • Tài xế                                                    │
│ • Đội vận hành (Fleet Operations/Dispatch)                  |
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ Workflow thủ công hiện tại (3–5 bước):                      │
│ 1. Hệ thống nhận yêu cầu đặt xe.                            │
│    ↓                                                        │
│ 2. Tìm tài xế gần nhất theo vị trí hiện tại.                │
│    ↓                                                        │
│ 3. Phân bổ chuyến dựa trên quy tắc/khoảng cách.             │
│    ↓                                                        │
│ 4. Tài xế di chuyển đến điểm đón hoặc hệ thống phân lại xe. │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ → Bước 2 & 3                                                │
│ ⏱ Khoảng 30 giây – 2 phút/chuyến (khi cung không đủ cầu).   │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ → Trước khi phân bổ chuyến:                                 │
│ • Dự báo nhu cầu theo khu vực và thời gian.                 │
│ • Dự báo lượng xe sắp rảnh.                                 │
│ • Gợi ý điều chuyển xe (reposition) trước giờ cao điểm.     │
│ • Tối ưu ghép tài xế – khách theo ETA thay vì khoảng cách.  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ • Giảm thời gian chờ khách từ 6 phút xuống dưới 4 phút.     │
│ • Giảm quãng đường chạy rỗng của tài xế ≥10%.               │
│ • Tăng tỷ lệ nhận chuyến thành công ≥5%.                    │
│ • Giảm tỷ lệ hủy chuyến do chờ lâu ≥15%.                    │
│ • Tăng số chuyến hoàn thành/xe/ngày khoảng 5–10%.           │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI   [ ] Rule   [ ] LLM   [x] ML + Optimization Agent│
└─────────────────────────────────────────────────────────────┘
```

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Kiểm tra hư hỏng phương tiện bằng hình    |
| ảnh để tự động phát hiện vết trầy, móp và nứt trên xe.      |
│ Công ty thành viên:                                         │
│ [x] VinFast   [x] Xanh SM   [ ] Vinhomes                    |
| [ ] Vinmec   [ ] Khác: ____________                         │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ • Nhân viên giám định xe                                    │
│ • Cố vấn dịch vụ (Service Advisor)                          │
│ • Đội Fleet Operations                                      │
│ • Khách hàng chờ kết quả giám định                          │
│                                                             │
│ Workflow thủ công hiện tại (3–5 bước):                      │
│ 1. Chụp ảnh nhiều góc của xe.                               │
│    ↓                                                        │
│ 2. Nhân viên xem từng ảnh để tìm vết trầy, móp, nứt.        │
│    ↓                                                        │
│ 3. Đánh dấu vị trí hư hỏng và đánh giá mức độ.              │
│    ↓                                                        │
│ 4. Lập biên bản và báo giá sửa chữa.                        │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ → Bước 2 & 3                                                │
│ ⏱ Khoảng 10–20 phút/xe (nhiều ảnh và dễ bỏ sót lỗi nhỏ).   |
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ → Sau khi tải ảnh lên hệ thống:                             │
│ • Tự phát hiện vùng hư hỏng (Object Detection/Segmentation).│
│ • Đánh dấu vị trí trên ảnh.                                 │
│ • Phân loại loại hư hỏng (trầy, móp, nứt...).               │
│ • Ước lượng mức độ nghiêm trọng và gợi ý chi phí sửa chữa.  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ • Giảm thời gian giám định từ 15 phút xuống dưới 5 phút/xe. │
│ • Recall phát hiện hư hỏng ≥95%.                            │
│ • Giảm tỷ lệ bỏ sót hư hỏng ≥30%.                           │
│ • Tăng số xe giám định mỗi nhân viên từ khoảng 30           |
|  lên 60 xe/ngày.                                            │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI   [ ] Rule   [ ] LLM   [x] Computer Vision        │
└─────────────────────────────────────────────────────────────┘
```
