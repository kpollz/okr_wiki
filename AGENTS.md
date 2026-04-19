# AGENTS.md — Lược đồ Wiki LLM

Tệp cấu hình này định nghĩa cách bạn (agent LLM) vận hành bộ não thứ hai này.  
MọI thao tác trên wiki **PHẢI** tuân thủ các quy tắc dướI đây.

---

## 1. Vai trò & Triết lý

- **Bạn là ngườI bảo trì wiki.** NgườI dùng đọc wiki; bạn viết và cập nhật.
- **Wiki là tàI sản tích lũy.** MỗI nguồn mớI phảI được tích hợp vào cấu trúc hiện có, không chỉ lưu trữ độc lập.
- **Nguồn gốc (`raw/`) là bất biến.** Không bao giờ sửa đổI tệp trong `raw/`.
- **Ưu tiên liên kết chéo.** MọI trang wiki nên liên kết đến các trang liên quan.
- **Ngôn ngữ chính: Tiếng Việt.** Giữ nguyên thuật ngữ tiếng Anh khi cần độ chính xác, sau đó giảI thích trong ngoặc hoặc tạo trang khái niệm rIêng.

---

## 2. Cấu trúc thư mục

```
<root>/
├── AGENTS.md              # Lược đồ này
├── index.md               # Mục lục toàn bộ wiki
├── log.md                 # Nhật ký thao tác (append-only)
├── raw/                   # Nguồn gốc — CHỈ ĐỌC
│   ├── sources/           # TàI liệu, bàI viết, giấy tờ
│   └── assets/            # Hình ảnh, file đính kèm
├── wiki/                  # Bạn sở hữu toàn bộ thư mục này
│   ├── entities/          # Thực thể: ngườI, công ty, sản phẩm, dự án...
│   ├── concepts/          # Khái niệm: lý thuyết, framework, phương pháp...
│   ├── sources/           # Tóm tắt nguồn (1 trang / nguồn)
│   ├── synthesis/         # Tổng hợp, so sánh, phân tích chủ đề
│   └── meta/              # Trang về wiki: hướng dẫn sử dụng, số liệu...
└── queries/               # Câu trả lờI từ truy vấn được lưu lạI
```

---

## 3. Quy ước đặt tên & Định dạng

### 3.1 Tệp
- Tên tệp viết thường, dùng gạch ngang: `objectives-and-key-results.md`, `john-doerr.md`.
- Tiếng Việt có dấu được khuyến khích để dễ đọc trong Obsidian.
- ĐuôI `.md` bắt buộc.

### 3.2 Tiêu đề & Frontmatter
MọI trang trong `wiki/` **PHẢI** có frontmatter YAML ở đầu tệp:

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
- Nếu trang chưa tồn tạI, tạo nó trong quá trình INGEST hoặc đánh dấu `#todo` để tạo sau.

### 3.4 Phong cách viết
- Ưu tiên ngắn gọn, dùng danh sách gạch đầu dòng.
- Không sao chép nguyên văn nguồn; hãy tổng hợp và diễn giảI.
- Khi cập nhật thông tin cũ, không xóa — hãy ghi chú "*Đã cập nhật: ...*" hoặc di chuyển vào mục lịch sử.

---

## 4. Quy trình INGEST (Nhập dữ liệu)

Khi ngườI dùng cung cấp một nguồn mớI (hoặc yêu cầu xử lý nguồn trong `raw/`):

### Bước 1: Tiếp nhận
- Xác định đường dẫn nguồn trong `raw/sources/`.
- Ghi nhận metadata: tiêu đề, tác giả, ngày, URL (nếu có).

### Bước 2: Phân tích
- Đọc toàn bộ nguồn.
- Trích xuất: ý chính, thực thể mớI, khái niệm mớI, dữ liệu quan trọng, mâu thuẫn vớI wiki hiện tạI.

### Bước 3: Tạo / cập nhật trang wiki
1. **Trang tóm tắt nguồn** trong `wiki/sources/`: tóm tắt nguồn, trích dẫn quan trọng.
2. **Các trang thực thể** trong `wiki/entities/`: nếu nguồn đề cập ngườI, công ty, sản phẩm...
3. **Các trang khái niệm** trong `wiki/concepts/`: nếu nguồn giớI thiệu lý thuyết, framework...
4. **Cập nhật trang tổng hợp** trong `wiki/synthesis/`: đIều chỉnh bức tranh lớn.
5. **Ghi chú mâu thuẫn**: nếu dữ liệu mớI mâu thuẫn vớI wiki cũ, ghi rõ trong trang liên quan và đánh dấu `#contradiction`.

### Bước 4: Cập nhật `index.md`
- Thêm liên kết đến trang tóm tắt nguồn mớI.
- Thêm / cập nhật các mục thực thể, khái niệm mớI.

### Bước 5: Ghi `log.md`
Thêm mục theo định dạng chuẩn:
```markdown
## [YYYY-MM-DD] ingest | <Tiêu đề nguồn>
- Nguồn: `raw/sources/<tên tệp>`
- Trang mớI: [[Trang 1]], [[Trang 2]]...
- Trang cập nhật: [[Trang 3]], [[Trang 4]]...
```

---

## 5. Quy trình QUERY (Truy vấn)

Khi ngườI dùng đặt câu hỏI:

### Bước 1: Khám phá
- Đọc `index.md` để xác định trang liên quan.
- Đọc các trang wiki liên quan (không đọc `raw/` trừ khi cần trích dẫn gốc).

### Bước 2: Tổng hợp
- Tổng hợp câu trả lờI từ wiki hiện có.
- Dẫn chứng bằng liên kết đến trang wiki: `theo [[Trang Tóm Tắt]]...`

### Bước 3: Lưu câu trả lờI (nếu có giá trị lâu dàI)
- HỏI ngườI dùng có muốn lưu không (trừ khi họ yêu cầu rõ ràng từ đầu).
- Nếu có, lưu vào `queries/YYYY-MM-DD-cau-hoi-rut-gon.md` vớI frontmatter `tags: [query]`.
- Liên kết câu trả lờI từ `index.md` nếu phù hợp.
- Ghi `log.md`:
  ```markdown
  ## [YYYY-MM-DD] query | <Câu hỏI rút gọn>
  - Trang kết quả: [[Trang Kết Quả]]
  ```

---

## 6. Quy trình LINT (Kiểm tra sức khỏe toàn project)

Thực hiện định kỳ khi được yêu cầu. Phạm vi: **toàn bộ project**, không chỉ `wiki/`.

### A. Kiểm tra root & vùng ngoàI wiki
7. **File rác / orphan ở root**: Tìm file 0 byte, file không liên quan đến dự án (ví dụ: `Welcome.md` mặc định Obsidian), file trùng lặp vớI `wiki/`.
8. **Đồng bộ `raw/sources` ↔ `wiki/sources`**: MỗI file trong `raw/sources/` phảI có đúng 1 trang tóm tắt trong `wiki/sources/`. Ngược lạI, không có trang tóm tắt nào trỏ đến file `raw/` không tồn tạI.
9. **Kiểm tra `queries/`**: Nếu `queries/` không rỗng, đảm bảo mọI file đều được liệt kê trong `index.md`.

### B. Kiểm tra nộI dung wiki
1. **Mâu thuẫn**: Quét các ghi chú `#contradiction`, kiểm tra tính nhất quán giữa các trang.
2. **Trang mồ côi (orphan)**: Tìm trang trong `wiki/` không có liên kết đến từ trang khác.
3. **Khái niệm thIếu trang**: Tìm các `[[Liên Kết Chưa Tồn Tại]]` hoặc khái niệm quan trọng chưa có trang rIêng.
4. **Tổng hợp lỗI thờI**: Kiểm tra các trang `synthesis/` có cần cập nhật từ nguồn mớI không.
5. **Frontmatter & định dạng**: Kiểm tra mọI file trong `wiki/` có frontmatter YAML hợp lệ.

### C. Báo cáo & Ghi log
10. **Báo cáo**: Tạo / cập nhật trang `wiki/meta/lint-report.md` ghi lạI phát hiện và đề xuất.
11. **Ghi `log.md`**:
    ```markdown
    ## [YYYY-MM-DD] lint | Kiểm tra sức khỏe toàn project
    - Báo cáo: [[wiki/meta/lint-report.md]]
    ```

---

## 7. Quy tắc đặc biệt

- **Không bao giờ xóa thông tin**, trừ khi ngườI dùng yêu cầu rõ ràng. Khi cập nhật, hãy thêm mớI và đánh dấu lỗI thờI.
- **MỗI nguồn chỉ tóm tắt một lần.** Tóm tắt trong `wiki/sources/`, không lặp lại trong các trang khái niệm.
- **Ưu tiên ngắn gọn.** Wiki không phảI bản sao của nguồn; nó là sự tổng hợp.
- **Không tự ý sửa đổI `AGENTS.md`.** Chỉ cập nhật khi ngườI dùng yêu cầu thay đổI quy tắc.
