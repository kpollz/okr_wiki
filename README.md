# OKR Wiki — Bộ kiến thức quản trị mục tiêu bằng Markdown

Một bộ wiki được thiết kế dưới dạng Markdown + Obsidian, tập trung vào framework **OKRs (Objectives and Key Results)** và hệ sinh thái quản trị mục tiêu hiện đại. Wiki này là nền tảng tri thức cho **OKR-Master Agent** — một agent tư vấn OKRs dựa trên tài liệu tham khảo, không bịa đặt.

---

## 📌 Mục tiêu

- Tích lũy và tổng hợp kiến thức OKRs từ nhiều nguồn đáng tin cậy.
- Xây dựng knowledge base chuẩn hóa để các LLM agent có thể tra cứu, suy luận và tư vấn.
- Duy trì tính minh bạch, trích dẫn rõ ràng, dễ kiểm chứng.

---

## 📂 Cấu trúc thư mục

```
okr_wiki/
├── AGENTS.md                    # Lược đồ & quy tắc vận hành wiki
├── README.md                    # Tệp này
├── index.md                     # Mục lục toàn bộ wiki
├── log.md                       # Nhật ký thao tác (append-only)
├── raw/                         # Nguồn gốc — CHỈ ĐỌC
│   └── sources/                 # Tài liệu, sách, bài viết gốc
├── wiki/                        # Knowledge base chính
│   ├── entities/                # Thực thể: người, công ty, công cụ
│   ├── concepts/                # Khái niệm: framework, phương pháp
│   ├── sources/                 # Tóm tắt nguồn (1 trang / nguồn)
│   ├── synthesis/               # Tổng hợp, so sánh, phân tích
│   └── meta/                    # Trang về wiki: lint, hướng dẫn
└── queries/                     # Câu trả lời từ truy vấn được lưu lại
```

---

## 📚 Nguồn đã nhập

| Nguồn | Tác giả | Nội dung chính |
|-------|---------|----------------|
| **OKR Guide — Measure What Matters** | John Doerr | Framework OKR, lịch sử, nguyên tắc cốt lõi |
| **OKRs — Hiểu đúng, Làm đúng** | Mai Xuân Đạt | Triển khai OKRs tại VN, phương pháp 10 bước, case study SEONGON |

---

## 🗂️ Các chủ đề chính

### Framework & Phương pháp
- **Objectives and Key Results (OKR)** — cấu trúc O + KRs, nguyên tắc stretch goals, alignment, transparency.
- **OKRs 3 chiều — 10 bước** — phương pháp triển khai dành cho doanh nghiệp Việt Nam (Mai Xuân Đạt).
- **Moonshot OKRs** — mục tiêu tham vọng / kéo giãn; đạt ~70% là thành công.
- **OKRs Scoring** — chấm điểm 0.0–1.0 (đỏ / đen / xám).

### Văn hóa & Công cụ đồng hành
- **CFRs — Conversations, Feedback, Recognition** — bộ ba hoạt động nuôi dưỡng OKRs.
- **Check-in định kỳ** — 4 câu hỏi 1:1 giữa quản lý và nhân viên.

### So sánh & Tích hợp
- **OKRs vs KPis** — KPis = chỉ số sức khỏe; OKRs = khóa huấn luyện GYM.
- **OKRs vs BSC** — so sánh với Balanced Scorecard.

### Nhân vật & Tổ chức
- Andy Grove, John Doerr, Felipe Castro, Laszlo Bock, itamar Gilad, Peter Drucker
- Mai Xuân Đạt, SEONGON, VNOKRs

---

## 🚀 Cách sử dụng

### 1. Đọc bằng Obsidian (Khuyến nghị)
Mở thư mục gốc `okr_wiki/` trong [Obsidian](https://obsidian.md/) để tận dụng đầy đủ liên kết `[[Wiki Links]]`, graph view và frontmatter.

### 2. Đọc bằng trình duyệt Markdown bất kỳ
Tất cả tệp đều là Markdown thuần, có thể đọc trực tiếp trên GitHub, VS Code, hoặc bất kỳ MD viewer nào.

### 3. Dùng làm Resource cho LLM Agent
Wiki được thiết kế để agent có thể:
- Đọc `index.md` để định vị trang liên quan.
- Theo dõi `[[links]]` để khai thác sâu.
- Dựa vào YAML frontmatter (`sources`, `tags`) để trích dẫn và kiểm chứng.

---

## 🤖 Tương lai: OKR-Master Agent

Wiki này là **knowledge base duy nhất** cho agent OKR-Master. Agent sẽ:
- Chỉ trả lời dựa trên nội dung wiki.
- Trích dẫn nguồn bằng `[[wiki/...]]` sau mọi claim.
- Thực hiện suy luận đầy đủ (Wiki-ReAct) trước khi trả lời.
- Không bịa đặt thông tin ngoài tài liệu.

---

## 📝 Quy tắc đóng góp / ingest nguồn mới

Nếu bạn muốn bổ sung nguồn mới:
1. Đặt tệp gốc vào `raw/sources/`.
2. Agent sẽ thực hiện quy trình **iNGEST** theo `AGENTS.md`:
   - Phân tích → Tạo trang tóm tắt (`wiki/sources/`)
   - Trích xuất entities & concepts → Tạo/cập nhật trang (`wiki/entities/`, `wiki/concepts/`)
   - Cập nhật `wiki/synthesis/overview.md`
   - Ghi nhật ký vào `log.md`
3. Không bao giờ sửa đổi tệp trong `raw/`.

---

## 📄 License

Nội dung wiki là sự tổng hợp từ các nguồn đã ghi rõ. Các trích dẫn và tóm tắt tuân thủ nguyên tắc fair use. Vui lòng tham khảo tác giả gốc khi sử dụng cho mục đích thương mại.

---

*Built with Obsidian + Markdown. Maintained by agent & human.*
