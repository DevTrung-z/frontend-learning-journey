Dưới đây là bản “**CSS Master Map**” — gom toàn bộ kiến thức nền tảng + thực chiến, có thể coi là _tài liệu cốt lõi_ trước khi bước qua React/Next.js.

---

# 🎨 **I. KHÁI NIỆM & MỤC ĐÍCH CỦA CSS**

CSS (Cascading Style Sheets) là ngôn ngữ **mô tả cách trình bày của HTML** – tức là điều khiển:

- Màu sắc, kích thước, bố cục, font chữ, hiệu ứng, responsive,...
- CSS _không_ tạo nội dung mới, mà _trang trí và định vị_ nội dung HTML.

Cấu trúc cơ bản:

```css
selector {
  property: value;
}
```

Ví dụ:

```css
p {
  color: red;
  font-size: 18px;
}
```

---

# 🧱 **II. CÁCH NHÚNG CSS VÀO HTML**

1. **Inline CSS**

   ```html
   <p style="color: blue;">Hello</p>
   ```

2. **Internal CSS**
   Trong `<style>` trong file HTML.
3. **External CSS (Khuyên dùng)**

   ```html
   <link rel="stylesheet" href="style.css" />
   ```

👉 Ưu tiên: External > Internal > Inline (theo chuẩn clean code).

---

# 🎯 **III. SELECTOR (BỘ CHỌN)**

### 1️⃣ Cơ bản

| Selector            | Ví dụ              | Mô tả                    |
| ------------------- | ------------------ | ------------------------ |
| `*`                 | `* {}`             | Chọn tất cả phần tử      |
| `element`           | `p {}`             | Chọn theo tên thẻ        |
| `.class`            | `.box {}`          | Chọn theo class          |
| `#id`               | `#main {}`         | Chọn theo ID             |
| `element, element`  | `h1, h2 {}`        | Gộp nhiều phần tử        |
| `element element`   | `div p {}`         | Con cháu                 |
| `element > element` | `div > p {}`       | Con trực tiếp            |
| `element + element` | `h1 + p {}`        | Phần tử kế tiếp ngay sau |
| `[attribute]`       | `[type="text"] {}` | Theo thuộc tính          |

### 2️⃣ Nâng cao

- `:hover`, `:focus`, `:checked`, `:nth-child()`, `:first-child`, `:last-of-type`
- `::before`, `::after`, `::placeholder` (pseudo elements)

---

# 💅 **IV. THUỘC TÍNH CƠ BẢN NHẤT**

### 🔹 Màu sắc & văn bản

```css
color: #333;
background-color: lightblue;
font-size: 16px;
font-family: "Roboto", sans-serif;
text-align: center;
text-transform: uppercase;
text-decoration: none;
font-weight: bold;
line-height: 1.5;
```

### 🔹 Kích thước & khoảng cách

```css
width: 200px;
height: 100px;
margin: 20px; /* Khoảng cách ngoài */
padding: 10px; /* Khoảng cách trong */
border: 1px solid #000;
border-radius: 10px;
box-sizing: border-box;
```

### 🔹 Display & Visibility

```css
display: block | inline | inline-block | none | flex | grid;
visibility: hidden;
overflow: hidden | scroll | auto;
```

---

# 🧭 **V. BOX MODEL**

Cực kỳ quan trọng — toàn bộ bố cục web dựa vào nó:

```
+---------------------+
|      margin         |
|  +--------------+   |
|  |   border     |   |
|  | +----------+ |   |
|  | | padding  | |   |
|  | | content  | |   |
|  | +----------+ |   |
|  +--------------+   |
+---------------------+
```

Tổng kích thước phần tử =
`width + padding + border + margin`

---

# 🧮 **VI. POSITION & DISPLAY**

| Thuộc tính | Mô tả                                                         | Dùng khi nào           |
| ---------- | ------------------------------------------------------------- | ---------------------- |
| `static`   | mặc định                                                      | khi không cần định vị  |
| `relative` | dịch chuyển so với vị trí ban đầu                             | khi muốn căn chỉnh nhẹ |
| `absolute` | định vị tuyệt đối trong container cha có `position: relative` | layout nhỏ             |
| `fixed`    | cố định theo màn hình (ví dụ navbar)                          | header/footer cố định  |
| `sticky`   | dính khi cuộn tới vị trí                                      | menu dính đầu trang    |

---

Tốt lắm Trung 👏 — đây là hai phần **xương sống của CSS hiện đại**:
`Flexbox` (bố cục 1 chiều) và `Grid` (bố cục 2 chiều).
Tôi sẽ giải thích kỹ, trực quan, có ví dụ, quy tắc, và cách kết hợp — để Trung hiểu bản chất chứ không cần học thuộc.

---

# 🧭 **VII. FLEXBOX – BỐ CỤC 1 CHIỀU**

## 🎯 Mục tiêu:

Flexbox giúp sắp xếp các phần tử **theo một trục duy nhất**: ngang (row) hoặc dọc (column).
Dễ nhất để căn giữa, giãn cách, sắp xếp item trong hàng hoặc cột mà không cần float hay position.

---

## 🔹 1. Kích hoạt Flexbox

```css
.container {
  display: flex; /* hoặc inline-flex */
}
```

→ Lúc này `.container` trở thành **Flex container**, các phần tử con của nó là **Flex items**.

---

## 🔹 2. Hai trục quan trọng

```
Main Axis  →  (theo flex-direction)
Cross Axis ↓  (vuông góc main)
```

- Nếu `flex-direction: row` → trục chính là **ngang**, trục phụ là **dọc**.
- Nếu `flex-direction: column` → trục chính là **dọc**, trục phụ là **ngang**.

---

## 🔹 3. Các thuộc tính của _Container_

| Thuộc tính            | Chức năng                              | Giá trị hay dùng                                                        |
| --------------------- | -------------------------------------- | ----------------------------------------------------------------------- | -------------- |
| **`flex-direction`**  | Hướng sắp xếp                          | `row` (ngang)                                                           | `column` (dọc) |
| **`justify-content`** | Căn trên _main axis_ (ngang nếu row)   | `flex-start`, `center`, `space-between`, `space-around`, `space-evenly` |
| **`align-items`**     | Căn trên _cross axis_ (vuông góc main) | `flex-start`, `center`, `flex-end`, `stretch`                           |
| **`align-content`**   | Khi có nhiều dòng (wrap), căn cả nhóm  | Giống align-items                                                       |
| **`flex-wrap`**       | Cho phép item xuống dòng               | `nowrap` (mặc định), `wrap`, `wrap-reverse`                             |
| **`gap`**             | Khoảng cách giữa các item              | `gap: 20px`                                                             |

💡 Gộp lại:

```css
.container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
}
```

---

## 🔹 4. Các thuộc tính của _Item_

| Thuộc tính        | Chức năng                                           |
| ----------------- | --------------------------------------------------- |
| **`flex-grow`**   | Mức độ giãn khi còn không gian                      |
| **`flex-shrink`** | Mức độ co khi thiếu chỗ                             |
| **`flex-basis`**  | Kích thước ban đầu (có thể coi là “width” mặc định) |
| **`align-self`**  | Ghi đè `align-items` riêng từng item                |
| **`order`**       | Thay đổi thứ tự hiển thị mà không đổi HTML          |

Shortcut:

```css
.item {
  flex: 1 0 200px; /* grow shrink basis */
}
```

---

## 🔹 5. Ví dụ trực quan

```html
<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
</div>
```

```css
.container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 200px;
  border: 2px solid #333;
}
.item {
  background: #4a90e2;
  color: white;
  padding: 20px;
}
```

---

## 🔹 6. Khi nào dùng Flexbox

- Bố cục **một hàng hoặc một cột** (navbar, card list, button group).
- Căn giữa phần tử dễ dàng.
- Cần sắp xếp các phần tử có kích thước khác nhau.

💡 Ví dụ: Căn giữa phần tử trong container:

```css
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

---

# 🧩 **VIII. CSS GRID – BỐ CỤC 2 CHIỀU**

## 🎯 Mục tiêu:

Grid là hệ thống chia lưới **cả 2 chiều (hàng và cột)**.
Thích hợp cho layout phức tạp, nơi Flexbox phải “chắp vá”.

---

## 🔹 1. Kích hoạt Grid

```css
.container {
  display: grid;
}
```

---

## 🔹 2. Tạo lưới cơ bản

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr 1fr;
  grid-template-rows: 100px auto;
  gap: 20px;
}
```

- `grid-template-columns` → chia cột
- `grid-template-rows` → chia hàng
- `fr` (fractional unit) → chia phần linh hoạt
- `gap` → khoảng cách giữa ô

---

## 🔹 3. Đặt item vào lưới

```css
.item1 {
  grid-column: 1 / 3; /* chiếm từ cột 1 đến 2 */
  grid-row: 1 / 2;
}
```

Hoặc dùng cú pháp ngắn:

```css
grid-column: span 2; /* chiếm 2 cột */
grid-row: span 1;
```

---

## 🔹 4. Các thuộc tính quan trọng của _Container_

| Thuộc tính                             | Ý nghĩa                     |
| -------------------------------------- | --------------------------- |
| `grid-template-columns`                | Định nghĩa cột              |
| `grid-template-rows`                   | Định nghĩa hàng             |
| `grid-template-areas`                  | Đặt tên vùng layout         |
| `grid-auto-rows` / `grid-auto-columns` | Kích thước hàng/cột tự sinh |
| `justify-items` / `align-items`        | Căn chỉnh nội dung item     |
| `justify-content` / `align-content`    | Căn toàn bộ lưới            |
| `gap`, `row-gap`, `column-gap`         | Khoảng cách                 |

---

## 🔹 5. Các thuộc tính của _Item_

| Thuộc tính                             | Ý nghĩa                        |
| -------------------------------------- | ------------------------------ |
| `grid-column-start`, `grid-column-end` | Bắt đầu/kết thúc cột           |
| `grid-row-start`, `grid-row-end`       | Bắt đầu/kết thúc hàng          |
| `grid-area`                            | Dùng với `grid-template-areas` |
| `justify-self`, `align-self`           | Căn riêng từng item            |

---

## 🔹 6. Ví dụ cơ bản

```html
<div class="grid">
  <div class="item header">Header</div>
  <div class="item sidebar">Sidebar</div>
  <div class="item main">Main</div>
  <div class="item footer">Footer</div>
</div>
```

```css
.grid {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: 100px 1fr 50px;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  gap: 10px;
}
.header {
  grid-area: header;
  background: #4a90e2;
}
.sidebar {
  grid-area: sidebar;
  background: #7b4397;
}
.main {
  grid-area: main;
  background: #f5af19;
}
.footer {
  grid-area: footer;
  background: #333;
}
```

→ Tạo layout chuẩn “Header–Sidebar–Main–Footer”.

---

## 🔹 7. Khi nào dùng Grid

- Layout tổng thể của trang (Header, Nav, Main, Footer).
- Khi cần chia hàng và cột đồng thời.
- Khi item phải chiếm vùng xác định (vd: Dashboard, Gallery).

---

## 🔹 8. Kết hợp Flex + Grid

Thường dùng chung:

- **Grid** cho khung tổng thể (macro layout)
- **Flexbox** cho sắp xếp trong từng vùng nhỏ (micro layout)

Ví dụ:

```html
<div class="layout">
  <header>...</header>
  <main class="cards">
    <div class="card">1</div>
    <div class="card">2</div>
  </main>
  <footer>...</footer>
</div>
```

```css
.layout {
  display: grid;
  grid-template-rows: auto 1fr auto;
}
.cards {
  display: flex;
  gap: 20px;
}
```

---

## ⚡ Tổng so sánh nhanh

| Tính năng       | Flexbox                   | Grid                                      |
| --------------- | ------------------------- | ----------------------------------------- |
| Bố cục          | 1 chiều (row hoặc column) | 2 chiều (hàng + cột)                      |
| Dễ học          | Dễ hơn                    | Hơi phức tạp hơn                          |
| Tình huống dùng | Menu, card list, căn giữa | Layout trang, dashboard                   |
| Căn chỉnh       | `justify-*`, `align-*`    | Có thêm `grid-area`, `grid-template`      |
| Responsive      | Linh hoạt                 | Cực mạnh khi dùng `auto-fit` / `minmax()` |

---

## 🌈 Mẹo chuyên nghiệp:

- Dùng `gap` thay vì `margin` cho khoảng cách đều.
- Dùng `auto-fit` + `minmax()` để responsive tự động:

```css
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
```

→ Khi màn hình nhỏ, các item tự xuống hàng đều nhau.

# 🪄 **IX. RESPONSIVE & MEDIA QUERY**

Cho phép thay đổi giao diện theo kích thước màn hình.

```css
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
  .container {
    flex-direction: column;
  }
}
```

---

# 🌈 **X. HIỆU ỨNG & TRANSITION**

```css
.box {
  transition: all 0.3s ease;
}
.box:hover {
  transform: scale(1.1);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}
```

Cũng bao gồm:

- `animation`, `@keyframes`
- `transform: rotate(), translate(), scale()`
- `opacity`, `filter`

---

# 🧩 **XI. PSEUDO & CUSTOM PROPERTIES**

```css
button::before {
  content: "👉 ";
}
:root {
  --main-color: #2f80ed;
}
h1 {
  color: var(--main-color);
}
```

---

# 🪶 **XII. Z-INDEX & STACKING CONTEXT**

```css
.modal {
  z-index: 9999;
  position: fixed;
}
```

Chỉ hoạt động khi có `position` khác `static`.

---

# ⚙️ **XIII. ADVANCED FEATURES**

| Chủ đề            | Mô tả                               |
| ----------------- | ----------------------------------- |
| `object-fit`      | Kiểm soát ảnh trong khung           |
| `clip-path`       | Cắt hình dạng tùy ý                 |
| `filter`          | Làm mờ, grayscale, brightness       |
| `backdrop-filter` | Tạo hiệu ứng mờ nền (glassmorphism) |
| `aspect-ratio`    | Giữ tỉ lệ ảnh/video                 |
| `scroll-behavior` | Cuộn mượt                           |

---

# 🧩 **XIV. CÁC MODULE MỞ RỘNG**

- **CSS Variables** (`--var`)
- **CSS Functions:** `calc()`, `min()`, `max()`, `clamp()`
- **CSS Grid Level 2:** `subgrid`
- **Container Queries** (CSS mới)
- **Custom Fonts:** `@font-face`
- **Transitions & Animations:** `@keyframes`

---

# 🧠 **XV. CÁC ITEM CSS ĐƯỢC DÙNG NHIỀU NHẤT**

| Nhóm       | Thuộc tính phổ biến                                                                |
| ---------- | ---------------------------------------------------------------------------------- |
| Text       | `color`, `font-size`, `font-weight`, `line-height`, `text-align`, `text-transform` |
| Box        | `margin`, `padding`, `border`, `border-radius`, `box-shadow`                       |
| Layout     | `display`, `flex`, `grid`, `position`, `z-index`, `overflow`, `gap`                |
| Background | `background-color`, `background-image`, `background-size`, `background-position`   |
| Transition | `transition`, `transform`, `animation`                                             |
| Responsive | `@media`, `width`, `max-width`, `min-width`, `aspect-ratio`                        |

---

# 🧾 **XVI. BEST PRACTICES**

- **Tách file CSS riêng**, đặt tên rõ ràng.
- **Dùng class thay vì id** để tái sử dụng.
- **Luôn reset CSS** (`* { margin: 0; padding: 0; box-sizing: border-box; }`).
- **Tuân thủ mô hình BEM** khi đặt tên class:

  ```
  .card__title--highlight
  ```

- **Tránh inline CSS**, vì khó bảo trì.

---

# 🧩 **XVII. KẾT HỢP HTML + CSS CHUYÊN NGHIỆP**

Ví dụ mẫu:

```html
<div class="card">
  <img src="image.jpg" alt="ảnh" />
  <h2>Tiêu đề</h2>
  <p>Mô tả ngắn gọn</p>
  <button>Xem thêm</button>
</div>
```

```css
.card {
  background: #fff;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: 0.3s;
}
.card:hover {
  transform: translateY(-5px);
}
```

---

# ✅ **TỔNG KẾT**

| Cấp độ     | Kiến thức chính                                    |
| ---------- | -------------------------------------------------- |
| Cơ bản     | Syntax, selector, text, box model, colors          |
| Trung cấp  | Position, display, flexbox, responsive             |
| Nâng cao   | Grid, transition, transform, variables, animations |
| Thực chiến | BEM naming, CSS architecture, component styling    |

---
