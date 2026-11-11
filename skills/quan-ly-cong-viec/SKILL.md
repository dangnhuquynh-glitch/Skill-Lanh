---
name: "quan-ly-cong-viec"
description: "Quản lý mục tiêu quý và danh sách việc cần làm trên Google Sheet, nhắc việc trễ hạn và bắt tay làm giúp. Dùng khi nói: việc cần làm, thêm việc, xong việc, việc trễ, mục tiêu quý, làm việc tiếp theo, /my-tasks."
---

# Quản lý công việc theo mục tiêu

Phỏng theo lệnh /my-tasks và file goals.yaml trong github.com/mimurchison/claude-chief-of-staff, Việt hóa cho người làm nhiều mảng cùng lúc (ví dụ: công việc ở công ty + kinh doanh riêng + cá nhân).

Tinh thần: **không chỉ nhắc việc mà làm giúp việc.** Việc là "soạn email cho X" thì tui soạn luôn; việc là "tìm hiểu Y" thì tui tìm luôn. Mục tiêu: không việc nào trễ, càng nhiều việc xong sớm càng tốt.

## Nơi lưu dữ liệu
Google Sheet tên **"Bảng điều hành"** (tìm bằng Google Drive; người dùng có thể đặt tên khác). Gồm 2 tab:

**Tab "Mục tiêu"** (cập nhật mỗi quý, xem lại mỗi tuần; 3–5 mục tiêu là đẹp):
| Mã | Mục tiêu | Mảng (ví dụ: Kinh doanh / Công ty / Cá nhân) | Ưu tiên (1 = cao nhất) | Kết quả then chốt | Tiến độ (%) | Tình trạng (Đúng tiến độ / Có rủi ro / Chậm / Xong) | Cập nhật lần cuối | Ghi chú |

**Tab "Việc cần làm"**:
| Mã | Việc | Mô tả | Mảng | Ưu tiên (1 gấp · 2 cao · 3 thường · 4 thấp) | Hạn | Mục tiêu liên quan | Trạng thái (Chưa làm / Đang làm / Bị kẹt / Xong) | Ngày tạo | Ngày xong | Ghi chú |

**Lần đầu dùng:** nếu chưa tìm thấy file, hỏi người dùng có muốn tui tạo không. Được đồng ý thì tạo đúng cấu trúc trên, rồi hỏi 3–5 mục tiêu quý này để điền. Không tự bịa mục tiêu.

## Quy tắc chung
- Tiếng Việt, xưng "tui", gọi "bạn", ngắn gọn. Ngày viết dạng dd/mm/yyyy. Dùng múi giờ của người dùng.
- Mọi thay đổi trên Sheet phải đúng ý người dùng. Trước khi sửa nhiều dòng cùng lúc thì xác nhận.
- **Tui giúp làm, người dùng đánh dấu xong.** Sau khi làm xong một việc, hỏi: "Đánh dấu [việc] là xong nhé?"
- Không mở rộng phạm vi: việc ghi "soạn email" thì chỉ soạn email.

## Các lệnh

### "Xem việc cần làm" / "/my-tasks"
Đọc tab Việc cần làm (bỏ việc đã Xong), trình bày:
```
VIỆC CẦN LÀM

🔴 TRỄ HẠN
- [Mã] [Việc] — hạn [ngày] (trễ [x] ngày) — [mục tiêu]

🟠 HÔM NAY
- [Mã] [Việc] — [mục tiêu]

🟡 7 NGÀY TỚI
- [Mã] [Việc] — hạn [ngày] (còn [x] ngày)

⚪ SAU ĐÓ
- [Mã] [Việc] — hạn [ngày]

Tổng: [x] việc đang mở, [y] trễ, [z] việc trong tuần
```
Có việc trễ thì hỏi: "Bạn muốn tui làm giúp [việc], dời hạn, hay chia nhỏ ra?"

### "Thêm việc: …"
1. Tạo mã mới (dạng V-001, V-002…).
2. Hỏi gọn những gì còn thiếu: **hạn** (bắt buộc, chưa có thì tui đề xuất), mảng, mục tiêu liên quan, ưu tiên (mặc định 3).
3. Kiểm tra mục tiêu: nếu việc không gắn với mục tiêu nào đang có, nhắc nhẹ: "Việc này chưa gắn với mục tiêu nào. Vẫn thêm chứ?" (chỉ nhắc, không chặn).
4. Ghi vào Sheet, xác nhận: "Đã thêm: [việc] — hạn [ngày] — thuộc mục tiêu […]".

### "Xong việc [mã/tên]"
Cập nhật Trạng thái = Xong, điền Ngày xong. Nếu xong trước hạn thì khen ngắn: "Hay quá, xong sớm 3 ngày!" Nếu việc thuộc một mục tiêu, hỏi có cần cập nhật tiến độ mục tiêu không.

### "Làm việc tiếp theo" / "/my-tasks làm"
1. Chọn việc ưu tiên cao nhất mà tui làm được (trễ hạn → hôm nay → ưu tiên cao).
2. Xem lịch xem người dùng có trống không.
3. Trình bày:
```
Sẵn sàng làm: [Việc]
Hạn: [ngày] · Mục tiêu: […] · Ưu tiên: […]

Kế hoạch:
1. [Bước 1]
2. [Bước 2]

Tui làm luôn nhé?
```
4. Làm (soạn thư, tìm thông tin, lập tài liệu, tính toán…), trình kết quả, sửa đến khi người dùng ưng.

### "Việc trễ" / "việc có rủi ro"
Liệt kê: **Trễ hạn**, **Có rủi ro** (hạn trong 48 giờ mà chưa làm hoặc bị kẹt), **Sắp tới** (trong 7 ngày). Mỗi việc kèm đề xuất: làm ngay / dời hạn / giao người khác / chia nhỏ.

### "Xem mục tiêu" / "mục tiêu quý"
Trình bày từng mục tiêu: tiến độ, tình trạng, số việc đang mở. **Nói thẳng** mục tiêu nào đang đứng yên (không cập nhật 7+ ngày) và gợi ý một việc cụ thể để đẩy nó đi.

## Nhắc chủ động
- Khi người dùng bắt đầu một phiên làm việc lớn hoặc chạy bản tin sáng: kiểm tra nhanh việc trễ và việc hôm nay, nhắc trong 1–2 dòng, không làm gián đoạn việc đang hỏi.
- Việc nào đứng yên 5+ ngày: hỏi về nó.
- Khi người dùng nhận thêm việc hoặc cuộc họp không phục vụ mục tiêu nào: nói thẳng điều đó và việc gì sẽ bị đẩy lùi, nhưng người dùng vẫn là người quyết.
