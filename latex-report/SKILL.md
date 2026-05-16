---
name: latex-report
description: LaTeX report writer for academic reports, theses, and conference papers. Use when creating .tex files, formatting bibliographies in BibTeX, compiling LaTeX documents, writing reports in Vietnamese or English, or following IEEE/APA/Harvard/Chicago citation styles. Triggers on "báo cáo LaTeX", "luận văn", "tạo file .tex", "cite IEEE", "BibTeX", "conference paper", "academic report", "thesis".
license: MIT
metadata:
  author: latex-report-skills
  version: "1.0.0"
---

# LaTeX Report Writer

Skill hướng dẫn tạo báo cáo học thuật/kỹ thuật chuẩn LaTeX, bao gồm cấu trúc tài liệu, trích dẫn, bibliography và compile.

## When to Apply

- Người dùng yêu cầu viết báo cáo, luận văn, bài báo khoa học
- Người dùng muốn tạo file `.tex` hoặc `.pdf`
- Người dùng cần format tài liệu tham khảo (BibTeX)
- Người dùng hỏi về trích dẫn APA / IEEE / Harvard / Chicago
- Người dùng cần template LaTeX cho báo cáo học phần, đồ án, luận văn

## Rule Categories by Priority

| Priority | Category | Impact | Prefix |
|----------|----------|--------|--------|
| 1 | Document Type & Class | CRITICAL | `doctype-` |
| 2 | Encoding & Language | CRITICAL | `encoding-` |
| 3 | Citation & Bibliography | HIGH | `citation-` |
| 4 | Document Structure | HIGH | `structure-` |
| 5 | LaTeX Syntax & Packages | MEDIUM | `syntax-` |
| 6 | Compile & Build | MEDIUM | `compile-` |

## Quick Reference

### 1. Document Type (CRITICAL)

| Loại báo cáo | documentclass | Ghi chú |
|-------------|--------------|---------|
| Báo cáo học thuật, đồ án | `report` | Có `\chapter` |
| Bài báo ngắn, tiểu luận | `article` | Không có `\chapter` |
| IEEE conference paper | `IEEEtran` | Download từ IEEE |
| Luận văn | `report` hoặc template trường | Theo quy định từng trường |

### 2. Encoding & Language (CRITICAL)

- **Tiếng Việt BẮT BUỘC dùng XeLaTeX** — không dùng `pdflatex` vì sẽ lỗi font
- XeLaTeX cần `fontspec` + `polyglossia` (hoặc `babel` với option `vietnamese`)
- Lưu file `.tex` với encoding **UTF-8**

### 3. Citation Styles (HIGH)

| Style | In-text | Dùng trong | biblatex style |
|-------|---------|-----------|----------------|
| IEEE  | `[1]` | Kỹ thuật, CS, điện tử | `ieee` |
| APA 7 | `(Nguyen, 2023)` | Tâm lý, giáo dục, KHXH | `apa` |
| Harvard | `Nguyen (2023)` | Kinh tế, quản trị | `authoryear` |
| Chicago | footnote hoặc `(Nguyen 2023)` | Lịch sử, nhân văn | `chicago-authordate` |

### 4. Document Structure (HIGH)

Cấu trúc bắt buộc theo thứ tự:

```
1. Title page
2. Abstract (150–250 từ)
3. Table of Contents  — \tableofcontents
4. List of Figures    — nếu có hình ảnh
5. List of Tables     — nếu có bảng
6. Abbreviations      — danh mục viết tắt (nếu nhiều)
7. Main body          — Introduction → ... → Conclusion
8. Bibliography       — \printbibliography (BẮT BUỘC ở cuối)
9. Appendices         — phụ lục, nếu có
```

### 5. LaTeX Special Characters (MEDIUM)

Escape khi viết nội dung người dùng:

```
& → \&    % → \%    $ → \$    # → \#
_ → \_    { → \{    } → \}
~ → \textasciitilde{}
^ → \textasciicircum{}
\ → \textbackslash{}
```

### 6. Compile Commands (MEDIUM)

```bash
# Tiếng Việt — PHẢI dùng XeLaTeX
xelatex main.tex && biber main && xelatex main.tex && xelatex main.tex

# Tiếng Anh — có thể dùng pdflatex
pdflatex main.tex && bibtex main && pdflatex main.tex && pdflatex main.tex

# Tự động multi-pass với latexmk
latexmk -xelatex main.tex   # tiếng Việt
latexmk -pdf main.tex       # tiếng Anh
```

## Workflow khi nhận yêu cầu

### Bước 1 — Hỏi người dùng (nếu chưa rõ)

| Câu hỏi | Các lựa chọn |
|---------|-------------|
| Loại báo cáo | `academic` \| `thesis` \| `technical` \| `conference paper` |
| Ngôn ngữ | `tiếng Việt` \| `tiếng Anh` |
| Citation style | `IEEE` \| `APA 7` \| `Harvard` \| `Chicago` |
| Compile ra PDF? | `có` \| `không` |

### Bước 2 — Đọc references theo nhu cầu

- **Cấu trúc tài liệu** → [`references/document-structure.md`](./references/document-structure.md)
- **Trích dẫn & BibTeX** → [`references/citation-rules.md`](./references/citation-rules.md)
- **Syntax LaTeX & packages** → [`references/latex-syntax-guide.md`](./references/latex-syntax-guide.md)
- **Ví dụ thực tế** → [`examples/`](./examples/)

### Bước 3 — Tạo file

| File | Mô tả |
|------|-------|
| `report.tex` | Nội dung chính |
| `references.bib` | Tài liệu tham khảo BibTeX |
| `compile.sh` | Script compile (nếu user cần) |

## Lưu ý quan trọng

- **Mọi claim phải có citation** — số liệu, định nghĩa, phát biểu của người khác
- **Không bịa tài liệu tham khảo** — dùng `\todo{Cần tìm nguồn}` nếu chưa có
- Không cite Wikipedia trong báo cáo học thuật — tìm nguồn gốc
- DOI ưu tiên hơn URL cho bài báo học thuật

## Reference Files

```
references/document-structure.md   - Cấu trúc tài liệu bắt buộc, skeletons
references/citation-rules.md       - Quy tắc trích dẫn, BibTeX entry types đầy đủ
references/latex-syntax-guide.md   - Packages, syntax, compile commands

examples/academic-report-vi.tex    - Template báo cáo tiếng Việt (XeLaTeX)
examples/ieee-paper.tex            - Template IEEE conference paper
examples/thesis-chapter.tex        - Template chapter luận văn thạc sĩ
examples/sample.bib                - BibTeX mẫu đầy đủ các loại entry
```
