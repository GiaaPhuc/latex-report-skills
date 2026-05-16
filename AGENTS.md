# AGENTS.md

Hướng dẫn cho AI coding agents (Cursor, Claude Code, Copilot, OpenCode...) khi làm việc với repo này.

## Tổng quan Repository

Một bộ skills cho AI agent về viết báo cáo LaTeX học thuật. Skills là các file hướng dẫn đóng gói giúp agent tạo báo cáo LaTeX chuẩn — bao gồm cấu trúc tài liệu, trích dẫn BibTeX, chọn packages phù hợp, và compile.

## Tạo Skill Mới

### Cấu trúc thư mục

```
{skill-name}/
  SKILL.md              # Bắt buộc: định nghĩa skill với YAML frontmatter
  references/           # Tùy chọn: các file reference chi tiết
    {category}-{rule}.md
  examples/             # Tùy chọn: các file ví dụ (.tex, .bib)
    {example}.tex
    {example}.bib
```

### Quy tắc đặt tên

- **Thư mục skill**: `kebab-case` (ví dụ: `latex-report`, `beamer-slides`)
- **SKILL.md**: Luôn viết hoa, luôn đúng tên file này
- **Reference files**: `{category}-{rule-name}.md` dạng kebab-case
- **Examples**: tên mô tả loại tài liệu (ví dụ: `academic-report-vi.tex`, `ieee-paper.tex`)

### Format SKILL.md

```markdown
---
name: {skill-name}
description: {Một câu mô tả khi nào dùng skill này. Bao gồm trigger phrases.}
license: MIT
metadata:
  author: {github-username}
  version: "1.0.0"
---

# {Skill Title}

{Mô tả ngắn skill làm gì.}

## When to Apply

{Danh sách bullet các tình huống nên dùng skill này}

## Rule Categories by Priority

| Priority | Category | Impact | Prefix |
|----------|----------|--------|--------|
| 1 | {Category} | CRITICAL | `{prefix}-` |
| 2 | {Category} | HIGH | `{prefix}-` |

## Quick Reference

### 1. {Category} (CRITICAL)

- `{prefix}-{rule}` — Mô tả ngắn
...

## Reference Files

```
references/{prefix}-{rule}.md   - Mô tả
```
```

### Format Reference File

```markdown
# {category}-{rule-name}

{Một câu tóm tắt quy tắc.}

## Priority

{CRITICAL | HIGH | MEDIUM | LOW}

## Tại sao quan trọng

{2-3 câu giải thích tác động.}

## Sai

```latex
{Ví dụ code sai}
```

{Giải thích ngắn tại sao sai}

## Đúng

```latex
{Ví dụ code đúng}
```

{Giải thích ngắn tại sao đúng hơn}

## Tham khảo

- [LaTeX Documentation](https://www.latex-project.org/help/documentation/)
```

## Best Practices để tối ưu Context

Skills được load theo yêu cầu — chỉ tên và description được load lúc khởi động. `SKILL.md` đầy đủ chỉ load khi agent quyết định skill phù hợp.

- **Giữ SKILL.md dưới 500 dòng** — đưa chi tiết vào reference files
- **Viết description cụ thể** — giúp agent biết chính xác khi nào kích hoạt skill
- **Progressive disclosure** — reference files chỉ được đọc khi cần
- **Bao gồm trigger phrases** — ví dụ "báo cáo LaTeX", "cite IEEE", "BibTeX"

## Priority Levels

- **CRITICAL**: Gây lỗi compile, lỗi font, hoặc vi phạm chuẩn học thuật nghiêm trọng
- **HIGH**: Ảnh hưởng đáng kể đến chất lượng output hoặc trải nghiệm người dùng
- **MEDIUM**: Cải thiện chất lượng code LaTeX nhưng không thiết yếu
- **LOW**: Tối ưu tùy chọn hoặc preferences

## Cài đặt để Test Locally

```bash
# Cài tất cả skills
npx skills add {github-username}/latex-report-skills

# Cài skill cụ thể
npx skills add {github-username}/latex-report-skills --skill latex-report

# Xem danh sách skills có sẵn
npx skills add {github-username}/latex-report-skills --list

# Xem danh sách skills đã cài
npx skills list
```

## Cài thủ công

**Cursor** — copy vào `.cursor/skills/`:
```powershell
Copy-Item -Recurse latex-report "$env:USERPROFILE\.cursor\skills\"
```

**Claude Code** — copy vào `~/.claude/skills/`:
```bash
cp -r latex-report ~/.claude/skills/
```

**OpenCode** — copy vào `~/.config/opencode/skill/`:
```bash
cp -r latex-report ~/.config/opencode/skill/
```
