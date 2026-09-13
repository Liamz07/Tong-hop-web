# HTML Cheat Sheet – Tổng hợp kiến thức HTML

> Tài liệu tổng hợp các thẻ HTML quan trọng, chức năng và ví dụ thông dụng.
> Phù hợp để học HTML từ cơ bản đến nâng cao và làm các project web.

---

## 1. HTML là gì?

**HTML (HyperText Markup Language)** là ngôn ngữ đánh dấu dùng để xây dựng **cấu trúc và nội dung của trang web**.

Có thể hình dung:

```text
HTML        CSS          JavaScript
 │           │               │
 ▼           ▼               ▼
Cấu trúc → Giao diện → Tương tác
```

- **HTML** → cấu trúc
- **CSS** → giao diện
- **JavaScript** → hành vi và tương tác

Ví dụ:

```html
<h1>To-Do List App</h1>
<p>Organize your tasks, simplify your day.</p>
<button>Add Task</button>
```

---

# 2. Cấu trúc cơ bản của file HTML

```html
<!DOCTYPE html>

<html lang="vi">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Trang web của tôi</title>
</head>

<body>

    <h1>Hello World!</h1>

</body>

</html>
```

## `<!DOCTYPE html>`

Khai báo tài liệu sử dụng **HTML5**.

```html
<!DOCTYPE html>
```

Đây không phải là một HTML tag.

## `<html>`

Phần tử gốc của toàn bộ tài liệu HTML.

```html
<html lang="vi">
```

`lang="vi"` cho biết ngôn ngữ chính của trang là tiếng Việt.

---

# 3. `<head>` và các thẻ bên trong

`<head>` chứa các thông tin về trang, phần lớn không hiển thị trực tiếp trên giao diện.

```html
<head>

    <meta charset="UTF-8">

    <meta name="viewport"
          content="width=device-width, initial-scale=1.0">

    <title>My Website</title>

    <link rel="stylesheet" href="style.css">

</head>
```

## `<title>` ⭐⭐⭐

Tiêu đề xuất hiện trên tab trình duyệt.

```html
<title>To-Do List App</title>
```

## `<meta>` ⭐⭐⭐

Cung cấp metadata cho trình duyệt và công cụ tìm kiếm.

### UTF-8

```html
<meta charset="UTF-8">
```

Giúp trang hiển thị tiếng Việt và các ký tự Unicode.

### Responsive

```html
<meta name="viewport"
      content="width=device-width, initial-scale=1.0">
```

Rất quan trọng khi làm website responsive trên điện thoại.

## `<link>` ⭐⭐⭐

Liên kết tài nguyên bên ngoài.

Ví dụ liên kết CSS:

```html
<link rel="stylesheet" href="style.css">
```

Favicon:

```html
<link rel="icon" href="favicon.ico">
```

## `<style>`

Viết CSS trực tiếp trong HTML.

```html
<style>
    body {
        background-color: black;
    }
</style>
```

Trong project thực tế thường ưu tiên file CSS riêng:

```html
<link rel="stylesheet" href="style.css">
```

## `<script>` ⭐⭐⭐

Nhúng JavaScript.

```html
<script src="script.js"></script>
```

Thông thường có thể dùng:

```html
<script src="script.js" defer></script>
```

`defer` giúp script được thực thi sau khi HTML được phân tích.

---

# 4. Heading – tiêu đề ⭐⭐⭐

HTML có 6 cấp độ heading:

```html
<h1>Tiêu đề lớn nhất</h1>
<h2>Tiêu đề cấp 2</h2>
<h3>Tiêu đề cấp 3</h3>
<h4>Tiêu đề cấp 4</h4>
<h5>Tiêu đề cấp 5</h5>
<h6>Tiêu đề cấp 6</h6>
```

Ví dụ:

```html
<h1>Quản lý chi tiêu cá nhân</h1>

<h2>Thống kê</h2>

<h3>Chi tiêu tháng 9</h3>
```

Thông thường có thể tổ chức:

```text
h1
 ├── h2
 │    ├── h3
 │    └── h3
 └── h2
      └── h3
```

`<h1>` thường là tiêu đề chính của trang.

---

# 5. Văn bản ⭐⭐⭐

## `<p>`

Paragraph – đoạn văn.

```html
<p>Đây là một đoạn văn.</p>
```

## `<br>`

Xuống dòng.

```html
<p>
    Xin chào!<br>
    Tôi đang học HTML.
</p>
```

`<br>` là void element, không cần thẻ đóng.

## `<hr>`

Tạo đường phân cách.

```html
<p>Phần 1</p>

<hr>

<p>Phần 2</p>
```

## `<strong>` ⭐

Nhấn mạnh nội dung quan trọng, thường hiển thị in đậm.

```html
<p>
    Đây là <strong>thông tin quan trọng</strong>.
</p>
```

## `<em>`

Nhấn mạnh về mặt ngữ nghĩa, thường hiển thị in nghiêng.

```html
<p>
    Đây là <em>nội dung cần chú ý</em>.
</p>
```

## `<b>`

In đậm về mặt trình bày.

```html
<b>Bold text</b>
```

Nếu muốn thể hiện ý nghĩa "quan trọng", ưu tiên `<strong>`.

## `<i>`

In nghiêng về mặt trình bày.

```html
<i>Hello</i>
```

## `<u>`

Gạch chân.

```html
<u>Gạch chân</u>
```

Không nên lạm dụng vì người dùng thường có thể hiểu text gạch chân là link.

## `<mark>`

Highlight nội dung.

```html
<p>
    HTML là <mark>ngôn ngữ đánh dấu</mark>.
</p>
```

## `<small>`

Chữ nhỏ hơn.

```html
<small>Copyright © 2026</small>
```

## `<del>`

Nội dung bị xóa.

```html
<del>200.000đ</del>
```

Ví dụ:

```html
<p>
    <del>200.000đ</del> 150.000đ
</p>
```

## `<ins>`

Nội dung được thêm vào.

```html
<ins>Nội dung mới</ins>
```

## `<sub>`

Chỉ số dưới.

```html
H<sub>2</sub>O
```

Kết quả: H₂O

## `<sup>`

Chỉ số trên.

```html
x<sup>2</sup>
```

Kết quả: x²

---

# 6. `<div>` và `<span>` ⭐⭐⭐

## `<div>`

Container dạng block.

```html
<div class="card">
    <h2>Task</h2>
    <p>Learn HTML</p>
</div>
```

Thường dùng để gom nhóm các phần tử.

## `<span>`

Container dạng inline.

```html
<p>
    Xin chào <span class="username">Minh</span>
</p>
```

Thường dùng để style một phần nhỏ của text.

### So sánh

```html
<div>Hello</div>
<div>World</div>
```

Thường nằm thành các dòng riêng.

Trong khi:

```html
<span>Hello</span>
<span>World</span>
```

Có thể nằm cùng dòng.

---

# 7. Link – `<a>` ⭐⭐⭐

Dùng để tạo hyperlink.

```html
<a href="https://example.com">
    Truy cập website
</a>
```

Mở tab mới:

```html
<a href="https://example.com" target="_blank">
    Mở website
</a>
```

Link tới trang khác trong project:

```html
<a href="about.html">About</a>
```

Link tới một phần trong cùng trang:

```html
<a href="#contact">Liên hệ</a>

<section id="contact">
    <h2>Liên hệ</h2>
</section>
```

---

# 8. Hình ảnh – `<img>` ⭐⭐⭐

```html
<img src="cat.jpg" alt="Một con mèo">
```

Các thuộc tính quan trọng:

```text
src → đường dẫn hình ảnh
alt → mô tả hình ảnh
```

Ví dụ:

```html
<img
    src="images/avatar.png"
    alt="Ảnh đại diện"
    width="200"
>
```

`alt` quan trọng cho accessibility và trường hợp ảnh không tải được.

---

# 9. `<picture>`

Cho phép trình duyệt lựa chọn hình ảnh phù hợp theo điều kiện.

```html
<picture>
    <source media="(max-width: 600px)"
            srcset="mobile.jpg">

    <img src="desktop.jpg"
         alt="Ảnh minh họa">
</picture>
```

---

# 10. Audio và Video ⭐⭐

## `<audio>`

```html
<audio controls>
    <source src="music.mp3" type="audio/mpeg">
</audio>
```

## `<video>`

```html
<video controls width="600">
    <source src="video.mp4" type="video/mp4">
</video>
```

Một số thuộc tính:

```html
<video controls autoplay muted loop>
```

- `controls` → hiện nút điều khiển
- `autoplay` → tự động phát
- `muted` → tắt tiếng
- `loop` → lặp lại

---

# 11. `<iframe>` ⭐⭐

Nhúng một trang hoặc tài nguyên khác.

Ví dụ:

```html
<iframe
    src="https://www.youtube.com/embed/..."
    width="560"
    height="315">
</iframe>
```

Có thể dùng để nhúng YouTube, Google Maps và một số nội dung bên ngoài.

---

# 12. Danh sách ⭐⭐⭐

## `<ul>` – unordered list

Danh sách không đánh số.

```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

## `<ol>` – ordered list

Danh sách có thứ tự.

```html
<ol>
    <li>Học HTML</li>
    <li>Học CSS</li>
    <li>Học JavaScript</li>
</ol>
```

## `<li>`

List item.

```html
<li>HTML</li>
```

Thường nằm trong `<ul>` hoặc `<ol>`.

## `<dl>`, `<dt>`, `<dd>`

Description list.

```html
<dl>
    <dt>HTML</dt>
    <dd>Ngôn ngữ đánh dấu.</dd>

    <dt>CSS</dt>
    <dd>Ngôn ngữ tạo kiểu.</dd>
</dl>
```

---

# 13. Table – bảng ⭐⭐

Các thẻ quan trọng:

```text
<table>
 ├── <thead>
 │    └── <tr>
 │         └── <th>
 │
 ├── <tbody>
 │    └── <tr>
 │         └── <td>
 │
 └── <tfoot>
```

Ví dụ:

```html
<table>
    <thead>
        <tr>
            <th>Tên</th>
            <th>Tuổi</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>Minh</td>
            <td>20</td>
        </tr>

        <tr>
            <td>An</td>
            <td>21</td>
        </tr>
    </tbody>
</table>
```

## `<table>`

Tạo bảng.

## `<tr>`

Table row – một hàng.

## `<th>`

Table header – ô tiêu đề.

## `<td>`

Table data – ô dữ liệu.

## `<thead>`

Phần đầu bảng.

## `<tbody>`

Phần thân bảng.

## `<tfoot>`

Phần cuối bảng.

---

# 14. Gộp ô trong bảng

## `colspan`

Gộp nhiều cột:

```html
<td colspan="2">
    Tổng cộng
</td>
```

## `rowspan`

Gộp nhiều hàng:

```html
<td rowspan="2">
    Nguyễn Văn A
</td>
```

---

# 15. Form ⭐⭐⭐

Form là phần rất quan trọng khi làm web.

Ví dụ:

```html
<form>
    <label for="username">Tên:</label>

    <input
        type="text"
        id="username"
        name="username"
    >

    <button type="submit">
        Đăng nhập
    </button>
</form>
```

---

# 16. `<form>`

Container chứa form.

```html
<form action="/login" method="post">
    ...
</form>
```

Thuộc tính quan trọng:

```text
action → gửi dữ liệu tới đâu
method → gửi dữ liệu bằng phương thức nào
```

Ví dụ:

```html
<form action="/login" method="POST">
```

---

# 17. `<label>` ⭐⭐⭐

Tên hoặc mô tả cho input.

```html
<label for="email">
    Email
</label>

<input id="email" type="email">
```

`for="email"` liên kết với:

```html
id="email"
```

---

# 18. `<input>` ⭐⭐⭐

Một trong những thẻ quan trọng nhất trong form.

```html
<input type="text">
```

Các `type` phổ biến:

### Text

```html
<input type="text">
```

### Password

```html
<input type="password">
```

### Email

```html
<input type="email">
```

### Number

```html
<input type="number">
```

### Checkbox

```html
<input type="checkbox">
```

### Radio

```html
<input type="radio">
```

### Date

```html
<input type="date">
```

### Time

```html
<input type="time">
```

### File

```html
<input type="file">
```

### Color

```html
<input type="color">
```

### Range

```html
<input type="range">
```

### Search

```html
<input type="search">
```

### Hidden

```html
<input type="hidden">
```

### Submit

```html
<input type="submit" value="Gửi">
```

---

# 19. Các thuộc tính `<input>` quan trọng ⭐⭐⭐

Ví dụ:

```html
<input
    type="text"
    id="username"
    name="username"
    placeholder="Nhập tên..."
    required
>
```

## `id`

Định danh của phần tử.

```html
id="username"
```

Mỗi `id` nên là duy nhất trong trang.

## `class`

Dùng để CSS hoặc JavaScript nhóm các phần tử.

```html
class="input-field"
```

## `name`

Tên dữ liệu khi form gửi đi.

```html
name="username"
```

## `placeholder`

Text gợi ý.

```html
placeholder="Nhập tên..."
```

## `required`

Bắt buộc nhập.

```html
required
```

## `disabled`

Vô hiệu hóa.

```html
disabled
```

## `readonly`

Chỉ đọc, không cho sửa.

```html
readonly
```

## `min`, `max`

Giới hạn giá trị số.

```html
<input type="number" min="1" max="100">
```

## `minlength`, `maxlength`

Giới hạn độ dài.

```html
<input
    type="text"
    minlength="3"
    maxlength="20"
>
```

---

# 20. `<textarea>` ⭐⭐

Nhập văn bản nhiều dòng.

```html
<textarea
    placeholder="Nhập mô tả..."
></textarea>
```

Ví dụ:

```html
<label for="description">
    Mô tả
</label>

<textarea
    id="description"
    name="description"
    rows="5"
></textarea>
```

---

# 21. `<select>` ⭐⭐

Tạo dropdown.

```html
<select>
    <option>Nam</option>
    <option>Nữ</option>
    <option>Khác</option>
</select>
```

Ví dụ filter trong To-Do List:

```html
<select id="filter">
    <option value="all">All</option>
    <option value="completed">Completed</option>
    <option value="pending">Pending</option>
</select>
```

---

# 22. `<option>`

Một lựa chọn trong `<select>`.

```html
<option value="completed">
    Completed
</option>
```

---

# 23. `<optgroup>`

Nhóm các option.

```html
<select>
    <optgroup label="Frontend">
        <option>HTML</option>
        <option>CSS</option>
        <option>JavaScript</option>
    </optgroup>

    <optgroup label="Backend">
        <option>Node.js</option>
        <option>Python</option>
    </optgroup>
</select>
```

---

# 24. `<button>` ⭐⭐⭐

Tạo nút bấm.

```html
<button>Click me</button>
```

Trong form:

```html
<button type="submit">
    Submit
</button>
```

Các loại phổ biến:

```html
<button type="submit">Submit</button>

<button type="button">Click</button>

<button type="reset">Reset</button>
```

- `submit` → gửi form
- `button` → nút thông thường
- `reset` → reset form

---

# 25. `<fieldset>` và `<legend>`

Dùng để nhóm các trường form.

```html
<fieldset>
    <legend>Thông tin cá nhân</legend>

    <label>Họ tên:</label>
    <input type="text">

    <label>Email:</label>
    <input type="email">
</fieldset>
```

---

# 26. Semantic HTML ⭐⭐⭐

Semantic HTML giúp cấu trúc trang có **ý nghĩa rõ ràng**.

Thay vì:

```html
<div class="header"></div>
<div class="nav"></div>
<div class="main"></div>
<div class="footer"></div>
```

HTML5 cung cấp:

```html
<header>
<nav>
<main>
<section>
<article>
<aside>
<footer>
```

---

# 27. `<header>` ⭐⭐⭐

Phần đầu của trang hoặc một section.

```html
<header>
    <h1>My Website</h1>
    <p>Welcome to my website.</p>
</header>
```

Ví dụ phù hợp với To-Do List:

```html
<header>
    <h1>✏️ To-Do List App</h1>
    <p>Organize your tasks, simplify your day.</p>
</header>
```

---

# 28. `<nav>` ⭐⭐⭐

Khu vực chứa navigation.

```html
<nav>
    <a href="/">Home</a>
    <a href="/about">About</a>
    <a href="/contact">Contact</a>
</nav>
```

---

# 29. `<main>` ⭐⭐⭐

Nội dung chính của trang.

```html
<main>
    <h1>Dashboard</h1>
    ...
</main>
```

Một trang thường chỉ có một `<main>` chính.

---

# 30. `<section>` ⭐⭐⭐

Chia nội dung thành các khu vực có chủ đề.

Ví dụ To-Do List:

```html
<main>

    <section>
        <h2>Add a Task</h2>
        ...
    </section>

    <section>
        <h2>Search & Filter</h2>
        ...
    </section>

    <section>
        <h2>Task List</h2>
        ...
    </section>

</main>
```

---

# 31. `<article>`

Một nội dung độc lập.

Ví dụ blog:

```html
<article>
    <h2>Học HTML cơ bản</h2>
    <p>HTML là nền tảng của web...</p>
</article>
```

Một article có thể được lấy ra khỏi trang mà vẫn có ý nghĩa riêng.

---

# 32. `<aside>`

Nội dung phụ.

```html
<main>

    <article>
        <h1>Bài viết</h1>
        <p>...</p>
    </article>

    <aside>
        <h2>Bài viết liên quan</h2>
    </aside>

</main>
```

---

# 33. `<footer>` ⭐⭐

Phần cuối trang hoặc một section.

```html
<footer>
    <p>© 2026 My Website</p>
</footer>
```

---

# 34. `<figure>` và `<figcaption>`

Dùng cho hình ảnh có chú thích.

```html
<figure>
    <img src="cat.jpg" alt="Con mèo">

    <figcaption>
        Hình 1: Một chú mèo.
    </figcaption>
</figure>
```

---

# 35. `<details>` và `<summary>`

Tạo nội dung có thể mở/đóng.

```html
<details>
    <summary>HTML là gì?</summary>

    <p>
        HTML là ngôn ngữ đánh dấu dùng để xây dựng cấu trúc website.
    </p>
</details>
```

Rất phù hợp cho FAQ.

---

# 36. `<dialog>`

Tạo dialog/modal.

```html
<dialog id="myDialog">
    <p>Bạn có chắc muốn xóa task?</p>
    <button>Cancel</button>
</dialog>
```

JavaScript có thể điều khiển dialog.

---

# 37. `<progress>`

Thanh tiến trình.

```html
<progress value="70" max="100"></progress>
```

Ví dụ:

```text
██████████████░░░░░░ 70%
```

---

# 38. `<meter>`

Biểu thị một giá trị trong một phạm vi.

```html
<meter
    min="0"
    max="100"
    value="80">
</meter>
```

Có thể dùng cho:

- mức pin
- mức sử dụng
- điểm đánh giá
- dung lượng

---

# 39. `<time>`

Biểu diễn thời gian/ngày tháng.

```html
<time datetime="2026-09-13">
    13/09/2026
</time>
```

---

# 40. `<code>`

Hiển thị đoạn code.

```html
<p>
    Sử dụng <code>console.log()</code> để debug.
</p>
```

---

# 41. `<pre>`

Giữ nguyên khoảng trắng và xuống dòng.

```html
<pre>
Hello
    World
        HTML
</pre>
```

Thường kết hợp với `<code>`:

```html
<pre>
<code>
const x = 10;
console.log(x);
</code>
</pre>
```

---

# 42. `<blockquote>`

Trích dẫn một đoạn nội dung dài.

```html
<blockquote>
    The only way to learn programming is to practice.
</blockquote>
```

---

# 43. `<q>`

Trích dẫn ngắn.

```html
<p>
    Anh ấy nói <q>Hãy luyện tập mỗi ngày.</q>
</p>
```

---

# 44. `<abbr>`

Viết tắt.

```html
<abbr title="HyperText Markup Language">
    HTML
</abbr>
```

Khi hover có thể xem phần giải thích.

---

# 45. `<address>`

Thông tin liên hệ.

```html
<address>
    Email: example@gmail.com<br>
    TP. Hồ Chí Minh, Việt Nam
</address>
```

---

# 46. Comment trong HTML ⭐⭐

Comment:

```html
<!-- Đây là comment -->
```

Trình duyệt không hiển thị nội dung này.

Ví dụ:

```html
<!-- Header -->
<header>
    ...
</header>
```

---

# 47. Global Attributes – thuộc tính dùng ở nhiều thẻ ⭐⭐⭐

## `id`

```html
<div id="app"></div>
```

Dùng để định danh một phần tử.

Thông thường một `id` nên là duy nhất trong trang.

## `class`

```html
<div class="card"></div>
```

Nhiều phần tử có thể dùng cùng class:

```html
<div class="card"></div>
<div class="card"></div>
<div class="card"></div>
```

## `style`

Viết CSS trực tiếp:

```html
<p style="color: red;">
    Hello
</p>
```

Không nên lạm dụng trong project lớn.

## `title`

Tooltip khi hover:

```html
<button title="Xóa task">
    🗑
</button>
```

## `hidden`

Ẩn phần tử:

```html
<div hidden>
    Nội dung này đang bị ẩn.
</div>
```

## `data-*`

Lưu dữ liệu tùy chỉnh:

```html
<button
    data-id="123"
    data-category="work">
    Delete
</button>
```

JavaScript có thể đọc các thuộc tính `data-*`.

---

# 48. `aria-*` – Accessibility ⭐⭐

Ví dụ:

```html
<button aria-label="Đóng menu">
    ✕
</button>
```

Giúp các công cụ hỗ trợ như screen reader hiểu giao diện.

Ví dụ notification trong To-Do List:

```html
<div
    id="app-notification"
    class="app-notification"
    role="status"
    aria-live="polite"
    hidden>
</div>
```

Đây là ví dụ về accessibility.

---

# 49. Thuộc tính `role`

Xác định vai trò của phần tử.

```html
<div role="alert">
    Có lỗi xảy ra!
</div>
```

Nếu đã có semantic tag phù hợp thì thường nên dùng semantic tag trước thay vì tự thêm `role`.

---

# 50. Một số thẻ HTML khác

| Thẻ | Chức năng |
|---|---|
| `<canvas>` | Vùng vẽ bằng JavaScript |
| `<svg>` | Vector graphics |
| `<object>` | Nhúng tài nguyên |
| `<embed>` | Nhúng tài nguyên |
| `<template>` | HTML template chưa render |
| `<slot>` | Web Components |
| `<noscript>` | Nội dung khi JavaScript bị tắt |
| `<bdi>` | Cô lập hướng văn bản |
| `<bdo>` | Thay đổi hướng văn bản |
| `<ruby>` | Ruby annotation |
| `<wbr>` | Điểm có thể xuống dòng |

Những thẻ này không cần ưu tiên học ngay.

---

# 51. Các thẻ HTML cũ/không nên dùng

Có thể gặp trên Internet nhưng không nên dùng cho project mới:

```html
<center>
<font>
<marquee>
<big>
<strike>
```

Ví dụ cũ:

```html
<center>Hello</center>
```

Ngày nay nên dùng CSS:

```html
<div class="text-center">
    Hello
</div>
```

```css
.text-center {
    text-align: center;
}
```

---

# 52. Block vs Inline

Đây là khái niệm rất quan trọng khi học HTML + CSS.

## Một số block elements

```text
<div>
<p>
<h1> ... <h6>
<section>
<header>
<footer>
<main>
<ul>
<ol>
<table>
<form>
```

Thường chiếm một dòng riêng.

## Một số inline elements

```text
<span>
<a>
<strong>
<em>
<i>
<b>
<code>
<small>
```

Thường nằm cùng dòng với nội dung khác.

Ví dụ:

```html
<p>
    Tôi đang học
    <strong>HTML</strong>
    và
    <strong>CSS</strong>.
</p>
```

---

# 53. Ví dụ một trang web thực tế

```html
<!DOCTYPE html>

<html lang="vi">

<head>

    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0">

    <title>My Website</title>

    <link rel="stylesheet" href="style.css">

</head>

<body>

    <header>

        <h1>My Website</h1>

        <nav>
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/contact">Contact</a>
        </nav>

    </header>

    <main>

        <section>

            <h2>About me</h2>

            <p>
                Xin chào! Tôi đang học
                <strong>Computer Science</strong>.
            </p>

        </section>

        <section>

            <h2>Skills</h2>

            <ul>
                <li>C++</li>
                <li>HTML</li>
                <li>CSS</li>
                <li>JavaScript</li>
            </ul>

        </section>

        <section>

            <h2>Contact</h2>

            <form>

                <label for="email">
                    Email
                </label>

                <input
                    type="email"
                    id="email"
                    name="email"
                    placeholder="example@gmail.com"
                    required
                >

                <button type="submit">
                    Send
                </button>

            </form>

        </section>

    </main>

    <footer>

        <p>
            © 2026 My Website
        </p>

    </footer>

    <script
        src="script.js"
        defer>
    </script>

</body>

</html>
```

Đây là cấu trúc khá gần với cách tổ chức một website thực tế.

---

# 54. Thứ tự học HTML đề xuất

Không nên cố học hết tất cả các thẻ ngay.

## 🟢 Level 1 – Bắt buộc

Học thật chắc:

```text
html
head
body
title
meta
h1 → h6
p
div
span
a
img
ul
ol
li
```

## 🟡 Level 2 – Form

```text
form
label
input
button
textarea
select
option
```

Cùng với:

```text
required
placeholder
name
id
class
disabled
readonly
```

## 🟠 Level 3 – Semantic HTML

```text
header
nav
main
section
article
aside
footer
figure
figcaption
```

Đây là phần nên học kỹ nếu muốn làm web chuyên nghiệp.

## 🔵 Level 4 – Multimedia / nâng cao

```text
audio
video
iframe
picture
source
canvas
svg
details
summary
dialog
progress
meter
```

## 🟣 Level 5 – Accessibility + HTML nâng cao

```text
aria-*
role
data-*
template
slot
time
abbr
```

---

# 55. Quan trọng hơn việc nhớ tên thẻ

Không cần học HTML theo kiểu:

> "Thẻ `<bdi>` dùng để làm gì?"

Quan trọng hơn là học cách nhìn giao diện và suy nghĩ:

> **"Nội dung này về mặt ngữ nghĩa là gì?"**

Ví dụ giao diện To-Do List:

```text
┌───────────────────────────────────┐
│ ✏️ To-Do List App                 │
│ Organize your tasks...            │
│                    ☀ Light mode   │
├───────────────────────────────────┤
│ Add a Task                        │
│ [ Enter your task... ] [Add Task] │
│                                   │
│ Search & Filter                   │
│ [ Search... ] [ All ▼ ]           │
│                                   │
│ Task List                         │
│ □ Learn HTML              [🗑]     │
│ □ Learn CSS               [🗑]     │
├───────────────────────────────────┤
│ © 2026                            │
└───────────────────────────────────┘
```

Có thể tư duy thành:

```html
<body>

    <header>
        ...
    </header>

    <main>

        <section>
            Add Task
        </section>

        <section>
            Search & Filter
        </section>

        <section>
            Task List
        </section>

    </main>

    <footer>
        ...
    </footer>

</body>
```

Sau đó mới tiếp tục:

```text
HTML
 ↓
CSS
 ↓
JavaScript
 ↓
LocalStorage / API
 ↓
Backend
 ↓
Database
 ↓
Deploy
```

**Đây mới là tư duy quan trọng khi học web**, thay vì chỉ học thuộc danh sách các thẻ.
