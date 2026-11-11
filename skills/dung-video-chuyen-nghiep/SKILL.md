---
name: "dung-video-chuyen-nghiep"
description: "Dựng và hậu kỳ video cho thương hiệu, sự kiện hoặc phim hoạt hình: cắt ghép, phụ đề tiếng Việt, intro/outro, khung tên, chữ chuyển động, nhạc, xuất nhiều tỉ lệ (9:16, 16:9, 1:1). Dùng khi nói: chỉnh video, dựng video, làm phụ đề, làm intro, video TikTok, motion graphics."
---

# Dựng video chuyên nghiệp

Tổng hợp từ thư viện cuongmeai.com/tai-lieu: Hyperframes (github.com/heygen-com/hyperframes, của HeyGen), Motion Studio (github.com/flaviorg/motion-studio, giấy phép MIT), Remotion (remotion.dev) trong bộ Studio AI. Đã chỉnh để Claude **tự dựng trong môi trường làm việc đám mây** (có sẵn FFmpeg, Node.js, Python, Chromium/Playwright). Người dùng không cần cài Claude Code hay Terminal trên máy, chỉ cần gửi file.

## Quy tắc chung
- Tiếng Việt, xưng "tui", gọi "bạn". Thuật ngữ mở ngoặc.
- **File gốc của người dùng là bản gốc:** làm trên bản sao, gửi lại file mới, không ghi đè.
- **Hỏi brief trước khi dựng** (gộp trong 1 lượt hỏi), trừ khi yêu cầu đã rõ.
- **Mỗi yêu cầu nhắm một lần render đầy đủ.** Trước đó chụp vài khung hình ở những thời điểm nhiều thứ nhất trên màn hình để tự kiểm tra.
- Mã hóa H.264 với `-preset veryfast` (trừ khi cần chất lượng cao nhất), 30 fps trừ khi được yêu cầu khác.
- **Không bịa** thông tin trong video (giá, hotline, ngày, tên người, chức danh). Thiếu thì hỏi.
- **Thực phẩm sức khỏe:** chữ trên video không được ngụ ý chữa bệnh hay thay thuốc.
- **Giọng nói, hình ảnh người thật:** không giả giọng hay hình ảnh người thật nếu chưa có sự đồng ý. Nhạc nền phải là nhạc người dùng có quyền dùng.

## Brief (hỏi gọn)
1. Video dùng ở đâu? (TikTok/Reels → 9:16 · YouTube/màn hình hội nghị → 16:9 · Fanpage → 1:1 hoặc 4:5)
2. Mục đích và cảm xúc (giới thiệu sản phẩm mới, kỷ niệm sự kiện, giáo dục thiếu nhi…; vui tươi, ấm áp, trang trọng).
3. Độ dài mong muốn.
4. Cần những gì: cắt đoạn thừa, phụ đề, intro/outro, khung tên, chữ nhấn, nhạc, logo góc màn hình, tua nhanh/chậm.
5. Có sẵn gì: transcript hoặc file `.srt`, logo, nhạc, danh sách tên + mốc giây cho khung tên.

Video trên 20 giây hoặc video cho khách/đối tác: brief là bắt buộc.

## Nhận diện thương hiệu (brand kit)
Lần đầu làm cho một thương hiệu, lập một file `brand.md` (màu, font, logo, giọng, kích thước chữ phụ đề, vị trí logo, hotline, tài khoản mạng xã hội) và gửi lại cho người dùng giữ, để các video sau dùng lại. Nếu có Brand Kit trên Canva, lấy màu và font từ đó.

## Các việc và cách làm

### 1. Cắt ghép, tinh chỉnh cơ bản (FFmpeg)
- Cắt đoạn thừa, ghép nhiều clip, đổi tỉ lệ (cắt khung hoặc thêm nền mờ cho video ngang sang 9:16), tăng giảm tốc độ, chỉnh độ sáng và màu nhẹ, chèn logo góc màn hình, nén nhỏ để gửi Zalo.
- Không tự đoán chỗ cắt: xem vài khung hình hoặc lời thoại rồi đề xuất các mốc giây, người dùng duyệt rồi mới cắt.
- Kiểm tra độ dài video **trước khi** đặt bất kỳ mốc thời gian nào.
- Muốn đổi nhạc hoặc cắt ngắn phần cuối: dùng `-c:v copy`, không mã hóa lại hình.

### 2. Phụ đề tiếng Việt
- **Nguồn thời gian, ưu tiên theo thứ tự:** file `.srt`/`.vtt` có sẵn → transcript kèm mốc giây → tự nhận dạng giọng nói (Whisper). Nhận dạng tự động tiếng Việt có thể sai dấu và tên riêng; nếu không tải được mô hình trong môi trường thì nói thẳng và xin transcript.
- **Luôn gửi file `.srt` cho người dùng duyệt chữ trước**, rồi mới đóng cứng vào hình.
- Font phải hỗ trợ đầy đủ dấu tiếng Việt (ví dụ Be Vietnam Pro, Inter, Roboto, Montserrat); kiểm tra bằng ảnh chụp các chữ ế, ở, ự, đ.
- Mỗi dòng tối đa khoảng 40–45 ký tự, tối đa 2 dòng. Đặt ở 1/3 dưới khung hình; video 9:16 thì để cao hơn một chút cho khỏi bị nút của TikTok che. Chữ có viền hoặc nền mờ để đọc được trên mọi nền.
- Có thể gửi kèm file `.srt` riêng để tải lên YouTube/TikTok dạng phụ đề bật/tắt.

### 3. Intro, outro, khung tên, chữ chuyển động (motion graphics)
Cách làm theo tinh thần Hyperframes và Motion Studio: viết cảnh bằng HTML/CSS/Canvas, quay từng khung bằng trình duyệt ẩn, rồi ghép bằng FFmpeg. (Có thể cài Hyperframes bằng `npx` nếu môi trường cho phép; không được thì tự dựng theo cùng nguyên tắc.)
- **Quy trình cho cảnh chuyển động:**
  1. Brief → 2. Lấy tư liệu thật (logo, màu, ảnh sản phẩm người dùng gửi) → 3. **Lưới nhịp** (bảng: giây nào xuất hiện gì), **dừng lại chờ người dùng duyệt** → 4. Viết cảnh → 5. Ghép âm thanh → 6. **Tự chấm** → 7. Render cuối → 8. Lưu brand kit.
- **Luật kỹ thuật:** mỗi khung hình chỉ phụ thuộc vào thời điểm `t` (có hàm `seek(t)`). Không dùng `setTimeout`, `requestAnimationFrame`, transition CSS, hay số ngẫu nhiên không cố định, vì sẽ làm khung hình lệch. Hiệu ứng xuất hiện khoảng 0,4–0,6 giây là mượt.
- **Tự chấm trước khi đưa người dùng xem:** xuất ảnh kiểm tra mỗi 0,5 giây ghép thành một tờ tổng (contact sheet). Chấm 8 tiêu chí: bố cục, chữ đọc được, dấu tiếng Việt, đúng màu thương hiệu, nhịp, chuyển cảnh, không tràn mép/bị che, âm thanh. Sửa 3 tiêu chí thấp nhất mỗi vòng; dừng khi tất cả ≥ 8/10 hoặc sau 5 vòng (nói rõ còn thiếu gì). Đây là điểm tự chấm, người dùng vẫn là người duyệt cuối.
- **Khung tên hàng loạt:** người dùng gửi danh sách "mốc giây – tên – chức danh", tui đặt tất cả trong một lần render. Chức danh phải đúng nguyên văn được cung cấp (ví dụ "TS.BS Nguyễn Văn A – Giám đốc").
- Video dài trên 1 phút: dựng theo từng cảnh 30–90 giây rồi ghép.

### 4. Âm thanh
- Ghép nhạc nền được cung cấp, hạ nhạc xuống khi có lời nói, fade đầu và cuối.
- Không để đỉnh âm vượt -1 dBFS. Cân mức âm lượng tổng khoảng -14 LUFS cho mạng xã hội.
- Giọng đọc AI (ElevenLabs…) cần tài khoản và có phí nếu dùng thương mại; chỉ làm khi người dùng đã có và đồng ý.

### 5. Xuất file
- Xuất nhiều tỉ lệ từ cùng một nguồn khi cần (9:16 cho TikTok, 16:9 cho YouTube, 1:1 cho Fanpage).
- Gửi file MP4 qua khung trò chuyện. Nếu máy người dùng đang được liên kết và họ muốn, ghi thẳng vào thư mục họ chỉ định.
- File đầu vào quá nặng: đề nghị gửi qua thư mục trên máy đã liên kết, hoặc gửi bản nén nhẹ hơn để làm thử trước.

## Giới hạn cần nói rõ
- Kỹ năng này **hậu kỳ và làm hình đồ họa 2D** (chữ, hình khối, logo, biểu đồ, ảnh trượt Ken Burns). **Không tạo được cảnh quay người thật hay hoạt hình 3D.** Cảnh 3D vẫn tạo bằng Gemini hoặc công cụ video AI khác, rồi đưa vào đây để ghép cảnh, làm phụ đề, tiêu đề, nhạc.
- Video ra mắt công khai: nên xem lại toàn bộ, nhất là dấu tiếng Việt, số điện thoại, giá, tên người.
- Cảnh chuyển động 8–15 giây có thể mất 20–40 phút vì vòng tự chấm; việc cắt ghép hay phụ đề nhanh hơn nhiều.

## Mẫu câu có thể dùng
- "Cắt video này còn 30 giây cho TikTok, thêm phụ đề và logo góc trên."
- "Làm intro 5 giây và outro có hotline cho video giới thiệu sản phẩm mới."
- "Thêm khung tên cho các diễn giả theo danh sách này: [mốc giây – tên – chức danh]."
- "Ghép 4 cảnh phim hoạt hình này, thêm tiêu đề tập và phụ đề."
- "Xuất video này ra 3 tỉ lệ 9:16, 16:9 và 1:1."
