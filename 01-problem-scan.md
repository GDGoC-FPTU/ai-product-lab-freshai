# 01 — Problem Scan (Cá nhân)
# Lab 02: AI Product Scoping — Vin Smart Future

> **Họ và tên:** [Điền họ tên của bạn]
> **MSSV:** [Điền MSSV]
> **Ngày thực hiện:** 24/07/2026

---

# 🔍 Phase 1 — SCAN: Bảng quét cơ hội AI

Sử dụng **4 Lenses** để quét qua vận hành của các công ty thành viên Vingroup.

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | **Xanh SM (GSM)** | 😤 Stakeholder Pain | Tài xế phàn nàn về cuốc xe bị phân công sai khu vực — cuối ca nhận cuốc ở quận xa nhà, phải gọi tổng đài điều chỉnh thủ công. Ước tính ~200 cuốc/ngày tại Hà Nội cần điều chỉnh lại, mỗi lượt mất 8–10 phút xử lý thủ công, gây stress tài xế và rò rỉ doanh thu. |
| 2 | **Vinmec** | 😤 Stakeholder Pain | Bác sĩ mất quá nhiều thời gian viết tóm tắt hồ sơ xuất viện — mỗi tóm tắt mất 20–30 phút/bệnh nhân, trung bình 15–20 bệnh nhân/ngày, chiếm 30–40% thời gian không trực tiếp chữa bệnh. Bác sĩ phàn nàn vì kiệt sức hành chính thay vì tập trung vào khám chữa. |
| 3 | **Xanh SM (GSM)** | 🔁 Lặp lại | Tổng hợp và phân loại lý do hủy chuyến từ ghi chú tài xế — cuối ngày, team Ops đọc 300+ ghi chú văn bản tiếng Việt không có cấu trúc để tìm pattern lỗi hệ thống, mất 3–4 giờ/ngày. Thông tin này quan trọng để cải thiện thuật toán điều vận nhưng bị bỏ bê vì tốn công. |
| 4 | **VinFast** | 🔁 Lặp lại | Kế toán đối chiếu thủ công 1.000+ hóa đơn sạc điện giữa VinFast và các trạm sạc đối tác mỗi tuần — mỗi hóa đơn có định dạng khác nhau (PDF, email, Excel), phải đọc và so khớp tay, mất 2 ngày làm việc/tuần, tỉ lệ lỗi đối chiếu ~5%. |
| 5 | **Vinhomes** | 🤖 AI-upgrade | App Vinhomes nhận 500+ yêu cầu hỗ trợ từ cư dân mỗi ngày (sửa chữa hạ tầng, phí quản lý, an ninh, vệ sinh...). Nhân viên CSKH đọc từng yêu cầu và forward tay đến đúng bộ phận, mất 3–5 phút/yêu cầu, SLA cam kết 12 giờ nhưng thực tế 24–48 giờ do routing sai và quá tải. |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

Chọn **top 3 bài toán tiềm năng nhất** từ bảng SCAN trên: **#1 (Xanh SM cuốc sai), #5 (Vinhomes CSKH), #2 (Vinmec hồ sơ)**.

---

## Quick Problem Card #1 — Xanh SM: Tối ưu hóa phân công cuốc xe theo khu vực

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Tài xế Xanh SM nhận cuốc xe bị phân công sai    │
│ khu vực (xa nhà hoặc xa điểm cuối ca), phải gọi tổng đài   │
│ điều chỉnh thủ công gây tốn thời gian và stress tài xế.    │
│                                                             │
│ Công ty thành viên: [x] Xanh SM (GSM)                      │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│   • Tài xế Xanh SM (người nhận cuốc sai, bị ảnh hưởng      │
│     thu nhập và sức khỏe tâm lý cuối ca)                   │
│   • Điều phối viên (Dispatcher) — phải xử lý 200+ cuộc     │
│     gọi khiếu nại/điều chỉnh mỗi ngày                     │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Hệ thống tự động phân cuốc cho tài xế gần nhất        │
│      (không tính vị trí nhà/khu vực hoạt động ưa thích)   │
│   --> 2. Tài xế nhận thông báo cuốc sai khu vực            │
│   --> 3. Tài xế gọi tổng đài để yêu cầu điều chỉnh        │
│   --> 4. Dispatcher nghe, xác nhận lý do, tìm tài xế       │
│           khác phù hợp hơn thay thế thủ công               │
│   --> 5. Re-assign cuốc, thông báo lại cả 2 tài xế         │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│   Bước 3-4 (⏱ 8-10 phút/lượt, ~200 lượt/ngày)             │
│   Dispatcher phải nghe, hiểu ngữ cảnh, xử lý thủ công     │
│   trong khi quản lý đồng thời nhiều cuộc gọi khác          │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│   Bước 1 & 4: AI phân công thông minh ngay từ đầu dựa      │
│   trên: vị trí hiện tại tài xế, điểm kết thúc ca, lịch     │
│   sử khu vực hoạt động, và tự động tạo draft gợi ý         │
│   re-assign cho Dispatcher duyệt trong dưới 30 giây.       │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   • Giảm số cuốc khiếu nại từ 200/ngày xuống dưới 40/ngày  │
│     (giảm 80%)                                             │
│   • Giảm thời gian xử lý mỗi lượt từ 10 phút              │
│     xuống dưới 2 phút (Dispatcher chỉ cần click duyệt)    │
│                                                             │
│ Quick Architecture: [x] LLM Feature                        │
│   (Scoring + ranking gợi ý re-assign, không cần Agent       │
│    tự trị vì vẫn cần Dispatcher phê duyệt trước khi gửi)  │
└─────────────────────────────────────────────────────────────┘
```

---

## Quick Problem Card #2 — Vinhomes: Định tuyến thông minh yêu cầu hỗ trợ cư dân

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Nhân viên CSKH Vinhomes đọc và forward thủ công  │
│ 500+ yêu cầu hỗ trợ mỗi ngày từ app cư dân đến đúng bộ    │
│ phận xử lý — gây SLA vi phạm và trải nghiệm cư dân kém.   │
│                                                             │
│ Công ty thành viên: [x] Vinhomes                           │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│   • Cư dân Vinhomes (chờ 24-48h thay vì SLA cam kết 12h)  │
│   • Nhân viên CSKH (đọc và phân loại thủ công, bị quá tải) │
│   • Quản lý khu đô thị (vi phạm SLA gây khiếu nại leo      │
│     thang lên ban lãnh đạo Vinhomes)                       │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cư dân gửi yêu cầu qua App Vinhomes Resident          │
│   --> 2. Nhân viên CSKH đọc từng yêu cầu                   │
│   --> 3. Phân loại tay (sửa chữa / phí / an ninh / vệ sinh)│
│           và forward email đến bộ phận phụ trách           │
│   --> 4. Bộ phận nhận email, xử lý, phản hồi cư dân        │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│   Bước 2-3 (⏱ 3-5 phút/yêu cầu x 500 yêu cầu/ngày)        │
│   Forward sai bộ phận ~15% trường hợp → yêu cầu bị đẩy    │
│   lại, mất thêm 4-8 giờ mỗi lần routing sai.              │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│   Bước 2-3: LLM đọc nội dung yêu cầu, phân loại category,  │
│   gắn tag ưu tiên (khẩn cấp / thường), tự động forward     │
│   đến đúng team kèm confidence score hiển thị cho CSKH.   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   • 90% yêu cầu được phân loại và routing đúng trong <10s  │
│   • Giảm tỉ lệ routing sai từ 15% xuống dưới 3%           │
│   • Cải thiện SLA thực tế từ 36 giờ xuống đúng cam kết 12h │
│                                                             │
│ Quick Architecture: [x] LLM Feature                        │
│   (Text classification + routing. Human review khi          │
│    confidence < 80%, không tự động gửi đi nếu chưa duyệt) │
└─────────────────────────────────────────────────────────────┘
```

---

## Quick Problem Card #3 — Vinmec: AI hỗ trợ bác sĩ soạn tóm tắt hồ sơ xuất viện

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Bác sĩ Vinmec viết thủ công tóm tắt hồ sơ xuất  │
│ viện (discharge summary) — chiếm 30-40% thời gian làm      │
│ việc/ngày của bác sĩ, để lại ít thời gian khám bệnh hơn.  │
│                                                             │
│ Công ty thành viên: [x] Vinmec                             │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│   • Bác sĩ điều trị (quá tải hành chính, kiệt sức)        │
│   • Bệnh nhân (bác sĩ ít thời gian khám trực tiếp hơn)    │
│   • Vinmec (chi phí nhân sự cao, bác sĩ giỏi làm việc      │
│     thư ký thay vì tập trung vào giá trị y tế cốt lõi)    │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Bác sĩ mở hệ thống HIS sau khi kết thúc điều trị     │
│   --> 2. Đọc lại toàn bộ hồ sơ: xét nghiệm, chẩn đoán,   │
│           đơn thuốc, ghi chú ca trực                       │
│   --> 3. Viết tóm tắt tay theo mẫu chuẩn Vinmec            │
│           (chẩn đoán, điều trị, kết quả, đơn thuốc ra      │
│            viện, lịch tái khám)                            │
│   --> 4. Kiểm tra lại và ký duyệt                          │
│   --> 5. In và lưu trữ hồ sơ                               │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│   Bước 2-3 (⏱ 20-25 phút/bệnh nhân x 15-20 BN/ngày)      │
│   Lỗi: thiếu thông tin, sai đơn thuốc, format không nhất  │
│   quán → phải sửa lại khi kiểm duyệt (mất thêm 10 phút). │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│   Bước 2-3: LLM đọc dữ liệu có cấu trúc từ HIS (xét       │
│   nghiệm, chẩn đoán ICD-10, đơn thuốc), tự động generate  │
│   bản nháp tóm tắt theo mẫu Vinmec. Bác sĩ chỉ review,   │
│   chỉnh và ký — không cần viết từ đầu nữa.                │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   • Giảm thời gian hoàn thiện tóm tắt từ 25 phút          │
│     xuống dưới 5 phút/bệnh nhân (review + ký)             │
│   • Độ chính xác draft: 95% thông tin đúng không cần sửa  │
│     lớn (đo bằng audit 100 hồ sơ đầu tiên)               │
│                                                             │
│ Quick Architecture: [x] LLM Feature                        │
│   (Structured data extraction + text generation.           │
│    Bắt buộc HITL: bác sĩ PHẢI ký duyệt bản cuối.         │
│    CẤM tự động lưu hồ sơ khi chưa có chữ ký số bác sĩ.)  │
└─────────────────────────────────────────────────────────────┘
```

---

> **✅ Checklist hoàn thành file này:**
> - [ ] Điền đầy đủ Họ tên và MSSV ở đầu file
> - [ ] Bảng SCAN có đủ 5 bài toán từ ≥2 công ty Vingroup
> - [ ] Mỗi bài toán xác định đúng Lens (Lặp lại / Tốn thời gian / AI-upgrade / Stakeholder Pain)
> - [ ] 3 Quick Cards mỗi card đủ 7 trường thông tin
> - [ ] Metric có con số cụ thể (không viết chung chung)
> - [ ] Quick Architecture được chọn và có giải thích ngắn
