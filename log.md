# Log — Nhật ký Wiki

Định dạng mỗi mục:
```
## [YYYY-MM-DD] <loại> | <mô tả ngắn>
- Chi tiết...
```

Loại thao tác: `ingest`, `query`, `lint`, `create`, `update`, `delete`

---

## [2026-04-19] create | Khởi tạo Wiki LLM
- Tạo cấu trúc thư mục: `raw/`, `wiki/`, `queries/`.
- Viết `AGENTS.md`, `index.md`, `log.md`.
- Thiết lập quy ước frontmatter, liên kết Wiki, và quy trình INGEST / QUERY / LINT.

## [2026-04-19] ingest | OKR Guide — Measure What Matters
- Nguồn: `raw/sources/okr-guide-measure-what-matters.md`
- Trang mới:
  - [[wiki/sources/okr-guide-measure-what-matters.md|Tóm tắt OKR Guide]]
  - [[wiki/entities/andy-grove.md|Andy Grove]]
  - [[wiki/entities/john-doerr.md|John Doerr]]
  - [[wiki/concepts/objectives-and-key-results.md|Objectives and Key Results (OKR)]]
  - [[wiki/concepts/cfrs.md|CFRs — Conversations, Feedback, Recognition]]
- Trang cập nhật:
  - [[wiki/synthesis/overview.md|Tổng quan chủ đề]] (khởi tạo)
  - `index.md`

## [2026-04-19] ingest | OKRs — Hiểu đúng, Làm đúng
- Nguồn: `raw/sources/okr-hieu-dung-lam-dung.md` (4093 dòng, ~280KB)
- Trang mới:
  - [[wiki/sources/okr-hieu-dung-lam-dung.md|Tóm tắt sách Mai Xuân Đạt]]
  - [[wiki/entities/mai-xuan-dat.md|Mai Xuân Đạt]]
  - [[wiki/entities/seongon.md|SEONGON]]
  - [[wiki/entities/vnokrs.md|VNOKRs]]
  - [[wiki/concepts/okrs-3-chieu.md|OKRs 3 chiều — 10 bước]]
  - [[wiki/concepts/moonshot-okrs.md|Moonshot OKRs]]
  - [[wiki/concepts/okrs-scoring.md|OKRs Scoring]]
  - [[wiki/concepts/okrs-vs-kpis.md|OKRs vs KPIs]]
  - [[wiki/concepts/okrs-vs-bsc.md|OKRs vs BSC]]
- Trang cập nhật:
  - [[wiki/concepts/objectives-and-key-results.md|Objectives and Key Results (OKR)]] (bổ sung cách viết, liên kết chéo, 10 lỗi phổ biến)
  - [[wiki/concepts/cfrs.md|CFRs]] (bổ sung check-in, ghi nhận & lương thưởng)
  - [[wiki/entities/andy-grove.md|Andy Grove]] (bổ sung nguồn)
  - [[wiki/entities/john-doerr.md|John Doerr]] (bổ sung công thức & quote)
  - [[wiki/synthesis/overview.md|Tổng quan chủ đề]] (cập nhật trụ cột & nguồn)
  - `index.md`

## [2026-04-19] lint | Kiểm tra sức khỏe wiki
- Phạm vi: Toàn bộ `wiki/`
- Báo cáo: [[wiki/meta/lint-report.md]]
- Kết quả:
  - Không phát hIện mâu thuẫn (#contradiction).
  - Không phát hIện liên kết hỏng.
  - Không phát hIện trang mồ côI (trừ file draft tạm).
  - Tất cả trang chính thức đều có frontmatter.
  - `overview.md` đã được cập nhật đầy đủ.

## [2026-04-19] lint | Phát hiện & xóa file rác
- Phát hiện 2 file rỗng ở root: `Andy Grove.md` và `Felipe Castro.md` (0 byte).
- Nguyên nhân: Có thể do lỗI encoding trong quá trình ingest.
- Hành động: Đã xóa.
