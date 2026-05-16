# LaTeX Report Writer

## Mô tả

Skill này hướng dẫn cách tạo báo cáo học thuật/kỹ thuật chuẩn LaTeX,
bao gồm cấu trúc tài liệu, trích dẫn, bibliography và compile.

## Khi nào dùng skill này

- Người dùng yêu cầu viết báo cáo, luận văn, bài báo khoa học
- Người dùng muốn tạo file `.tex` hoặc `.pdf`
- Người dùng cần format tài liệu tham khảo (BibTeX)
- Người dùng hỏi về trích dẫn APA / IEEE / Harvard
- Người dùng cần template LaTeX cho báo cáo học phần, đồ án, luận văn

## Workflow khi nhận yêu cầu

### Bước 1 — Hỏi người dùng (nếu chưa rõ)

| Câu hỏi | Các lựa chọn |
|---------|-------------|
| Loại báo cáo | `academic` \| `thesis` \| `technical` \| `conference paper` |
| Ngôn ngữ | `tiếng Việt` \| `tiếng Anh` |
| Citation style | `IEEE` \| `APA 7` \| `Harvard` \| `Chicago` |
| Compile ra PDF? | `có` \| `không` |

### Bước 2 — Đọc thêm theo loại báo cáo

- **Cấu trúc tài liệu** → xem [`document-structure.md`](./document-structure.md)
- **Trích dẫn & BibTeX** → xem [`citation-rules.md`](./citation-rules.md)
- **Syntax LaTeX & packages** → xem [`latex-syntax-guide.md`](./latex-syntax-guide.md)
- **Ví dụ thực tế** → xem thư mục [`examples/`](./examples/)

### Bước 3 — Tạo file

| File | Mô tả |
|------|-------|
| `report.tex` | Nội dung chính |
| `references.bib` | Tài liệu tham khảo BibTeX |
| `compile.sh` | Script compile (nếu user cần) |

### Bước 4 — Compile (nếu user yêu cầu và có LaTeX installed)

```bash
# Tiếng Việt — PHẢI dùng XeLaTeX
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex

# Tiếng Anh — có thể dùng pdflatex
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex

# Tự động multi-pass với latexmk
latexmk -xelatex main.tex   # tiếng Việt
latexmk -pdf main.tex        # tiếng Anh
```

## Lưu ý quan trọng

### Encoding & Ngôn ngữ

- **Tiếng Việt BẮT BUỘC dùng XeLaTeX** — không dùng `pdflatex` vì sẽ lỗi font
- XeLaTeX cần `fontspec` + `polyglossia` (hoặc `babel` với option `vietnamese`)
- Lưu file `.tex` với encoding **UTF-8**

### Trích dẫn & Nguồn

- **Mọi claim phải có citation** — số liệu, định nghĩa, phát biểu của người khác
- **Không bịa tài liệu tham khảo** — dùng `\todo{Cần tìm nguồn}` nếu chưa có
- Không cite Wikipedia trong báo cáo học thuật — tìm nguồn gốc

### Escape LaTeX special characters

Khi viết nội dung user, phải escape các ký tự đặc biệt:

```
& → \&       % → \%       $ → \$       # → \#
_ → \_       { → \{       } → \}
~ → \textasciitilde{}
^ → \textasciicircum{}
\ → \textbackslash{}
```

### Chọn documentclass

| Loại báo cáo | documentclass | Ghi chú |
|-------------|--------------|---------|
| Báo cáo học thuật, đồ án | `report` | Có `\chapter` |
| Bài báo ngắn, tiểu luận | `article` | Không có `\chapter` |
| IEEE conference paper | `IEEEtran` | Download từ IEEE |
| Luận văn | `report` hoặc template trường | Theo quy định từng trường |

## Files trong skill này

| File | Nội dung |
|------|---------|
| `SKILL.md` | File này — entry point, workflow tổng quan |
| `document-structure.md` | Cấu trúc tài liệu bắt buộc theo thứ tự |
| `citation-rules.md` | Quy tắc trích dẫn, BibTeX entry types đầy đủ |
| `latex-syntax-guide.md` | Packages, commands, và compile instructions |
| `examples/academic-report-vi.tex` | Template báo cáo tiếng Việt đầy đủ |
| `examples/ieee-paper.tex` | Template IEEE conference paper |
| `examples/thesis-chapter.tex` | Template chapter luận văn |
| `examples/sample.bib` | File BibTeX mẫu đầy đủ các loại entry |
