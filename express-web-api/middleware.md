
# เรียนรู้ และใช้งาน Middleware

1. เปิดไฟล์ **index.js**
2. เราจะสร้าง middleware function ถัดจากคำสั่งที่สร้างตัวแปร `app`

```js
const express = require('express');
let app = express();


app.use((req, res, next)=>{
    console.log(`Got a request, ${new Date()}`)
})
```

3. บันทึกไฟล์ และทดสอบการทำงาน

## การเขียน และใช้งาน Middleware

- Middleware คือ function ที่รับค่าเข้ามา 3 ตัวคือ
  - `request` (`req`): ข้อมูลที่ส่งมาจาก Client
  - `response` (`res`): ตัวแปรที่ใช้ตอบกลับ client
  - `next`: เป็น function ที่สั่งให้การทำงานของ web server ส่ง request ไปที่ route หรือ middleware อื่นต่อ
- การใช้ middleware กับตัว `app` จะทำผ่าน `app.use(function)`


## ตัวอย่าง middleware
```js
app.use((req, res, next) => {

    // เมื่อสิ้นสุดการทำงานของ middleware ค่อยปล่อยผ่านไปต่อ
    next();
})
```