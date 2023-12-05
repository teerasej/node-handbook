
# การติดตั้ง Module ด้วย NPM (Node Package Manager)

เราสามารถหา Node Module ได้จากเว็บไซต์ 

https://npmjs.com

## 1. คำสั่ง `NPM`

คำสั่ง `npm` ใช้ในการจัดการ Node module โดยเฉพาะ

เราสามารถดูคำสั่งของ npm ได้โดยใช้คำสั่ง 

```bash
npm --help
```

## 2. วิธีการติดตั้ง 

รันคำสั่ง

```bash
npm install [ชื่อ node module]
```

หรือแบบสั้นๆ

```bash
npm i [ชื่อ node module]
```

## 3. วิธีการติดตั้ง **Express** Module ในโปรเจค

ให้ทำการรันคำสั่งด้านล่างใน terminal ที่อยู่ใน directory ของโปรเจค Node.js ของเรา


เช่น 

```bash
npm i express
```

ตัว npm จะดาวน์โหลด และเอา Node module ชื่อ express และที่เกี่ยวข้องทั้งหมดมาที่ directory ที่ชื่อ `node_modules/`


## 4. ทดสอบเรียกใช้ module แบบ javascript

สร้างไฟล์ `index.js` และเขียน (หรือแทนที่โค้ดทั้งหมดในไฟล์เดิมด้วย) โค้ดด้านล่าง เสร็จแล้วให้บันทึกไฟล์ให้เรียบร้อย


```js
// index.js

const express = require('express');

const app = express();
app.get('/', (req, res) => {
    res.send('Hello World');
});

app.listen(3000, () => {
    console.log('Server is running on port 3000');
});
```

จากนั้นรันคำสั่ง

```bash
node index.js
```

ถ้าไม่มี error ขึ้นมาใน terminal ให้ลองเข้าไปที่ลิ้งค์ 

http://localhost:3000 

ใน browser ดูว่ามีข้อความ `Hello World` ขึ้นมาหรือไม่
