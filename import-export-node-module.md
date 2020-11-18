
# การใช้ keyword import และ export ใน Node.js

**ข้อมูลนี้ใช้ได้กับ Node 13.2 เป็นต้นไป**

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
const hello = () => {
    console.log('hello');
}

export { hello };
```

## 3. ใช้คำสั่ง import กับ module ที่ต้องการได้เลย

- ต้องกำหนดชื่อไฟล์โดยตรง เช่น `./func.mjs` ใช้รูปย่อไม่ได้ เช่น `./func` 

```js
// index.js

import { hello } from './func.mjs';

hello();
```