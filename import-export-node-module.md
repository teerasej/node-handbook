
# การใช้ keyword import และ export ใน Node.js

**ข้อมูลนี้ใช้ได้กับ Node 14 เป็นต้นไป**

keyword `import` และ `export` ได้รับความนิยมมากขึ้นในการทำงานกับ module ใน Node.js การจะใช้งานได้ ต้องทำตามขั้นตอนต่อไปนี้


## 1. เพิ่มค่า settting ใน package.json

```js
// package.json
{
  ...
  "type": "module"
}

```

## 2. ตั้งชื่อไฟล์ที่ต้องการเป็น .mjs

แล้วสามารถใช้ `export` กับส่วนที่ต้องการได้เลย

```js
// func.mjs
export const hello = () => {
    console.log('hello');
}

export default {
  sayHello: hello
}
```

## 3. ใช้คำสั่ง import กับ module ที่ต้องการได้เลย

- ปัจจุบันต้องกำหนดชื่อไฟล์โดยตรง เช่น `./func.mjs` ใช้รูปย่อไม่ได้แบบด้านขวาไม่ได้ --> `./func` 

```js
// index.js

import Greeting, { hello } from './func.mjs';

hello();
Greeting.sayHello();
```