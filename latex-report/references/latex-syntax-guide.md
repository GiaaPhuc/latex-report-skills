# LaTeX Syntax Guide — Tổng hợp syntax và packages hay dùng

## Packages cơ bản

### Encoding & Ngôn ngữ

```latex
%% ---- XeLaTeX (KHUYẾN NGHỊ cho tiếng Việt) ----
\usepackage{fontspec}
\usepackage{polyglossia}
\setmainlanguage{vietnamese}
\setotherlanguage{english}
\setmainfont{Times New Roman}        % Font serif chuẩn
% Hoặc: \setmainfont{DejaVu Serif}   % Font mã nguồn mở

%% ---- pdfLaTeX (chỉ cho tiếng Anh) ----
\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[english]{babel}
```

### Layout & Lề

```latex
\usepackage{geometry}

% Chuẩn A4 — quy định nhiều trường VN
\geometry{
  a4paper,
  top=3cm, bottom=2.5cm,
  left=3.5cm, right=2cm
}

% Chuẩn A4 — quốc tế (đều 2.5cm)
\geometry{a4paper, margin=2.5cm}

% Chuẩn US Letter
\geometry{letterpaper, margin=1in}
```

### Header & Footer

```latex
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}                           % Xoá default
\fancyhead[L]{\leftmark}            % Tên chapter/section bên trái
\fancyhead[R]{\thepage}             % Số trang bên phải
\fancyfoot[C]{Tên Báo Cáo}          % Footer giữa
\renewcommand{\headrulewidth}{0.4pt}
```

### Hình ảnh & Đồ thị

```latex
\usepackage{graphicx}
\usepackage{float}                   % Cho [H] specifier
\usepackage{subcaption}             % Cho subfigure a, b, c...

% Đặt thư mục chứa ảnh
\graphicspath{{figures/}{images/}}
```

### Bảng

```latex
\usepackage{booktabs}               % \toprule, \midrule, \bottomrule
\usepackage{longtable}              % Bảng nhiều trang
\usepackage{tabularx}               % Bảng có cột tự co giãn (X column)
\usepackage{multirow}               % Gộp nhiều hàng
\usepackage{array}                  % Cột tùy chỉnh
```

### Toán học

```latex
\usepackage{amsmath}                % align, equation, gather...
\usepackage{amssymb}               % Ký hiệu toán học mở rộng
\usepackage{mathtools}              % Mở rộng amsmath
```

### Code listing

```latex
\usepackage{listings}
\usepackage{xcolor}

\lstset{
  basicstyle=\ttfamily\small,
  keywordstyle=\color{blue}\bfseries,
  commentstyle=\color{gray}\itshape,
  stringstyle=\color{orange},
  numbers=left,
  numberstyle=\tiny\color{gray},
  breaklines=true,
  frame=single,
  captionpos=b
}

% Dùng trong document
\begin{lstlisting}[language=Python, caption={Ví dụ code Python}]
def hello(name):
    print(f"Hello, {name}!")
\end{lstlisting}
```

### Hyperlinks & PDF metadata

```latex
\usepackage{hyperref}
\hypersetup{
  colorlinks=true,
  linkcolor=black,                  % Màu link nội bộ (toc, ref...)
  citecolor=blue,                   % Màu citation
  urlcolor=blue,                    % Màu URL
  pdftitle={Tiêu đề Báo Cáo},
  pdfauthor={Tác giả},
  pdfkeywords={keyword1, keyword2}
}
```

### Danh mục viết tắt

```latex
\usepackage[acronym, toc]{glossaries}
\makeglossaries

% Định nghĩa (trong preamble)
\newacronym{ai}{AI}{Artificial Intelligence}
\newacronym{ml}{ML}{Machine Learning}

% Dùng trong văn bản
\gls{ai}    % lần đầu: "Artificial Intelligence (AI)"
\gls{ai}    % lần sau: "AI"
\Gls{ml}    % In hoa chữ đầu

% In danh mục
\printglossary[type=\acronymtype, title={Danh mục viết tắt}]
```

### Todo notes (trong quá trình viết)

```latex
\usepackage[colorinlistoftodos]{todonotes}

\todo{Cần tìm nguồn}
\todo[inline]{Đoạn này cần viết lại}
\missingfigure{Thêm biểu đồ kết quả ở đây}
\listoftodos    % In danh sách tất cả todo
```

---

## Escape special characters

Khi viết nội dung có ký tự đặc biệt, PHẢI escape:

| Ký tự gốc | LaTeX escape | Ghi chú |
|-----------|-------------|---------|
| `&` | `\&` | Dùng trong table |
| `%` | `\%` | Comment trong LaTeX |
| `$` | `\$` | Bắt đầu math mode |
| `#` | `\#` | Tham số macro |
| `_` | `\_` | Subscript trong math |
| `{` | `\{` | Bắt đầu group |
| `}` | `\}` | Kết thúc group |
| `~` | `\textasciitilde{}` | Non-breaking space |
| `^` | `\textasciicircum{}` | Superscript trong math |
| `\` | `\textbackslash{}` | Backslash |

---

## Math mode

### Inline math

```latex
Phương trình \(E = mc^2\) là...
% Hoặc: $E = mc^2$
```

### Display math (có số)

```latex
\begin{equation}
  \label{eq:softmax}
  \sigma(z_i) = \frac{e^{z_i}}{\sum_{j=1}^{K} e^{z_j}}
\end{equation}

% Tham chiếu
Phương trình \eqref{eq:softmax} là hàm softmax.
```

### Aligned equations

```latex
\begin{align}
  f(x) &= ax^2 + bx + c \label{eq:quad} \\
       &= a\left(x + \frac{b}{2a}\right)^2 - \frac{b^2 - 4ac}{4a}
\end{align}
```

### Ký hiệu math hay dùng

```latex
% Phân số
\frac{a}{b}

% Tổng, tích, tích phân
\sum_{i=1}^{n} x_i
\prod_{i=1}^{n} x_i
\int_0^\infty f(x)\,dx

% Giới hạn
\lim_{x \to \infty} f(x)

% Vector, ma trận
\mathbf{x}        % vector in đậm
\boldsymbol{\mu}  % ký tự Greek in đậm
\mathbb{R}        % tập số thực

% Dấu ngoặc tự co giãn
\left( \frac{a}{b} \right)
\left[ x + y \right]
\left\{ z \right\}

% Norm
\|x\| \quad \|x\|_2 \quad \|x\|_\infty
```

---

## Typography tips

### Dấu câu và khoảng cách

```latex
% Dấu gạch ngang
- (hyphen)        → từ ghép: state-of-the-art
-- (en-dash)      → khoảng: pages 10--20, 2020--2024
--- (em-dash)     → ngắt câu --- như thế này

% Dấu nháy đúng
``trích dẫn tiếng Anh''     % "trích dẫn tiếng Anh"
`từ đơn'                    % 'từ đơn'

% Non-breaking space (giữa số và đơn vị, giữa tên và số)
Hình~\ref{fig:arch}
95\,\%           % khoảng mỏng trước %
10\,MB
```

### Font formatting

```latex
\textbf{in đậm}
\textit{in nghiêng}
\underline{gạch dưới}
\texttt{monospace/code}
\textsc{Small Caps}
\emph{nhấn mạnh — tự chọn nghiêng hay đứng}
```

---

## Lists

```latex
% Unordered list
\begin{itemize}
  \item Mục đầu tiên
  \item Mục thứ hai
    \begin{itemize}
      \item Mục con
    \end{itemize}
\end{itemize}

% Ordered list
\begin{enumerate}
  \item Bước 1
  \item Bước 2
\end{enumerate}

% Description list
\begin{description}
  \item[Thuật ngữ] Định nghĩa của thuật ngữ
  \item[AI] Trí tuệ nhân tạo
\end{description}
```

---

## Compile commands

```bash
# ===== TIẾNG VIỆT — XeLaTeX + Biber =====
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex

# ===== TIẾNG ANH — pdflatex + BibTeX =====
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex

# ===== LATEXMK (tự động multi-pass) =====
latexmk -xelatex main.tex       # tiếng Việt
latexmk -pdf main.tex           # tiếng Anh

# Dọn file phụ
latexmk -c                       # giữ PDF
latexmk -C                       # xoá cả PDF

# ===== COMPILE SCRIPT cho tiếng Việt =====
#!/bin/bash
# compile.sh
set -e
xelatex -interaction=nonstopmode main.tex
biber main
xelatex -interaction=nonstopmode main.tex
xelatex -interaction=nonstopmode main.tex
echo "Done: main.pdf"
```

---

## File `.latexmkrc` (cấu hình latexmk)

```perl
# .latexmkrc — đặt ở thư mục project
$pdf_mode = 5;          # 5 = xelatex
$pdflatex = 'xelatex -interaction=nonstopmode -synctex=1 %O %S';
$bibtex_use = 2;        # tự dùng biber
$clean_ext = 'bbl bcf fls xml';
```

---

## Cấu trúc file thư mục dự án LaTeX

```
project/
├── main.tex              # File chính
├── references.bib        # BibTeX database
├── .latexmkrc            # Cấu hình latexmk
├── compile.sh            # Script compile thủ công
│
├── chapters/             # Các chapter riêng (include vào main.tex)
│   ├── 01-intro.tex
│   ├── 02-theory.tex
│   └── 03-method.tex
│
├── figures/              # Hình ảnh (.png, .pdf, .eps)
│   └── architecture.png
│
└── appendices/           # Phụ lục
    └── appendix-a.tex
```

### Include chapters trong main.tex

```latex
\include{chapters/01-intro}     % \include tự thêm \clearpage
\input{chapters/02-theory}      % \input không thêm clearpage
```

---

## Kiểm tra lỗi phổ biến

| Lỗi | Nguyên nhân | Giải pháp |
|-----|------------|-----------|
| `! Undefined control sequence` | Dùng lệnh không tồn tại hoặc quên package | Thêm package cần thiết |
| `Missing $ inserted` | Ký tự math ngoài math mode (`_`, `^`) | Escape: `\_`, `\textasciicircum{}` |
| `Overfull \hbox` | Từ/URL quá dài không xuống dòng được | Thêm `\usepackage[hyphens]{url}` |
| `Citation undefined` | Chưa chạy biber/bibtex | Chạy: `biber main` rồi xelatex lại |
| Font không hiển thị tiếng Việt | Dùng pdflatex với tiếng Việt | Chuyển sang xelatex + fontspec |
| `Package babel Error` | Xung đột babel và polyglossia | Chỉ dùng một trong hai |
