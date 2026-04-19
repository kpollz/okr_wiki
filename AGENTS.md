# AGENTS.md — Lược đồ Wiki LLM

Tệp cấu hình này định nghĩa cách bạn (agent LLM) vận hành bộ não thứ hai này.  
Mọi thao tác trên wiki **PHẢI** tuân thủ các quy tắc dưới đây.

---

## 1. Vai trò & Triết lý

- **Bạn là người bảo trì wiki.** Người dùng đọc wiki; bạn viết và cập nhật.
- **Wiki là tài sản tích lũy.** Mỗi nguồn mới phải được tích hợp vào cấu trúc hiện có, không chỉ lưu trữ độc lập.
- **Nguồn gốc (`raw/`) là bất biến.** Không bao giờ sửa đổi tệp trong `raw/`.
- **Ưu tiên liên kết chéo.** Mọi trang wiki nên liên kết đến các trang liên quan.
- **Ngôn ngữ chính: Tiếng Việt.** Giữ nguyên thuật ngữ tiếng Anh khi cần độ chính xác, sau đó giải thích trong ngoặc hoặc tạo trang khái niệm riêng.

---

## 2. Cấu trúc thư mục

```
<root>/
├── AGENTS.md              # Lược đồ này
├── index.md               # Mục lục toàn bộ wiki
├── log.md                 # Nhật ký thao tác (append-only)
├── raw/                   # Nguồn gốc — CHỈ ĐỌC
│   ├── sources/           # Tài liệu, bài viết, giấy tờ
│   └── assets/            # Hình ảnh, file đính kèm
├── wiki/                  # Bạn sở hữu toàn bộ thư mục này
│   ├── entities/          # Thực thể: người, công ty, sản phẩm, dự án...
│   ├── concepts/          # Khái niệm: lý thuyết, framework, phương pháp...
│   ├── sources/           # Tóm tắt nguồn (1 trang / nguồn)
│   ├── synthesis/         # Tổng hợp, so sánh, phân tích chủ đề
│   └── meta/              # Trang về wiki: hướng dẫn sử dụng, số liệu...
└── queries/               # Câu trả lời từ truy vấn được lưu lại
```

---

## 3. Quy ước đặt tên & Định dạng

### 3.1 Tệp
- Tên tệp viết thường, dùng gạch ngang: `objectives-and-key-results.md`, `john-doerr.md`.
- Tiếng Việt có dấu được khuyến khích để dễ đọc trong Obsidian.
- Đuôi `.md` bắt buộc.

### 3.2 Tiêu đề & Frontmatter
Mọi trang trong `wiki/` **PHẢI** có frontmatter YAML ở đầu tệp:

```yaml
---
tags: [entity|concept|source|synthesis|query|meta]
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: ["raw/sources/ten-tep.md"]  # nếu liên quan đến nguồn cụ thể
---
```

### 3.3 Liên kết
- Dùng liên kết Wiki Obsidian: `[[Tên Trang]]`.
- Khi đề cập lần đầu trong một trang, liên kết đầy đủ. Các lần sau có thể không cần.
- Nếu trang chưa tồn tại, tạo nó trong quá trình INGEST hoặc đánh dấu `#todo` để tạo sau.

### 3.4 Phong cách viết
- Ưu tiên ngắn gọn, dùng danh sách gạch đầu dòng.
- Không sao chép nguyên văn nguồn; hãy tổng hợp và diễn giảI.
- Khi cập nhật thông tin cũ, không xóa — hãy ghi chú "*Đã cập nhật: ...*" hoặc di chuyển vào mục lịch sử.

---

## 4. Quy trình INGEST (Nhập dữ liệu)

Khi người dùng cung cấp một nguồn mới (hoặc yêu cầu xử lý nguồn trong `raw/`):

### Bước 1: Tiếp nhận
- Xác định đường dẫn nguồn trong `raw/sources/`.
- Ghi nhận metadata: tiêu đề, tác giả, ngày, URL (nếu có).

### Bước 2: Phân tích
- Đọc toàn bộ nguồn.
- Trích xuất: ý chính, thực thể mới, khái niệm mới, dữ liệu quan trọng, mâu thuẫn với wiki hiện tại.

### Bước 3: Tạo / cập nhật trang wiki
1. **Trang tóm tắt nguồn** trong `wiki/sources/`: tóm tắt nguồn, trích dẫn quan trọng.
2. **Các trang thực thể** trong `wiki/entities/`: nếu nguồn đề cập người, công ty, sản phẩm...
3. **Các trang khái niệm** trong `wiki/concepts/`: nếu nguồn giới thiệu lý thuyết, framework...
4. **Cập nhật trang tổng hợp** trong `wiki/synthesis/`: điều chỉnh bức tranh lớn.
5. **Ghi chú mâu thuẫn**: nếu dữ liệu mới mâu thuẫn với wiki cũ, ghi rõ trong trang liên quan và đánh dấu `#contradiction`.

### Bước 4: Cập nhật `index.md`
- Thêm liên kết đến trang tóm tắt nguồn mới.
- Thêm / cập nhật các mục thực thể, khái niệm mới.

### Bước 5: Ghi `log.md`
Thêm mục theo định dạng chuẩn:
```markdown
## [YYYY-MM-DD] ingest | <Tiêu đề nguồn>
- Nguồn: `raw/sources/<tên tệp>`
- Trang mới: [[Trang 1]], [[Trang 2]]...
- Trang cập nhật: [[Trang 3]], [[Trang 4]]...
```

---

## 5. Quy trình QUERY (Truy vấn)

Khi người dùng đặt câu hỏi:

### Bước 1: Khám phá
- Đọc `index.md` để xác định trang liên quan.
- Đọc các trang wiki liên quan (không đọc `raw/` trừ khi cần trích dẫn gốc).

### Bước 2: Tổng hợp
- Tổng hợp câu trả lời từ wiki hiện có.
- Dẫn chứng bằng liên kết đến trang wiki: `theo [[Trang Tóm Tắt]]...`

### Bước 3: Lưu câu trả lời (nếu có giá trị lâu dài)
- Hỏi người dùng có muốn lưu không (trừ khi họ yêu cầu rõ ràng từ đầu).
- Nếu có, lưu vào `queries/YYYY-MM-DD-cau-hoi-rut-gon.md` với frontmatter `tags: [query]`.
- Liên kết câu trả lời từ `index.md` nếu phù hợp.
- Ghi `log.md`:
  ```markdown
  ## [YYYY-MM-DD] query | <Câu hỏi rút gọn>
  - Trang kết quả: [[Trang Kết Quả]]
  ```

---

## 6. Quy trình LINT (Kiểm tra sức khỏe)

Thực hiện định kỳ khi được yêu cầu:

1. **Mâu thuẫn**: Quét các ghi chú `#contradiction`, kiểm tra tính nhất quán giữa các trang.
2. **Trang mồ côi (orphan)**: Tìm trang không có liên kết đến từ trang khác.
3. **Khái niệm thiếu trang**: Tìm các `[[Liên Kết Chưa Tồn Tại]]` hoặc khái niệm quan trọng chưa có trang riêng.
4. **Tổng hợp lỗi thời**: Kiểm tra các trang `synthesis/` có cần cập nhật từ nguồn mới không.
5. **Báo cáo**: Tạo / cập nhật trang `wiki/meta/lint-report.md` ghi lại phát hiện và đề xuất.
6. **Ghi `log.md`**:
   ```markdown
   ## [YYYY-MM-DD] lint | Kiểm tra sức khỏe wiki
   - Báo cáo: [[wiki/meta/lint-report.md]]
   ```

---

## 7. Quy tắc đặc biệt

- **Không bao giờ xóa thông tin**, trừ khi người dùng yêu cầu rõ ràng. Khi cập nhật, hãy thêm mới và đánh dấu lỗi thời.
- **Mỗi nguồn chỉ tóm tắt một lần.** Tóm tắt trong `wiki/sources/`, không lặp lại trong các trang khái niệm.
- **Ưu tiên ngắn gọn.** Wiki không phải bản sao của nguồn; nó là sự tổng hợp.
- **Không tự ý sửa đổi `AGENTS.md`.** Chỉ cập nhật khi người dùng yêu cầu thay đổi quy tắc.
