---
name: "phan-loai-hop-thu"
description: "Quét Gmail, phân loại thư theo 3 mức khẩn và soạn sẵn thư trả lời, chỉ gửi khi người dùng duyệt. Dùng khi nói: dọn hộp thư, phân loại email, /triage, có mail gì cần trả lời."
---

# Phân loại hộp thư (Inbox Triage)

Phỏng theo lệnh /triage trong github.com/mimurchison/claude-chief-of-staff, Việt hóa cho người làm thư ký/trợ lý lãnh đạo kiêm quản lý một thương hiệu nhỏ.

Mục tiêu: dọn hộp thư trong **2–3 phút**. Tui lọc, xếp mức độ khẩn, soạn sẵn thư trả lời; người dùng chỉ việc duyệt.

## Cách gọi
| Người dùng nói | Tui làm |
|---|---|
| "dọn hộp thư nhanh" / "/triage nhanh" | Chỉ liệt kê thư Mức 1, không soạn |
| "tóm tắt hộp thư" / "/triage tóm tắt" | Soạn thư Mức 1, tóm tắt Mức 2 |
| "dọn hộp thư" / "/triage" | Quét đầy đủ, soạn thư cho Mức 1 và 2 |

## Quy tắc bắt buộc
- **KHÔNG BAO GIỜ tự gửi thư.** Chỉ gửi khi người dùng gõ rõ "Gửi" (hoặc "Gửi hết") cho từng thư đã xem. Không ngoại lệ, kể cả thư ngắn.
- Nếu người dùng muốn tự sửa trước khi gửi → lưu thành **bản nháp trong Gmail** (Gmail draft).
- Tiếng Việt, xưng "tui", gọi "bạn". Thuật ngữ tiếng Anh mở ngoặc dịch nghĩa.
- Không bịa nội dung thư hay thông tin chưa được cung cấp. Thiếu thông tin để trả lời thì để chỗ trống `[cần điền: …]`.

## Bước 0: Xác định thời gian
Lấy giờ hiện tại (theo múi giờ của người dùng) để biết "hôm nay", "gần đây" là khi nào. Xem nhanh lịch hôm nay để biết người dùng đang ở đoạn nào trong ngày.

## Bước 1: Quét Gmail
- Tìm: `in:inbox newer_than:1d` (hoặc từ lần dọn trước). Nếu ít thư thì mở rộng `newer_than:3d is:unread`.
- Tập trung: thư gửi trực tiếp cho người dùng. Bỏ qua thư quảng cáo, bản tin, thông báo tự động, hóa đơn, thông báo giao hàng, thư chỉ được CC.
- Chuỗi thư dài: tóm tắt cả chuỗi, không chỉ trích thư cuối.
- Kênh nhắn tin chưa kết nối được thì bỏ qua, không nhắc.

## Bước 2: Xếp mức độ
| Mức | Tiêu chí | Hành động |
|---|---|---|
| **Mức 1 — Trả lời ngay** | Từ sếp trực tiếp/CEO; từ lãnh đạo, đối tác quan trọng; khách doanh nghiệp hoặc nhà cung cấp đang chờ; có hạn chót hôm nay/ngày mai; có người đang bị kẹt chờ mình; liên quan lịch của sếp | Xử lý ngay |
| **Mức 2 — Xử lý trong ngày** | Quan trọng nhưng chưa gấp; cần trả lời kỹ; công văn, hồ sơ, báo giá | Gom làm một lượt |
| **Mức 3 — Để biết** | Thông báo, bản tin, việc không cần hồi âm | Liệt kê ngắn, gợi ý lưu trữ |

Yếu tố nâng mức: người gửi quan trọng, đã chờ lâu, có hạn chót, gắn với mục tiêu đang theo (xem tab "Mục tiêu" trong bảng điều hành nếu có).

## Bước 3: Kiểm tra đã trả lời chưa
Trước khi soạn, xem thư mục đã gửi (`in:sent`) cùng chuỗi. Nếu đã trả lời rồi thì bỏ qua.

## Bước 4: Soạn thư trả lời
Thư soạn phải **gửi được ngay**, không phải bản nháp sơ sài.

**Giọng văn:**
- Gửi đối tác/cơ quan bên ngoài thay mặt tổ chức: trang trọng, lịch sự, ngắn gọn; xưng "tôi"/"em" tùy quan hệ, kính gửi đúng chức danh.
- Gửi sếp/CEO: kính trọng, đi thẳng vào việc, nêu rõ việc cần sếp quyết.
- Gửi khách/đối tác của thương hiệu: thân thiện, ấm áp, chuyên nghiệp.
- Câu ngắn, mỗi đoạn 2–3 dòng.
- Chữ ký: dùng chữ ký người dùng đã cung cấp; chưa có thì hỏi một lần.

**Hẹn lịch trong thư:**
- KHÔNG viết kiểu "Anh/chị rảnh khi nào?" hay "Mình sắp xếp thời gian sau nhé".
- PHẢI xem lịch trước (lịch của người dùng, hoặc lịch của sếp nếu hẹn với sếp), rồi đề xuất 2–3 khung giờ cụ thể. Ví dụ: "Bên em có thể sắp xếp 9h sáng thứ Ba hoặc 14h chiều thứ Năm, anh/chị chọn giúp em khung nào tiện nhé."
- Nếu không xem được lịch: viết "Em sẽ kiểm tra lịch và gửi anh/chị vài khung giờ phù hợp", không tự đoán giờ.

**Chủ đề nhạy cảm** (lương, nhân sự, cho nghỉ việc, hợp đồng, tranh chấp, tài chính): trước khi soạn, nhắc người dùng kiểm tra lại người nhận và danh sách CC.

## Bước 5: Trình bày
```
Đã quét: Gmail ([số] thư)

🔴 MỨC 1 — Trả lời ngay
1. [Người gửi] — [Tiêu đề/tóm tắt] (đã chờ [x giờ/ngày])
   Thư soạn sẵn:
   "[nội dung]"

🟡 MỨC 2 — Xử lý trong ngày
2. [Người gửi] — [Tóm tắt]
   Thư soạn sẵn: "[nội dung]"

⚪ MỨC 3 — Để biết
3–N. [Danh sách ngắn]

TỔNG: [x] thư cần xử lý, [y] thư đã soạn sẵn.
```
Không có gì gấp thì nói rõ: "Hộp thư sạch, không có thư cần xử lý ngay."

## Bước 6: Chờ duyệt
Người dùng có thể nói:
- "Gửi 1" / "Gửi hết" → gửi đúng thư đó
- "Sửa 2: …" → sửa rồi trình lại
- "Lưu nháp 3" → tạo bản nháp trong Gmail
- "Bỏ qua 4"

Sau khi xử lý xong, nếu thư sinh ra việc cần làm (nộp hồ sơ, gửi báo giá…), hỏi: "Thêm vào danh sách việc cần làm không?" (dùng kỹ năng **quan-ly-cong-viec**).
