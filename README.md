## Tổng hợp những câu hỏi JavaScript

### 1. Output là gì?

```javascript
var a = (!+[] + [] + ![]);

console.log(a.length);

```

<details><summary><b>Đáp án</b></summary>
<p>

#### Đáp án: 9

- +[]: [] là empty array, khi +[] sẽ ép kiểu về số có giá trị là 0.
- ! +[]: sẽ là true.
- true + []: "true".
- ![]: [] là giá trị truthy, nên ![] là false.
- "true" + false: "truefalse", nên a.length có gi trị là 9.

</p>
</details>

---

### 2. Output sẽ là gì?

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

#### Đáp án: C

- For 1:
    - setTimeout là một hàm bất đồng bộ, nên nó đưa các callback (hàm bên trong setTimeout) vào hàng đợi (queue) để thực
      thi sau khi call stack trống.
    - Trong khi các callback chờ được thực thi, vòng lặp for chạy đến hết (tăng i lên 3). Biến var có phạm vi toàn cục
      hoặc hàm (function scope). Trong vòng lặp for, chỉ có một biến i duy nhất được chia sẻ giữa tất cả các lần lặp.
    - Các callback trong setTimeout sẽ chạy sau khi vòng lặp kết thúc, nên tất cả chúng truy cập cùng một biến i đã được
      tăng lên 3.
- For 2:
    - setTimeout là một hàm bất đồng bộ, nên nó đưa các callback (hàm bên trong setTimeout) vào hàng đợi (queue) để thực
      thi sau khi call stack trống.
    - Trong khi các callback chờ được thực thi, vòng lặp for chạy. Biến let có phạm vi block (block scope). Trong vòng
      lặp for, mỗi lần lặp tạo ra một biến i mới, độc lập. Khi callback được tạo trong mỗi lần lặp, nó "ghi nhớ" (
      closure) giá trị hiện tại của i tại thời điểm callback được tạo.
    - Call stack trống, các callback chạy, chúng truy cập đúng giá trị của i được lưu trữ riêng trong từng vòng lặp.

</p>
</details>

---
