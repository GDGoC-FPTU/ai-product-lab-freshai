### 📝 List bài toán
 
| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | VinFast | Lặp lại (Repetitive) | Đối chiếu hồ sơ bảo hành/triệu hồi (VIN, lịch sử sửa chữa, phụ tùng thay thế) giữa các trung tâm dịch vụ — tác vụ lặp lại hàng nghìn lần/tháng, hiện làm thủ công qua tra cứu từng hồ sơ |
| 2 | Xanh SM | Tốn thời gian (Time-consuming) | Xác minh hồ sơ onboarding tài xế mới (GPLX, lý lịch tư pháp, đối chiếu thông tin) — trung bình 2-5 ngày/hồ sơ do nhân sự kiểm tra thủ công, trong khi công ty đang tuyển hàng chục nghìn tài xế/đợt |
| 3 | Vinhomes | AI có thể tốt hơn (AI-upgrade) | Soạn thảo phản hồi yêu cầu dịch vụ/khiếu nại của cư dân (sửa chữa, phàn nàn tiện ích) hiện theo mẫu rập khuôn hoặc do nhân viên gõ tay từng case — dễ tự động hóa bằng AI để tăng tốc độ và cá nhân hóa phản hồi |
| 4 | Vinmec | Pain từ người khác (Stakeholder Pain) | Bác sĩ phàn nàn vì phải đọc thủ công phần lớn phim X-quang/CT/MRI ngay cả với ca sàng lọc thông thường, gây quá tải giờ làm và chậm trả kết quả cho bệnh nhân chờ khám |
| 5 | Vinpearl | Lặp lại + AI-upgrade | Tổng đài CSKH xử lý lặp đi lặp lại các câu hỏi giống nhau (giờ nhận/trả phòng, chính sách trẻ em, đặt vé VinWonders) qua điện thoại/chat thủ công, thay vì chatbot AI trả lời tức thì 24/7 |

## QUICK PROBLEM CARD #1
 
**Bài toán:** Xác minh hồ sơ onboarding tài xế mới tại Xanh SM tốn 2-5 ngày/hồ sơ do kiểm tra thủ công.
 
**Công ty thành viên:** [x] Xanh SM  [ ] VinFast  [ ] Vinhomes  [ ] Vinmec  [ ] Khác
 
**Ai đang đau (Actor)?** Nhân viên nhân sự/vận hành tuyển dụng tài xế (HR Ops), và gián tiếp là ứng viên tài xế phải chờ lâu để được duyệt hồ sơ.
 
**Workflow thủ công hiện tại (3-5 bước):**
1. Ứng viên nộp hồ sơ (GPLX, CMND/CCCD, lý lịch tư pháp) qua form/nộp trực tiếp
2. Nhân viên HR kiểm tra tính hợp lệ từng giấy tờ bằng mắt
3. Nhân viên đối chiếu thông tin chéo giữa các giấy tờ (tên, ngày sinh, số GPLX...)
4. Xác minh lý lịch tư pháp/tiền án tiền sự qua liên hệ cơ quan chức năng hoặc chờ giấy hẹn
5. Duyệt/từ chối hồ sơ, thông báo kết quả cho ứng viên
**Bước nào tốn thời gian/lỗi nhất?** Bước 2-3 (kiểm tra & đối chiếu thủ công) ⏱ ước tính 30-45 phút/hồ sơ, nhân với hàng chục nghìn hồ sơ/đợt tuyển → dễ sai sót, sót lỗi chính tả/số liệu
 
**AI có thể nhảy vào hỗ trợ ở bước nào?** Bước 2-3: OCR + trích xuất thông tin tự động từ ảnh chụp giấy tờ, đối chiếu chéo tự động (fuzzy matching tên/số) và gắn cờ (flag) các hồ sơ bất thường để nhân viên chỉ cần review case exception
 
**Đo thành công bằng gì (Metric có số)?** Giảm thời gian xử lý hồ sơ từ ~2-5 ngày → dưới 4 giờ; giảm tỷ lệ lỗi nhập liệu/đối chiếu sai xuống dưới 1%
 
**Quick Architecture:** [ ] No AI  [ ] Rule  [x] LLM (OCR + extraction)  [ ] Agent
 
---
 
## QUICK PROBLEM CARD #2
 
**Bài toán:** Nhân viên Vinhomes soạn phản hồi khiếu nại/yêu cầu dịch vụ của cư dân theo mẫu rập khuôn hoặc gõ tay từng case, chậm và thiếu cá nhân hóa.
 
**Công ty thành viên:** [x] Vinhomes  [ ] VinFast  [ ] Xanh SM  [ ] Vinmec  [ ] Khác
 
**Ai đang đau (Actor)?** Nhân viên chăm sóc khách hàng/quản lý tòa nhà (Building Management/CS team), và cư dân phải chờ phản hồi.
 
**Workflow thủ công hiện tại (3-5 bước):**
1. Cư dân gửi khiếu nại/yêu cầu qua app, hotline hoặc quầy lễ tân
2. Nhân viên CS đọc, phân loại mức độ ưu tiên và loại vấn đề (kỹ thuật, dịch vụ, thanh toán...)
3. Nhân viên soạn phản hồi thủ công hoặc copy mẫu có sẵn rồi chỉnh sửa
4. Chuyển yêu cầu tới bộ phận liên quan (kỹ thuật, bảo vệ, kế toán...) nếu cần xử lý thực địa
5. Theo dõi và đóng ticket sau khi xử lý xong
**Bước nào tốn thời gian/lỗi nhất?** Bước 2-3 (phân loại + soạn phản hồi) ⏱ ước tính 10-15 phút/case, riêng phản hồi 1-star review có thể mất 20-30 phút để soạn cho phù hợp giọng điệu
 
**AI có thể nhảy vào hỗ trợ ở bước nào?** Bước 2-3: AI tự động phân loại + gắn ưu tiên ticket, đồng thời generate draft phản hồi cá nhân hóa theo ngữ cảnh để nhân viên chỉ cần review/chỉnh sửa trước khi gửi
 
**Đo thành công bằng gì (Metric có số)?** Giảm thời gian soạn phản hồi từ 10-15 phút → dưới 2 phút; giảm thời gian phản hồi trung bình (first response time) 25-40%
 
**Quick Architecture:** [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent
 
---
 
## QUICK PROBLEM CARD #3
 
**Bài toán:** Bác sĩ tại Vinmec phải đọc thủ công phần lớn phim X-quang/CT/MRI ngay cả với ca sàng lọc thông thường, gây quá tải và chậm trả kết quả.
 
**Công ty thành viên:** [x] Vinmec  [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  [ ] Khác
 
**Ai đang đau (Actor)?** Bác sĩ chẩn đoán hình ảnh (radiologist), và bệnh nhân phải chờ kết quả lâu hơn cần thiết.
 
**Workflow thủ công hiện tại (3-5 bước):**
1. Bệnh nhân chụp X-quang/CT/MRI, ảnh được lưu vào hệ thống PACS
2. Bác sĩ nhận danh sách ca cần đọc, xếp hàng theo thứ tự/ưu tiên thủ công
3. Bác sĩ xem từng phim, đối chiếu với hồ sơ bệnh án, ghi nhận bất thường
4. Soạn báo cáo chẩn đoán bằng tay hoặc đọc-chép (dictation)
5. Gửi kết quả cho bác sĩ điều trị/bệnh nhân
**Bước nào tốn thời gian/lỗi nhất?** Bước 2-3 (xếp hàng + đọc phim thủ công cho cả ca đơn giản lẫn phức tạp) ⏱ ước tính 10-20 phút/ca sàng lọc thông thường, dồn ứ vào giờ cao điểm
 
**AI có thể nhảy vào hỗ trợ ở bước nào?** Bước 2-3: AI pre-screening để tự động phát hiện bất thường rõ ràng và ưu tiên ca nghi ngờ lên đầu hàng đợi (triage), giúp bác sĩ tập trung vào ca phức tạp và xác nhận nhanh ca bình thường
 
**Đo thành công bằng gì (Metric có số)?** Giảm thời gian đọc phim cho ca sàng lọc thông thường 20-30%; giảm thời gian trả kết quả trung bình cho bệnh nhân
 
**Quick Architecture:** [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent (AI imaging model + triage pipeline)
 