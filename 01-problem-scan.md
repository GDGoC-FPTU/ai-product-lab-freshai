### 📝 List bài toán của tôi:

| # | Subsidiary (VinFast)                                                                   | Lens                   | Mô tả ngắn bài toán                                                                                                                                                                                                                                                                                      |
| - | -------------------------------------------------------------------------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Kiểm duyệt chứng từ chất lượng linh kiện đầu vào                            | Lặp lại              | Kỹ sư IQC phải kiểm tra và so sánh thủ công hàng ngàn tờ COA (Certificate of Analysis), Packing List, thông số vật liệu từ hàng trăm nhà cung cấp linh kiện/cell pin mỗi ngày.                                                                                                         |
| 2 | Phân loại & Ghép nối Cell Pin tự động                                           | Tốn thời gian        | Kỹ thuật viên mất nhiều giờ lập lịch tính toán tổ hợp ghép nhóm sao cho mức độ đồng đều giữa các cell trong cùng một module là cao nhất                                                                                                                                            |
| 3 | Chẩn đoán mã lỗi Telematics (DTC) & Đặt lịch sửa chữa tại Xưởng dịch vụ | AI có thể tốt hơn  | Dịch vụ CSKH hiện tại thường phản hồi theo kịch bản rập khuôn ("Bác mang xe ra xưởng gần nhất"). AI Anomaly Detection trên dữ liệu Telemetry có thể dự báo trước lỗi (Predictive Diagnostics), tự động phân tích nguyên nhân gốc và gợi ý phương án xử lý cho KTV. |
| 4 | Phân tích Log thử nghiệm ADAS & Phân loại Bug phần mềm                         | Pain từ người khác | **Đội ngũ Kỹ sư phần mềm & Kiểm thử (QA/QC)** luôn trong trạng thái quá tải, trong khi ban quản lý phàn nàn vì tiến độ tung các bản cập nhật OTA bị chậm.                                                                                                                   |
| 5 | Đối soát & Xử lý khiếu nại giao dịch sạc điện                               | Tốn thời gian        | Khi giao dịch sạc bị lỗi (xe ngắt sạc giữa chừng, tài khoản bị trừ tiền nhưng súng sạc không kích hoạt), nhân viên mất từ 24–48 giờ để tra cứu log kết nối MQTT/OCPP giữa trụ sạc và cloud backend.                                                                         |

---

### Quick problem card

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Dùng AI để kiểm duyệt chứng từ COA/Packing List   │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ sư IQC │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tiếp nhận & Phân loại luồng ──> 2. Xử lý Kiểm duyệt ──> 3. Tích hợp Hệ thống MES/WMS & Kiểm định Thực tế │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Xử lý Kiểm duyệt (⏱ 30 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Xử lý Kiểm duyệt│
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian xử lý từ 30 phút -> dưới 1 phút│
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Phân loại & Ghép nối Cell Pin tự động   │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ sư Quy trình & Kiểm định Pin │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Đọc dữ liệu đo (Voltage/IR/Capacitance) từ máy test ──> 2. Tính toán & Phân nhóm    │
│   cell (Grouping) bằng Rule cứng ──> 3. Lập sơ đồ ghép Module ──> 4. Xuất lệnh đóng Pack │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Tính toán & Phân nhóm cell (⏱ 2-4 giờ/lô 10.000 cells)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Xử lý Kiểm duyệt│
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian tính toán từ 3 giờ ──> dưới 2 phút; │
│                                       Giảm tỷ lệ lệch áp (Delta V) giữa các cell trong  │
│                                       Pack từ 15mV ──> under 5mV│
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #4                                                                   │
│                                                                                         │
│ Bài toán: Phân tích Log thử nghiệm ADAS & Phân loại Bug phần mềm (Automotive Software   │
│           Log Triaging & Edge-Case Detection)                                          │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes                              │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________                              │
│                                                                                         │
│ Ai đang đau (Actor)? Kỹ sư Phần mềm ADAS / Kỹ sư Kiểm thử (ADAS Test & QA Engineer)    │
│                                                                                         │
│ Workflow thủ công hiện tại (3-5 bước):                                                  │
│   1. Tải log chuỗi thời gian (CAN bus, Camera, LiDAR) ──> 2. Quét log tìm sự cố/Phantom │
│   Braking ──> 3. Cắt clip & Gán nhãn thủ công ──> 4. Phân loại & Assign ticket Bug cho Dev│
│                                                                                         │
│ Bước nào tốn thời gian/lỗi nhất? Quét log tìm sự cố & Cắt clip (⏱ 4-8 giờ/ca test-drive)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Quét log tìm sự cố & Phân loại Assign ticket Bug │
│                                                                                         │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian Triaging log từ 6 giờ ──> under 15 min;│
│                                       Tăng tỷ lệ phát hiện sớm Edge Cases từ 60% ──> 95%│
│                                                                                         │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent (Anomaly Detection + LLM Agent)│
└─────────────────────────────────────────────────────────────────────────────────────────┘
```
