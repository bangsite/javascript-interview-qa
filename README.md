## Tổng hợp những câu hỏi JavaScript <a id="title"/>

## Lí thuyết

### 1. `scope` trong Javascript là gì ?

```javascript

```

### 2. So sánh sự khác nhau giữa `var | let | const` ?

```javascript

```

### 3. So sánh sự khác nhau giữa `isNaN` và `Number.isNaN` ?

```javascript

```

### 4. So sánh sự khác nhau giữa toán tử `==` và `===` là gì?

```javascript

```

### 5. So sánh sự khác nhau giữa `null` và `undefined` là gì?

```javascript

```

### 6. So sánh sự khác nhau giữa `slice` và `splice` ?

```javascript

```

### 7. So sánh sự khác nhau giữa `Call | Apply | Bind` ?

```javascript

```

### 8. So sánh sự khác nhau giữa `Set | Map | Object` ?

```javascript

```

### 9. `Temporal Dead Zone`  là gì?

```javascript

```

### 10. Hoisting  là gì?

```javascript

```

### 11. Closures là gì?

```javascript

```

### 12. Currying function  là gì?

```javascript

```

### 13. Memoization  là gì?

```javascript

```

### 14. setTimeout  là gì?

```javascript

```

### 15. setInterval  là gì?

```javascript

```

### 16. Callback là gì?

```javascript

```

### 17. Promise là gì?

```javascript

```

### 18. Async/Await là gì?

```javascript

```

### 19. Call stack  là gì?

```javascript

```

### 20. Heap là gì?

```javascript

```

### 21. Event table là gì?

```javascript

```

### 22. Event queue là gì?

```javascript

```

### 23. Microtask queue là gì?

```javascript

```

### 24. Event loop  là gì?

```javascript

```

### 25. `observable` là gì?

```javascript

```

### 26. So sánh `Promise.all | Promise.setted | Promise.race | Promise.any`  là gì?

```javascript

```

### 27. So sánh `cookie | locale Storage | session Storage`  là gì?

```javascript

```

### 28. Service worker là gì?

```javascript

```

### 29. Phân biệt debouncing & throttling ?

```javascript

```

### 30. Có những cách nào để execute các file js từ bên ngoài ?

- `<script>`: Với thẻ script không có thuộc tính gì khác thì trong quá trình phân tích cú pháp `HTML` nếu phải thẻ
  script, đến lúc này thì quá trình phân tích cú pháp `HTML` sẽ tạm dùng và để tải tệp js, sau đó thực thi luôn tệp js,
  rồi mới tiếp tục lại quá trình phân tích cú pháp `HTML`.
- `<script async>`: Tệp `js` được tải xuống song song cùng với quá trình phân tích cú pháp `HTML`. Sau khi hoàn tất tải
  xuống, tệp js sẽ thực thi, quá trình phân tích cú pháp `HTML` sẽ bị tạm ngừng cho tới khi tệp `js` thưc thi xong, thì
  mới tiếp tục.
- `<script defer>`: Tệp `js` được tải xuống song song cùng với quá trình phân tích cú pháp `HTML`. Và chỉ thực thi sau
  khi quá trình phân tích cú pháp `HTML` hoàn tất.

## Viết mã

### 1. Output là gì?

```javascript
(function () {
    var message = "IIFE";
    console.log(message);
})();

console.log(message);
```

<details><summary><b>Đáp án</b></summary>
<p>

```shell
'IIFE'
ReferenceError: message is not defined
```

- Hàm trên là một IIFE (Immediately Invoked Function Expression), cho phép bạn khai báo một hàm ẩn danh và thực thi nó
  ngay lập tức. Các biến trong IIFE được bảo vệ khỏi phạm vi toàn cục, giúp tránh xung đột biến.
- Vì message là một biến cục bộ của hàm, nên nó không tồn tại trong phạm vi toàn cục.
- Nếu cố gắng truy cập message bên ngoài hàm, sẽ gặp lỗi ReferenceError.

</p>
</details>

---

### 2. Output là gì?

```javascript
console.log(typeof typeof 0);
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
string
```

- `typeof 0`: "number".
- `typeof  "number"`: string.

</p>
</details>

---

### 3. Output là gì?

```javascript
function say() {
    return
    {
        message: "hello"
    }
}

var a = say();

console.log(a);
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
undefined
```

- Do cơ chế ASI (Automatic Semicolon Insertion), JavaScript tự động thêm dấu chấm phẩy (;) sau từ khóa return. Điều này
  dẫn đến việc hàm trả về undefined thay vì object `{ message: "hello" }`.

</p>
</details>

---

### 4. Output là gì?

```javascript
let fruits = ["Apple", "Orange", "Lemon", "Mango"];

let pick = fruits.slice(1, 3);

console.log(fruits);
console.log(pick);

fruits.splice(2, 0, "Banana", "Kiwi");

console.log(fruits);
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
["Apple", "Orange", "Lemon", "Mango"];
['Orange', 'Lemon'];
["Apple", "Orange", "Banana", "Kiwi", "Lemon", "Mango"];
```

</p>
</details>

---

### 5. Output là gì?

```javascript
console.log(undefined * 2)

console.log(null * 2)

console.log("" * 2)
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
NaN
0
0
```

</p>
</details>

---

### 6. Output là gì?

```javascript
let name = "Alex";
const age = 18;

name = "John";
age = 20;

console.log(name);
console.log(age);
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
"John"
"TypeError: Assignment to constant variable."
```

</p>
</details>

---

### 7. Output là gì?

```javascript
var number = ["one", "two", "three", "four"]

console.log(number.pop());
console.log(number.shift());
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
"four"
"one"
```

</p>
</details>

---

### 8. Output là gì?

```javascript
var student = {name: 'Lyly', age: 20};

delete student.age;

console.log(student);
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
{
    name: 'Lyly'
}
```

</p>
</details>

---

### 9. Output là gì?

```javascript
console.log(9 + 12 + "7");
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
"217"
```

</p>
</details>

---

### 10. Output là gì?

```javascript
let a = [10];
let b = new Array(10);

console.log(a);
console.log(b);
```

<details><summary><b>Đáp án</b></summary>
<p>

```text
[10]
[<empty × 10>]
```

</p>
</details>

---

### 11. Output là gì?

```javascript
var student = {
    name: "Alex",
    age: 20,
    getName: function () {
        return this.name;
    }
};

console.log(student.getName())
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
"Alex"
```

</p>
</details>

---

### 12. Output là gì?

```javascript
say();

function say() {
    console.log("Hello");
}

function say() {
    console.log("Bye");
}
```

- A: Reference error: say is not defined
- B: Hello
- C: Bye
- D: Compile time error

<details><summary><b>Đáp án</b></summary>
<p>

```text
C: Bye
```

- Trong JavaScript, cả khai báo hàm (function declaration) và thân hàm đều được hoisting. Khi có hai hàm cùng tên, hàm
  được định nghĩa sau cùng sẽ ghi đè lên hàm trước.
- Hàm say() đầu tiên được ghi vào bộ nhớ. Sau đó, nó bị ghi đè bởi hàm say() thứ hai, nên khi gọi say(), hàm thứ hai
  được thực thi.

</p>
</details>

---

### 13. Output là gì?

```javascript
var location = "HaNoi";

var changeLocation = function () {
    console.log("Current City:", location);
    var location = "Japan";
    console.log("Current City:", location);
};

changeLocation();
```

- A: HaNoi, Japan
- B: HaNoi, HaNoi
- C: undefined, Japan
- D: Japan, Japan

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
C: undefined, Japan
```

- Khi khai báo `var location` trong hàm `changeLocation`, khai báo được hoisting lên đầu hàm với giá trị mặc định
  là `undefined`.
- Nên `console.log(location)` đầu tiên in `undefined`. Sau khi gán giá trị "Japan", dòng `console.log(location)` thứ hai
  in "Japan".
- Chú ý hoisting chỉ đưa khai báo lên đầu, nhưng không di chuyển giá trị.

</p>
</details>

---

### 14. Output là gì?

```javascript
const numbers = [8, 22, 91, 28, 101, 16, 300];
numbers.sort();
console.log(numbers);
```

- A: [8, 16, 22, 28, 91, 101, 300]
- B: [101, 16, 22, 28, 300, 8, 91]
- C: [8, 22, 91, 28, 101, 16, 300]
- D: Cannot sort numbers

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
B: [101, 16, 22, 28, 300, 8, 91]
```

- Mặc định, hàm `sort` trong Javascript sẽ sắp xếp theo bảng chữ cái, cho các phần tử trong mảng bị chuyển đổi
  thành `string`, do đó các số sẽ không sắp xếp như ta mong đợi
- Để sắp xếp chính xác theo số theo thứ tự tăng dần, ta có thể viêt lại như sau:

```javascript
const numbers = [8, 22, 91, 28, 101, 16, 300];
numbers.sort((a, b) => a - b);
console.log(numbers);
```

</p>
</details>

---

### 15. Output là gì?

```javascript
var of = ["loop"];
for (var of of of) {
    console.log(of);
}
```

- A: loop
- B: SyntaxError: Unexpected token of
- C: SyntaxError: Identifier 'of' has already been declared
- D: ReferenceError: of is not defined

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
A: loop
```

- Mã vẫn chạy và in ra `loop`, vì `of` trong Javascript không phải là từ khóa riêng, cho nên việc khai báo
  biến `var of = ["loop"]` là hợp lệ.
- Nhưng lưu ý, nếu ta khai báo `var in = ["loop"]` thì sẽ có lỗi cú pháp `SyntaxError: Unexpected token 'in'`, vì vây
  nên tránh khai báo các `keyword` trong Javascript

```javascript
const numbers = [8, 22, 91, 28, 101, 16, 300];
numbers.sort((a, b) => a - b);
console.log(numbers);
```

</p>
</details>

---

### 20. Output là gì?

```javascript
var a = (!+[] + [] + ![]);

console.log(a.length);

```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
9
```

- `+[]`: `[]` là empty array, khi `+[]` sẽ ép kiểu về số có giá trị là 0.
- `! +[]`: sẽ là true.
- `true + []`: "true".
- `![]`: [] là giá trị truthy, nên `![]` là false.
- `"true" + false`: "truefalse", nên a.length có gi trị là 9.

</p>
</details>

---

### 21. Output sẽ là gì?

```javascript
const a = [1, 2, 3];
const b = [1, 2, 3];
const c = "1,2,3";

console.log(a == c);
console.log(a == b);
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
true, false
```

- Với `console.log(a == c)`
    - Khi so sánh `a` (một array) với `c` (một string), JavaScript sẽ thực hiện ép kiểu ngầm định để so sánh giá trị của
      hai bên. Và a sẽ chuyển sang chuỗi bằng cách gọi phương thức
      Array.prototype.toString(): `a.toString(); // "1,2,3"`
    - So sánh với chuỗi `c`, và vì "1,2,3" == "1,2,3", kết quả sẽ là true.
- Với `console.log(a == b)`
    - `a` và `b` là array (object trong JavaScript). Khi so sánh object bằng toán tử `==` hoặc `===`, JavaScript so sánh
      tham chiếu (reference) thay vì giá trị.
    - Cho nên dù `a` và `b` có cùng nội dung `[1, 2, 3]`, nhưng vì chúng nằm ở hai vùng nhớ khác nhau trong bộ nhớ, tham
      chiếu
      không giống nhau, kết quả sẽ là false.

</p>
</details>

---

### 22. Output sẽ là gì?

```javascript
function para(a, b = 2) {
    console.log(arguments.length);
}

para(undefined);
para();
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
1
0
```

- Hàm gọi với giá trị `undefined` thì `undefined` được coi là 1 parameter( tham số ). Nên `arguments.length` sẽ là 1.
- Hàm không được truyền bất kì tham số nào, cho dù hàm có tham số mặc định `b = 2`, thì arguments( đối số ) vẫn là 0

</p>
</details>

---

### 23. Output sẽ là gì?

```javascript
function para(a, b = 2) {
    console.log(arguments.length);
}

para(undefined);
para();
```

<details><summary><b>Đáp án</b></summary>
<p>

```javascript
1
0
```

- Hàm gọi với giá trị `undefined` thì `undefined` được coi là 1 parameter( tham số ). Nên `arguments.length` sẽ là 1.
- Hàm không được truyền bất kì tham số nào, cho dù hàm có tham số mặc định `b = 2`, thì arguments( đối số ) vẫn là 0

</p>
</details>

---

### 29. Output sẽ là gì?

```javascript
for (var i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 1);
}

for (let i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 1);
}
```

- A: `0 1 2` and `0 1 2`
- B: `0 1 2` and `3 3 3`
- C: `3 3 3` and `0 1 2`

<details><summary><b>Đáp án</b></summary>
<p>

```text
C: `3 3 3`  and  `0 1 2`
```

- For 1:
    - `setTimeout` là một hàm bất đồng bộ, nên nó đưa các callback (hàm bên trong setTimeout) vào hàng đợi (queue) để
      thực
      thi sau khi call stack trống.
    - Trong khi các callback chờ được thực thi, vòng lặp for chạy đến hết (tăng i lên 3). Biến `var` có phạm vi toàn cục
      nên vòng lặp `for` chỉ có một biến `i` duy nhất được chia sẻ giữa tất cả các lần lặp.
    - Các callback trong setTimeout sẽ chạy sau khi vòng lặp kết thúc, nên tất cả chúng truy cập cùng một biến `i` đã
      được
      tăng lên `3`.
- For 2:
    - `setTimeout` là một hàm bất đồng bộ, nên nó đưa các callback (hàm bên trong setTimeout) vào hàng đợi (queue) để
      thực
      thi sau khi call stack trống.
    - Trong khi các callback chờ được thực thi, vòng lặp `for` chạy. Biến `let` có phạm vi block (block scope). Trong
      vòng
      lặp `for`, mỗi lần lặp tạo ra một biến i mới, độc lập. Khi callback được tạo trong mỗi lần lặp, nó "ghi nhớ" (
      closure) giá trị hiện tại của i tại thời điểm callback được tạo.
    - Call stack trống, các callback chạy, chúng truy cập đúng giá trị của `i` được lưu trữ riêng trong từng vòng lặp.

</p>
</details>

---

### 30. Output sẽ là gì?

```javascript
for (var i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 1);
}

for (let i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 1);
}
```

- A: `0 1 2` and `0 1 2`
- B: `0 1 2` and `3 3 3`
- C: `3 3 3` and `0 1 2`

<details><summary><b>Đáp án</b></summary>
<p>

```text
C: `3 3 3`  and  `0 1 2`
```

- For 1:
    - `setTimeout` là một hàm bất đồng bộ, nên nó đưa các callback (hàm bên trong setTimeout) vào hàng đợi (queue) để
      thực
      thi sau khi call stack trống.
    - Trong khi các callback chờ được thực thi, vòng lặp for chạy đến hết (tăng i lên 3). Biến `var` có phạm vi toàn cục
      nên vòng lặp `for` chỉ có một biến `i` duy nhất được chia sẻ giữa tất cả các lần lặp.
    - Các callback trong setTimeout sẽ chạy sau khi vòng lặp kết thúc, nên tất cả chúng truy cập cùng một biến `i` đã
      được
      tăng lên `3`.
- For 2:
    - `setTimeout` là một hàm bất đồng bộ, nên nó đưa các callback (hàm bên trong setTimeout) vào hàng đợi (queue) để
      thực
      thi sau khi call stack trống.
    - Trong khi các callback chờ được thực thi, vòng lặp `for` chạy. Biến `let` có phạm vi block (block scope). Trong
      vòng
      lặp `for`, mỗi lần lặp tạo ra một biến i mới, độc lập. Khi callback được tạo trong mỗi lần lặp, nó "ghi nhớ" (
      closure) giá trị hiện tại của i tại thời điểm callback được tạo.
    - Call stack trống, các callback chạy, chúng truy cập đúng giá trị của `i` được lưu trữ riêng trong từng vòng lặp.

</p>
</details>

---

### 31. What is the time taken to execute below timeout callback?

```javascript
console.log("Start");

setTimeout(function () {
    console.log("Callback");
}, 5000);

console.log("After Callback");


let startTime = new Date().getTime();
let endTime = startTime;

while (endTime <= startTime + 10000) {
    endTime = new Date().getTime();
}

console.log("End");
```

- A: > 10 sec
- B: Immediately
- C: < 10 sec
- D: <= 5sec

<details><summary><b>Đáp án</b></summary>
<p>

```text
A: > 10 sec
```

- `setTimeout` đưa hàm `callback` vào `callback queue` và chờ Call Stack trống để thực thi.
- Vòng lặp while kéo dài 10 giây, ngăn callback thực thi trong thời gian này.Sau khi vòng lặp kết thúc, callback được
  thực thi.
- Thời gian chờ tối thiểu của setTimeout là 5 giây, nhưng tổng thời gian thực tế phụ thuộc vào khi nào Call Stack trống.
  Vì vòng lặp chiếm 10 giây, callback thực thi sau khoảng hơn 10 giây.

</p>
</details>

[⬆ Back to Top](#title)

---
