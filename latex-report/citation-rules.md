# Citation Rules — Quy tắc trích dẫn trong LaTeX

## Hai hệ thống trích dẫn chính

### Vancouver (Numbered) — dùng cho IEEE, kỹ thuật, khoa học tự nhiên

- **In-text:** `[1]`, `[2,3]`, `[4--6]`
- **Đánh số** theo thứ tự xuất hiện trong văn bản
- **Bibliography** sắp xếp theo số thứ tự
- **LaTeX setup:**

```latex
\usepackage[backend=biber, style=numeric, sorting=none]{biblatex}
\addbibresource{references.bib}
```

### Harvard (Author-Date) — dùng cho APA, KHXH, kinh tế

- **In-text:** `(Nguyen, 2024)` hoặc `Nguyen (2024) cho thấy...`
- **Bibliography** sắp xếp theo alphabet tên tác giả
- **LaTeX setup:**

```latex
\usepackage[backend=biber, style=authoryear, maxcitenames=2]{biblatex}
\addbibresource{references.bib}
```

---

## Bảng so sánh citation styles

| Style | In-text | Dùng trong | LaTeX style name |
|-------|---------|-----------|-----------------|
| IEEE | `[1]` | Kỹ thuật, CS, điện tử | `ieee` |
| APA 7 | `(Nguyen, 2023)` | Tâm lý, giáo dục, KHXH | `apa` |
| Harvard | `Nguyen (2023)` | Kinh tế, quản trị | `authoryear` |
| Chicago Author-Date | `(Nguyen 2023)` | Lịch sử, nhân văn | `chicago-authordate` |
| Chicago Notes | footnote | Lịch sử, nhân văn | `chicago-notes` |
| Vancouver | `[1]` | Y học, sinh học | `vancouver` |

---

## BibTeX entry types đầy đủ

### `@article` — Bài báo tạp chí

```bibtex
@article{Nguyen2024,
  author  = {Nguyen, Van An and Tran, Thi Binh},
  title   = {Tiêu đề bài báo},
  journal = {Tên tạp chí},
  year    = {2024},
  volume  = {10},
  number  = {2},
  pages   = {100--115},
  doi     = {10.xxxx/xxx}
}
```

### `@book` — Sách

```bibtex
@book{Smith2023,
  author    = {Smith, John},
  title     = {Book Title},
  publisher = {Publisher Name},
  year      = {2023},
  address   = {New York},
  edition   = {2nd},
  isbn      = {978-xxx}
}
```

### `@incollection` — Chương sách

```bibtex
@incollection{Brown2022,
  author    = {Brown, Alice},
  title     = {Chapter Title},
  booktitle = {Book Title},
  editor    = {Editor, Name},
  publisher = {Publisher},
  year      = {2022},
  pages     = {45--67}
}
```

### `@inproceedings` — Bài hội nghị / Conference paper

```bibtex
@inproceedings{Le2024,
  author    = {Le, Van C.},
  title     = {Paper Title},
  booktitle = {Proceedings of the International Conference on Name (CONF'24)},
  year      = {2024},
  pages     = {50--60},
  publisher = {ACM},
  address   = {New York},
  doi       = {10.xxxx/xxx}
}
```

### `@online` — Trang web / Website

```bibtex
@online{Website2024,
  author  = {Author, Name},
  title   = {Page Title},
  url     = {https://example.com/page},
  year    = {2024},
  urldate = {2026-05-16}
}
```

> **Lưu ý:** `urldate` là ngày truy cập — BẮT BUỘC vì nội dung web có thể thay đổi.

### `@mastersthesis` — Luận văn thạc sĩ

```bibtex
@mastersthesis{Hoang2024,
  author = {Hoang, Van D.},
  title  = {Tiêu đề luận văn thạc sĩ},
  school = {Trường Đại học Bách Khoa Hà Nội},
  year   = {2024},
  type   = {Luận văn thạc sĩ}
}
```

### `@phdthesis` — Luận án tiến sĩ

```bibtex
@phdthesis{Pham2023,
  author = {Pham, Thi E.},
  title  = {Dissertation Title},
  school = {University Name},
  year   = {2023}
}
```

### `@techreport` — Báo cáo kỹ thuật

```bibtex
@techreport{NIST2024,
  author      = {{National Institute of Standards and Technology}},
  title       = {Report Title},
  institution = {NIST},
  year        = {2024},
  number      = {NIST SP 800-xxx},
  url         = {https://nvlpubs.nist.gov/...}
}
```

> **Lưu ý:** Tổ chức làm tác giả cần bọc trong `{{ }}` để BibTeX không cắt thành Lastname, Firstname.

### `@misc` — Nguồn khác (phần mềm, dataset, tiêu chuẩn...)

```bibtex
@misc{TensorFlow2024,
  author       = {{Google Brain Team}},
  title        = {TensorFlow: Large-Scale Machine Learning on Heterogeneous Systems},
  year         = {2024},
  howpublished = {\url{https://tensorflow.org}},
  note         = {Software available from tensorflow.org}
}
```

---

## Commands trích dẫn trong LaTeX

| Command | Kết quả | Dùng khi |
|---------|---------|----------|
| `\cite{key}` | `[1]` hoặc `(Nguyen, 2024)` | Trích dẫn cơ bản |
| `\cite{key1,key2}` | `[1,2]` | Nhiều nguồn cùng lúc |
| `\textcite{key}` | `Nguyen (2024)` | Tên tác giả làm chủ ngữ |
| `\parencite{key}` | `(Nguyen, 2024)` | Trích dẫn trong ngoặc |
| `\footcite{key}` | footnote | Chicago notes style |
| `\cite[p.~15]{key}` | `[1, p. 15]` | Chỉ số trang cụ thể |
| `\cite[xem thêm][]{key}` | `(xem thêm Nguyen, 2024)` | Với pre-note |
| `\nocite{*}` | (ẩn) | Đưa tất cả vào bibliography dù không cite |

---

## In bibliography

```latex
% Cuối document, trước \end{document}
\printbibliography[title={Tài liệu tham khảo}]

% Chia theo loại (tuỳ chọn)
\printbibliography[type=article, title={Bài báo}]
\printbibliography[type=book, title={Sách}]
\printbibliography[nottype=article, nottype=book, title={Nguồn khác}]
```

---

## Quy tắc vàng (7 quy tắc bắt buộc)

1. **Mọi claim phải có citation** — số liệu, định nghĩa, phát biểu, kết quả của người khác
2. **Không cite Wikipedia** — tìm nguồn gốc: bài báo, sách, báo cáo chính thức
3. **DOI ưu tiên hơn URL** cho bài báo học thuật — DOI bền vĩnh hơn
4. **URL phải có `urldate`** — ghi ngày truy cập vì trang web có thể thay đổi
5. **Tên tác giả nhất quán** — format: `Last, First Middle` (ví dụ: `Nguyen, Van An`)
6. **Không bịa tài liệu** — dùng `\todo{Cần tìm nguồn}` nếu chưa có nguồn
7. **Citation key** theo pattern: `AuthorYear` (ví dụ: `Nguyen2024`, `Smith2023b`)

---

## Tên tác giả Việt Nam

Tên Việt Nam có thể gây nhầm lẫn vì thứ tự: Họ - Tên đệm - Tên.

```bibtex
% Nguyễn Văn An → BibTeX cần format: Last, First Middle
author = {Nguyen, Van An}

% Nhiều tác giả dùng "and"
author = {Nguyen, Van An and Tran, Thi Binh and Le, Van C.}

% Tổ chức làm tác giả — bọc bằng {{ }}
author = {{Bộ Giáo dục và Đào tạo}}
```

---

## Ví dụ in-text citation đúng cách

```latex
% IEEE style (numeric)
Theo nghiên cứu gần đây \cite{Nguyen2024}, mô hình đạt độ chính xác 95\%.

% Nhiều nguồn
Nhiều nghiên cứu đã chứng minh điều này \cite{Nguyen2024, Smith2023, Le2022}.

% APA/Harvard style
\textcite{Nguyen2024} cho thấy mô hình đạt độ chính xác 95\%.
Mô hình đạt độ chính xác 95\% \parencite{Nguyen2024}.

% Với số trang
Định nghĩa chính xác được trình bày tại \cite[p.~42]{Smith2023}.
```
