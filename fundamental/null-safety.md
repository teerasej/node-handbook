
# การทำงานกับค่า `undefined` หรือค่า `null`

## ความหมายของค่า `undefined` และ `null`

ค่า `undefined` และ `null` มีความหมายเหมือนกันคือ ค่าที่ไม่มีค่า หรือไม่มีข้อมูล แต่มีความแตกต่างกันคือ ค่า `undefined` จะเกิดขึ้นเมื่อเราไม่ได้กำหนดค่าให้กับตัวแปร หรือไม่ได้ return ค่าใดๆ จาก function ในขณะที่ `null` จะเกิดขึ้นเมื่อเรากำหนดค่าให้กับตัวแปรเป็น `null` โดยตรง

## 1. เปิดการทำงานของ strictNullChecks

เปิดไฟล์ `tsconfig.json` และเพิ่มค่า `strictNullChecks` ให้เป็น `true` เข้าไปในส่วน `compilerOptions` ดังตัวอย่าง 

และบันทึกไฟล์

```json
{
  "compilerOptions": {
    ...
    "strictNullChecks": true, 
    ...
  }
}
```

## 2. ประกาศตัวแปร nullable หรือ undefinedable

เขียนโค้ดต่อไปนี้ลงในไฟล์ `src/index.ts`

```ts
let counter: number = null;
```

จะเห็นว่ามี error ขึ้นมาว่า

```
Type 'null' is not assignable to type 'number'.
```

เพราะว่าตัวแปร `counter` มี type เป็น `number` แต่กำหนดค่าให้เป็น `null` ซึ่งไม่สามารถทำได้

ให้เราทำการปรับปรุงโค้ดให้เป็นดังนี้

```ts
let counter: number | null = null;
```

จะเห็นว่า error จะหายไป เพราะว่าเราได้บอกให้ TypeScript รู้ว่าตัวแปร `counter` นี้ อาจจะมีค่าเป็น `null` ได้


## 3. การเช็คค่า `null` ก่อนใช้งาน

### 3.1 การเช็คค่า `null` ด้วย `ternary operator`

เราสามารถเช็คค่า `null` ก่อนใช้งานได้ด้วยการใช้ `if` หรือ `ternary operator` ดังตัวอย่าง

```ts
let counter: number | null = null;

if (counter !== null) {
  counter++;
}

console.log(counter);
```

### 3.2 การเช็คค่า `null` ด้วย `Nullish Coalescing Operator`


เราสามารถเช็คค่า `null` ก่อนใช้งานได้ด้วยการใช้ `Nullish Coalescing Operator` ดังตัวอย่าง

```ts
let counter: number | null = null;

counter = counter ?? 100;

console.log(counter);
```

Nullish Coalescing Operator เป็นการกำหนดค่าเริ่มต้นให้กับตัวแปรที่อาจจะเป็น null หรือ undefined. ถ้าค่าที่ตรวจสอบเป็น null หรือ undefined, ค่าทางขวาของ operator จะถูกใช้.


## 4. การใช้ Optional Chaining Operator

เราสามารถเข้าถึง property หรือเรียก method ของ object ที่อาจจะเป็น null หรือ undefined ได้ด้วยการใช้ `Optional Chaining Operator` ดังตัวอย่าง

```ts
// สร้างไฟล์ src/count.ts

export let counter: number | null = null;
```

และทดสอบ import นำมาใช้งานในไฟล์ `src/index.ts`
เสร็จแล้วบันทึกไฟล์ และรันคำสั่ง `npm start` จะเห็นว่าไม่มี error ขึ้นมา แต่เราจะได้ค่า undefined ออกมาแทน

```ts
// index.ts
import { counter } from './count';

console.log(counter?.toFixed(2));
```

Optional Chaining Operator ใช้เมื่อต้องการเข้าถึง property หรือเรียก method ของ object ที่อาจจะเป็น null หรือ undefined. ถ้าค่าที่เรียกเป็น null หรือ undefined, การดำเนินการจะหยุดและคืนค่า undefined.



