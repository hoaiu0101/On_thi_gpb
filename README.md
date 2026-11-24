# Ôn thi Giải phẫu bệnh – HIU

Ứng dụng web ôn thi trắc nghiệm môn **Giải phẫu bệnh** (Răng Hàm Mặt – Đại học Quốc tế Hồng Bàng), bám sát slide bài giảng TS.BS. Tiền Thanh Liêm.

- **211 câu**: 204 câu từ slide (8 bài) + 7 câu “Mở rộng” ngoài slide (có ghi nguồn).
- Mức độ: Dễ 65 · Trung bình 66 · Khó 50 · Rất khó 30 (≈ 30/30/25/15%).
- Mỗi câu có: đáp án, giải thích, lý do các phương án khác sai (câu khó), bẫy thường gặp, cảnh báo “cần xác minh”, nguồn slide.
- **Luyện tập** theo bài / mức độ / ưu tiên · **Thi thử**: 3 đề mô phỏng 40 câu – 50 phút, và đề ngẫu nhiên cân bằng độ khó · **Flashcard** · **Ôn câu sai** · **Ghi nhớ**: trọng tâm, cặp khái niệm dễ nhầm, nội dung cần xác minh, tra cứu không dấu.
- Dùng được **offline** sau lần mở đầu tiên, có thể **thêm vào màn hình chính** như một ứng dụng.
- Tiến độ lưu trên trình duyệt của từng thiết bị; dùng “Sao lưu (JSON)” để chuyển sang máy khác.

## Các file

| File | Vai trò |
|---|---|
| `index.html` | Toàn bộ ứng dụng + ngân hàng câu hỏi |
| `manifest.webmanifest`, `sw.js` | Cài lên màn hình chính, dùng offline |
| `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | Biểu tượng |
| `tai-lieu/` | (Không bắt buộc) File PowerPoint/Excel để tải về. Thiếu thư mục này thì trang tự ẩn mục “Tài liệu kèm theo”. |

## Đưa lên GitHub Pages

**Cách 1 – kho (repo) mới** (ví dụ tên `on-thi-gpb`)

1. Trên GitHub bấm **New repository** → đặt tên → chọn **Public** → **Create repository**.
2. Bấm **Add file → Upload files**, kéo thả *tất cả* file ở trên (và thư mục `tai-lieu` nếu muốn) → **Commit changes**.
3. Vào **Settings → Pages** → *Source*: **Deploy from a branch** → *Branch*: **main**, thư mục **/(root)** → **Save**.
4. Đợi 1–2 phút, trang có địa chỉ: `https://<tên-tài-khoản>.github.io/on-thi-gpb/`

**Cách 2 – thêm vào kho đang có** (ví dụ `Hoaiuhocbai`, giữ nguyên trang Ký sinh trùng)

1. Trong kho `Hoaiuhocbai` bấm **Add file → Upload files**, kéo cả thư mục chứa các file này (ví dụ đặt tên thư mục `gpb`) → **Commit changes**.
2. Trang có địa chỉ: `https://<tên-tài-khoản>.github.io/Hoaiuhocbai/gpb/`

> Kéo thả thư mục làm dễ nhất trên máy tính (Chrome/Edge). Trên điện thoại, trang GitHub chỉ cho chọn từng file.

## Thêm vào màn hình chính

- **iPhone (Safari)**: mở trang → nút Chia sẻ → **Thêm vào MH chính**.
- **Android (Chrome)**: mở trang → menu ⋮ → **Thêm vào màn hình chính / Cài đặt ứng dụng**.

## Sửa hoặc thêm câu hỏi

Ngân hàng câu hỏi nằm trong `index.html`, ở dòng bắt đầu bằng `const QUESTIONS = [...]`. Mỗi câu có dạng:

```
{"c":"GPB38-20","t":"3.8","l":3,"p":"C","y":"Tình huống","q":"Câu hỏi…","o":["A","B","C","D"],"a":1,
 "e":"Giải thích…","w":"Vì sao phương án khác sai…","k":"Bẫy…","f":"Cần xác minh…","s":"3.8 – slide 29"}
```

`a` là số thứ tự đáp án đúng (0 = A, 1 = B, 2 = C, 3 = D). Trong `e`, `w`, `k`, ký hiệu `{#2}` sẽ tự hiện thành chữ cái của phương án thứ 3 sau khi đáp án được đảo. Sau khi sửa, đổi `CACHE = "gpb-hiu-v2"` trong `sw.js` sang số mới (v3, v4…) để máy người dùng nhận bản mới.

## Lưu ý

- Tài liệu ôn tập do người học tự biên soạn, không thay thế giáo trình và đề thi chính thức. Khi thi theo bài giảng, ưu tiên nội dung slide; các mục “Cần xác minh” nên hỏi lại giảng viên.
- Câu “Mở rộng” ghi nguồn ngay trong câu (MSD Manual, PathologyOutlines, Tạp chí Y học Việt Nam, PubMed Central…).
