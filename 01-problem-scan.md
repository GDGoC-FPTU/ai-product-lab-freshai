
<!-- Nguyễn Đình Phúc-2A202601835 -->
| Subsidiary | Bài toán                                        | AI phù hợp               | Giá trị                            |
| ---------- | ----------------------------------------------- | ------------------------ | ---------------------------------- |
| VinFast    | Dự báo lỗi linh kiện trước khi bảo hành         | Predictive Maintenance   | Giảm chi phí bảo hành              |
| VinFast    | AI đọc và kiểm tra bản vẽ kỹ thuật, BOM         | LLM + OCR                | Giảm lỗi sản xuất                  |
| Xanh SM    | Dự báo nhu cầu theo khu vực để điều phối xe     | Time Series Forecasting  | Tăng doanh thu, giảm thời gian chờ |
| Xanh SM    | AI phát hiện hành vi lái xe nguy hiểm           | Computer Vision + Sensor | An toàn hơn                        |
| Vinhomes   | AI dự báo hỏng thiết bị (thang máy, máy bơm...) | Predictive Maintenance   | Giảm sự cố                         |
| Vinmec     | AI hỗ trợ đọc X-ray/CT/MRI                      | Computer Vision          | Hỗ trợ chẩn đoán                   |

<!-- Phase2 -->

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: AI tự động phân loại và điều phối phản ánh của    │
│ cư dân đến đúng bộ phận xử lý.                              │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [✓] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ - Cư dân                                                    │
│ - Nhân viên CSKH                                             │
│ - Ban quản lý tòa nhà                                       │
│                                                             │
│ Workflow hiện tại:                                          │
│ 1. Cư dân gửi phản ánh                                      │
│      ↓                                                      │
│ 2. CSKH đọc nội dung                                        │
│      ↓                                                      │
│ 3. Xác định loại sự cố                                      │
│      ↓                                                      │
│ 4. Chuyển ticket sang bộ phận phù hợp                       │
│      ↓                                                      │
│ 5. Theo dõi tiến độ                                         │
│                                                             │
│ Bước tốn thời gian nhất?                                    │
│ Phân loại & chuyển ticket                                   │
│ (~4–8 phút/ticket)                                          │
│                                                             │
│ AI hỗ trợ ở bước nào?                                       │
│ - Hiểu nội dung phản ánh                                    │
│ - Phân loại                                                  │
│ - Gán mức độ ưu tiên                                        │
│ - Route đúng bộ phận                                        │
│                                                             │
│ Metric                                                      │
│ • Routing accuracy >95%                                     │
│ • Giảm thời gian xử lý từ 6 phút → dưới 1 phút              │
│ • Giảm 70% ticket phải chuyển lại                           │
│                                                             │
│ Quick Architecture                                          │
│ ☑ LLM + Rule Engine                                         │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: AI hỗ trợ bác sĩ tóm tắt bệnh án và sinh báo cáo  │
│ khám.                                                       │
│                                                             │
│ Công ty thành viên:                                         │
│ [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes                      │
│ [✓] Vinmec                                                  │
│                                                             │
│ Ai đang đau?                                                │
│ - Bác sĩ                                                    │
│ - Điều dưỡng                                                │
│                                                             │
│ Workflow hiện tại                                           │
│ 1. Mở hồ sơ bệnh án                                         │
│      ↓                                                      │
│ 2. Đọc lịch sử khám                                         │
│      ↓                                                      │
│ 3. Khám bệnh                                                │
│      ↓                                                      │
│ 4. Ghi chép báo cáo                                         │
│      ↓                                                      │
│ 5. Lưu EMR                                                  │
│                                                             │
│ Bước tốn thời gian nhất                                     │
│ Đọc bệnh án + ghi báo cáo                                   │
│ (~10–20 phút/lượt khám)                                     │
│                                                             │
│ AI hỗ trợ                                                   │
│ - Tóm tắt lịch sử                                           │
│ - Trích xuất thông tin                                      │
│ - Sinh báo cáo khám                                         │
│ - Gợi ý ICD                                                 │
│                                                             │
│ Metric                                                      │
│ • Giảm thời gian ghi chép từ 15 → 5 phút                    │
│ • Độ chính xác >95%                                         │
│ • Giảm 60% thời gian nhập liệu                              │
│                                                             │
│ Quick Architecture                                          │
│ ☑ LLM + RAG                                                 │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: AI tự động kiểm tra lỗi ngoại thất xe sau lắp ráp │
│ bằng hình ảnh camera.                                       │
│                                                             │
│ Công ty thành viên                                          │
│ [✓] VinFast                                                 │
│                                                             │
│ Ai đang đau?                                                │
│ - Kỹ sư QC                                                  │
│ - Công nhân kiểm định                                       │
│                                                             │
│ Workflow hiện tại                                           │
│ 1. Xe hoàn thiện                                            │
│      ↓                                                      │
│ 2. Đưa vào khu QC                                           │
│      ↓                                                      │
│ 3. Nhân viên kiểm tra thủ công                              │
│      ↓                                                      │
│ 4. Ghi nhận lỗi                                              │
│      ↓                                                      │
│ 5. Chuyển sửa chữa                                          │
│                                                             │
│ Bước tốn thời gian nhất                                     │
│ Kiểm tra ngoại thất                                         │
│ (~8–12 phút/xe)                                             │
│                                                             │
│ AI hỗ trợ                                                   │
│ - Phát hiện vết xước                                        │
│ - Sai khe hở cửa                                            │
│ - Lỗi sơn                                                   │
│ - Thiếu logo/phụ kiện                                       │
│                                                             │
│ Metric                                                      │
│ • Recall >98%                                               │
│ • False Positive <2%                                        │
│ • Giảm thời gian QC từ 10 → 3 phút                          │
│                                                             │
│ Quick Architecture                                          │
│ ☑ Computer Vision                                           │
└─────────────────────────────────────────────────────────────┘