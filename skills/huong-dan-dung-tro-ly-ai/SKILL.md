---
name: "huong-dan-dung-tro-ly-ai"
description: "Huấn luyện người dùng dùng Claude hiệu quả: chọn đúng chế độ, viết prompt 4 bước, xây thư viện prompt, dùng skill/plugin/kết nối (Canva, Gmail, Drive), quản lý bộ nhớ, tiết kiệm lượt dùng. Dùng khi nói: viết prompt giúp tui, dùng Claude sao cho tốt, nên dùng cái nào, mẹo Claude."
---

# Hướng dẫn dùng Claude

Tổng hợp từ thư viện tài liệu cuongmeai.com/tai-lieu (Cường Mê AI): Cẩm nang bộ tứ Claude, 9 bước làm chủ Claude, 4 bước viết prompt chuẩn, Prompt hội đồng chuyên gia, Claude + Canva, Hồ sơ bộ nhớ, 6 skill marketing, MarkItDown. Đã lọc và chỉnh cho người làm văn phòng kiêm quản lý một thương hiệu nhỏ.

## Quy tắc chung
- Tiếng Việt, xưng "tui", gọi "bạn", ngắn gọn. Thuật ngữ mở ngoặc dịch nghĩa.
- Đây là tài liệu của bên thứ ba. **Tên menu, giá gói, giới hạn sử dụng có thể đã đổi.** Khi người dùng hỏi cách bấm cụ thể trong ứng dụng, giá hay giới hạn, tra support.claude.com trước rồi mới trả lời, kèm link nguồn.
- Ưu tiên **làm luôn** hơn là chỉ cách: nếu người dùng nhờ viết prompt cho một việc mà tui làm được ngay, hỏi người dùng muốn lấy prompt để dùng lại hay muốn tui làm luôn.

---

## 1. Chọn đúng cách làm việc
| Việc kết thúc bằng… | Dùng | Ví dụ |
|---|---|---|
| **Chữ** (bài viết, email, bản dịch, giải thích, kế hoạch) | Trò chuyện thường | Viết caption, soạn công văn, lên ý tưởng hộp quà |
| **Đụng vào file hoặc gửi đi đâu đó** (đọc Excel, tính toán, email, lịch, Sheets) | Claude làm việc với file và ứng dụng đã kết nối (trước đây gọi là Cowork) | Tính lương từ file chấm công, dọn hộp thư, đọc số bán trên phần mềm bán hàng |
| **Phần mềm hoặc đoạn mã** | Claude Code | Web chấm công, Google Apps Script đặt lịch |
| **Hình ảnh, slide, giao diện** | Thiết kế / Slides / Canva | Poster sản phẩm mới, hồ sơ năng lực, bộ slide trình sếp |

**Quy trình khép kín cho một ý tưởng lớn:** chốt logic bằng trò chuyện → chuẩn bị dữ liệu mẫu sạch → dựng sản phẩm chạy được (tự test, tự sửa) → làm đẹp và làm tài liệu ra mắt. Đầu ra bước trước là đầu vào bước sau. **Đừng nhảy vào viết code khi ý tưởng còn mơ hồ**, sẽ phải sửa nhiều lần.

**An toàn:** việc không hoàn tác được (gửi email, đăng bài, xóa file, chuyển tiền) thì yêu cầu dừng ở **bản nháp** để người dùng tự kiểm. Khi nhờ viết công cụ, nói rõ cách muốn nó tự kiểm tra (ví dụ "chạy thử trên màn hình điện thoại với 3 nhân viên mẫu").

---

## 2. Viết prompt 4 bước
Khi người dùng nhờ "viết prompt", dựng theo khung:
1. **Vai trò:** chuyên môn + phạm vi việc + tiêu chuẩn ưu tiên. ("Đóng vai chuyên gia viết kịch bản TikTok ngắn cho thương hiệu thực phẩm sức khỏe, ưu tiên tự nhiên, dễ nói")
2. **Bối cảnh:** mục tiêu, đối tượng (trình độ, nỗi đau), nền tảng, giọng, điều cần tránh. Thay tiêu chí mơ hồ ("viết hay") bằng tiêu chí đo được ("ngắn, câu đầu gây tò mò, người mới cũng hiểu").
3. **Yêu cầu chi tiết:** số phiên bản, độ dài, cấu trúc (móc câu – thân – kêu gọi hành động), mỗi bản khác nhau ở đâu, thứ bắt buộc có và cấm có. Chi tiết nào không nói, AI sẽ tự quyết theo mức trung bình.
4. **Định dạng đầu ra:** bảng (để so sánh), gạch đầu dòng (để đọc nhanh), mẫu có nhãn (để chép sang Docs/Canva).

Kết thúc prompt bằng: *"Nếu thiếu thông tin, hỏi tôi tối đa 3 câu trước khi làm."*

**Kỹ thuật nâng cao:**
- **Đưa ví dụ mẫu (few-shot):** dán 1–3 bài người dùng thích để AI bắt giọng.
- **Suy luận từng bước:** với việc tính toán, so sánh, ra quyết định.
- **Tự phản biện:** yêu cầu AI tự chấm bản vừa viết, chỉ điểm yếu, rồi viết lại.
- **Đóng gói lại:** khi đã ra kết quả ưng, nhờ AI rút cả cuộc trò chuyện thành một prompt mẫu có chỗ trống `[...]` để dùng lại.

**Checklist trước khi gửi:** vai trò đủ cụ thể? bối cảnh đủ mục tiêu, đối tượng, giọng, điều cần tránh? yêu cầu đo được? định dạng dùng được ngay? đã cho AI hỏi lại chưa?

**Khi người dùng đưa một prompt ngắn:** viết lại theo 4 bước, cho xem bản trước/sau, giải thích ngắn 2–3 thay đổi quan trọng nhất.

*Ví dụ:* "Viết quảng cáo sữa hạt" → "Đóng vai copywriter cho thương hiệu thực phẩm sức khỏe. Khách là dân văn phòng 25–35 tuổi hay bỏ bữa sáng. Viết 3 caption Facebook dưới 80 chữ, mỗi cái mở đầu bằng một cách khác nhau, có kêu gọi đặt qua app giao đồ ăn. Không dùng từ 'thần kỳ', không hứa chữa bệnh. Trình bày dạng danh sách đánh số."

**Prompt "hội đồng chuyên gia" (God mode):** bản chất là yêu cầu AI tách vấn đề thành 2–4 khía cạnh, tìm điểm đòn bẩy và điểm mù, kết hợp kiến thức nhiều ngành, rồi kết bằng một hành động. Đây là kỹ thuật viết prompt, không phải "mở khóa" gì cả. Giọng tự tin của nó có thể làm thông tin sai nghe có vẻ đúng, nên không dùng cho việc tra cứu nhanh hoặc việc pháp lý, y tế, tài chính. Nếu đã cài, dùng kỹ năng **hoi-dong-co-van**.

---

## 3. Thư viện prompt, skill và plugin
- **Prompt** dùng cho yêu cầu cố định, lặp lại (tóm tắt văn bản, viết caption theo mẫu). Lưu thành file có tên rõ ràng.
- **Skill** dùng cho quy trình nhiều bước (tính lương, bản tin sáng, chấm bài). Cách cài: đưa link GitHub cho Claude để Claude đọc và đề xuất thẻ lưu, hoặc tự tải lên file .zip trong mục Skills.
- **Plugin** là gói gồm skill, công cụ và kết nối cho một ngành. Nên cài một plugin cho mảng chính trước, quen rồi mới thêm.
- **Gợi ý thư viện prompt khởi đầu:** tóm tắt tài liệu (1 câu tiêu đề + 3–7 ý + 1 câu kết, không thêm ý kiến); chân dung khách hàng; mẫu caption sản phẩm mới; mẫu công văn/email thay mặt công ty; mẫu biên bản họp.
- **Nguồn skill marketing bên ngoài đáng xem** (đọc giấy phép và giới hạn trước khi cài): marketingskills của coreyhaines31 (giấy phép MIT, có ai-seo, marketing-council), Brand-building-skills của arnabbagxd (brand-context, brand-voice), head-of-content của bradautomates (cần API trả phí).  Anthropic cũng có sẵn plugin marketing.

---

## 4. Cho Claude hiểu bạn: file bối cảnh và Project
- Hai file quan trọng nhất: **"Về tôi"** (làm gì, bán gì, khách là ai: tuổi, nhu cầu, nỗi đau) và **"Giọng viết"** (giọng, độ dài, dán vài đoạn mình ưng).
- Gắn hai file vào **Project** để mọi cuộc trò chuyện trong Project đó dùng chung. Gợi ý tách Project theo mảng: thương hiệu riêng, công ty, từng dự án lớn. Mỗi Project có bộ nhớ riêng.
- Project dùng chung cho nhóm (gói Team/Enterprise): tải lên quy định, quy trình, thông tin sản phẩm để cả nhóm làm cùng bối cảnh.

## 5. Bộ nhớ của Claude
- Xem, sửa, xóa từng mục: Settings → Memory (theo tài liệu; tên mục có thể đổi).
- Dừng ghi nhớ mới: tắt "Generate memory from chats". Không muốn Claude tìm lại chat cũ: tắt "Search and reference chats" (hai nút riêng).
- Chuyện nhạy cảm: dùng cuộc trò chuyện ẩn danh (Incognito), không tạo ghi nhớ.
- Muốn biết Claude nhớ gì về mình: hỏi thẳng "Liệt kê những gì bạn đã ghi nhớ về tôi". Các câu kiểu "đoán tính cách, đoán quyết định tiếp theo của tôi" chỉ là suy đoán, không phải đánh giá đáng tin.

## 6. Kết nối ứng dụng (Connectors)
- Các kết nối hay dùng: Gmail, Google Calendar, Drive, Docs, Sheets, Canva, Notion, phần mềm bán hàng (POS). Claude hỏi quyền trước khi truy cập hoặc hành động; nên đọc kỹ từng yêu cầu.
- **Canva:** hỏi Claude "bạn làm được gì trong Canva" trước. Mô tả kỹ kích thước, màu, thành phần bắt buộc (tiêu đề, giá, hotline, logo). Thêm "dùng Brand Kit của tôi" để đúng logo, màu, font. **Luôn xem bản xem trước** và soát kỹ số điện thoại, ngày, giá trước khi xuất hoặc đăng.
  - Mẫu poster sản phẩm mới: "Thiết kế poster quảng cáo món mới, khổ 4:5, cho thương hiệu [tên thương hiệu]. Tiêu đề lớn 'MÓN MỚI', [tên món], [2 ly sản phẩm kèm nhãn giá], nguyên liệu tự nhiên làm nền, băng rôn nhỏ, chân trang có hotline [số hotline] và logo. Dùng Brand Kit của tôi."
  - Mẫu carousel 5 slide 1080×1080: bìa móc câu → 3 slide nội dung → slide kêu gọi hành động.
- **Lịch tự động:** việc lặp lại (bản tin sáng, dọn hộp thư trưa) có thể đặt thành tác vụ hẹn giờ. Bắt đầu bằng việc ít rủi ro.

## 7. Tiết kiệm lượt dùng khi gửi tài liệu dài
- PDF được xử lý cả dạng chữ lẫn dạng ảnh từng trang nên tốn hơn. Với PDF nhiều chữ, có thể chuyển sang Markdown (định dạng văn bản thuần) bằng công cụ miễn phí **MarkItDown** của Microsoft rồi gửi file .md. Nếu người dùng muốn, tui có thể tự chuyển đổi giúp.
- Không chuyển với: PDF scan, tài liệu mà biểu đồ/hình mang ý chính, biểu mẫu nhiều cột. Với hợp đồng hay báo cáo tài chính, kiểm tra lại bản chuyển đổi.
- Tài liệu dài: chỉ gửi chương hoặc trang cần dùng.

---

## Cách trả lời
- Được hỏi "nên dùng cái nào" → trả lời theo bảng mục 1, một câu lý do, rồi đề nghị làm luôn.
- Được nhờ "viết prompt" → đưa prompt hoàn chỉnh theo 4 bước trong một khối để chép, có chỗ trống `[...]`, kèm 1–2 dòng giải thích.
- Được hỏi cách cài, bấm, giá, giới hạn → tra support.claude.com trước, ghi nguồn.
- Không hướng dẫn cách xoá dấu vết nhận biết nội dung do AI tạo để giả làm người viết.