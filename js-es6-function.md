
# 4. JavaScirpt ES6 - Function 

การประกาศ Function แบบเดิม

```js
function plus(first, second) {
    return first + second;
}

console.log(plus(10,9)); // 19 
```

## 1. การประกาศแบบ Arrow Function

```js
let plus = (first, second) => {
    return first + second;
}

console.log(plus(10,9)); // 19 
```

## 2. รูปย่อของ Arrow Function

การประกาศแบบ Arrow Function ยังสามารถย่อรูปได้ด้วย เช่น

### แบบมี 1 parameter: ไม่จำเป็นต้องใส่ ()

ในกรณีที่ตัว function มี parameter เดียว เราสามารถละเว้นเครื่องหมาย `()` ออกได้

```js
let hello = name => {
    return "Hello, " + name;
}

console.log(hello('Pon')); // Hello, Pon
```

### แบบ return ค่าทันที

ในบางกรณี function ของเรา เขียนเพื่อคำนวนอะไรบางอย่าง และ return ค่าทันทีใน 1 statement 

ในกรณีนี้เราสามารถละเว้น keyword `return` และเครื่องหมาย `{}` ที่กำหนด scope ของ function ได้ 

#### เขียนแบบทั่วไป

```js
let hello = name => {
    return "Hello, " + name;
}

console.log(hello('Pon')); // Hello, Pon
```

#### เขียนแบบย่อ

```js
let hello = name => "Hello, " + name;

console.log(hello('Pon')); // Hello, Pon
```

