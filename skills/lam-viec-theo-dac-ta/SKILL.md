---
name: "lam-viec-theo-dac-ta"
description: "Dùng cho việc nhiều bước (kế hoạch, dự án, chiến dịch, quy trình mới, mở chi nhánh, dịch vụ mới…): đi qua Đặc tả → Làm rõ → Kế hoạch → Đầu việc → Rà soát → Thực hiện, theo tinh thần spec-kit."
---

# Làm việc theo đặc tả (phỏng theo GitHub Spec Kit)

Nguồn tham khảo: GitHub Spec Kit — https://github.com/github/spec-kit

Tinh thần: làm rõ **CÁI GÌ và VÌ SAO** trước, rồi mới bàn **LÀM THẾ NÀO**. Tinh chỉnh qua nhiều bước, có điểm dừng để người dùng duyệt, thay vì làm một phát ra ngay.

## Khi nào dùng
- DÙNG: việc có từ 3 bước trở lên hoặc kết quả là một kế hoạch/dự án: mở chi nhánh, ra mắt dịch vụ mới, chiến dịch marketing, chính sách (vd giới thiệu khách – referral), quy trình nội bộ, bộ nội dung nhiều phần, hệ thống bảng tính/biểu mẫu mới, dự án cho nơi làm việc.
- KHÔNG DÙNG: câu hỏi nhanh, soạn 1 email/1 bài đăng, sửa nhỏ, tính toán đơn lẻ → trả lời thẳng.
- Người dùng nói "làm theo spec", "/spec" → luôn dùng.

## Quy ước giao tiếp
- Tiếng Việt, xưng "tui" – gọi "bạn". Thuật ngữ tiếng Anh phải mở ngoặc dịch nghĩa.
- Gọn, chuyên nghiệp, không mở đầu lan man.
- Không bịa số liệu. Chỗ chưa biết ghi `[CẦN LÀM RÕ: …]`.

## Bước 0 – Nguyên tắc nền (Hiến chương)
Trước khi đặc tả, kiểm tra các nguyên tắc sẵn có của dự án (bộ nhớ, file dự án: bộ nhận diện thương hiệu, cẩm nang văn hóa, quy định nội bộ…). Nếu dự án chưa có, đề xuất một hiến chương ngắn (tối đa 7 dòng: giá trị thương hiệu, giọng văn, giới hạn ngân sách, điều không được làm, ai duyệt). Chỉ làm một lần cho mỗi dự án, các lần sau dùng lại.

## Bước 1 – Đặc tả (chỉ CÁI GÌ, VÌ SAO – chưa bàn cách làm)
- **Mục tiêu:** muốn đạt điều gì
- **Lý do:** vì sao cần làm bây giờ
- **Đối tượng:** ai hưởng lợi / ai dùng (khách hàng, nhân viên, CEO…)
- **Kết quả cần giao:** sản phẩm cuối là gì, định dạng nào (Sheets, Docs, Canva, email…)
- **Tiêu chí thành công:** đo được (số, hạn, tỷ lệ)
- **Ràng buộc:** ngân sách, thời hạn, nhân sự, pháp lý
- **Ngoài phạm vi:** những gì KHÔNG làm lần này

## Bước 2 – Làm rõ
- Liệt kê chỗ mơ hồ ảnh hưởng đến kết quả, hỏi tối đa 3–5 câu, ưu tiên câu có lựa chọn sẵn.
- Không hỏi điều đã có trong bộ nhớ / tài liệu.
- ⏸ **Điểm dừng 1:** gửi Đặc tả + câu hỏi, chờ người dùng duyệt/trả lời.

## Bước 3 – Kế hoạch (LÀM THẾ NÀO)
- Cách làm chính, các giai đoạn, nguồn lực, chi phí ước tính (ghi rõ nguồn hoặc giả định).
- Rủi ro chính + phương án dự phòng.
- Nếu có 2 hướng đi khác nhau rõ rệt, trình bày ngắn cả hai và nêu đánh đổi.

## Bước 4 – Đầu việc
Bảng việc: STT · Việc · Người phụ trách · Hạn · Phụ thuộc việc nào · Có làm song song được không. Việc nhỏ đến mức làm xong trong 1 buổi.
- ⏸ **Điểm dừng 2:** gửi Kế hoạch + Đầu việc, chờ duyệt.

## Bước 5 – Rà soát (trước khi thực hiện)
Tự kiểm tra và báo ngắn:
- Mỗi tiêu chí thành công đã có đầu việc tương ứng chưa?
- Có mâu thuẫn giữa đặc tả, kế hoạch, ngân sách, thời hạn không?
- Có trái hiến chương / nguyên tắc thương hiệu không?
- Số liệu nào chưa có nguồn?

## Bước 6 – Thực hiện
- Làm theo danh sách việc, đánh dấu việc xong.
- Giao kết quả dạng file đúng định dạng đã chốt.
- Nếu giữa chừng phát hiện đặc tả sai/thiếu → quay lại sửa đặc tả trước, báo người dùng, không lặng lẽ đổi hướng.

## Co giãn theo quy mô
- **Dự án nhỏ** (vài ngày, 1 người): gộp Bước 1+2 thành một tin nhắn, Bước 3+4 thành một bảng, Rà soát chỉ 2–3 dòng.
- **Dự án lớn** (mở chi nhánh, ra mắt dịch vụ mới): làm đủ các bước, lưu Đặc tả – Kế hoạch – Đầu việc thành tài liệu riêng để cập nhật dần.

## Mẫu Đặc tả ngắn
```
ĐẶC TẢ: <tên việc>
Mục tiêu: …
Lý do: …
Đối tượng: …
Kết quả cần giao: … (định dạng: …)
Tiêu chí thành công: 1) … 2) …
Ràng buộc: ngân sách … | hạn … | nhân sự …
Ngoài phạm vi: …
Cần làm rõ: 1) … 2) … 3) …
```