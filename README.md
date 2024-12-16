## Tổng hợp những câu hỏi JavaScript <a id="title"/>

### References

- [Javascript interview questions](https://github.com/sudheerj/javascript-interview-questions)
- [Javascript questions](https://github.com/lydiahallie/javascript-questions)
- [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [The Modern JavaScript Tutorial](https://javascript.info/)

### Lí thuyết

#### 1. `scope` trong Javascript là gì ?

<details><summary><b>Đáp án</b></summary>
<p>

Scope là phạm vi của một biến được khai báo mà ta có thể truy cập được.

Scope trong JavaScript quyết định nơi các biến, hàm hoặc đối tượng có thể được truy cập hoặc thay đổi trong mã nguồn.
Scope giúp bảo vệ biến khỏi xung đột và làm cho mã dễ hiểu hơn.

Từ ES6 JavaScript có 4 loại `scope` chính:

- Global Scope (Phạm vi toàn cục).
- Function Scope (Phạm vi hàm).
- Block Scope (Phạm vi khối) - Được giới thiệu từ ES6.
- Module Scope (Phạm vi mô-đun)- Được giới thiệu từ ES6 modules.
    - Trước **ES6**, JavaScript không có cơ chế chính thức để chia nhỏ mã nguồn thành các đơn vị độc lập. Mọi thứ đều
      thuộc phạm vi toàn cục hoặc phạm vi hàm.
    - Với **ES6**, mô-đun (module) đã trở thành một phần của ngôn ngữ, và mỗi mô-đun có một phạm vi riêng, gọi
      là `module scope`.
    - Mỗi file JavaScript được xem như là một mô-đun, và các biến và hàm được khai báo trong mô-đun đó có phạm vi chỉ
      trong mô-đun đó.

> Lưu ý: Bất kỳ biến nào được khai báo bằng từ khóa `var`đều không thể có `block scope`. Do đó biến được khai báo bằng
> từ khóa `var` bên trong khối `{}` thì có thể được truy cập ở bên ngoài khối đó.

</p>
</details>

---

#### 2. So sánh sự khác nhau giữa `var | let | const` ?

<details><summary><b>Đáp án</b></summary>
<p>

- **`var`**:
    - Phạm vi: Global hoặc function scope.
    - Hoisting: Có hoisting (chuỗi khai báo được đưa lên đầu).
    - Có thể được khai báo lại và gán giá trị mới.

- **`let`**:
    - Phạm vi: Global, function, và block scope.
    - Hoisting: Có hoisting nhưng không thể sử dụng trước khai báo (biến ở trạng thái "temporal dead zone").
    - Có thể được khai báo lại trong khối khác nhưng không thể khai báo lại trong cùng một khối.

- **`const`**:
    - Phạm vi: Global, function, và block scope.
    - Hoisting: Có hoisting nhưng giống như `let`, không thể sử dụng trước khai báo.
    - Không thể được khai báo lại và giá trị không thể thay đổi (nhưng nếu là một đối tượng, thuộc tính vẫn có thể thay
      đổi).

> `let` và `const` được giới thiệu trong ES6, trong khi `var` là kiểu khai báo cũ hơn và ít an toàn hơn.

> Đối với `let` và `const`, mặc dù khai báo của chúng được `hoisted`, nhưng chúng không thể được sử dụng trước khi chúng
> được khai báo trong mã. Nếu bạn cố gắng truy cập vào một biến `let` hoặc `const` trước khi nó được khai báo, bạn sẽ
> gặp
> lỗi ReferenceError do Temporal Dead Zone ( vùng chết tạm thời).

</p>
</details>

---

#### 3. So sánh sự khác nhau giữa `isNaN` và `Number.isNaN` ?

NaN (Not-a-Number) được định nghĩa là một giá trị không phải là số. Một số biểu thức trong JavaScript sẽ trả về NaN, ví
dụ:

- Kết quả của phép chia `0/0`
- Kết quả của phép toán với một giá trị không phải là số, như `Math.sqrt(-1)`.

<details><summary><b>Đáp án</b></summary>
<p>

- `isNaN()` kiểm tra xem "giá trị này có chuyển được thành số hợp lệ không". Nếu không, trả về `true`.

```javascript
isNaN(NaN)//true (vì NaN không phải là số).
isNaN("abc")//true (vì khi cố gắng chuyển đổi "abc" thành số, nó trả về NaN).
isNaN(undefined)//true (vì undefined chuyển đổi thành NaN).
isNaN(123)//false (vì 123 là một số hợp lệ).
```

- `Number.isNaN()` không chuyển đổi giá trị truyền vào. Nó chỉ trả về `true` nếu giá trị đó thực sự là `NaN`.

```javascript
Number.isNaN(NaN)//true.
Number.isNaN(123)//false.
Number.isNaN("abc")//false (không chuyển đổi, "abc" không phải là NaN).
Number.isNaN(undefined)//false.
```

> Vấn đề lớn ở đây là `isNaN()` có thể trả về `true` cho những giá trị không phải là `NaN` thực sự (chẳng hạn như các
> giá trị không có khả năng chuyển đổi thành số).
>
> `Number.isNaN()` giúp lập trình viên xác định chính xác giá trị `NaN` mà không phải lo lắng về việc chuyển đổi kiểu dữ
> liệu không cần thiết. Đối với nhiều tình huống cần kiểm tra `NaN`, việc sử dụng `Number.isNaN()` là lựa chọn tốt hơn
> vì
> nó loại bỏ những trường hợp gây nhầm lẫn mà `isNaN()` có thể tạo ra.
</p>
</details>

---

#### 4. So sánh sự khác nhau giữa toán tử `==` và `===` là gì?

<details><summary><b>Đáp án</b></summary>
<p>

- `==` So sánh một cách gượng ép và trả kết quả về true nếu các biến có giá trị như nhau mà không cần trùng kiểu dữ
  liệu.
- `===` So sánh bằng tuyệt đối, nghĩa là toán tử này không chỉ so sánh các giá trị mà còn so sánh cả luôn kiểu dữ liệu
  của biến. Nếu không thỏa mãn cả 2 điều kiện trên thì chắc chắn kết quả trả về là `false`.

</p>
</details>

---

#### 5. So sánh sự khác nhau giữa `null` và `undefined` là gì?

<details><summary><b>Đáp án</b></summary>
<p>

- `null` có nghĩa là một giá trị rỗng hoặc không tồn tại. `null` được gán cho một biến như là một đại diện không có giá
  trị.

- `undefined` có nghĩa là không xác định. Trong javascript, khi bạn khai báo một biến nhưng chưa gán giá trị cho nó, giá
  trị của biến đó sẽ là `undefined`.

> - `undefined` và `null` đều là giá trị `falsy` khi sử dụng trong các điều kiện.
>
> - Khi so sánh với `==` (loose equality), `null` và `undefined` được coi là bằng nhau.
>
> - Khi sử dụng `===` (strict equality), chúng không được coi là bằng nhau, vì chúng có kiểu dữ liệu khác
    nhau (`undefined` là `undefined`, `null` là `object`).


</p>
</details>

---

#### 6. So sánh sự khác nhau giữa `slice` và `splice` ?

- slice
    - Cắt bỏ 1 phần của mảng
    - Tạo ra 1 mảng mới
    - Trả về mảng con mới từ mảng gốc

```javascript
array.slice(from, until)
```

- splice
    - Thêm hoặc xóa phần tử trong mảng
    - Thay đổi trực tiếp mảng gốc
    - Trả về mảng các phần tử đã xóa

```text
array.splice(index, number of elements);
```

#### 7. So sánh sự khác nhau giữa `Call | Apply | Bind` ?

**Call:** Gọi hàm và cho phép bạn truyền vào một object và các đối số phân cách nhau bởi dấu phẩy

```javascript
let name = {firstName: "David", lastName: "John"};

function sayName(param1, param2) {
    console.log(
        param1 + " " + this.firstName + " " + this.lastName + ", " + param2
    );
}

sayName.call(name, "Hello", "How are you?"); // Hello David John, How are you?
```

**Apply:** Tương tự như `call()`. Gọi hàm và cho phép bạn truyền vào một object và các đối số thông qua mảng

```javascript
let name = {firstName: "David", lastName: "John"};

function sayName(param1, param2) {
    console.log(
        param1 + " " + this.firstName + " " + this.lastName + ", " + param2
    );
}

invite.apply(name, ["Hello", "How are you?"]); // Hello David John, How are you?

```

**Bind:** Trả về một hàm mới, cho phép bạn truyền vào một object và các đối số phân cách nhau bởi dấu phẩy.

```javascript
let name = {firstName: "David", lastName: "John"};

function sayName(param1, param2) {
    console.log(
        param1 + " " + this.firstName + " " + this.lastName + ", " + param2
    );
}

let say = sayName.bind(name, "Hello", "How are you?");

say(); // Hello David John, How are you?
```

> Một lưu ý chung cho cả ba phương thức trên là this sẽ đề cập đến object mà ta truyền vào.
>
> `call`, `apply`, `bind` giúp chúng ta giải quyết vấn đề ngữ cảnh động của this trong javascript


**[⬆ Back to Top](#table-of-contents)**

#### 8. So sánh sự khác nhau giữa `Set | Map | Object` ?

<details><summary><b>Đáp án</b></summary>
<p>

- `Set`:
    - Là 1 collection dạng tập hợp, chứa các giá trị duy nhất.
    - Không lưu trữ theo cặp key-value.
    - Duy trì thứ tự chèn (insertion order).
- `Map` :
    - Là 1 collection dưới dạng `key-value`, chứa các giá trị duy nhất..
    - Cho phép bất kỳ kiểu dữ liệu nào làm key, không giới hạn như Object (chỉ chuỗi và Symbol).
    - Duy trì thứ tự các `key` truyền bào,
    - Không kế thừa thuộc tính từ Object.prototype nên tránh được các vấn đề liên quan đến xung đột tên.
- `Object`:
    - Một cấu trúc dữ liệu dạng `key-value`, nhưng key chỉ có thể là chuỗi hoặc Symbol.
    - Không đảm bảo thứ tự chèn cho các key là chuỗi (nhưng đảm bảo cho số nguyên).
    - Kế thừa các thuộc tính và phương thức từ Object.prototype, có thể gây ra xung đột tên nếu không cẩn thận.

```javascript
const mySet = new Set(['a', 'a', 'b', 1, 2, 1]);
console.log(mySet);  // {'a', 'b', 1, 2}

let myMap = new Map([['a', 111], ['b', 222]]);
console.log(myMap);  // {"a" => 111, "b" => 222}

let myObject = {a: 1, b: 2};
console.log(Object.keys(myObject)); // [a, b];
```

</p>
</details>

---

#### 9. `Temporal Dead Zone` (TDZ) là gì?

<details><summary><b>Đáp án</b></summary>
<p>

- Là vùng chết tạm thời trong `scope`, nơi biến được khai báo bằng let hoặc const không thể truy cập trước khi khởi tạo.
- Khi cố gắng truy cập biến trong TDZ, chương trình sẽ ném lỗi ReferenceError.

</p>

```javascript
function somethingDo() {
    console.log(numberFirst); // undefined
    console.log(numberSecond); // ReferenceError

    var numberFirst = 1;
    let numberSecond = 2;
}

somethingDo();
```

</details>

---

#### 10. Hoisting  là gì?

<details><summary><b>Đáp án</b></summary>
<p>

- Là cơ chế mà JavaScript đưa các khai báo (biến, hàm) lên đầu phạm vi `scope` trước khi thực thi mã.

> Lưu ý: Chỉ khai báo được hoisted, không phải giá trị.

- `var`:
    - `Hoisted` với giá trị mặc định `undefined`.
    - Không gây lỗi khi truy cập trước khi khai báo, nhưng giá trị là `undefined`.
- `let`, `const`:
    - Hoisted nhưng nằm trong TDZ (không được khởi tạo).
    - Gây lỗi `ReferenceError` nếu truy cập trước khi khai báo.
- Function Declarations:
    - Hoisted hoàn toàn, có thể gọi trước khi khai báo.
- Function Expressions và Arrow Functions:
    - Không hoisted; sẽ gặp ReferenceError nếu truy cập trước khi khai báo.

</p>

```javascript
console.log(a); // undefined (hoisting)
var a = 5;

console.log(b); // ReferenceError (TDZ)
let b = 10;

add(); // Chạy được (hoisting cho function declaration)
function add() {
    console.log('Adding');
}

sub(); // ReferenceError (function expression không hoisted)
const sub = () => console.log('Subtracting');
```

</details>

---

#### 11. Closures là gì?

<details><summary><b>Đáp án</b></summary>
<p>

- Closure là một hàm có thể ghi nhớ và truy cập phạm vi biến của hàm cha bao quanh nó ngay cả khi hàm cha đã kết thúc thực thi.
- Nói cách khác, `closure` "đóng gói" phạm vi tại thời điểm nó được tạo.

</p>

```javascript
function createCounter() {
    let count = 0; // Biến của hàm cha
    
    return function () {
        count++;
        return count;
    };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3

```

</details>

---

#### 12. Currying function  là gì?

```javascript

```

#### 13. Memoization  là gì?

```javascript

```

#### 14. setTimeout  là gì?

```javascript

```

#### 15. setInterval  là gì?

```javascript

```

#### 16. Callback là gì?

```javascript

```

#### 17. Promise là gì?

```javascript

```

#### 18. Async/Await là gì?

```javascript

```

#### 19. Call stack  là gì?

```javascript

```

#### 20. Heap là gì?

```javascript

```

#### 21. Event table là gì?

```javascript

```

#### 22. Event queue là gì?

```javascript

```

#### 23. Microtask queue là gì?

```javascript

```

#### 24. Event loop  là gì?

```javascript

```

#### 25. `observable` là gì?

```javascript

```

#### 26. So sánh `Promise.all | Promise.setted | Promise.race | Promise.any`  là gì?

```javascript

```

#### 27. So sánh `cookie | locale Storage | session Storage`  là gì?

```javascript

```

#### 28. Service worker là gì?

```javascript

```

#### 29. Phân biệt debouncing & throttling ?

```javascript

```

#### 30. Có những cách nào để execute các file js từ bên ngoài ?

- `<script>`: Với thẻ script không có thuộc tính gì khác thì trong quá trình phân tích cú pháp `HTML` nếu phải thẻ
  script, đến lúc này thì quá trình phân tích cú pháp `HTML` sẽ tạm dùng và để tải tệp js, sau đó thực thi luôn tệp js,
  rồi mới tiếp tục lại quá trình phân tích cú pháp `HTML`.
- `<script async>`: Tệp `js` được tải xuống song song cùng với quá trình phân tích cú pháp `HTML`. Sau khi hoàn tất tải
  xuống, tệp js sẽ thực thi, quá trình phân tích cú pháp `HTML` sẽ bị tạm ngừng cho tới khi tệp `js` thưc thi xong, thì
  mới tiếp tục.
- `<script defer>`: Tệp `js` được tải xuống song song cùng với quá trình phân tích cú pháp `HTML`. Và chỉ thực thi sau
  khi quá trình phân tích cú pháp `HTML` hoàn tất.

---

### Viết mã

#### 1. Output là gì?

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

#### 2. Output là gì?

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

#### 3. Output là gì?

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

#### 4. Output là gì?

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

#### 5. Output là gì?

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

#### 6. Output là gì?

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

#### 7. Output là gì?

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

#### 8. Output là gì?

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

#### 9. Output là gì?

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

#### 10. Output là gì?

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

#### 11. Output là gì?

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

#### 12. Output là gì?

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

#### 13. Output là gì?

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

#### 14. Output là gì?

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

[⬆ Back to Top](#title)

---

#### 15. Output là gì?

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

[⬆ Back to Top](#title)

---

#### 20. Output là gì?

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

[⬆ Back to Top](#title)

---

#### 21. Output sẽ là gì?

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

[⬆ Back to Top](#title)

---

#### 22. Output sẽ là gì?

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

[⬆ Back to Top](#title)

---

#### 23. Output sẽ là gì?

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

[⬆ Back to Top](#title)

---

#### 29. Output sẽ là gì?

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

[⬆ Back to Top](#title)

---

#### 30. Output sẽ là gì?

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

[⬆ Back to Top](#title)

---

#### 31. What is the time taken to execute below timeout callback?

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
