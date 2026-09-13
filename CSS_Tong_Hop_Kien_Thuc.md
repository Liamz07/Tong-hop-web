# CSS — Tổng hợp kiến thức từ cơ bản đến thực tế

> Tài liệu này tập trung vào **cách hiểu CSS, cách chọn thuộc tính, cách xác định bố cục và cách áp dụng CSS vào project web thực tế**.  
> Ví dụ được xây dựng theo hướng phù hợp với người mới học HTML/CSS/JavaScript.

---

## Mục lục

1. [CSS là gì?](#1-css-là-gì)
2. [Cấu trúc một rule CSS](#2-cấu-trúc-một-rule-css)
3. [Cách nhúng CSS](#3-cách-nhúng-css)
4. [Selector](#4-selector)
5. [Cascade, specificity và inheritance](#5-cascade-specificity-và-inheritance)
6. [Đơn vị trong CSS](#6-đơn-vị-trong-css)
7. [Box Model](#7-box-model)
8. [Width, height và kích thước](#8-width-height-và-kích-thước)
9. [Margin, padding, border](#9-margin-padding-border)
10. [Màu sắc và background](#10-màu-sắc-và-background)
11. [Font và text](#11-font-và-text)
12. [Display](#12-display)
13. [Position](#13-position)
14. [Flexbox](#14-flexbox)
15. [CSS Grid](#15-css-grid)
16. [Overflow](#16-overflow)
17. [Shadow và border-radius](#17-shadow-và-border-radius)
18. [Pseudo-class và pseudo-element](#18-pseudo-class-và-pseudo-element)
19. [Transition và transform](#19-transition-và-transform)
20. [Animation](#20-animation)
21. [Responsive Web Design](#21-responsive-web-design)
22. [Media Query](#22-media-query)
23. [CSS Variables](#23-css-variables)
24. [Các hàm CSS thường dùng](#24-các-hàm-css-thường-dùng)
25. [Z-index](#25-z-index)
26. [Bố cục website được xác định như thế nào?](#26-bố-cục-website-được-xác-định-như-thế-nào)
27. [Quy trình thiết kế UI bằng CSS](#27-quy-trình-thiết-kế-ui-bằng-css)
28. [Ví dụ project thực tế: To-Do List](#28-ví-dụ-project-thực-tế-to-do-list)
29. [Ví dụ project thực tế: Dashboard quản lý chi tiêu](#29-ví-dụ-project-thực-tế-dashboard-quản-lý-chi-tiêu)
30. [Tổ chức file CSS](#30-tổ-chức-file-css)
31. [CSS Framework là gì?](#31-css-framework-là-gì)
32. [Bootstrap](#32-bootstrap)
33. [Tailwind CSS](#33-tailwind-css)
34. [So sánh CSS thuần, Bootstrap và Tailwind](#34-so-sánh-css-thuần-bootstrap-và-tailwind)
35. [Khi nào nên dùng framework?](#35-khi-nào-nên-dùng-framework)
36. [Lộ trình học CSS](#36-lộ-trình-học-css)
37. [Checklist CSS khi làm project](#37-checklist-css-khi-làm-project)

---

# 1. CSS là gì?

**CSS (Cascading Style Sheets)** là ngôn ngữ dùng để mô tả **cách HTML được hiển thị**.

HTML trả lời:

> Website có những thành phần gì?

CSS trả lời:

> Những thành phần đó trông như thế nào và nằm ở đâu?

Ví dụ:

```html
<button class="button">Add Task</button>
```

```css
.button {
    background: #2563eb;
    color: white;
    padding: 10px 16px;
    border-radius: 8px;
    border: none;
}
```

HTML tạo ra button.

CSS quyết định:

- màu
- kích thước
- khoảng cách
- bo góc
- vị trí
- hiệu ứng
- responsive

---

# 2. Cấu trúc một rule CSS

Cấu trúc cơ bản:

```css
selector {
    property: value;
}
```

Ví dụ:

```css
h1 {
    color: blue;
    font-size: 32px;
}
```

Trong đó:

- `h1`: selector
- `color`: property
- `blue`: value
- `font-size`: property
- `32px`: value

Một selector có thể có nhiều property:

```css
.card {
    width: 300px;
    padding: 20px;
    background-color: white;
    border-radius: 12px;
}
```

---

# 3. Cách nhúng CSS

## 3.1. Inline CSS

Viết trực tiếp trong HTML:

```html
<p style="color: red;">Hello</p>
```

Không nên sử dụng nhiều trong project lớn.

---

## 3.2. Internal CSS

Viết trong thẻ `<style>`:

```html
<style>
    p {
        color: red;
    }
</style>
```

Phù hợp với ví dụ nhỏ hoặc thử nghiệm.

---

## 3.3. External CSS

Tạo file:

```text
style.css
```

HTML:

```html
<link rel="stylesheet" href="style.css">
```

CSS:

```css
body {
    margin: 0;
}
```

**Đây là cách nên dùng cho project.**

---

# 4. Selector

## 4.1. Element selector

Chọn theo tên thẻ:

```css
p {
    color: gray;
}
```

Áp dụng cho tất cả `<p>`.

---

## 4.2. Class selector

```css
.card {
    padding: 20px;
}
```

HTML:

```html
<div class="card"></div>
```

Class là selector được sử dụng rất nhiều khi xây dựng UI.

---

## 4.3. ID selector

```css
#header {
    background: black;
}
```

HTML:

```html
<header id="header"></header>
```

ID thường dùng cho một phần tử duy nhất.

Trong CSS UI hiện đại, class thường được ưu tiên hơn ID.

---

## 4.4. Universal selector

```css
* {
    box-sizing: border-box;
}
```

`*` chọn tất cả phần tử.

Một thiết lập thường gặp:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

---

## 4.5. Group selector

```css
h1, h2, h3 {
    font-family: Arial, sans-serif;
}
```

---

## 4.6. Descendant selector

```css
.card p {
    color: gray;
}
```

Chọn `<p>` nằm bên trong `.card`.

---

## 4.7. Child selector

```css
.card > p {
    color: gray;
}
```

Chỉ chọn `<p>` là **con trực tiếp** của `.card`.

---

## 4.8. Attribute selector

```css
input[type="text"] {
    border: 1px solid gray;
}
```

---

# 5. Cascade, specificity và inheritance

CSS có chữ **Cascading** vì khi nhiều rule cùng tác động lên một phần tử, trình duyệt phải quyết định rule nào được áp dụng.

Ví dụ:

```css
p {
    color: blue;
}

.text {
    color: red;
}
```

```html
<p class="text">Hello</p>
```

`.text` có specificity cao hơn `p`, nên chữ thường sẽ có màu đỏ.

Thứ tự khái quát:

```text
Inline style
    ↓
ID
    ↓
Class / attribute / pseudo-class
    ↓
Element / pseudo-element
```

Không nên lạm dụng:

```css
!important
```

Hãy cố gắng tổ chức selector rõ ràng thay vì giải quyết mọi vấn đề bằng `!important`.

---

## Inheritance

Một số thuộc tính có thể được kế thừa từ phần tử cha.

Ví dụ:

```css
body {
    font-family: Arial, sans-serif;
    color: #222;
}
```

Nhiều phần tử con sẽ kế thừa `font-family` và `color`.

---

# 6. Đơn vị trong CSS

## 6.1. `px`

Đơn vị cố định tương đối với CSS pixel.

```css
font-size: 16px;
padding: 20px;
```

Dễ hiểu và thường dùng cho:

- border
- icon
- kích thước nhỏ
- một số khoảng cách cụ thể

---

## 6.2. `%`

Tỷ lệ dựa trên phần tử chứa.

```css
width: 50%;
```

Ví dụ:

```css
.container {
    width: 80%;
}
```

---

## 6.3. `rem`

Dựa trên `font-size` của phần tử gốc (`html`).

```css
font-size: 1rem;
```

Nếu mặc định browser là 16px:

```text
1rem = 16px
2rem = 32px
```

`rem` rất hữu ích cho typography và spacing.

---

## 6.4. `em`

Dựa vào font-size của phần tử hiện tại/ngữ cảnh kế thừa.

```css
padding: 1em;
```

`em` có thể gây khó theo dõi khi lồng nhiều cấp.

---

## 6.5. `vw` và `vh`

Dựa trên kích thước viewport.

```css
width: 50vw;
height: 100vh;
```

Ví dụ:

```css
.hero {
    min-height: 100vh;
}
```

---

## 6.6. `vmin`, `vmax`

```css
width: 50vmin;
```

Dựa trên cạnh nhỏ/lớn hơn của viewport.

---

# 7. Box Model

Mọi phần tử HTML có thể được hình dung như một chiếc hộp:

```text
┌───────────────────────────────┐
│            margin             │
│  ┌─────────────────────────┐  │
│  │         border          │  │
│  │  ┌───────────────────┐  │  │
│  │  │      padding      │  │  │
│  │  │  ┌─────────────┐  │  │  │
│  │  │  │   content   │  │  │  │
│  │  │  └─────────────┘  │  │  │
│  │  └───────────────────┘  │  │
│  └─────────────────────────┘  │
└───────────────────────────────┘
```

Gồm:

```text
Content
Padding
Border
Margin
```

---

# 8. Width, height và kích thước

## `width`

```css
.card {
    width: 300px;
}
```

## `height`

```css
.card {
    height: 200px;
}
```

## `min-width`

Kích thước tối thiểu:

```css
.container {
    min-width: 300px;
}
```

## `max-width`

Rất hữu ích khi xây layout:

```css
.container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
}
```

Ý nghĩa:

- màn hình nhỏ → dùng gần như toàn bộ chiều rộng
- màn hình lớn → không kéo quá 1200px
- `margin: 0 auto` → căn giữa

## `min-height`

```css
.card {
    min-height: 200px;
}
```

---

# 9. Margin, padding, border

## Margin

Khoảng cách **bên ngoài** phần tử:

```css
.card {
    margin: 20px;
}
```

Có thể chỉ định:

```css
margin-top: 10px;
margin-right: 20px;
margin-bottom: 10px;
margin-left: 20px;
```

Hoặc:

```css
margin: 10px 20px;
```

Nghĩa là:

```text
top/bottom = 10px
left/right = 20px
```

---

## Padding

Khoảng cách **từ content đến border**:

```css
.card {
    padding: 20px;
}
```

---

## Border

```css
.card {
    border: 1px solid #ddd;
}
```

Các thành phần:

```css
border-width: 1px;
border-style: solid;
border-color: #ddd;
```

---

## `box-sizing`

Nên thiết lập:

```css
* {
    box-sizing: border-box;
}
```

Khi đó:

```css
width: 300px;
padding: 20px;
border: 1px solid;
```

`width` đã bao gồm padding và border.

Điều này giúp việc tính kích thước dễ hơn.

---

# 10. Màu sắc và background

## `color`

Màu chữ:

```css
p {
    color: #333;
}
```

## `background-color`

```css
body {
    background-color: #f5f5f5;
}
```

## `background-image`

```css
.hero {
    background-image: url("hero.jpg");
}
```

## `background-size`

```css
.hero {
    background-size: cover;
}
```

`cover` thường dùng cho ảnh background cần phủ kín khu vực.

## `background-position`

```css
.hero {
    background-position: center;
}
```

## `background-repeat`

```css
background-repeat: no-repeat;
```

---

# 11. Font và text

## `font-family`

```css
body {
    font-family: Arial, sans-serif;
}
```

Có thể khai báo fallback:

```css
body {
    font-family: "Inter", Arial, sans-serif;
}
```

Nếu máy không có Inter → dùng Arial.

---

## `font-size`

```css
h1 {
    font-size: 32px;
}
```

---

## `font-weight`

```css
h1 {
    font-weight: 700;
}
```

Một số giá trị:

```text
400 → normal
500 → medium
600 → semibold
700 → bold
```

---

## `line-height`

Khoảng cách giữa các dòng:

```css
p {
    line-height: 1.6;
}
```

Đặc biệt quan trọng với đoạn văn.

---

## `text-align`

```css
text-align: center;
```

Các giá trị:

```text
left
center
right
justify
```

---

## `text-decoration`

```css
a {
    text-decoration: none;
}
```

---

## `text-transform`

```css
.title {
    text-transform: uppercase;
}
```

---

## `letter-spacing`

```css
.logo {
    letter-spacing: 1px;
}
```

---

## `white-space`

```css
white-space: nowrap;
```

Ngăn text xuống dòng.

---

## `text-overflow`

Thường kết hợp với:

```css
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
```

Kết quả:

```text
Một đoạn văn bản rất dài...
```

---

# 12. Display

## `block`

```css
display: block;
```

Phần tử thường chiếm toàn bộ chiều ngang khả dụng.

Ví dụ:

```text
[       div       ]
[       div       ]
```

---

## `inline`

```css
display: inline;
```

Nằm cùng dòng với nội dung khác.

---

## `inline-block`

```css
display: inline-block;
```

Vẫn nằm cùng dòng nhưng có thể kiểm soát width/height.

---

## `none`

```css
display: none;
```

Phần tử không được hiển thị và không chiếm không gian layout.

---

## `flex`

```css
display: flex;
```

Dùng để xây dựng layout một chiều.

---

## `grid`

```css
display: grid;
```

Dùng để xây dựng layout hai chiều.

---

# 13. Position

## `static`

Mặc định.

```css
position: static;
```

---

## `relative`

```css
.card {
    position: relative;
}
```

Phần tử vẫn nằm trong flow bình thường nhưng có thể làm mốc cho phần tử `absolute`.

---

## `absolute`

```css
.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

Phần tử được định vị tương đối với containing block phù hợp, thường là ancestor có `position` khác `static`.

Ví dụ:

```css
.card {
    position: relative;
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

---

## `fixed`

```css
.button {
    position: fixed;
    bottom: 20px;
    right: 20px;
}
```

Phần tử cố định theo viewport.

Thường dùng cho:

- floating button
- chat button
- nút scroll top

---

## `sticky`

```css
header {
    position: sticky;
    top: 0;
}
```

Có thể "dính" khi scroll đến vị trí phù hợp.

---

# 14. Flexbox

Flexbox là một trong những công cụ quan trọng nhất để xây layout.

Bắt đầu:

```css
.container {
    display: flex;
}
```

Ví dụ:

```html
<div class="container">
    <div>Logo</div>
    <div>Menu</div>
    <div>Login</div>
</div>
```

```css
.container {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
```

Kết quả:

```text
Logo                  Menu    Login
```

---

## `flex-direction`

```css
flex-direction: row;
```

Mặc định.

```css
flex-direction: column;
```

Xếp theo chiều dọc.

---

## `justify-content`

Điều chỉnh theo **main axis**.

```css
justify-content: center;
```

Các giá trị thường gặp:

```text
flex-start
center
flex-end
space-between
space-around
space-evenly
```

---

## `align-items`

Điều chỉnh theo **cross axis**:

```css
align-items: center;
```

---

## `gap`

Khoảng cách giữa các item:

```css
.container {
    display: flex;
    gap: 16px;
}
```

Thường tốt hơn việc tự đặt margin cho từng item.

---

## `flex-wrap`

Cho phép xuống dòng:

```css
.container {
    display: flex;
    flex-wrap: wrap;
}
```

---

## `flex`

```css
.item {
    flex: 1;
}
```

Cho phép các item chia không gian.

---

## Ứng dụng thực tế: Navbar

```css
.navbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 24px;
}
```

---

# 15. CSS Grid

Grid phù hợp với layout dạng hàng + cột.

Ví dụ:

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 20px;
}
```

Kết quả:

```text
┌───────┐ ┌───────┐ ┌───────┐
│ Card  │ │ Card  │ │ Card  │
└───────┘ └───────┘ └───────┘
```

---

## `grid-template-columns`

```css
grid-template-columns: 200px 1fr;
```

Ví dụ dashboard:

```text
┌──────────┬──────────────────────────┐
│ Sidebar  │ Main                     │
│ 200px    │ 1fr                      │
└──────────┴──────────────────────────┘
```

---

## `repeat()`

```css
grid-template-columns: repeat(3, 1fr);
```

Tương đương:

```css
grid-template-columns: 1fr 1fr 1fr;
```

---

## `minmax()`

```css
grid-template-columns: repeat(
    auto-fit,
    minmax(250px, 1fr)
);
```

Đây là một kỹ thuật rất hữu ích để tạo grid responsive.

---

## `grid-column`

Cho item chiếm nhiều cột:

```css
.big-card {
    grid-column: span 2;
}
```

---

# 16. Overflow

Kiểm soát nội dung vượt khỏi kích thước phần tử.

```css
.box {
    overflow: hidden;
}
```

Các giá trị:

```text
visible
hidden
scroll
auto
```

Ví dụ:

```css
.task-list {
    max-height: 400px;
    overflow-y: auto;
}
```

Task list sẽ scroll theo chiều dọc khi quá cao.

---

# 17. Shadow và border-radius

## `border-radius`

```css
.card {
    border-radius: 12px;
}
```

Bo góc.

---

## `box-shadow`

```css
.card {
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}
```

Cấu trúc:

```text
offset-x
offset-y
blur
spread
color
```

Shadow nên dùng vừa phải. Quá nhiều shadow khiến UI nặng và rối.

---

# 18. Pseudo-class và pseudo-element

## `:hover`

```css
.button:hover {
    background-color: #1d4ed8;
}
```

Khi đưa chuột lên button.

---

## `:focus`

```css
input:focus {
    outline: 2px solid blue;
}
```

Khi input được focus.

---

## `:active`

```css
.button:active {
    transform: scale(0.98);
}
```

Khi đang nhấn.

---

## `:disabled`

```css
button:disabled {
    opacity: 0.5;
}
```

---

## `:first-child`

```css
li:first-child {
    font-weight: bold;
}
```

---

## `::before`

```css
.title::before {
    content: "★ ";
}
```

---

## `::after`

```css
.title::after {
    content: "";
    display: block;
    width: 40px;
    height: 3px;
}
```

---

# 19. Transition và transform

## `transition`

Tạo chuyển đổi mượt:

```css
.button {
    background: blue;
    transition: 0.2s;
}

.button:hover {
    background: darkblue;
}
```

Nên chỉ rõ property khi cần:

```css
transition: background-color 0.2s ease,
            transform 0.2s ease;
```

---

## `transform`

### Scale

```css
.card:hover {
    transform: scale(1.02);
}
```

### Translate

```css
.card:hover {
    transform: translateY(-4px);
}
```

### Rotate

```css
.icon {
    transform: rotate(45deg);
}
```

---

# 20. Animation

Ví dụ:

```css
@keyframes fadeIn {
    from {
        opacity: 0;
    }

    to {
        opacity: 1;
    }
}

.card {
    animation: fadeIn 0.4s ease;
}
```

Animation phù hợp cho:

- loading
- notification
- modal
- xuất hiện component
- micro-interaction

Không nên animation mọi thứ.

---

# 21. Responsive Web Design

Responsive nghĩa là giao diện thích ứng với kích thước màn hình.

Ví dụ:

```text
Desktop
┌────────────┬───────────────────┐
│ Sidebar    │ Main              │
└────────────┴───────────────────┘

Mobile
┌───────────────────────────────┐
│ Main                          │
└───────────────────────────────┘
```

Không nên thiết kế:

```css
width: 1200px;
```

một cách cứng nhắc cho mọi màn hình.

Nên sử dụng:

```css
width: 100%;
max-width: 1200px;
```

và media query khi cần.

---

# 22. Media Query

Ví dụ:

```css
@media (max-width: 768px) {
    .sidebar {
        display: none;
    }

    .main {
        width: 100%;
    }
}
```

Ý nghĩa:

> Khi màn hình ≤ 768px thì áp dụng các rule bên trong.

---

## Mobile-first

Một cách tiếp cận phổ biến:

```css
.card {
    width: 100%;
}

@media (min-width: 768px) {
    .card {
        width: 50%;
    }
}

@media (min-width: 1024px) {
    .card {
        width: 33.333%;
    }
}
```

Tức là:

```text
Mobile
  ↓
Tablet
  ↓
Desktop
```

---

# 23. CSS Variables

Khai báo:

```css
:root {
    --primary-color: #2563eb;
    --background-color: #f8fafc;
    --text-color: #1e293b;
    --radius: 12px;
}
```

Sử dụng:

```css
.button {
    background-color: var(--primary-color);
    border-radius: var(--radius);
}
```

Lợi ích:

Nếu muốn đổi màu chính:

```css
--primary-color: #7c3aed;
```

không cần sửa hàng chục selector.

---

## Dark mode

Ví dụ:

```css
:root {
    --background-color: #ffffff;
    --text-color: #111827;
}

.dark {
    --background-color: #111827;
    --text-color: #f9fafb;
}
```

```css
body {
    background: var(--background-color);
    color: var(--text-color);
}
```

JavaScript có thể thêm/xóa class `.dark` trên `<body>`.

---

# 24. Các hàm CSS thường dùng

## `calc()`

Tính toán:

```css
width: calc(100% - 40px);
```

Ví dụ:

```css
.main {
    width: calc(100% - 240px);
}
```

---

## `min()`

```css
width: min(90%, 1200px);
```

---

## `max()`

```css
padding: max(16px, 3vw);
```

---

## `clamp()`

Rất hữu ích cho responsive typography:

```css
h1 {
    font-size: clamp(2rem, 5vw, 4rem);
}
```

Nghĩa là:

```text
minimum = 2rem
preferred = 5vw
maximum = 4rem
```

---

# 25. Z-index

Điều chỉnh thứ tự chồng lớp:

```css
.modal {
    position: fixed;
    z-index: 1000;
}
```

Ví dụ:

```text
z-index: 1000 → Modal
z-index: 100  → Navbar
z-index: 1    → Card
```

`z-index` chỉ hoạt động theo các quy tắc stacking context; không nên cứ tăng lên `999999` để giải quyết vấn đề mà chưa hiểu stacking context.

---

# 26. Bố cục website được xác định như thế nào?

Đây là phần rất quan trọng.

**Không nên bắt đầu bằng việc viết CSS ngay.**

Trước tiên hãy chia website thành các khu vực.

Ví dụ một trang dashboard:

```text
┌───────────────────────────────────────────┐
│ Header                                    │
├──────────────┬────────────────────────────┤
│              │                            │
│ Sidebar      │ Main                       │
│              │                            │
│              │ ┌──────┐ ┌──────┐ ┌────┐ │
│              │ │Card 1│ │Card 2│ │Card│ │
│              │ └──────┘ └──────┘ └────┘ │
│              │                            │
│              │ ┌────────────────────────┐ │
│              │ │ Chart                  │ │
│              │ └────────────────────────┘ │
└──────────────┴────────────────────────────┘
```

Sau đó quyết định công cụ layout:

```text
Toàn trang
    ↓
CSS Grid

Header
    ↓
Flexbox

Sidebar + Main
    ↓
Grid

Các Card
    ↓
Grid

Nội dung bên trong Card
    ↓
Flexbox
```

---

## Nguyên tắc quan trọng

Đừng nghĩ:

> "Mình phải đặt thẻ này ở `left: 300px`."

Hãy nghĩ:

> "Phần này thuộc layout nào?"

Ví dụ không nên:

```css
.card {
    position: absolute;
    left: 430px;
    top: 180px;
}
```

cho một layout thông thường.

Nên:

```css
.dashboard {
    display: grid;
    grid-template-columns: 240px 1fr;
}
```

CSS sẽ tự tính vị trí dựa trên cấu trúc.

---

# 27. Quy trình thiết kế UI bằng CSS

Một workflow tốt:

```text
1. Xác định mục đích website
          ↓
2. Xác định các trang
          ↓
3. Phác thảo wireframe
          ↓
4. Chia layout
          ↓
5. Xác định component
          ↓
6. Chọn typography
          ↓
7. Chọn màu sắc
          ↓
8. Viết HTML semantic
          ↓
9. CSS layout
          ↓
10. CSS component
          ↓
11. Responsive
          ↓
12. Hover / focus / animation
          ↓
13. Kiểm tra trên nhiều kích thước
```

---

## 27.1. Wireframe

Trước tiên chỉ cần:

```text
Header
Sidebar
Main
Card
Button
Footer
```

Chưa cần màu sắc đẹp.

---

## 27.2. Xác định component

Ví dụ To-Do List:

```text
App
├── Header
│   ├── Logo
│   ├── Description
│   └── Theme Toggle
│
├── Main
│   ├── Add Task
│   ├── Search
│   ├── Filter
│   └── Task List
│       └── Task Card
│
└── Footer
```

---

## 27.3. Design tokens

Xác định trước:

```css
:root {
    --primary: #2563eb;
    --danger: #dc2626;

    --bg: #f8fafc;
    --surface: #ffffff;

    --text: #1e293b;
    --muted: #64748b;

    --radius-sm: 6px;
    --radius-md: 10px;
    --radius-lg: 16px;

    --space-sm: 8px;
    --space-md: 16px;
    --space-lg: 24px;
}
```

Sau đó tái sử dụng.

---

# 28. Ví dụ project thực tế: To-Do List

Giả sử HTML:

```html
<body>
    <header class="header">
        <h1>✏️ To-Do List App</h1>
        <p>Organize your tasks, simplify your day.</p>
        <button class="theme-toggle">☀ Light mode</button>
    </header>

    <main class="main">
        <section class="add-task">
            <h2>Add a Task</h2>

            <form class="task-form">
                <input type="text" placeholder="Enter your task...">
                <button type="submit">Add Task</button>
            </form>
        </section>

        <section class="task-list-section">
            <h2>Your Tasks</h2>

            <ul class="task-list">
                <li class="task-item">
                    <span>Learn CSS</span>
                    <button>Delete</button>
                </li>
            </ul>
        </section>
    </main>
</body>
```

---

## Bước 1: Reset cơ bản

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
}
```

---

## Bước 2: Body

```css
body {
    min-height: 100vh;
    background: #f8fafc;
    color: #1e293b;
}
```

---

## Bước 3: Header

```css
.header {
    padding: 32px 20px;
    text-align: center;
}
```

---

## Bước 4: Main container

```css
.main {
    width: 100%;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
}
```

---

## Bước 5: Form

```css
.task-form {
    display: flex;
    gap: 12px;
}

.task-form input {
    flex: 1;
}
```

---

## Bước 6: Task item

```css
.task-item {
    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 16px;

    background: white;
    border-radius: 10px;
    border: 1px solid #e2e8f0;
}
```

---

## Bước 7: Responsive

```css
@media (max-width: 600px) {
    .task-form {
        flex-direction: column;
    }

    .task-form button {
        width: 100%;
    }
}
```

Điểm quan trọng:

Không cần `position: absolute` để căn từng phần tử.

Layout được giải quyết bằng:

```text
container
    ↓
max-width
    ↓
margin auto
    ↓
flex
    ↓
gap
    ↓
media query
```

---

# 29. Ví dụ project thực tế: Dashboard quản lý chi tiêu

Một dashboard có thể chia:

```text
Dashboard
│
├── Sidebar
│
└── Main
    │
    ├── Header
    │
    ├── Summary Cards
    │
    ├── Charts
    │
    └── Recent Transactions
```

Layout:

```css
.dashboard {
    display: grid;
    grid-template-columns: 240px 1fr;
    min-height: 100vh;
}
```

Cards:

```css
.summary-cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}
```

Responsive:

```css
@media (max-width: 768px) {
    .dashboard {
        grid-template-columns: 1fr;
    }

    .sidebar {
        display: none;
    }

    .summary-cards {
        grid-template-columns: 1fr;
    }
}
```

---

## Khi nào dùng Flexbox và Grid?

Quy tắc đơn giản:

```text
Flexbox
→ Một chiều
→ Hàng hoặc cột
→ Navbar
→ Button group
→ Nội dung bên trong card

Grid
→ Hai chiều
→ Hàng + cột
→ Dashboard
→ Gallery
→ Card layout
```

Không phải quy tắc tuyệt đối, nhưng rất hữu ích khi mới học.

---

# 30. Tổ chức file CSS

Project nhỏ:

```text
project/
├── index.html
├── style.css
└── script.js
```

Project lớn hơn:

```text
project/
├── index.html
├── css/
│   ├── reset.css
│   ├── variables.css
│   ├── layout.css
│   ├── components.css
│   └── responsive.css
│
├── js/
│   ├── main.js
│   └── ...
│
└── assets/
```

Một cách khác là tổ chức theo component:

```text
css/
├── base.css
├── layout.css
├── navbar.css
├── sidebar.css
├── card.css
├── form.css
└── modal.css
```

Không có một cấu trúc duy nhất bắt buộc. Quan trọng là project lớn phải dễ tìm và dễ sửa.

---

# 31. CSS Framework là gì?

CSS Framework là tập hợp các CSS/component được xây dựng sẵn để giúp phát triển giao diện nhanh hơn.

Một số framework/library phổ biến:

```text
Bootstrap
Tailwind CSS
Bulma
Foundation
```

Ngoài ra còn có UI component libraries/ecosystems như:

```text
Material UI
Ant Design
```

Đặc biệt thường gặp khi dùng React.

---

# 32. Bootstrap

Bootstrap cung cấp hệ thống:

- Grid
- Button
- Form
- Card
- Navbar
- Modal
- Alert
- Responsive utilities

Ví dụ:

```html
<button class="btn btn-primary">
    Add Task
</button>
```

Card:

```html
<div class="card">
    <div class="card-body">
        <h5 class="card-title">Learn CSS</h5>
        <p class="card-text">Practice Flexbox and Grid.</p>
    </div>
</div>
```

Grid:

```html
<div class="row">
    <div class="col-md-4">Card 1</div>
    <div class="col-md-4">Card 2</div>
    <div class="col-md-4">Card 3</div>
</div>
```

Bootstrap phù hợp khi muốn:

> Có UI khá hoàn chỉnh và phát triển nhanh.

---

# 33. Tailwind CSS

Tailwind sử dụng utility classes.

Ví dụ:

```html
<button
    class="px-4 py-2 rounded-lg bg-blue-600 text-white hover:bg-blue-700">
    Add Task
</button>
```

Có thể hiểu:

```text
px-4       → padding ngang
py-2       → padding dọc
rounded-lg → bo góc
bg-blue-600 → background
text-white → màu chữ
hover:...  → trạng thái hover
```

Grid:

```html
<div class="grid grid-cols-3 gap-4">
    ...
</div>
```

Responsive:

```html
<div class="grid grid-cols-1 md:grid-cols-3">
    ...
</div>
```

Tailwind rất mạnh khi muốn:

- xây UI nhanh
- tùy biến cao
- responsive
- tránh phải tự đặt tên class cho mọi utility nhỏ

Nhược điểm là HTML có thể chứa rất nhiều class.

---

# 34. So sánh CSS thuần, Bootstrap và Tailwind

| Tiêu chí | CSS thuần | Bootstrap | Tailwind |
|---|---|---|---|
| Dễ hiểu CSS | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| Tốc độ làm UI | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Tùy biến | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Học CSS | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| Component có sẵn | Ít | Nhiều | Ít hơn Bootstrap |
| Responsive | Tự làm | Có sẵn | Có sẵn |
| Phù hợp người mới học CSS | Rất tốt | Tốt | Tốt sau khi hiểu CSS |
| Phù hợp prototype | Tùy | Rất tốt | Rất tốt |

---

# 35. Khi nào nên dùng framework?

## Dùng CSS thuần khi:

- đang học CSS
- project nhỏ
- muốn hiểu layout
- cần thiết kế UI hoàn toàn riêng

## Dùng Bootstrap khi:

- cần làm nhanh
- cần nhiều component có sẵn
- muốn hệ thống grid và responsive thuận tiện

## Dùng Tailwind khi:

- muốn xây UI tùy biến
- project có design system rõ
- muốn utility-first
- làm frontend hiện đại

---

## Một workflow rất tốt

Không nhất thiết:

```text
CSS hoặc Framework
```

Mà có thể:

```text
CSS fundamentals
      ↓
CSS thuần
      ↓
Hiểu Flexbox + Grid + Responsive
      ↓
Bootstrap / Tailwind
      ↓
React / Vue
```

Framework **không thay thế kiến thức CSS**.

Nếu hiểu CSS, bạn sẽ học framework nhanh hơn.

---

# 36. Lộ trình học CSS

## Level 1 — Cơ bản

Học:

```text
Selector
Property / Value
Color
Background
Font
Margin
Padding
Border
Box Model
Width / Height
```

---

## Level 2 — Layout

Học thật chắc:

```text
display
Flexbox
Grid
position
overflow
```

Đặc biệt:

```text
Flexbox
Grid
```

là hai phần cực kỳ quan trọng.

---

## Level 3 — UI

Học:

```text
border-radius
box-shadow
hover
focus
transition
transform
animation
```

---

## Level 4 — Responsive

Học:

```text
%
rem
vw / vh
max-width
min-width
media query
mobile-first
clamp()
```

---

## Level 5 — Maintainable CSS

Học:

```text
CSS Variables
Component-based CSS
Naming convention
File organization
Design tokens
Specificity
Cascade
```

---

## Level 6 — Framework

Sau khi đã vững CSS:

```text
Bootstrap
      hoặc
Tailwind CSS
```

Không cần học tất cả framework.

---

# 37. Checklist CSS khi làm project

## Trước khi code

- [ ] Xác định các trang
- [ ] Xác định layout
- [ ] Vẽ wireframe
- [ ] Xác định component
- [ ] Chọn font
- [ ] Chọn màu
- [ ] Xác định spacing
- [ ] Xác định breakpoint

## Khi code

- [ ] Có `box-sizing: border-box`
- [ ] Dùng class rõ ràng
- [ ] Hạn chế `!important`
- [ ] Ưu tiên Flexbox/Grid cho layout
- [ ] Hạn chế absolute positioning cho layout chính
- [ ] Dùng `gap` khi phù hợp
- [ ] Dùng `max-width` cho content
- [ ] Tái sử dụng CSS Variables

## Responsive

- [ ] Kiểm tra mobile
- [ ] Kiểm tra tablet
- [ ] Kiểm tra desktop
- [ ] Kiểm tra text dài
- [ ] Kiểm tra button
- [ ] Kiểm tra form
- [ ] Kiểm tra navigation

## Accessibility

- [ ] Có focus state
- [ ] Màu chữ đủ tương phản
- [ ] Không chỉ dùng màu để truyền đạt thông tin
- [ ] Button/link có kích thước dễ thao tác
- [ ] Không xóa outline focus một cách tùy tiện

---

# 38. Những thuộc tính CSS nên nhớ trước tiên

Nếu mới học, **không cần học thuộc hàng trăm thuộc tính**.

Hãy ưu tiên:

```text
box-sizing
width
height
max-width
min-height

margin
padding
border
border-radius

color
background
font-family
font-size
font-weight
line-height
text-align

display
position
top
right
bottom
left
z-index

flex
flex-direction
justify-content
align-items
flex-wrap
gap

grid
grid-template-columns
grid-template-rows
grid-column
grid-row
gap

overflow

opacity

transition
transform

@media
```

Quan trọng nhất vẫn là **biết thuộc tính dùng để giải quyết vấn đề layout nào**, thay vì học thuộc tên.

---

# 39. Tư duy CSS quan trọng nhất

Khi nhìn một giao diện, hãy đặt câu hỏi theo thứ tự:

### Câu 1: Có những khu vực nào?

```text
Header
Sidebar
Main
Footer
```

### Câu 2: Quan hệ giữa chúng là gì?

```text
Sidebar | Main
```

→ Có thể dùng Grid.

### Câu 3: Các phần tử bên trong nằm theo hướng nào?

```text
Logo —— Menu —— Button
```

→ Flexbox.

### Câu 4: Khoảng cách giữa chúng bao nhiêu?

→ `padding`, `margin`, `gap`.

### Câu 5: Kích thước có cố định không?

→ `width`, `max-width`, `%`, `rem`, `minmax()`...

### Câu 6: Khi màn hình nhỏ thì chuyện gì xảy ra?

→ Responsive + Media Query.

### Câu 7: Đây có phải một component có thể tái sử dụng không?

→ Tách class/component.

---

# 40. Ví dụ tư duy hoàn chỉnh

Giả sử muốn tạo:

```text
┌─────────────────────────────────────┐
│ Header                              │
├──────────────┬──────────────────────┤
│ Sidebar      │ Main                 │
│              │                      │
│              │ ┌────┐ ┌────┐ ┌────┐│
│              │ │Card│ │Card│ │Card││
│              │ └────┘ └────┘ └────┘│
│              │                      │
└──────────────┴──────────────────────┘
```

Không nên bắt đầu bằng:

```css
left: 300px;
top: 100px;
```

Mà tư duy:

```text
Toàn bộ dashboard
        ↓
      Grid
        ↓
┌───────┴────────┐
Sidebar          Main
                  ↓
                Grid
                  ↓
             3 Card columns
                  ↓
             Card nội bộ
                  ↓
                Flex
```

CSS:

```css
.dashboard {
    display: grid;
    grid-template-columns: 240px 1fr;
}

.cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}

.card {
    display: flex;
    flex-direction: column;
    gap: 12px;
}
```

Đây chính là tư duy **layout → component → style**, thay vì **tọa độ → sửa từng phần tử**.

---

# 41. Kết luận

CSS không chỉ là:

```text
color
font-size
background
```

Mà có thể chia thành các nhóm lớn:

```text
CSS
│
├── Selector
│
├── Box Model
│
├── Typography
│
├── Color / Background
│
├── Layout
│   ├── Normal Flow
│   ├── Flexbox
│   ├── Grid
│   └── Position
│
├── Responsive
│
├── UI Effects
│   ├── Shadow
│   ├── Radius
│   ├── Transition
│   └── Animation
│
├── Maintainability
│   ├── Variables
│   ├── Components
│   └── File organization
│
└── Framework
    ├── Bootstrap
    └── Tailwind CSS
```

Nếu mục tiêu là **tự xây dựng website**, thứ tự ưu tiên nên là:

```text
HTML
 ↓
CSS cơ bản
 ↓
Box Model
 ↓
Flexbox
 ↓
Grid
 ↓
Position
 ↓
Responsive
 ↓
CSS Variables
 ↓
UI/UX
 ↓
Bootstrap / Tailwind
 ↓
JavaScript
 ↓
Framework frontend
```

> **Nguyên tắc quan trọng nhất:**  
> Đừng cố nhớ tất cả thuộc tính CSS. Hãy học cách nhìn một giao diện và chuyển nó thành **layout → component → spacing → typography → responsive → interaction**.
