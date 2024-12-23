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

<details><summary><b>Đáp án</b></summary>
<p>

NaN (Not-a-Number) được định nghĩa là một giá trị không phải là số. Một số biểu thức trong JavaScript sẽ trả về NaN, ví
dụ:

- Kết quả của phép chia `0/0`
- Kết quả của phép toán với một giá trị không phải là số, như `Math.sqrt(-1)`.

`isNaN()` kiểm tra xem "giá trị này có chuyển được thành số hợp lệ không". Nếu không, trả về `true`.

```javascript
isNaN(NaN)//true (vì NaN không phải là số).
isNaN("abc")//true (vì khi cố gắng chuyển đổi "abc" thành số, nó trả về NaN).
isNaN(undefined)//true (vì undefined chuyển đổi thành NaN).
isNaN(123)//false (vì 123 là một số hợp lệ).
```

`Number.isNaN()` không chuyển đổi giá trị truyền vào. Nó chỉ trả về `true` nếu giá trị đó thực sự là `NaN`.

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
**[⬆ Back to Top](#title)**

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
**[⬆ Back to Top](#title)**

#### 6. So sánh sự khác nhau giữa `slice` và `splice` ?

<details><summary><b>Đáp án</b></summary>
<p>

- `slice`
    - Cắt bỏ 1 phần của mảng
    - Tạo ra 1 mảng mới
    - Trả về mảng con mới từ mảng gốc

```javascript
array.slice(from, until)
```

- `splice`
    - Thêm hoặc xóa phần tử trong mảng
    - Thay đổi trực tiếp mảng gốc
    - Trả về mảng các phần tử đã xóa

```text
array.splice(index, number of elements);
```

</p>
</details>

---
**[⬆ Back to Top](#title)**

#### 7. So sánh sự khác nhau giữa `Call | Apply | Bind` ?

<details><summary><b>Đáp án</b></summary>
<p>

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

</p>
</details>

---


**[⬆ Back to Top](#title)**

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
**[⬆ Back to Top](#title)**

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
**[⬆ Back to Top](#title)**

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
**[⬆ Back to Top](#title)**

#### 11. Closures là gì?

<details><summary><b>Đáp án</b></summary>
<p>

- Closure là một hàm có thể ghi nhớ và truy cập phạm vi biến của hàm cha bao quanh nó ngay cả khi hàm cha đã kết thúc
  thực thi.
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

**[⬆ Back to Top](#title)**

#### 12. Higher Order Function(HOF) là gì?

<details><summary><b>Đáp án</b></summary>
<p>

Higher Order Function (HOF) là một hàm nhận tham số đầu vào là một `funciton` hoặc trả về kết quả là một `function` hoặc
cả hai.

- HOF giúp chúng ta viết mã dễ đọc, dễ bảo trì và tái sử dụng.
- Các phương thức như `map`, `filter`, `reduce` là các ví dụ phổ biến của HOF.

```javascript
function greet(name) {
    return `Hello, ${name}`;
}

function greetUser(greet) {
    return greet('Alice');
}

console.log(greetUser(greet)); // Hello, Alice
```

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 13. Currying function  là gì?

<details><summary><b>Đáp án</b></summary>
<p>

Currying là một kỹ thuật trong lập trình hàm, nó chuyển đổi một hàm nhận nhiều tham số thành chuỗi các hàm mỗi hàm chỉ
nhận một tham số. Khi tất cả các tham số đã được truyền vào, hàm gốc sẽ được gọi.

- Currying giúp chúng ta tạo ra các hàm mà chúng ta có thể sử dụng lại với các tham số khác nhau.

```javascript
function multiply(a, b, c) {
    return a * b * c;
}

console.log(multiply(2, 3, 4)); // 24

function multiply(a) {
    return function (b) {
        return function (c) {
            return a * b * c;
        };
    };
}

console.log(multiply(2)(3)(4)); // 24

```

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 13. Memoization  là gì?

<details><summary><b>Đáp án</b></summary>
<p>
Memoization là một kỹ thuật lưu trữ kết quả của các hàm gọi lại với các tham số giống nhau để giảm thời gian tính toán.

- Khi hàm được gọi với tham số đã được lưu trữ, kết quả sẽ được trả về từ bộ nhớ cache thay vì tính toán lại.
- Memoization giúp tăng tốc độ tính toán của hàm, đặc biệt là với các hàm đệ quy hoặc hàm có thời gian chạy lớn.
- Có thể sử dụng một object hoặc một Map để lưu trữ kết quả của hàm.
- Memoization thường được sử dụng trong các hàm đệ quy, hàm tính toán phức tạp, hoặc hàm truy cập dữ liệu từ API.

```javascript
function memoize(fn) {
    const cache = {};
    return function (...args) {
        const key = JSON.stringify(args);
        if (cache[key]) {
            console.log('Fetching from cache');
            return cache[key];
        } else {
            const result = fn(...args);
            cache[key] = result;
            return result;
        }
    };
}

function sum(a, b) {
    console.log('Calculating sum');
    return a + b;
}

const memoizedSum = memoize(sum);
console.log(memoizedSum(2, 3)); // Calculating sum
```

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 14. setTimeout  là gì?

<details><summary><b>Đáp án</b></summary>
<p>

`setTimeout` là một hàm trong JavaScript cho phép bạn thực thi một hàm hoặc một đoạn mã sau một khoảng thời gian nhất
định.

- `setTimeout` trả về một `timeoutID` mà bạn có thể sử dụng để hủy thực thi của hàm hoặc đoạn mã đó.
- Thời gian truyền vào `setTimeout` được đo bằng mili giây.
- `setTimeout` không đảm bảo thời gian chính xác mà hàm sẽ được thực thi, nó chỉ đảm bảo rằng hàm sẽ không được thực thi
  trước thời gian đã định.

```javascript
setTimeout(() => {
    console.log('Hello, World!');
}, 1000);

const timeoutID = setTimeout(() => {
    console.log('This will not be printed');
}, 1000);

clearTimeout(timeoutID); // Hủy thực thi của hàm trên

```

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 15. setInterval  là gì?

<details><summary><b>Đáp án</b></summary>
<p>

`setInterval` là một hàm trong JavaScript cho phép bạn thực thi một hàm hoặc một đoạn mã sau một khoảng thời gian nhất
định, và lặp lại sau mỗi khoảng thời gian đó.

- `setInterval` trả về một `intervalID` mà bạn có thể sử dụng để hủy thực thi của hàm hoặc đoạn mã đó.
- Thời gian truyền vào `setInterval` được đo bằng mili giây.
- `setInterval` không đảm bảo thời gian chính xác mà hàm sẽ được thực thi, nó chỉ đảm bảo rằng hàm sẽ được thực thi sau
  mỗi khoảng thời gian đã định.

```javascript
let count = 0;
const intervalID = setInterval(() => {
    count++;
    console.log(count);
    if (count === 5) {
        clearInterval(intervalID); // Hủy thực thi của hàm trên
    }
}, 1000);

```

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 16. Callback là gì?

<details><summary><b>Đáp án</b></summary>
<p>

`Callback` là một function, được truyền vào một function khác như một tham số, và được gọi sau khi một tác vụ hoàn
thành.

`Callback` được sử dụng trong các trường hợp cần xử lý đồng bộ, bất đồng bộ hoặc quản lý các nhiệm vụ nối tiếp nhau.

Ứng dụng của Callback:

- Gọi hàm khi sự kiện xảy ra: Như khi nhấn một nút, hoặc khi xử lý các thao tác bất đồng bộ như đọc dữ liệu từ API hoặc
  cơ sở dữ liệu.

- Giải quyết vấn đề đồng bộ: Giúp điều khiển luồng logic giữa nhiều tác vụ độc lập, giúp tránh lỗi chờ đợi.

```javascript
function greet(name, callback) {
    console.log(`Hello, ${name}`);
    callback();
}

greet('Alice', function () {
    console.log('This is a callback function.');
});

```

> Khi sử dụng quá nhiều `callback`, một vấn đề phức tạp gọi là `Callback Hell` có thể xuất hiện, làm cho code khó quản
> lý và theo dõi.
>
> Giải pháp thay thế: Promise, Async/Await.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 17. Promise là gì?

<details><summary><b>Đáp án</b></summary>
<p>

`Promise` là một object đại diện cho việc hoàn thành kết quả (hoặc sự thất bại) từ một lệnh bất đồng bộ, và giá trị kết
quả của lệnh đó.

Nó được sử dụng để xử lý các hoạt động không đồng bộ, chẳng hạn như thực hiện lệnh gọi API hoặc đọc tệp, theo cách có tổ
chức và dễ đọc hơn.
</p>

Một `Promise` có thể ở một trong những trạng thái sau:

- **Fulfilled** : trạng thái đã được thực hiện thành công.
- **Rejected** : trạng thái đã thất bại.
- **Pending** : trạng thái ban đầu, chưa được thực hiện hoặc bị từ chối.

`Promise` giúp xử lý các tác vụ bất đồng bộ bằng cách cung cấp các phương thức sau:

- **`.then()`**: Xử lý khi Promise được giải quyết thành công.
- **`.catch()`**: Xử lý khi Promise bị từ chối (có lỗi).
- **`.finally()`**: Thực thi bất kể Promise thành công hay thất bại.

```javascript
myPromise
    .then(result => console.log("Kết quả:", result))
    .catch(error => console.error("Lỗi:", error))
    .finally(() => console.log("Hoàn tất xử lý!"));

```

</details>

---

**[⬆ Back to Top](#title)**

#### 18. Async/Await là gì?

<details><summary><b>Đáp án</b></summary>
<p>

`Async/Await` là một cú pháp mới trong JavaScript giúp xử lý các hàm bất đồng bộ một cách dễ đọc và dễ quản lý hơn.

- `Async` là một từ khóa được sử dụng để định nghĩa một hàm bất đồng bộ, trả về một `Promise`.
- `Await` là một từ khóa được sử dụng bên trong hàm `async` để đợi cho một `Promise` được giải quyết hoặc bị từ chối.
- `Await` chỉ có thể được sử dụng bên trong hàm `async`.
- `Async/Await` giúp tránh `Callback Hell` và giúp code dễ đọc hơn so với `Promise`.
- `Async/Await` giúp xử lý các lỗi bằng cách sử dụng `try/catch`.
- `Async/Await` giúp viết code đồng bộ trong khi vẫn sử dụng các hàm bất đồng bộ.
- `Async/Await` giúp viết code dễ đọc hơn, dễ bảo trì và dễ theo dõi hơn so với `Promise`.
- `Async/Await` không thay thế `Promise`, mà là một cách viết code bất đồng bộ dễ đọc hơn.

```javascript
async function fetchData() {
    try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error('Error:', error);
    }
}

fetchData();

```

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 19. Call stack  là gì?

<details><summary><b>Đáp án</b></summary>
<p>

`Call stack` la một cấu trúc dữ liệu cho trình thông dịch JavaScript để theo dõi các hàm đang chờ thực thi.

- Khi một hàm được gọi, nó sẽ được đẩy vào đỉnh của `call stack`.
- Khi hàm hoàn thành thực thi, nó sẽ được loại bỏ khỏi `call stack`.
- `Call stack` hoạt động theo nguyên tắc "LIFO" (Last In, First Out), nghĩa là hàm cuối cùng được thêm vào `call stack`
  sẽ được thực thi đầu tiên.

```javascript
function multiply(a, b) {
    return a * b;
}

function square(n) {
    return multiply(n, n);
}

function printSquare(n) {
    const squared = square(n);
    console.log(squared);
}

printSquare(5);

```

- Khi `printSquare(5)` được gọi, nó sẽ được đẩy vào `call stack`.
- `printSquare(5)` gọi `square(5)`, nó sẽ được đẩy vào `call stack`.
- `square(5)` gọi `multiply(5, 5)`, nó sẽ được đẩy vào `call stack`.
- `multiply(5, 5)` trả về 25, và được loại bỏ khỏi `call stack`.
- `square(5)` trả về 25, và được loại bỏ khỏi `call stack`.
- `printSquare(5)` in ra 25, và được loại bỏ khỏi `call stack`.
- `call stack` trống.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 20. Heap là gì?

<details><summary><b>Đáp án</b></summary>
<p>

Heap hoặc (Heap bộ nhớ) là nơi lưu trữ dữ liệu động, bao gồm các đối tượng và các mảng. Đây là nơi diễn ra các lần phân
bổ và giải phóng bộ nhớ. Cả `heap` và `call stack `đều là một phần của bộ nhớ trong trình thông dịch JavaScript.

- Heap không có cấu trúc dữ liệu cụ thể, dữ liệu được lưu trữ theo cách không có thứ tự.
- Heap được sử dụng để lưu trữ dữ liệu động được tạo ra trong quá trình thực thi của chương trình.
- Heap được chia thành hai phần: Heap được quản lý và Heap không được quản lý.
- Heap được quản lý: Là phần của Heap được sử dụng để lưu trữ dữ liệu được cấp phát và giải phóng bởi trình thông dịch
  JavaScript.
- Heap không được quản lý: Là phần của Heap không được sử dụng để lưu trữ dữ liệu được cấp phát và giải phóng bởi trình
  thông dịch JavaScript.

```javascript
let object = {name: 'Alice'};
let array = [1, 2, 3];

```

- Khi `object` và `array` được khởi tạo, chúng sẽ được lưu trữ trong Heap.
- Khi chúng không còn được sử dụng, chúng sẽ được giải phóng khỏi Heap.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 21. Event table là gì?

<details><summary><b>Đáp án</b></summary>
<p>

Event table là một cấu trúc dữ liệu trong trình thông dịch JavaScript để theo dõi các sự kiện và callback của chúng.

- Khi một sự kiện xảy ra, nó sẽ được thêm vào `event table` với một callback tương ứng.
- Khi sự kiện được kích hoạt, callback tương ứng sẽ được thêm vào `call stack` để thực thi.

```javascript
document.getElementById('myButton').addEventListener('click', function () {
    console.log('Button clicked!');
});


```

- Khi nút được nhấn, sự kiện `click` sẽ được thêm vào `event table` với callback
  là `function () { console.log('Button clicked!'); }`.
- Khi sự kiện được kích hoạt, callback sẽ được thêm vào `call stack` để thực thi.
- Callback sẽ in ra `Button clicked!` trên console.
- Callback sẽ được loại bỏ khỏi `call stack`.
- `call stack` trống.
- `event table` trống.
- Quá trình hoàn tất.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 22. Event queue là gì?

<details><summary><b>Đáp án</b></summary>
<p>

`Event queue` là một cấu trúc dữ liệu trong trình thông dịch JavaScript để theo dõi các sự kiện và callback của chúng.

- Khi một sự kiện xảy ra, nó sẽ được thêm vào `event queue` với một callback tương ứng.
- Khi `call stack` trống, sự kiện đầu tiên trong `event queue` sẽ được thêm vào `call stack` để thực thi.

```javascript

setTimeout(() => {
    console.log('Hello, World!');
}, 1000);


```

- Khi `setTimeout` được gọi, sự kiện `setTimeout` sẽ được thêm vào `event queue` với callback
  là `function () { console.log('Hello, World!'); }`.
- Sau 1 giây, sự kiện `setTimeout` sẽ được thêm vào `call stack` để thực thi.
- Callback sẽ in ra `Hello, World!` trên console.
- Callback sẽ được loại bỏ khỏi `call stack`.
- `call stack` trống.
- `event queue` trống.
- Quá trình hoàn tất.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 23. Microtask queue là gì?

<details><summary><b>Đáp án</b></summary>
<p>

`Microtask queue` là một cấu trúc dữ liệu trong trình thông dịch JavaScript để theo dõi các microtask.

- Microtask là các tác vụ nhỏ được thực thi sau khi `call stack` trống, trước khi thực thi các sự kiện
  trong `event queue`.
- Microtask thường được tạo bởi `Promise`, `process.nextTick`, `queueMicrotask`, `MutationObserver`.

```javascript
Promise.resolve().then(() => console.log('Microtask 1'));
Promise.resolve().then(() => console.log('Microtask 2'));

```

- Khi `Promise.resolve().then()` được gọi, microtask 1 và microtask 2 sẽ được thêm vào `microtask queue` với callback tương ứng.
- Khi `call stack` trống, microtask 1 sẽ được thêm vào `call stack` để thực thi.
- Callback sẽ in ra `Microtask 1` trên console.Sau đó sẽ được loại bỏ khỏi `call stack`.
- Khi `call stack` trống, microtask 2 sẽ được thêm vào `call stack` để thực thi.
- Callback sẽ in ra `Microtask 2` trên console. Sau đó sẽ được loại bỏ khỏi `call stack`.
- `call stack` trống.
- `microtask queue` trống.
- Quá trình hoàn tất.
- `event queue` trống.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 24. Event loop  là gì?

<details><summary><b>Đáp án</b></summary>
<p>

Event loop là một cơ chế trong trình thông dịch JavaScript để theo dõi và thực thi các sự kiện, callback, và microtask.

- Event loop giữ cho `call stack` trống bằng cách thực thi các sự kiện trong `event queue` và `microtask queue`.
- Event loop sẽ thực thi các sự kiện trong `event queue` trước, sau đó thực thi các microtask trong `microtask queue`.
- Event loop giúp tránh `blocking` trong JavaScript, giúp chương trình chạy mượt mà và không bị treo.

```javascript
setTimeout(() => {
    console.log('Hello, World!');
}, 1000);



```

- Khi `setTimeout` được gọi, sự kiện `setTimeout` sẽ được thêm vào `event queue` với callback
  là `function () { console.log('Hello, World!'); }`.
- Sau 1 giây, sự kiện `setTimeout` sẽ được thêm vào `call stack` để thực thi.
- Callback sẽ in ra `Hello, World!` trên console.
- Callback sẽ được loại bỏ khỏi `call stack`.
- `call stack` trống.
- `event queue` trống.
- Quá trình hoàn tất.
- `microtask queue` trống.
- `event loop` sẽ tiếp tục theo dõi các sự kiện và microtask khác.
- `event loop` sẽ thực thi các microtask trước, sau đó thực thi các sự kiện trong `event queue`.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 25. `observable` là gì?

<details><summary><b>Đáp án</b></summary>
<p>

Observable là một giao thức hoặc một mẫu thiết kế cho việc xử lý các sự kiện và dữ liệu bất đồng bộ.

- Observable giúp theo dõi và xử lý các sự kiện và dữ liệu bất đồng bộ một cách dễ dàng và linh hoạt.
- Observable giúp xử lý các sự kiện và dữ liệu bất đồng bộ một cách dễ dàng và linh hoạt.

```javascript
const observable = new Observable(observer => {
    observer.next('Hello, World!');
    observer.complete();
});
```

- Khi `observable` được tạo, nó sẽ gọi hàm `Observable` với một `observer`.
- `observer` sẽ gọi `next` với giá trị `Hello, World!`.
- `observer` sẽ gọi `complete` để kết thúc observable.
- Observable sẽ hoàn tất.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 26. So sánh `Promise.all | Promise.setted | Promise.race | Promise.any`  là gì?

<details><summary><b>Đáp án</b></summary>
<p>

- `Promise.all`: Trả về một `Promise` khi tất cả các `Promise` con đã được giải quyết thành công. Nếu một trong
  các `Promise` con bị từ chối, `Promise.all` sẽ bị từ chối.
- `Promise.settled`: Trả về một `Promise` khi tất cả các `Promise` con đã được giải quyết hoặc bị từ
  chối. `Promise.settled` sẽ trả về một mảng chứa kết quả hoặc lỗi của từng `Promise` con.
- `Promise.race`: Trả về một `Promise` khi một trong các `Promise` con đã được giải quyết hoặc bị từ
  chối. `Promise.race` sẽ trả về kết quả hoặc lỗi của `Promise` con đầu tiên được giải quyết hoặc bị từ chối.
- `Promise.any`: Trả về một `Promise` khi một trong các `Promise` con đã được giải quyết thành công. `Promise.any` sẽ
  trả về kết quả của `Promise` con đầu tiên được giải quyết thành công.

```javascript

const promise1 = new Promise((resolve, reject) => setTimeout(resolve, 100, 'Promise 1'));
const promise2 = new Promise((resolve, reject) => setTimeout(resolve, 200, 'Promise 2'));
const promise3 = new Promise((resolve, reject) => setTimeout(reject, 300, 'Promise 3'));

Promise.all([promise1, promise2])
    .then(values => console.log(values))
    .catch(error => console.error(error));

Promise.settled([promise1, promise2, promise3])
    .then(values => console.log(values))
    .catch(error => console.error(error));

Promise.any([promise1, promise2, promise3])
    .then(value => console.log(value))
    .catch(error => console.error(error));

Promise.race([promise1, promise2, promise3])
    .then(value => console.log(value))
    .catch(error => console.error(error));

```

- `Promise.all` sẽ in ra `['Promise 1', 'Promise 2']`.
- `Promise.settled` sẽ in ra `['Promise 1', 'Promise 2', 'Promise 3']`.
- `Promise.any` sẽ in ra `'Promise 1'`.
- `Promise.race` sẽ in ra `'Promise 1'`.

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 27. So sánh `cookie | locale Storage | session Storage`  là gì?

<details><summary><b>Đáp án</b></summary>
<p>

Cookie, localStorage, và sessionStorage là các cách lưu trữ dữ liệu trong trình duyệt.

- `Cookie`: Lưu trữ dữ liệu dưới dạng chuỗi với dung lượng tối đa 4KB. Cookie được gửi từ máy chủ đến trình duyệt và
  được lưu trữ trên máy khách. Cookie có thể được sử dụng để xác thực, theo dõi, và lưu trữ thông tin người dùng.
- `localStorage`: Lưu trữ dữ liệu dưới dạng chuỗi với dung lượng tối đa 5MB. localStorage lưu trữ dữ liệu trên máy khách
  và không bao giờ hết hạn, trừ khi người dùng xóa nó hoặc xóa dữ liệu duyệt.
- `sessionStorage`: Lưu trữ dữ liệu dưới dạng chuỗi với dung lượng tối đa 5MB. sessionStorage lưu trữ dữ liệu trên máy
  khách và sẽ bị xóa khi cửa sổ trình duyệt đóng.

```javascript
// Cookie
document.cookie = 'name=Alice';
console.log(document.cookie); // 'name=Alice'

// localStorage
localStorage.setItem('name', 'Alice');
console.log(localStorage.getItem('name')); // 'Alice'

// sessionStorage
sessionStorage.setItem('name', 'Alice');
console.log(sessionStorage.getItem('name')); // 'Alice'


```

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 28. Service worker là gì?

<details><summary><b>Đáp án</b></summary>
<p>

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 29. Phân biệt debouncing & throttling ?

<details><summary><b>Đáp án</b></summary>
<p>

</p>

</details>

---

**[⬆ Back to Top](#title)**

#### 30. Các cách nhúng và thực thi tệp JavaScript trong HTML là gì? Giải thích sự khác biệt giữa `<script>`, `<script async>`,  `<script defer>` ?

<details><summary><b>Đáp án</b></summary>
<p>

Trong HTML, bạn có thể nhúng và thực thi tệp JavaScript thông qua thẻ `<script>`. Tuy nhiên, cách tệp JavaScript được
tải xuống và thực thi phụ thuộc vào thuộc tính của thẻ `<script>`:

- `<script>`:
    - Khi trình duyệt gặp thẻ `<script>`, nó sẽ dừng phân tích cú pháp HTML.
    - Tệp JavaScript được tải xuống và thực thi ngay lập tức.
    - Sau khi thực thi xong, quá trình phân tích cú pháp HTML tiếp tục.

> Chỉ dùng nếu JavaScript phải được thực thi ngay lập tức và ảnh hưởng trực tiếp đến nội dung HTML phía dưới.

- `<script async>`:
    - Tệp JavaScript được tải xuống song song (asynchronously) trong khi HTML vẫn tiếp tục được phân tích cú pháp.
    - Khi tệp JavaScript được tải xong, nó sẽ được thực thi ngay lập tức, tạm dừng HTML parsing.

> Thứ tự thực thi không được đảm bảo. Thích hợp với các tệp JavaScript không phụ thuộc vào nội dung HTML hoặc không phụ
> thuộc thứ tự với các script khác.

- Tệp `js` được tải xuống song song cùng với quá trình phân tích cú pháp `HTML`. Sau khi hoàn tất tải
  xuống, tệp js sẽ thực thi, quá trình phân tích cú pháp `HTML` sẽ bị tạm ngừng cho tới khi tệp `js` thưc thi xong, thì
  mới tiếp tục.
- `<script defer>`:
    - Tệp JavaScript được tải xuống song song trong khi HTML vẫn đang được phân tích cú pháp.
    - Tệp JavaScript chỉ được thực thi sau khi HTML parsing hoàn tất.

> Thích hợp với các tệp JavaScript phụ thuộc vào cấu trúc HTML nhưng không cần thực thi ngay lập tức.

</p>

</details>

---

**[⬆ Back to Top](#title)**

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

#### 32. Output sẽ là gì??

```javascript
const obj = {
    a: 1,
    b: {
        valueOf: () => 2
    }
};

console.log(obj.a + obj.b);

```

- A: 3
- B: 12
- C: undefined
- D: NaN

<details><summary><b>Đáp án</b></summary>
<p>

```text
A: 3
```

- Khi thưc hiện phép cộng `obj.a + obj.b`, JavaScript sẽ chuyển đổi `obj.a` và `obj.b` thành số.
- Đối với `obj.a`, giá trị là 1, không cần chuyển đổi. Đối với `obj.b`, JavaScript sẽ gọi phương thức `valueOf` của
  object `obj.b`, trả về giá trị 2, và kết quả của phép cộng là 3.

> Nếu `valueOf` không được định nghĩa, JavaScript sẽ thử chuyển đổi object thành chuỗi bằng phương thức `toString`.
>
> Nếu cả `valueOf` và `toString` trả về giá trị không phải là số, kết quả sẽ là `NaN`.


</p>
</details>

[⬆ Back to Top](#title)

---
