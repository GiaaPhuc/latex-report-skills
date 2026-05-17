# latex-report-skills

Bộ skills cho AI agent tạo báo cáo LaTeX chuẩn học thuật — báo cáo tiếng Việt, luận văn, IEEE conference paper.

Skills theo [Agent Skills](https://agentskills.io/) format và tương thích với `npx skills add`.

## Available Skills

### latex-report

Tạo báo cáo học thuật/kỹ thuật chuẩn LaTeX.

**Dùng khi:**

- Tạo báo cáo học phần, đồ án, luận văn
- Viết bài báo khoa học (IEEE, APA, Harvard citation)
- Format tài liệu tham khảo BibTeX
- Compile file `.tex` ra PDF (XeLaTeX hoặc pdflatex)

**Topics covered:**

- Chọn `documentclass` phù hợp (report, article, IEEEtran)
- Encoding tiếng Việt với XeLaTeX + fontspec + polyglossia
- Citation styles: IEEE, APA 7, Harvard, Chicago
- Cấu trúc tài liệu: title page → abstract → ToC → body → bibliography
- Compile: xelatex/pdflatex + biber/bibtex + latexmk
- Escape LaTeX special characters

---

## Installation

Cài tất cả skills:

```bash
npx skills add GiaaPhuc/latex-report-skills
```

Cài skill cụ thể:

```bash
npx skills add GiaaPhuc/latex-report-skills --skill latex-report
```

Xem danh sách skills có sẵn:

```bash
npx skills add GiaaPhuc/latex-report-skills --list
```

Xem danh sách skills đã cài:

```bash
npx skills list
```

## Cài thủ công

**Cursor** — vào Cursor Settings → Features → Skills → thêm URL repo này, hoặc copy local:

```powershell
Copy-Item -Recurse latex-report "$env:USERPROFILE\.cursor\skills\"
```

**Claude Code:**

```bash
cp -r latex-report ~/.claude/skills/
```

**OpenCode:**

```bash
cp -r latex-report ~/.config/opencode/skill/
```

## Usage

Sau khi cài, chỉ cần yêu cầu tự nhiên bằng tiếng Việt hoặc tiếng Anh:

```
Viết báo cáo LaTeX về deep learning, citation style IEEE
```

```
Tạo file .tex cho luận văn tiếng Việt, lề chuẩn A4
```

```
Format tài liệu tham khảo này sang BibTeX
```

```
Tạo template IEEE conference paper
```

```
Compile file .tex ra PDF, hướng dẫn cách dùng XeLaTeX
```

## Skill Structure

```
latex-report-skills/
├── README.md
├── AGENTS.md                           # Hướng dẫn tạo/sửa skills
│
└── latex-report/
    ├── SKILL.md                        # Entry point — YAML frontmatter + workflow
    ├── references/
    │   ├── document-structure.md       # Cấu trúc tài liệu bắt buộc, skeletons
    │   ├── citation-rules.md           # Quy tắc trích dẫn, BibTeX entry types
    │   └── latex-syntax-guide.md       # Packages, syntax, compile commands
    └── examples/
        ├── academic-report-vi.tex      # Template báo cáo tiếng Việt (XeLaTeX)
        ├── ieee-paper.tex              # Template IEEE conference paper
        ├── thesis-chapter.tex          # Template chapter luận văn thạc sĩ
        └── sample.bib                  # BibTeX mẫu đầy đủ các loại entry
```

## Yêu cầu hệ thống (để compile)

- **TeX distribution:** [TeX Live](https://tug.org/texlive/) (khuyến nghị) hoặc [MiKTeX](https://miktex.org/)
- **Tiếng Việt:** XeLaTeX + font Times New Roman hoặc DejaVu Serif
- **Tiếng Anh:** pdflatex hoặc xelatex
- **Bibliography:** Biber (đi kèm TeX Live)

## Contributing

Xem [AGENTS.md](./AGENTS.md) để biết cách tạo và sửa skills.

## License

MIT
