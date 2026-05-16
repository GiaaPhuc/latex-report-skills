# Document Structure — Cấu trúc tài liệu LaTeX chuẩn học thuật

## Cấu trúc bắt buộc theo thứ tự

```
1. Title page          — Tiêu đề, tác giả, cơ quan, ngày
2. Abstract            — 150–250 từ (tiếng Anh thường gọi là Summary)
3. Table of Contents   — \tableofcontents (tự động sinh từ \section)
4. List of Figures     — \listoffigures (nếu có hình ảnh)
5. List of Tables      — \listoftables (nếu có bảng)
6. Abbreviations       — Danh mục viết tắt (nếu > 5 từ viết tắt)
7. Main body           — Introduction → ... → Conclusion
8. Bibliography        — \printbibliography (BẮT BUỘC ở cuối phần nội dung)
9. Appendices          — Phụ lục, nếu có
```

---

## Chọn documentclass phù hợp

| Loại báo cáo | documentclass | Có `\chapter`? | Ghi chú |
|-------------|--------------|:--------------:|---------|
| Báo cáo học thuật, đồ án | `report` | ✓ | Phổ biến nhất ở VN |
| Bài báo ngắn, tiểu luận | `article` | ✗ | Không có chapter |
| IEEE conference paper | `IEEEtran` | ✗ | Download class từ IEEE |
| Luận văn thạc sĩ / tiến sĩ | `report` hoặc template trường | ✓ | Theo quy định từng trường |
| Sách | `book` | ✓ | Có front/main/back matter |

---

## Heading hierarchy

### Với `report` (có chapters)

```
\chapter{Chương 1: Tổng quan}
  \section{1.1 Đặt vấn đề}
    \subsection{1.1.1 Bối cảnh nghiên cứu}
      \subsubsection{Chi tiết nhỏ hơn}
        \paragraph{Đoạn văn có nhãn}
          \subparagraph{Hiếm dùng}
```

### Với `article` (không có chapters)

```
\section{1. Giới thiệu}
  \subsection{1.1 Đặt vấn đề}
    \subsubsection{1.1.1 Bối cảnh}
```

---

## Skeleton tài liệu tiếng Việt (report)

```latex
\documentclass[12pt, a4paper]{report}

%% ===== PACKAGES =====
\usepackage{fontspec}
\usepackage{polyglossia}
\setmainlanguage{vietnamese}
\setmainfont{Times New Roman}

\usepackage{geometry}
\geometry{a4paper, top=3cm, bottom=2.5cm, left=3.5cm, right=2cm}

\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{hyperref}
\usepackage[backend=biber, style=numeric, sorting=none]{biblatex}
\addbibresource{references.bib}

%% ===== BEGIN DOCUMENT =====
\begin{document}

%% 1. TITLE PAGE
\begin{titlepage}
  \centering
  {\large TRƯỜNG ĐẠI HỌC ABC\\[0.2cm]}
  {\large KHOA CÔNG NGHỆ THÔNG TIN\\[1cm]}
  {\Huge\bfseries Tiêu đề Báo Cáo\\[0.5cm]}
  {\large Môn học: Tên Môn Học\\[2cm]}
  \begin{tabular}{ll}
    Sinh viên thực hiện: & Nguyễn Văn An \\
    MSSV:               & 12345678 \\
    Giảng viên hướng dẫn: & TS. Trần Thị Bình \\
  \end{tabular}\\[2cm]
  {\large Hà Nội, tháng 5 năm 2026}
\end{titlepage}

%% 2. ABSTRACT
\begin{abstract}
  Tóm tắt ngắn gọn (150--250 từ) về nội dung, phương pháp và kết quả.
\end{abstract}

%% 3. TABLE OF CONTENTS
\tableofcontents
\newpage

%% 4–5. LIST OF FIGURES / TABLES (nếu có)
\listoffigures
\listoftables
\newpage

%% 7. MAIN BODY
\chapter{Tổng quan}
\section{Đặt vấn đề}
Nội dung chương 1...

\chapter{Cơ sở lý thuyết}
\section{Khái niệm cơ bản}
Theo \textcite{Nguyen2024}, ...

\chapter{Phương pháp nghiên cứu}

\chapter{Kết quả và thảo luận}

\chapter{Kết luận}

%% 8. BIBLIOGRAPHY
\printbibliography[title={Tài liệu tham khảo}]

%% 9. APPENDICES (nếu có)
\appendix
\chapter{Phụ lục A: Code nguồn}

\end{document}
```

---

## Skeleton tài liệu tiếng Anh (article)

```latex
\documentclass[12pt, a4paper]{article}

\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage{geometry}
\geometry{a4paper, margin=2.5cm}

\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{hyperref}
\usepackage[backend=biber, style=ieee]{biblatex}
\addbibresource{references.bib}

\title{Report Title}
\author{Author Name \\ \small Institution Name \\ \small \texttt{email@example.com}}
\date{\today}

\begin{document}

\maketitle

\begin{abstract}
  A concise summary of the report (150--250 words).
\end{abstract}

\tableofcontents
\newpage

\section{Introduction}
Background and motivation \cite{Smith2023}.

\section{Related Work}

\section{Methodology}

\section{Results}

\section{Conclusion}

\printbibliography

\appendix
\section{Additional Data}

\end{document}
```

---

## Main body — Cấu trúc nội dung chuẩn

### Chapter/Section chuẩn của báo cáo học thuật

| Chương/Section | Nội dung | Tỷ lệ (%) |
|----------------|---------|-----------|
| Giới thiệu / Introduction | Bối cảnh, vấn đề, mục tiêu, phạm vi | ~10% |
| Cơ sở lý thuyết / Related Work | Định nghĩa, lý thuyết nền, công trình liên quan | ~20% |
| Phương pháp / Methodology | Cách tiếp cận, thiết kế, công cụ | ~25% |
| Kết quả / Results | Số liệu, bảng, hình ảnh, phân tích | ~30% |
| Thảo luận / Discussion | Giải thích, hạn chế, so sánh | ~10% |
| Kết luận / Conclusion | Tóm tắt đóng góp, hướng phát triển | ~5% |

### Introduction chuẩn (mô hình phễu)

```
1. Context (rộng)  → Bối cảnh chung của lĩnh vực
2. Problem         → Vấn đề cụ thể chưa giải quyết
3. Gap             → Lý do nghiên cứu hiện tại chưa đủ
4. Contribution    → Đóng góp của báo cáo này
5. Outline         → Cấu trúc của tài liệu
```

---

## Figures và Tables

### Figure chuẩn

```latex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.8\textwidth]{figures/architecture.png}
  \caption{Kiến trúc hệ thống đề xuất}
  \label{fig:architecture}
\end{figure}

% Tham chiếu trong văn bản:
Hình \ref{fig:architecture} minh họa kiến trúc tổng thể...
```

### Table chuẩn (booktabs style)

```latex
\begin{table}[htbp]
  \centering
  \caption{So sánh hiệu suất các phương pháp}
  \label{tab:comparison}
  \begin{tabular}{lccc}
    \toprule
    Phương pháp & Độ chính xác & F1-score & Thời gian (ms) \\
    \midrule
    Baseline    & 85.2\%       & 0.841    & 120 \\
    Proposed    & \textbf{92.7\%} & \textbf{0.923} & 145 \\
    \bottomrule
  \end{tabular}
\end{table}

% Tham chiếu:
Bảng \ref{tab:comparison} cho thấy phương pháp đề xuất...
```

> **Quy tắc booktabs:** Chỉ dùng `\toprule`, `\midrule`, `\bottomrule` — KHÔNG dùng `\hline` và không dùng đường kẻ dọc `|`.

---

## Placement specifiers cho float

| Specifier | Ý nghĩa |
|-----------|---------|
| `h` | here — ngay tại vị trí trong code |
| `t` | top — đầu trang |
| `b` | bottom — cuối trang |
| `p` | page — trang riêng dành cho float |
| `H` | HERE (cần `float` package) — bắt buộc tại đây |

> Khuyến nghị: dùng `[htbp]` cho hầu hết trường hợp; `[H]` khi cần đặt cố định.

---

## Trang bìa tiếng Việt chuẩn (nhiều trường)

```latex
\begin{titlepage}
  \centering
  
  % Logo trường (nếu có)
  % \includegraphics[width=3cm]{logo.png}\\[0.5cm]
  
  {\LARGE\bfseries TRƯỜNG ĐẠI HỌC ABC\\}
  {\large KHOA CÔNG NGHỆ THÔNG TIN\\[0.5cm]}
  \rule{\textwidth}{0.5pt}\\[1cm]
  
  {\Huge\bfseries BÁO CÁO\\[0.3cm]}
  {\Large\bfseries Tiêu đề Đề tài Nghiên cứu\\}
  {\large Chương trình: Kỹ thuật Phần mềm\\[1.5cm]}
  
  \begin{minipage}{0.45\textwidth}
    \begin{flushleft}
      \textbf{Sinh viên thực hiện:}\\
      Nguyễn Văn An \quad 12345678\\
      Trần Thị Bình \quad 12345679
    \end{flushleft}
  \end{minipage}
  \begin{minipage}{0.45\textwidth}
    \begin{flushright}
      \textbf{Giảng viên hướng dẫn:}\\
      TS. Lê Văn Cường
    \end{flushright}
  \end{minipage}
  
  \vfill
  {\large Hà Nội, tháng 5 năm 2026}
\end{titlepage}
```
