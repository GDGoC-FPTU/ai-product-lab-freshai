# 02 — Deep-Dive Report (Nhóm)
# Lab 02: AI Product Scoping — Vin Smart Future

---

## 👥 Thông tin nhóm

> **Tên nhóm:** FreshAI
> **Công ty thành viên được chọn:** Xanh SM (GSM)

| Họ và tên | MSSV | Vai trò |
|---|---|---|
| Nguyễn Khánh Toàn | 2A202601843 | Leader |
| Nguyễn Ngọc Sơn | 2A202601948 | Thành viên |
| Nguyễn Đình Phúc | 2A202601835 | Thành viên |
| Lưu Quang Nhật | 2A202601920 | Thành viên |
| Nguyễn Quang Huy | 2A202601165 | Thành viên |
| Lường Duy Thái | 2A202601021 | Thành viên |

---

## 🗳️ Quyết định lựa chọn bài toán

**Bài toán được chọn để Deep-Dive:**
> **"Phát hiện tài xế lái xe trong trạng thái mệt mỏi / buồn ngủ (Driver Drowsiness Detection) — Xanh SM (GSM)"**

### Lý do lựa chọn:
- **Rủi ro cao, hậu quả không thể hoàn tác:** Tai nạn do tài xế buồn ngủ không thể xử lý sau khi xảy ra — cần phòng ngừa chủ động từ trước.
- **Điểm mù hoàn toàn của hệ thống hiện tại:** Không có bất kỳ công cụ nào phát hiện trạng thái mệt mỏi của tài xế trong thời gian thực. Hệ thống chỉ phản ứng *sau* khi tai nạn đã xảy ra.
- **Phù hợp AI:** Phân tích dữ liệu hành vi lái xe (tốc độ, lệch làn, phản xạ phanh) hoặc hình ảnh camera trong xe — đây là bài toán AI có thể phát hiện pattern mà con người không thể làm real-time.
- **Impact trực tiếp:** Ảnh hưởng đến an toàn tính mạng tài xế, hành khách và người đi đường, đồng thời bảo vệ thương hiệu Xanh SM.

---

# 🏗️ Phase 3 — DEEP-DIVE

## 3.1. Current-State Workflow (Từ sơ đồ vẽ tay)

Quy trình xử lý hiện tại khi tài xế lái xe trong trạng thái mệt mỏi:

```text
┌─────────────────────┐
│ Bước 1              │
│ Tài xế lái xe       │
│ trong tình trạng mệt│
│                     │
│ Ai: Tài xế          │
│ ⏱ Không đo được —  │
│   không có công cụ  │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Bước 2              │ ◄── 🔴 BOTTLENECK
│ KHÔNG CÓ            │
│ cảnh báo tự động    │
│                     │
│ ⏱ 0 phút —         │
│   không hành động   │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Bước 3              │ ◄── 🔴 BOTTLENECK
│ Suýt tai nạn /      │
│ Tai nạn xảy ra      │
│                     │
│ ⏱ Tức thời —       │
│   hậu quả đã xảy ra │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Bước 4              │
│ Khách / người đi    │ ◄── 🔄 Handoff: Hiện trường → Tổng đài
│ đường phản ánh      │
│                     │
│ ⏱ 5–15 phút        │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Bước 5              │
│ Tổng đài chuyển     │ ◄── 🔄 Handoff: Tổng đài → Quản lý đội xe
│ hồ sơ              │
│                     │
│ ⏱ 30–60 phút       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Bước 6              │
│ Điều tra & xử lý    │
│ sau sự cố           │
│                     │
│ ⏱ 1–3 ngày —       │
│   nhắc nhở, đào tạo,│
│   kỷ luật           │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────────────────────────────────────────────┐
│ TỔNG CỘNG (từ sự cố → xử lý xong): ≈ 1–3 ngày             │
│ ⚠️ Thời gian tài xế mệt: ĐIỂM MÙ HOÀN TOÀN               │
└─────────────────────────────────────────────────────────────┘

🔴 = Bottleneck   🔄 = Handoff
Điểm nghiêm trọng nhất: Bước 2 (0 phút hành động) → dẫn thẳng đến Bước 3 (tai nạn)
```

**Nhận xét từ sơ đồ:**
- Hệ thống hiện tại **hoàn toàn bị động** — chỉ xử lý *sau* sự cố, không có bất kỳ cơ chế phòng ngừa nào.
- Bottleneck chính là **Bước 2**: khoảng trống tuyệt đối — không có sensor, không có alert, không có AI. Tài xế mệt mỏi không được phát hiện → tai nạn xảy ra.
- Sau tai nạn, mất **1–3 ngày** để xử lý hành chính, trong khi thiệt hại đã không thể hoàn tác.

---

## 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Tài xế lái xe của Xanh SM (GSM) — đặc biệt các tài xế làm ca đêm (22:00–06:00) và ca kéo dài trên 8 tiếng liên tục. Đội quản lý an toàn vận hành (Fleet Safety Manager) là người cần nhận cảnh báo và hành động. |
| **2. Current Workflow** | Hiện tại không có công cụ nào theo dõi trạng thái tỉnh táo của tài xế trong thời gian thực. Tài xế lái xe trong trạng thái mệt (Bước 1) → không có cảnh báo nào được kích hoạt (Bước 2) → tai nạn hoặc suýt tai nạn xảy ra (Bước 3) → khách hàng/người đi đường báo cáo tổng đài (Bước 4, mất 5–15 phút) → tổng đài chuyển hồ sơ cho quản lý đội xe (Bước 5, mất 30–60 phút) → điều tra, nhắc nhở, đào tạo lại, kỷ luật (Bước 6, mất 1–3 ngày). Toàn bộ quy trình chỉ là **phản ứng sau sự cố**, không có khả năng phòng ngừa. |
| **3. Bottleneck** | **Bước 2 — Khoảng trống phát hiện (Detection Gap):** Không tồn tại bất kỳ cơ chế nào để phát hiện tài xế đang mệt mỏi trước khi tai nạn xảy ra. Đây là điểm mù công nghệ hoàn toàn. Thời gian từ khi tài xế bắt đầu buồn ngủ đến khi tai nạn xảy ra chỉ vài giây đến vài phút — con người không thể phản ứng kịp nếu không có hệ thống cảnh báo tự động. |
| **4. Business Impact** | (1) **An toàn tính mạng:** Tai nạn do buồn ngủ chiếm ~20–30% tổng số vụ tai nạn giao thông nghiêm trọng (WHO). Với đội xe hàng nghìn tài xế hoạt động 24/7, rủi ro rất cao. (2) **Chi phí bồi thường & pháp lý:** Mỗi vụ tai nạn nghiêm trọng có thể gây thiệt hại từ vài trăm triệu đến hàng tỷ đồng tiền bồi thường và xử lý pháp lý. (3) **Thương hiệu:** Một vụ tai nạn do tài xế buồn ngủ được lan truyền trên mạng xã hội có thể gây sụt giảm nghiêm trọng lòng tin của hành khách vào Xanh SM. (4) **Thời gian xử lý nội bộ:** 1–3 ngày/vụ cho team điều tra và quản lý đội xe. |
| **5. Success Metric** | 1. **Phát hiện sớm:** 85% trường hợp tài xế buồn ngủ được phát hiện và cảnh báo trước khi xảy ra sự cố (đo bằng pilot test 30 ngày với camera + sensor). 2. **Thời gian phản hồi:** Cảnh báo đến tài xế và Fleet Manager trong vòng dưới 5 giây kể từ khi phát hiện dấu hiệu buồn ngủ. 3. **Giảm tai nạn:** Giảm tỉ lệ tai nạn/suýt tai nạn do mệt mỏi xuống 60% sau 6 tháng triển khai. |
| **6. Operational Boundary** | **AI được phép:** (1) Phân tích dữ liệu hành vi lái xe (tần suất phanh, lệch làn, tốc độ phản xạ) từ sensor và GPS; (2) Kết hợp với lịch sử giờ làm việc của tài xế để tính điểm nguy cơ mệt mỏi; (3) Gửi cảnh báo rung/âm thanh đến thiết bị tài xế và thông báo cho Fleet Manager. **CẤM tuyệt đối:** (1) AI không được tự động dừng xe hoặc can thiệp điều khiển xe vật lý; (2) Không được lưu/chia sẻ hình ảnh khuôn mặt tài xế ra ngoài hệ thống nội bộ (bảo vệ quyền riêng tư); (3) Không được ra quyết định kỷ luật tài xế tự động — mọi quyết định kỷ luật phải do Fleet Manager phê duyệt (Bắt buộc HITL). |

---

## 3.3. Future-State Flow & AI Fit

### Xác định mức AI Fit:
**→ Chọn: LLM Feature kết hợp Rule-based Alert**

**Lý do không chọn Agentic Loop:** Hệ thống phòng ngừa tai nạn yêu cầu độ trễ cực thấp (dưới 5 giây) và độ tin cậy cao. Một Agent tự trị có thể bị hallucinate hoặc gọi tool thất bại trong môi trường thực địa không ổn định — không phù hợp cho hệ thống an toàn tính mạng. Rule-based alert xử lý phần trigger cảnh báo, LLM xử lý phần tổng hợp báo cáo và đề xuất hành động cho Fleet Manager.

### Quy trình tương lai (Future-State Flow):

```text
┌─────────────────────┐
│ Bước 1              │
│ Tài xế lái xe       │
│ (bình thường)       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Bước 2              │
│ 🔵 AI/Sensor        │
│ theo dõi real-time  │
│ hành vi lái xe:     │
│ - Lệch làn          │
│ - Phản xạ phanh     │
│ - Giờ lái liên tục  │
│ → Tính điểm nguy cơ │
└──────────┬──────────┘
           │
     ┌─────┴─────┐
     │           │
  Bình        Nguy cơ
  thường      cao (>70%)
     │           │
     ▼           ▼
  Tiếp tục  ┌─────────────────────┐
  giám sát  │ Bước 3              │
            │ 🔵 Rule-based Alert  │
            │ Cảnh báo rung/âm    │
            │ thanh tới tài xế    │
            │ (<5 giây)           │
            └──────────┬──────────┘
                       │
                       ▼
            ┌─────────────────────┐
            │ Bước 4              │
            │ 🟢 HITL:            │
            │ Fleet Manager nhận  │
            │ alert + báo cáo AI  │
            │ (điểm nguy cơ, vị   │
            │ trí, lịch sử giờ)  │
            │ → Quyết định: gọi  │
            │   tài xế / điều xe │
            │   thay thế         │
            └──────────┬──────────┘
                       │
                 ┌─────┴────────┐
                 │              │
            Tài xế          Fleet Manager
            xác nhận        can thiệp:
            tỉnh táo        điều xe thay,
            → tiếp tục      gọi điện, v.v.
                       │
                       ▼
            ↩️ Fallback:
            Nếu sensor mất kết nối
            hoặc AI không tự tin
            (confidence < 70%):
            → Gửi cảnh báo thủ công
              đến Fleet Manager để
              xác minh bằng gọi điện
              trực tiếp cho tài xế
```

---

# 🏁 Phase 5 — EVALUATE

## AI Readiness Checklist:

| # | Câu hỏi | Đánh giá |
|---|---|---|
| 1 | Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test? | ✅ **CÓ** — Xanh SM có GPS logs, dữ liệu lịch sử giờ lái, và có thể gắn OBD sensor vào xe để thu thập dữ liệu hành vi lái trong pilot. |
| 2 | Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)? | ✅ **CÓ** — AI chỉ cảnh báo, không tự điều khiển xe. Fleet Manager là người ra quyết định cuối. Fallback bằng gọi điện trực tiếp nếu hệ thống lỗi. |
| 3 | Stakeholders sẵn sàng thay đổi quy trình làm việc cũ? | ⚠️ **CẦN XEM XÉT** — Tài xế có thể lo ngại bị giám sát quá mức (privacy). Cần minh bạch về mục đích bảo vệ an toàn, không dùng để kỷ luật oan. Fleet Manager cần đào tạo vận hành hệ thống alert mới. |

## Quyết định của Ban Giám Đốc Vin Smart Future:

**[x] GO (Bắt đầu xây dựng Prototype với scope hẹp)**

### Justification — Lý giải quyết định:

**Lý do GO:**

1. **Bằng chứng kỹ thuật:**
   - Bài toán phát hiện hành vi lái xe bất thường là bài toán **có dữ liệu cấu trúc** (GPS, tốc độ, gia tốc, lịch sử giờ lái) — phù hợp với mô hình Rule-based kết hợp ML/LLM có độ chính xác cao.
   - Không cần camera khuôn mặt trong giai đoạn đầu → tránh vướng quyền riêng tư, giảm chi phí.
   - Nhiều hãng taxi và logistics quốc tế (Grab, Uber Freight, DHL) đã triển khai hệ thống tương tự thành công.

2. **Ước lượng chi phí triển khai (Scope hẹp — Pilot 50 xe, 30 ngày):**
   | Hạng mục | Chi phí ước tính |
   |---|---|
   | OBD sensor + GPS nâng cao (50 xe) | ~50 triệu VNĐ |
   | Phát triển rule-based alert engine | ~30 triệu VNĐ |
   | LLM API (Gemini 2.5 Flash) — báo cáo tóm tắt | ~2 triệu VNĐ/tháng |
   | Fleet Manager dashboard | ~20 triệu VNĐ |
   | **Tổng chi phí Pilot** | **~100–120 triệu VNĐ** |

3. **ROI ước tính:**
   - Nếu phòng ngừa được chỉ **1 vụ tai nạn nghiêm trọng/năm** → tiết kiệm ít nhất 500 triệu – 2 tỷ VNĐ chi phí bồi thường, pháp lý, bảo hiểm.
   - ROI dương ngay sau lần ngăn chặn tai nạn đầu tiên.

4. **Scope GO hẹp:**
   - Pilot trên **50 xe ca đêm** tại Hà Nội trong **30 ngày**.
   - Chỉ dùng dữ liệu GPS + OBD (không camera khuôn mặt).
   - Cảnh báo chỉ đến Fleet Manager — chưa gửi thẳng đến tài xế trong giai đoạn 1.
   - Đánh giá kết quả sau 30 ngày → quyết định mở rộng toàn đội xe.
