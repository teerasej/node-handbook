
# สร้างการทำงานของ Route Employee (Mongo)

เปิดไฟล์ `index.js`

## 1. เรียนใช้ Monk

```js
const db = require('monk')(`${MONGO_HOST}:${MONGO_PORT}/employeeDB`)
```

## 2. เพิ่มข้อมูล JSON จาก Request ลง Collection 

```js
app.post('/employees', async (req, res) => {
    
    const newEmployee = req.body;
    console.log('New employee:', newEmployee);
    
    // เรียกใช้ collection ชื่อ employees
    const employeeCollection = db.get('employees')

    // ส่ง json object เข้าไปใน collection
    // ผลลัพธ์ที่ได้ ก็คือ document ที่ insert ลงไปใน collection แล้ว (มี _id ติดมาด้วย)
    const insertedDocument = await employeeCollection.insert(newEmployee)

    res.json({ message: 'ok', doc: insertedDocument })
})
```

## 3. เขียนดึงข้อมูลจาก Database และคืนค่าเป็น JSON

```js
app.get('/employees', async (req, res) => {

     // เรียกใช้ collection ชื่อ employees
    const employeeCollection = db.get('employees')

    // ใช้ .find() เพื่อค้นหา collection ในที่นี้ไม่ได้กำหนดเงื่อนไข
    const collection = await employeeCollection.find({})

    res.json(collection);
})
```

## 5. ทดสอบด้วย POSTMan

## ไฟล์ index.js

```js
// เรียกใช้งาน environment variable
require('dotenv').config();

// เรียกใช้งาน express module 
const express = require('express');
const { enable } = require('express/lib/application');

let app = express();
const PORT = process.env.PORT

const MONGO_HOST = process.env.MONGO_DB_HOST
const MONGO_PORT = process.env.MONGO_DB_PORT

const db = require('monk')(`${MONGO_HOST}:${MONGO_PORT}/employeeDB`)

app.use(express.json());

// กำหนด route url 
app.get('/', (request, respond) => {
    respond.send('hello');
});

app.get('/employees', async (req, res) => {

    const employeeCollection = db.get('employees')
    const collection = await employeeCollection.find({})

    res.json(collection);
})

app.post('/employees', async (req, res) => {
    
    const newEmployee = req.body;
    console.log('New employee:', newEmployee);
    
    const employeeCollection = db.get('employees')
    const insertedDocument = await employeeCollection.insert(newEmployee)

    res.json({ message: 'ok', doc: insertedDocument })
})

// กำหนด port และเริ่มการทำงาน
app.listen(PORT, ()=>{
    console.log(`server is running at port http://localhost:${PORT}`);
})
```