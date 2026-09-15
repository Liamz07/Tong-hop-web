# JavaScript Chuyên Sâu & Thực Tiễn — Full Guide

> Tài liệu tổng hợp JavaScript theo hướng **học để làm project web thực tế**.  
> Trọng tâm: JavaScript hiện đại (ES6+), DOM, Event, Array, Async, API, Storage, Modules, Error Handling, Performance, Security và kiến trúc project.

---

## Mục lục

1. [Biến, Scope & Hoisting](#1-biến-scope--hoisting)
2. [Kiểu dữ liệu & Toán tử](#2-kiểu-dữ-liệu--toán-tử)
3. [Function & Arrow Function](#3-function--arrow-function)
4. [Object & Destructuring](#4-object--destructuring)
5. [Array Processing](#5-array-processing)
6. [String, Number & Date](#6-string-number--date)
7. [DOM](#7-dom)
8. [Event Handling](#8-event-handling)
9. [Form & Validation](#9-form--validation)
10. [Event Loop & Bất đồng bộ](#10-event-loop--bất-đồng-bộ)
11. [Promise & Async/Await](#11-promise--asyncawait)
12. [Fetch API & REST API](#12-fetch-api--rest-api)
13. [JSON](#13-json)
14. [LocalStorage, SessionStorage & Cookie](#14-localstorage-sessionstorage--cookie)
15. [Modules](#15-modules)
16. [Error Handling](#16-error-handling)
17. [Debounce & Throttle](#17-debounce--throttle)
18. [Performance & DOM Optimization](#18-performance--dom-optimization)
19. [Closures](#19-closures)
20. [this, call, apply, bind](#20-this-call-apply-bind)
21. [Prototype & Class](#21-prototype--class)
22. [Map, Set, WeakMap, WeakSet](#22-map-set-weakmap-weakset)
23. [Regular Expression](#23-regular-expression)
24. [Browser APIs hữu ích](#24-browser-apis-hữu-ích)
25. [Security cơ bản](#25-security-cơ-bản)
26. [Separation of Concerns & Project Architecture](#26-separation-of-concerns--project-architecture)
27. [Quản lý State](#27-quản-lý-state)
28. [Các Pattern thực tế cho Web App](#28-các-pattern-thực-tế-cho-web-app)
29. [Debug & DevTools](#29-debug--devtools)
30. [Checklist JavaScript khi làm Project](#30-checklist-javascript-khi-làm-project)
31. [Lộ trình học JavaScript để làm Project](#31-lộ-trình-học-javascript-để-làm-project)

---

# 1. Biến, Scope & Hoisting

## 1.1. `var`, `let`, `const`

| Từ khóa | Scope | Re-assign | Re-declare |
|---|---|---:|---:|
| `var` | Function | Có | Có |
| `let` | Block | Có | Không |
| `const` | Block | Không | Không |

```js
const name = "Minh";
let age = 20;

age = 21;
```

### Quy tắc thực tế

> **Ưu tiên `const` → dùng `let` khi cần thay đổi giá trị → hạn chế `var`.**

---

## 1.2. Scope

### Global Scope

```js
const appName = "Todo App";

function showName() {
    console.log(appName);
}
```

`appName` có thể được truy cập trong nhiều phạm vi bên dưới.

### Function Scope

```js
function test() {
    var x = 10;
}

console.log(x); // ReferenceError
```

### Block Scope

```js
if (true) {
    let x = 10;
    const y = 20;
}

console.log(x); // ReferenceError
```

---

## 1.3. Hoisting

JavaScript xử lý khai báo trước khi thực thi code theo cơ chế hoisting.

```js
console.log(a);
var a = 10;
```

Với `var`, biến được hoist nhưng giá trị ban đầu là `undefined`.

Với `let`/`const`:

```js
console.log(a);
let a = 10;
```

→ `ReferenceError` do biến đang ở **Temporal Dead Zone (TDZ)**.

### Cần nhớ

- Hoisting không có nghĩa là JavaScript "di chuyển code" theo nghĩa đen.
- `let`/`const` cũng được hoist về mặt cơ chế, nhưng không thể truy cập trước khai báo do TDZ.
- Function declaration có thể được gọi trước vị trí khai báo.

---

## 1.4. `Object.freeze()`

```js
const CONFIG = Object.freeze({
    API_ENDPOINT: "/api",
    RETRIES: 3
});
```

`Object.freeze()` ngăn việc thêm, xóa hoặc thay đổi các thuộc tính trực tiếp của object ở mức nông (**shallow freeze**).

> Không nên hiểu `Object.freeze()` là đóng băng sâu toàn bộ object lồng nhau.

---

# 2. Kiểu dữ liệu & Toán tử

## 2.1. Primitive Types

JavaScript có các primitive chính:

- `string`
- `number`
- `bigint`
- `boolean`
- `undefined`
- `null`
- `symbol`

Ngoài ra còn có `object`.

```js
const name = "An";       // string
const age = 20;          // number
const active = true;     // boolean
const x = undefined;     // undefined
const y = null;          // null
```

---

## 2.2. `typeof`

```js
typeof "hello";  // "string"
typeof 10;       // "number"
typeof true;     // "boolean"
typeof undefined; // "undefined"
typeof {};       // "object"
```

Một điểm đặc biệt:

```js
typeof null; // "object"
```

Đây là hành vi lịch sử của JavaScript.

---

## 2.3. `===` và `==`

### Nên ưu tiên `===`

```js
5 === 5;    // true
5 === "5";  // false
```

`==` cho phép type coercion:

```js
5 == "5"; // true
```

### Quy tắc thực tế

> Trong project, ưu tiên `===` và `!==` để tránh các chuyển đổi kiểu ngoài ý muốn.

---

## 2.4. Truthy và Falsy

Các giá trị falsy phổ biến:

```text
false
0
-0
0n
""
null
undefined
NaN
```

Ví dụ:

```js
const username = "";

if (!username) {
    console.log("Tên đang trống");
}
```

---

## 2.5. Nullish Coalescing `??`

Khác với `||`, `??` chỉ fallback khi giá trị là `null` hoặc `undefined`.

```js
const name = null;

console.log(name ?? "Guest");
// Guest
```

---

## 2.6. Optional Chaining `?.`

Tránh lỗi khi truy cập property có thể không tồn tại.

```js
const user = {
    profile: {
        name: "An"
    }
};

console.log(user.profile?.name);
console.log(user.address?.city);
```

---

# 3. Function & Arrow Function

## 3.1. Function Declaration

```js
function add(a, b) {
    return a + b;
}
```

---

## 3.2. Function Expression

```js
const add = function(a, b) {
    return a + b;
};
```

---

## 3.3. Arrow Function

```js
const add = (a, b) => {
    return a + b;
};
```

Có thể viết ngắn:

```js
const add = (a, b) => a + b;
```

---

## 3.4. Default Parameter

```js
function greet(name = "Guest") {
    console.log(`Hello ${name}`);
}
```

---

## 3.5. Rest Parameter

```js
function sum(...numbers) {
    return numbers.reduce((total, n) => total + n, 0);
}
```

---

## 3.6. Callback Function

Function có thể được truyền vào function khác.

```js
function processUser(callback) {
    callback();
}

processUser(() => {
    console.log("User processed");
});
```

Các phương thức như `map`, `filter`, `reduce`, `setTimeout`, `addEventListener` đều sử dụng callback.

---

# 4. Object & Destructuring

## 4.1. Object

```js
const user = {
    id: 1,
    name: "An",
    age: 20
};
```

Truy cập:

```js
user.name;
user["name"];
```

---

## 4.2. Object Shorthand

```js
const name = "An";
const age = 20;

const user = {
    name,
    age
};
```

---

## 4.3. Destructuring Object

```js
const user = {
    name: "An",
    age: 20
};

const { name, age } = user;
```

Đổi tên:

```js
const { name: userName } = user;
```

---

## 4.4. Destructuring Array

```js
const numbers = [10, 20, 30];

const [a, b, c] = numbers;
```

---

## 4.5. Spread Operator

```js
const oldUser = {
    name: "An",
    age: 20
};

const newUser = {
    ...oldUser,
    age: 21
};
```

Spread thường được dùng để tạo object/array mới thay vì sửa trực tiếp object cũ.

---

# 5. Array Processing

Đây là nhóm kiến thức **rất quan trọng khi làm web app**.

## 5.1. `forEach()`

Duyệt từng phần tử.

```js
numbers.forEach((number) => {
    console.log(number);
});
```

Không tạo array mới và không dùng để lấy một giá trị return tổng hợp.

---

## 5.2. `map()`

Biến đổi từng phần tử và tạo array mới.

```js
const numbers = [1, 2, 3];

const doubled = numbers.map(number => number * 2);
// [2, 4, 6]
```

---

## 5.3. `filter()`

Lọc phần tử.

```js
const numbers = [1, 2, 3, 4];

const evenNumbers = numbers.filter(number => number % 2 === 0);
// [2, 4]
```

---

## 5.4. `find()`

Tìm phần tử đầu tiên thỏa điều kiện.

```js
const user = users.find(user => user.id === 10);
```

Nếu không tìm thấy:

```js
undefined
```

---

## 5.5. `findIndex()`

```js
const index = users.findIndex(user => user.id === 10);
```

---

## 5.6. `some()`

Kiểm tra có ít nhất một phần tử đúng điều kiện.

```js
const hasAdmin = users.some(user => user.role === "admin");
```

---

## 5.7. `every()`

Kiểm tra tất cả phần tử.

```js
const allAdults = users.every(user => user.age >= 18);
```

---

## 5.8. `includes()`

```js
const fruits = ["apple", "banana"];

fruits.includes("apple"); // true
```

---

## 5.9. `sort()`

```js
const numbers = [10, 2, 5];

numbers.sort((a, b) => a - b);
```

> Cẩn thận: `sort()` **thay đổi array gốc**.

---

## 5.10. `reduce()`

Dùng để gom dữ liệu về một giá trị.

```js
const numbers = [1, 2, 3, 4];

const total = numbers.reduce(
    (sum, number) => sum + number,
    0
);
```

### Ví dụ thực tế

```js
const orders = [
    { id: 1, category: "Electronics", amount: 200, status: "completed" },
    { id: 2, category: "Books", amount: 50, status: "completed" },
    { id: 3, category: "Electronics", amount: 150, status: "pending" },
    { id: 4, category: "Books", amount: 30, status: "completed" }
];

const revenueByCategory = orders
    .filter(order => order.status === "completed")
    .reduce((acc, order) => {
        acc[order.category] =
            (acc[order.category] || 0) + order.amount;

        return acc;
    }, {});
```

Kết quả:

```js
{
    Electronics: 200,
    Books: 80
}
```

---

# 6. String, Number & Date

## 6.1. String

```js
const text = "  Hello JavaScript  ";

text.trim();
text.toLowerCase();
text.toUpperCase();
text.includes("JavaScript");
text.startsWith("Hello");
text.endsWith("Script");
```

### Kiểm tra chuỗi rỗng

```js
if (text.trim() === "") {
    console.log("Chuỗi rỗng");
}
```

---

## 6.2. Template Literal

```js
const name = "An";
const age = 20;

console.log(`Tên: ${name}, tuổi: ${age}`);
```

---

## 6.3. Number

```js
Number("123");       // 123
Number("abc");       // NaN
parseInt("123px");    // 123
parseFloat("12.5");  // 12.5
```

Kiểm tra số:

```js
Number.isNaN(value);
Number.isFinite(value);
```

---

## 6.4. Date

```js
const now = new Date();

now.getFullYear();
now.getMonth(); // 0 - 11
now.getDate();
```

> Khi xử lý ngày tháng phức tạp hoặc timezone trong project lớn, nên dùng thư viện hoặc API thời gian phù hợp thay vì tự xử lý mọi thứ bằng `Date`.

---

# 7. DOM

DOM là cách JavaScript tương tác với HTML.

---

## 7.1. Tìm phần tử

```js
document.querySelector("#app");
document.querySelector(".card");
document.querySelectorAll(".card");
```

`querySelector()` trả về phần tử đầu tiên.

`querySelectorAll()` trả về `NodeList`.

```js
document.querySelectorAll(".card").forEach(card => {
    console.log(card);
});
```

---

## 7.2. `getElementById()`

```js
const button = document.getElementById("submit-btn");
```

---

## 7.3. `closest()`

Tìm phần tử gần nhất khớp selector từ chính nó hoặc cha của nó.

```js
const card = event.target.closest(".card");
```

Rất hữu ích trong Event Delegation.

---

## 7.4. Nội dung

### `textContent`

```js
element.textContent = "Hello";
```

An toàn khi hiển thị text không tin cậy.

### `innerHTML`

```js
element.innerHTML = "<strong>Hello</strong>";
```

Cho phép chèn HTML nhưng phải cẩn thận với dữ liệu không tin cậy vì có thể gây XSS.

---

## 7.5. Input Value

```js
const input = document.querySelector("#username");

console.log(input.value);
input.value = "An";
```

---

## 7.6. Attribute

```js
element.getAttribute("id");

element.setAttribute("aria-label", "Close");

element.removeAttribute("disabled");
```

---

## 7.7. `dataset`

HTML:

```html
<button class="delete-btn" data-id="123">
    Delete
</button>
```

JavaScript:

```js
const id = button.dataset.id;
```

---

## 7.8. Class

```js
element.classList.add("active");
element.classList.remove("active");
element.classList.toggle("active");
element.classList.contains("active");
```

---

## 7.9. Style

```js
element.style.backgroundColor = "red";
```

> Với UI phức tạp, nên ưu tiên thêm/xóa class thay vì sửa quá nhiều inline style.

---

## 7.10. Tạo Element

```js
const li = document.createElement("li");

li.textContent = "Learn JavaScript";

document.querySelector("#task-list").append(li);
```

---

## 7.11. Xóa Element

```js
element.remove();
```

---

## 7.12. Geometry

```js
const rect = element.getBoundingClientRect();

rect.top;
rect.left;
rect.width;
rect.height;
```

Kích thước:

```js
element.offsetWidth;
element.offsetHeight;

element.clientWidth;
element.clientHeight;
```

Scroll:

```js
element.scrollTop;
element.scrollLeft;
```

---

# 8. Event Handling

## 8.1. `addEventListener()`

```js
button.addEventListener("click", () => {
    console.log("Clicked");
});
```

Các event thường gặp:

```text
click
input
change
submit
keydown
keyup
focus
blur
mouseover
mouseout
scroll
resize
DOMContentLoaded
```

---

## 8.2. Event Object

```js
button.addEventListener("click", (event) => {
    console.log(event.target);
});
```

---

## 8.3. `preventDefault()`

Ví dụ form:

```js
form.addEventListener("submit", (event) => {
    event.preventDefault();
});
```

Ngăn hành vi submit mặc định của browser.

---

## 8.4. `stopPropagation()`

```js
event.stopPropagation();
```

Dừng event tiếp tục truyền qua các phase.

> Không nên lạm dụng vì có thể làm event architecture khó kiểm soát.

---

## 8.5. Bubbling và Capturing

### Capturing

```text
document
   ↓
parent
   ↓
child
```

### Bubbling

```text
child
   ↑
parent
   ↑
document
```

Mặc định `addEventListener()` sử dụng bubbling.

---

## 8.6. Event Delegation

Thay vì gán event cho từng button:

```js
const list = document.querySelector("#task-list");

list.addEventListener("click", (event) => {
    const deleteBtn = event.target.closest(".btn-delete");

    if (!deleteBtn) return;

    const item = deleteBtn.closest(".task-item");
    const id = item.dataset.id;

    console.log("Xóa task:", id);
});
```

### Khi nào nên dùng?

- Todo list
- Table
- Comment list
- Product list
- Danh sách được render động

---

# 9. Form & Validation

## 9.1. Submit Form

```js
form.addEventListener("submit", (event) => {
    event.preventDefault();

    const formData = new FormData(form);

    const name = formData.get("name");
});
```

---

## 9.2. Kiểm tra input

```js
if (input.value.trim() === "") {
    console.log("Không được để trống");
}
```

HTML cũng hỗ trợ validation:

```html
<input
    type="email"
    required
    minlength="5"
>
```

Có thể kiểm tra:

```js
if (!form.checkValidity()) {
    form.reportValidity();
}
```

---

## 9.3. UX khi validate

Một form tốt nên:

1. Kiểm tra dữ liệu.
2. Hiển thị lỗi gần field.
3. Không xóa dữ liệu người dùng đã nhập.
4. Cho biết cách sửa.
5. Không chỉ dựa vào màu đỏ để biểu thị lỗi.

---

# 10. Event Loop & Bất đồng bộ

JavaScript chạy code đồng bộ trên **Call Stack**.

Các công việc bất đồng bộ được browser/runtime xử lý và callback được đưa vào queue.

Các khái niệm quan trọng:

```text
Call Stack
Web APIs / Runtime
Microtask Queue
Task (Macrotask) Queue
Event Loop
```

Ví dụ:

```js
console.log("1");

setTimeout(() => {
    console.log("2");
}, 0);

Promise.resolve().then(() => {
    console.log("3");
});

console.log("4");
```

Kết quả:

```text
1
4
3
2
```

### Vì sao?

1. Code đồng bộ chạy trước.
2. Microtask (`Promise.then`) được xử lý.
3. Task như `setTimeout` chạy sau.

> `requestAnimationFrame()` có cơ chế scheduling gắn với việc render của trình duyệt, nên không nên đơn giản hóa nó thành "một macrotask giống `setTimeout`".

---

# 11. Promise & Async/Await

## 11.1. Promise

Promise biểu diễn kết quả của một công việc bất đồng bộ.

Trạng thái:

```text
pending
fulfilled
rejected
```

---

## 11.2. `.then()` / `.catch()`

```js
fetch("/api/users")
    .then(response => response.json())
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error(error);
    });
```

---

## 11.3. Async/Await

```js
async function loadUsers() {
    try {
        const response = await fetch("/api/users");
        const users = await response.json();

        return users;
    } catch (error) {
        console.error(error);
    }
}
```

> `async/await` không làm code trở thành synchronous. Nó chỉ giúp viết flow Promise dễ đọc hơn.

---

## 11.4. `Promise.all()`

Chạy nhiều Promise đồng thời.

```js
const [users, posts] = await Promise.all([
    fetch("/api/users").then(res => res.json()),
    fetch("/api/posts").then(res => res.json())
]);
```

Nếu một Promise reject → `Promise.all()` reject.

---

## 11.5. `Promise.allSettled()`

Chờ tất cả Promise hoàn thành dù thành công hay thất bại.

```js
const results = await Promise.allSettled([
    fetch("/api/users"),
    fetch("/api/posts")
]);
```

---

## 11.6. `Promise.race()`

Promise nào settle trước thì quyết định kết quả.

```js
const result = await Promise.race([
    fetch("/api/data"),
    timeoutPromise
]);
```

Thường dùng để xây timeout.

---

## 11.7. `Promise.any()`

Resolve khi Promise đầu tiên **fulfill**.

Nếu tất cả đều reject → `AggregateError`.

---

# 12. Fetch API & REST API

## 12.1. GET

```js
const response = await fetch("/api/users");

if (!response.ok) {
    throw new Error(`HTTP ${response.status}`);
}

const users = await response.json();
```

### Quan trọng

`fetch()` **không tự reject chỉ vì HTTP 404/500**.

Do đó nên kiểm tra:

```js
response.ok
```

hoặc:

```js
response.status
```

---

## 12.2. POST JSON

```js
const response = await fetch("/api/users", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        name: "An",
        age: 20
    })
});
```

---

## 12.3. PUT / PATCH / DELETE

```js
fetch("/api/users/10", {
    method: "PATCH",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        name: "New Name"
    })
});
```

```js
fetch("/api/users/10", {
    method: "DELETE"
});
```

---

## 12.4. Tách API Service

Thay vì gọi `fetch()` ở khắp UI:

```js
async function getUsers() {
    const response = await fetch("/api/users");

    if (!response.ok) {
        throw new Error("Không thể lấy users");
    }

    return response.json();
}
```

UI:

```js
async function renderUsers() {
    const users = await getUsers();
    // render DOM
}
```

Lợi ích:

- Dễ test.
- Dễ thay API.
- UI ít phụ thuộc backend.
- Code dễ bảo trì.

---

# 13. JSON

JSON thường được dùng để trao đổi dữ liệu giữa frontend và backend.

Object:

```js
const user = {
    name: "An",
    age: 20
};
```

Object → JSON:

```js
const json = JSON.stringify(user);
```

JSON → Object:

```js
const data = JSON.parse(json);
```

> JSON không phải JavaScript Object. JSON là một định dạng dữ liệu dạng text.

---

# 14. LocalStorage, SessionStorage & Cookie

## 14.1. LocalStorage

Dữ liệu tồn tại qua nhiều lần mở/đóng browser.

```js
localStorage.setItem("theme", "dark");

const theme = localStorage.getItem("theme");

localStorage.removeItem("theme");

localStorage.clear();
```

Chỉ lưu string:

```js
localStorage.setItem(
    "user",
    JSON.stringify({ id: 1, name: "An" })
);

const user = JSON.parse(
    localStorage.getItem("user")
);
```

### Ứng dụng

- Theme.
- To-do list đơn giản.
- User preferences.
- Draft dữ liệu không nhạy cảm.

> Không nên lưu password hoặc secret nhạy cảm vào LocalStorage.

---

## 14.2. SessionStorage

Tương tự LocalStorage nhưng dữ liệu gắn với session của tab.

```js
sessionStorage.setItem("step", "2");
```

---

## 14.3. Cookie

Cookie thường được dùng trong các cơ chế session/authentication.

JavaScript có thể đọc cookie nếu cookie không có `HttpOnly`.

Cookie bảo mật thường cần các thuộc tính như:

```text
HttpOnly
Secure
SameSite
```

---

# 15. Modules

## 15.1. Export

`math.js`

```js
export function add(a, b) {
    return a + b;
}

export const PI = 3.14;
```

---

## 15.2. Import

```js
import { add, PI } from "./math.js";
```

HTML:

```html
<script type="module" src="./js/main.js"></script>
```

---

## 15.3. Default Export

```js
export default function greet() {
    console.log("Hello");
}
```

Import:

```js
import greet from "./greet.js";
```

---

## 15.4. Cấu trúc project nhỏ

```text
project/
├── index.html
├── css/
│   └── style.css
└── js/
    ├── main.js
    ├── api.js
    ├── dom.js
    ├── events.js
    ├── storage.js
    └── utils.js
```

---

# 16. Error Handling

## 16.1. `try...catch`

```js
try {
    const data = JSON.parse(text);
} catch (error) {
    console.error(error);
}
```

---

## 16.2. `finally`

```js
try {
    await loadData();
} catch (error) {
    console.error(error);
} finally {
    hideLoading();
}
```

`finally` chạy dù thành công hay thất bại.

---

## 16.3. `throw`

```js
if (!user) {
    throw new Error("User không tồn tại");
}
```

---

## 16.4. Custom Error

```js
class ApiError extends Error {
    constructor(message, status) {
        super(message);
        this.status = status;
    }
}
```

---

## 16.5. Error UI

Không nên chỉ:

```js
console.error(error);
```

Trong project thật, nên có:

```text
Loading...
    ↓
Success → render data
    ↓
Error → hiển thị thông báo
```

---

# 17. Debounce & Throttle

## 17.1. Debounce

Chỉ chạy sau khi người dùng dừng thao tác một khoảng thời gian.

Phù hợp:

- Search.
- Auto-save.
- Validation khi nhập.

```js
function debounce(func, delay = 300) {
    let timeoutId;

    return function (...args) {
        clearTimeout(timeoutId);

        timeoutId = setTimeout(() => {
            func.apply(this, args);
        }, delay);
    };
}
```

Dùng:

```js
searchInput.addEventListener(
    "input",
    debounce(handleSearch, 500)
);
```

---

## 17.2. Throttle

Giới hạn số lần chạy trong một khoảng thời gian.

Phù hợp:

- Scroll.
- Resize.
- Mouse move.
- Các event xảy ra rất thường xuyên.

```js
function throttle(func, delay) {
    let lastTime = 0;

    return function (...args) {
        const now = Date.now();

        if (now - lastTime >= delay) {
            lastTime = now;
            func.apply(this, args);
        }
    };
}
```

---

# 18. Performance & DOM Optimization

## 18.1. Hạn chế DOM manipulation không cần thiết

Không nên:

```js
for (...) {
    list.innerHTML += "...";
}
```

Có thể gây nhiều lần parse/update DOM.

Với lượng dữ liệu lớn, có thể xây dựng fragment:

```js
const fragment = document.createDocumentFragment();

for (const task of tasks) {
    const li = document.createElement("li");
    li.textContent = task.name;

    fragment.append(li);
}

list.append(fragment);
```

---

## 18.2. Cache DOM reference

Thay vì:

```js
document.querySelector("#task-list");
document.querySelector("#task-list");
document.querySelector("#task-list");
```

Có thể:

```js
const taskList = document.querySelector("#task-list");
```

---

## 18.3. Tránh layout thrashing

Hạn chế xen kẽ quá nhiều lần:

```text
đọc layout → sửa layout → đọc layout → sửa layout
```

Ví dụ các thao tác geometry như:

```js
offsetWidth
offsetHeight
getBoundingClientRect()
```

có thể khiến browser phải tính toán layout trong một số tình huống.

---

## 18.4. Render theo State

Một hướng tốt:

```text
User action
    ↓
Update state
    ↓
Render UI
```

Thay vì mỗi event tự sửa DOM theo cách khác nhau.

---

# 19. Closures

Closure xảy ra khi function bên trong vẫn truy cập được biến của scope bên ngoài ngay cả sau khi scope bên ngoài đã kết thúc.

```js
function createCounter() {
    let count = 0;

    return function () {
        count++;
        return count;
    };
}

const counter = createCounter();

console.log(counter()); // 1
console.log(counter()); // 2
```

Closure thường được dùng trong:

- Factory function.
- Private state.
- Debounce/throttle.
- Module pattern.
- Callback.

---

# 20. `this`, `call`, `apply`, `bind`

## 20.1. `this`

Giá trị của `this` phụ thuộc vào cách function được gọi.

```js
const user = {
    name: "An",

    greet() {
        console.log(this.name);
    }
};

user.greet();
```

---

## 20.2. Arrow Function và `this`

Arrow function không tạo `this` riêng.

```js
const user = {
    name: "An",

    greet: () => {
        console.log(this.name);
    }
};
```

Không nên dùng arrow function làm method nếu bạn cần `this` của object.

---

## 20.3. `call()`

```js
function greet() {
    console.log(this.name);
}

greet.call({ name: "An" });
```

---

## 20.4. `apply()`

Tương tự `call()` nhưng truyền arguments dưới dạng array.

---

## 20.5. `bind()`

Tạo function mới với `this` được gắn sẵn.

```js
const boundGreet = greet.bind({ name: "An" });

boundGreet();
```

---

# 21. Prototype & Class

## 21.1. Class

```js
class User {
    constructor(name) {
        this.name = name;
    }

    greet() {
        console.log(`Hello ${this.name}`);
    }
}

const user = new User("An");
```

---

## 21.2. Inheritance

```js
class Admin extends User {
    deleteUser() {
        console.log("Delete user");
    }
}
```

---

## 21.3. Static Method

```js
class MathUtil {
    static add(a, b) {
        return a + b;
    }
}

MathUtil.add(1, 2);
```

---

## 21.4. Private Field

```js
class Counter {
    #count = 0;

    increment() {
        this.#count++;
    }

    getCount() {
        return this.#count;
    }
}
```

---

## 21.5. Prototype

JavaScript sử dụng prototype-based inheritance.

Class là cú pháp thuận tiện để làm việc với cơ chế prototype.

---

# 22. Map, Set, WeakMap, WeakSet

## 22.1. Set

Lưu các giá trị không trùng.

```js
const numbers = new Set([1, 2, 2, 3]);

console.log(numbers);
// Set {1, 2, 3}
```

Ứng dụng:

```js
const uniqueNumbers = [...new Set(numbersArray)];
```

---

## 22.2. Map

Lưu dữ liệu dạng key-value.

```js
const users = new Map();

users.set(1, "An");
users.set(2, "Bình");

console.log(users.get(1));
```

Map hữu ích khi key không nhất thiết phải là string.

---

## 22.3. WeakMap / WeakSet

Dùng trong các trường hợp nâng cao khi muốn tham chiếu object mà không ngăn garbage collector thu hồi object.

> Đây là kiến thức nên học sau Map/Set.

---

# 23. Regular Expression

Regex dùng để tìm/kiểm tra pattern trong text.

Ví dụ:

```js
const pattern = /^[0-9]+$/;

pattern.test("123"); // true
pattern.test("abc"); // false
```

Một số ký hiệu:

| Ký hiệu | Ý nghĩa |
|---|---|
| `^` | Bắt đầu |
| `$` | Kết thúc |
| `.` | Một ký tự bất kỳ |
| `*` | 0 hoặc nhiều |
| `+` | 1 hoặc nhiều |
| `?` | 0 hoặc 1 |
| `\d` | Chữ số |
| `\w` | Word character |
| `\s` | Whitespace |
| `[]` | Character set |
| `()` | Group |

> Regex phù hợp cho validation đơn giản; đừng cố dùng một regex khổng lồ để xử lý mọi logic nghiệp vụ.

---

# 24. Browser APIs hữu ích

## 24.1. `setTimeout`

```js
const id = setTimeout(() => {
    console.log("Hello");
}, 1000);

clearTimeout(id);
```

---

## 24.2. `setInterval`

```js
const id = setInterval(() => {
    console.log("Running");
}, 1000);

clearInterval(id);
```

---

## 24.3. `requestAnimationFrame`

Phù hợp với animation/update gắn với quá trình render.

```js
function animate() {
    // update UI
    requestAnimationFrame(animate);
}

requestAnimationFrame(animate);
```

---

## 24.4. `IntersectionObserver`

Phát hiện element đi vào/ra viewport.

```js
const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            console.log("Element visible");
        }
    });
});

observer.observe(element);
```

Ứng dụng:

- Lazy loading.
- Animation khi scroll.
- Infinite scroll.

---

## 24.5. `AbortController`

Hủy request hoặc một số operation hỗ trợ AbortSignal.

```js
const controller = new AbortController();

fetch("/api/data", {
    signal: controller.signal
});

controller.abort();
```

Rất hữu ích khi:

- User đổi từ khóa search.
- Component/page không còn cần request.
- Muốn cancel request cũ.

---

## 24.6. URL và URLSearchParams

```js
const url = new URL("/search", window.location.origin);

url.searchParams.set("q", "javascript");
url.searchParams.set("page", "2");

console.log(url.toString());
```

Rất hữu ích khi làm:

- Search.
- Pagination.
- Filter.
- Query parameters.

---

# 25. Security cơ bản

## 25.1. XSS

Không nên:

```js
element.innerHTML = userInput;
```

Nếu `userInput` chứa HTML/JavaScript độc hại, có thể dẫn tới XSS.

An toàn hơn:

```js
element.textContent = userInput;
```

---

## 25.2. Không lưu secret trong Frontend

Không đặt:

```js
const API_SECRET = "super-secret";
```

trong code frontend với ý nghĩ nó được bảo mật.

Code frontend gửi tới browser → người dùng có thể xem.

> API key/secret cần được bảo vệ ở backend khi loại credential đó yêu cầu bí mật.

---

## 25.3. Authentication không chỉ là UI

Ẩn nút:

```js
deleteButton.style.display = "none";
```

không có nghĩa user không thể gọi API xóa dữ liệu.

Backend vẫn phải:

1. Xác thực user.
2. Kiểm tra quyền.
3. Validate input.
4. Thực hiện thao tác.

---

## 25.4. CORS

CORS là cơ chế browser kiểm soát request cross-origin dựa trên response headers.

Frontend không thể "tự bật CORS" bằng JavaScript.

CORS chủ yếu cần được cấu hình ở server.

---

# 26. Separation of Concerns & Project Architecture

Một project JavaScript nên phân tách trách nhiệm.

```text
            UI
             ↓
          State
             ↓
         Service/API
             ↓
          Backend
             ↓
         Database
```

Với frontend thuần JavaScript:

```text
js/
├── main.js
├── api.js
├── state.js
├── dom.js
├── events.js
├── storage.js
└── utils.js
```

---

## 26.1. API Layer

```js
export async function getUsers() {
    const response = await fetch("/api/users");

    if (!response.ok) {
        throw new Error("API Error");
    }

    return response.json();
}
```

---

## 26.2. State Layer

```js
export const state = {
    theme: "light",
    users: [],
    loading: false
};
```

---

## 26.3. UI Layer

```js
export function renderUsers(users) {
    // tạo DOM
}
```

---

## 26.4. Event Layer

```js
button.addEventListener("click", handleClick);
```

---

## 26.5. Main Entry

```js
import { getUsers } from "./api.js";
import { renderUsers } from "./dom.js";

async function init() {
    const users = await getUsers();

    renderUsers(users);
}

document.addEventListener("DOMContentLoaded", init);
```

---

# 27. Quản lý State

State là dữ liệu hiện tại mà UI phụ thuộc vào.

Ví dụ Todo App:

```js
const state = {
    tasks: [],
    search: "",
    filter: "all",
    theme: "dark"
};
```

Flow:

```text
User click
   ↓
Event Handler
   ↓
Update State
   ↓
Render
   ↓
UI thay đổi
```

Ví dụ:

```js
function addTask(task) {
    state.tasks.push(task);
    renderTasks();
}
```

Với project lớn, nên hạn chế để nhiều nơi tự ý sửa state.

---

# 28. Các Pattern thực tế cho Web App

## 28.1. Loading State

```text
idle
 ↓
loading
 ↓
success
```

Hoặc:

```text
idle
 ↓
loading
 ↓
error
```

UI:

```js
if (state.loading) {
    showLoading();
}
```

---

## 28.2. Search

Flow tốt:

```text
Input
 ↓
Debounce
 ↓
Abort request cũ nếu cần
 ↓
API
 ↓
Update State
 ↓
Render
```

---

## 28.3. CRUD

Hầu hết web app quản lý dữ liệu đều xoay quanh:

```text
Create
Read
Update
Delete
```

Ví dụ Todo:

```text
Add Task
View Tasks
Edit Task
Delete Task
```

---

## 28.4. Pagination

```text
page = 1
limit = 10
```

Request:

```text
/api/products?page=1&limit=10
```

---

## 28.5. Filter + Search + Sort

Không nên xử lý từng thứ một cách rời rạc.

Có thể xây dựng pipeline:

```js
const result = products
    .filter(product => matchesSearch(product))
    .filter(product => matchesCategory(product))
    .sort(compareProducts);
```

---

## 28.6. Modal

Một modal thường cần:

```text
Open
Close
Overlay click
Escape key
Focus handling
```

Ví dụ:

```js
document.addEventListener("keydown", event => {
    if (event.key === "Escape") {
        closeModal();
    }
});
```

---

## 28.7. Theme Toggle

HTML:

```html
<button id="theme-toggle">
    Toggle theme
</button>
```

JavaScript:

```js
const root = document.documentElement;

button.addEventListener("click", () => {
    root.classList.toggle("dark");
});
```

Có thể lưu preference:

```js
localStorage.setItem("theme", "dark");
```

---

# 29. Debug & DevTools

## 29.1. `console.log`

```js
console.log(value);
```

Các method hữu ích:

```js
console.warn();
console.error();
console.table();
console.time();
console.timeEnd();
```

---

## 29.2. Breakpoint

Trong Chrome DevTools:

```text
Sources
→ chọn file JS
→ click số dòng
```

Sau đó chạy code và quan sát:

- Variables.
- Call Stack.
- Scope.
- Watch.
- Step over.
- Step into.
- Step out.

---

## 29.3. Network Tab

Khi làm API, thường xuyên kiểm tra:

```text
Request URL
Request Method
Status Code
Request Headers
Request Payload
Response
Timing
```

Ví dụ:

```text
200 → thành công
201 → tạo resource thành công
400 → request không hợp lệ
401 → chưa xác thực
403 → không có quyền
404 → không tìm thấy
500 → lỗi server
```

---

## 29.4. Debug lỗi DOM

Nếu:

```js
const button = document.querySelector("#button");
```

có thể trả về:

```js
null
```

hãy kiểm tra:

1. ID có đúng không?
2. Script chạy trước HTML chưa?
3. Element đã tồn tại chưa?
4. Selector có đúng không?

Có thể đặt script:

```html
<script type="module" src="./js/main.js"></script>
```

ở cuối `body`, hoặc dùng module/DOMContentLoaded tùy cấu trúc.

---

# 30. Checklist JavaScript khi làm Project

## HTML → JS

- [ ] `id` / `class` rõ ràng.
- [ ] Dùng semantic HTML khi phù hợp.
- [ ] Form có `label`.
- [ ] Button có `type` phù hợp.
- [ ] Có `data-*` khi cần lưu identifier.

---

## DOM

- [ ] Cache các element dùng nhiều.
- [ ] Ưu tiên `textContent` khi chỉ cần text.
- [ ] Hạn chế `innerHTML` với dữ liệu không tin cậy.
- [ ] Ưu tiên class thay vì inline style.
- [ ] Dùng Event Delegation cho list động khi phù hợp.

---

## Event

- [ ] Dùng `addEventListener`.
- [ ] Biết khi nào cần `preventDefault`.
- [ ] Hiểu bubbling.
- [ ] Không lạm dụng `stopPropagation`.

---

## API

- [ ] Kiểm tra `response.ok`.
- [ ] Xử lý loading.
- [ ] Xử lý error.
- [ ] Validate dữ liệu.
- [ ] Không để secret trong frontend.
- [ ] Dùng `AbortController` khi cần cancel request.
- [ ] Dùng `Promise.all` khi các request độc lập có thể chạy đồng thời.

---

## State

- [ ] Xác định state chính.
- [ ] Hạn chế sửa state từ quá nhiều nơi.
- [ ] Có flow rõ ràng: Event → State → Render.
- [ ] Tách data logic khỏi DOM logic khi project bắt đầu lớn.

---

## Performance

- [ ] Debounce search.
- [ ] Throttle scroll/resize nếu cần.
- [ ] Hạn chế DOM update liên tục.
- [ ] Dùng `DocumentFragment` khi render nhiều element.
- [ ] Dùng lazy loading/IntersectionObserver khi phù hợp.
- [ ] Hủy request cũ khi search nhanh liên tục.

---

## Security

- [ ] Không chèn dữ liệu người dùng trực tiếp vào `innerHTML`.
- [ ] Không lưu password vào LocalStorage.
- [ ] Không đưa secret backend vào frontend.
- [ ] Không tin tưởng validation ở frontend.
- [ ] Backend vẫn phải kiểm tra quyền và dữ liệu.

---

# 31. Lộ trình học JavaScript để làm Project

## Level 1 — Nền tảng

Học chắc:

```text
let / const
Data Types
if / else
for / while
Function
Array
Object
String
```

Project:

- Calculator.
- Number guessing.
- Simple quiz.

---

## Level 2 — DOM

Học:

```text
querySelector
textContent
value
classList
createElement
append
remove
addEventListener
```

Project:

- To-Do List.
- Calculator UI.
- Notes App.

---

## Level 3 — Array + Event

Học:

```text
map
filter
find
some
every
reduce
Event Delegation
Form
Validation
```

Project:

- Product Filter.
- Expense Tracker.
- Student Management.

---

## Level 4 — Storage

Học:

```text
JSON
localStorage
sessionStorage
```

Project:

- Todo App có lưu dữ liệu.
- Expense Tracker.
- Notes App.

---

## Level 5 — Async + API

Học:

```text
Promise
async/await
fetch
HTTP
REST API
JSON
try/catch
Promise.all
AbortController
```

Project:

- Movie Search.
- Weather App.
- GitHub User Search.
- Password Generator có API nếu phù hợp.
- Dashboard lấy dữ liệu từ server.

---

## Level 6 — Architecture

Học:

```text
ES Modules
State
Service Layer
UI Layer
Event Layer
Error Handling
Loading State
Reusable Functions
```

Project:

- Expense Management.
- E-commerce frontend.
- Task Management.
- Movie Dashboard.

---

## Level 7 — Advanced

Học:

```text
Closure
this
Prototype
Class
Map / Set
Regex
Event Loop
Performance
Security
Design Patterns
Testing
```

Sau đó mới cần cân nhắc framework:

```text
React
Vue
Angular
Svelte
```

> Framework không thay thế kiến thức JavaScript nền tảng. Hiểu JavaScript tốt sẽ giúp học framework dễ hơn.

---

# Tổng kết — Những thứ cần nhớ nhất

Nếu mục tiêu là **làm website bằng HTML + CSS + JavaScript**, hãy ưu tiên theo thứ tự:

```text
1. Variable / Scope
        ↓
2. Function
        ↓
3. Array / Object
        ↓
4. DOM
        ↓
5. Event
        ↓
6. Form / Validation
        ↓
7. JSON
        ↓
8. LocalStorage
        ↓
9. Promise / Async Await
        ↓
10. Fetch / REST API
        ↓
11. Modules
        ↓
12. State Management
        ↓
13. Error Handling
        ↓
14. Performance
        ↓
15. Security
        ↓
16. Architecture
```

## Công thức tư duy khi xây dựng một tính năng

Mỗi khi muốn thêm một feature, hãy tự hỏi:

```text
1. Dữ liệu là gì?
        ↓
2. State nào cần lưu?
        ↓
3. User thao tác bằng event nào?
        ↓
4. Có cần API không?
        ↓
5. Có cần validate không?
        ↓
6. State thay đổi thế nào?
        ↓
7. UI render lại thế nào?
        ↓
8. Có loading / error không?
        ↓
9. Có vấn đề security không?
        ↓
10. Có cần tối ưu performance không?
```

Ví dụ với **Movie Search**:

```text
User nhập tên phim
        ↓
input event
        ↓
Debounce
        ↓
Fetch API
        ↓
Loading
        ↓
Nhận JSON
        ↓
Validate response
        ↓
Update state
        ↓
Render movie cards
        ↓
Nếu lỗi → Error UI
```

Ví dụ với **Todo List**:

```text
User nhập task
        ↓
Submit event
        ↓
Validate
        ↓
Update state.tasks
        ↓
Lưu LocalStorage
        ↓
Render task list
        ↓
Event Delegation
        ↓
Edit / Complete / Delete
```

> **Mục tiêu cuối cùng không phải là nhớ toàn bộ API của JavaScript.**  
> Quan trọng hơn là biết **chọn đúng công cụ cho đúng vấn đề**, tổ chức code rõ ràng và hiểu luồng dữ liệu từ **User → Event → Logic → State/API → UI**.
