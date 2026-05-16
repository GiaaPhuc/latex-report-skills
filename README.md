# latex-report-skills

Skills repo để AI agent tạo báo cáo LaTeX chuẩn học thuật.

## Cách add vào Cursor

1. Mở **Cursor Settings** → **Features** → **Skills**
2. Add URL: `https://github.com/your-username/latex-report-skills`

## Cách add vào Claude Desktop

1. Mở **Claude Desktop** → **Settings** → **Skills**
2. Add URL repo này

## Cách dùng sau khi add

Chỉ cần yêu cầu tự nhiên bằng tiếng Việt hoặc tiếng Anh:

- "Viết báo cáo LaTeX về deep learning, citation style IEEE"
- "Tạo file .tex cho luận văn tiếng Việt, lề chuẩn A4"
- "Format tài liệu tham khảo này sang BibTeX"
- "Tạo template IEEE conference paper"
- "Compile file .tex ra PDF, hướng dẫn cách dùng XeLaTeX"

## Skills có trong repo

| Skill | Mô tả |
|-------|-------|
| `latex-report/SKILL.md` | Entry point — workflow tổng quan, khi nào dùng |
| `latex-report/document-structure.md` | Cấu trúc tài liệu bắt buộc, skeletons theo loại |
| `latex-report/citation-rules.md` | Quy tắc trích dẫn, BibTeX entry types đầy đủ |
| `latex-report/latex-syntax-guide.md` | Packages, syntax, compile commands |
| `latex-report/examples/academic-report-vi.tex` | Template báo cáo tiếng Việt (XeLaTeX) |
| `latex-report/examples/ieee-paper.tex` | Template IEEE conference paper |
| `latex-report/examples/thesis-chapter.tex` | Template chapter luận văn thạc sĩ |
| `latex-report/examples/sample.bib` | BibTeX mẫu đầy đủ các loại entry |

## Yêu cầu hệ thống (để compile)

- **TeX distribution:** [TeX Live](https://tug.org/texlive/) (khuyến nghị) hoặc [MiKTeX](https://miktex.org/)
- **Tiếng Việt:** XeLaTeX + font Times New Roman hoặc DejaVu Serif
- **Tiếng Anh:** pdflatex hoặc xelatex
- **Bibliography:** Biber (đi kèm TeX Live)
