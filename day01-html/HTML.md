#Học và bắt đầu lại toàn bộ với kiến thức bằng 0

HTML (RoadMap: https://roadmap.sh/html )

1. Mục đích chính của HTML

- HTML là ngôn ngữ đánh dấu (markup) dùng để tạo cấu trúc nội dung cho trang web
  -> kế bên HTML là Css thứ tạo nên vẻ đẹp cho trang web

1️⃣ Câu trúc cơ bản của HTML

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Tên trang web</title>
  </head>
  <body>
    Nội dung hiển thị
  </body>
</html>

Nắm rõ vai trò của từng phần:

<!DOCTYPE html>: xác định phiên bản HTML5
<html>: bao toàn trang
<head>: chứa metadata, title, link CSS, SEO info
<body>: chứa nội dung hiển thị cho người dùng

2️⃣ Các thẻ nội dung chính

Tiêu đề: <h1> đến <h6>
Đoạn văn: <p>
Liên kết: <a href="...">
Ảnh: <img src="..." alt="...">

Danh sách:

- Dạng chấm: <ul><li></li></ul>9
- Dạng số: <ol><li></li></ol>
- Bảng: <table>, <tr>, <th>, <td>
- Form: <form>, <input>, <textarea>, <button>, <select>

3️⃣ Thẻ ngữ nghĩa (Semantic Tags)

Hiểu và bắt buộc dùng khi làm layout:

<header>: phần đầu trang (logo, nav, v.v.)
<nav>: menu điều hướng
<main>: nội dung chính
<section>: khối nội dung cùng chủ đề
<article>: bài viết độc lập
<aside>: sidebar hoặc thông tin phụ
<footer>: chân trang

💡 Giúp SEO tốt hơn và dễ đọc code hơn.

4️⃣ Thẻ chứa nội dung

<div>: khối chia bố cục (block)
<span>: nội dung inline nhỏ (chữ, từ, icon)

5️⃣ Thuộc tính (Attributes)

id, class — dùng để gắn CSS hoặc JavaScript
alt — mô tả hình ảnh
href, src, target, title
