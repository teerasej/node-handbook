
# สร้างการทำงานของ Route Employee (MySQL)

เปิดไฟล์ `index.js`

## 1. เรียกใช้งาน 

```js
const dbpool = require('./db');
```

## 2. กำหนด middleware ให้ express 

เพื่อให้รับข้อมูลแบบ JSON และข้อมูลที่ส่งจากการ Submit Web Form ทั่วไปได้

```js
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
```

## 3. เขียนดึงข้อมูลจาก Database และคืนค่าเป็น JSON

```js
app.get('/employees', async (req, res) => {
    let pool = await dbpool;
    let sql = 'SELECT * FROM Employee';
    let items = await pool.query(sql,[]);
    console.log(items);
    res.json(items);
})
```

## 4. เขียนดึงข้อมูล JSON จาก Request และเพิ่มลงฐานข้อมูล

```js
app.post('/employees/create', async (req, res) => {

    let newEmployee = req.body;
    console.log(newEmployee);

    let pool = await dbpool;
    let sql = 'INSERT INTO Employee (first_name, last_name, email) VALUES (?,?,?)';
    let result = await pool.query(sql,[newEmployee.first_name, newEmployee.last_name, newEmployee.email]);
    console.log(result);

    if(result.affectedRows > 0){
        res.json({ success: true })
    } else {
        res.json({ success: false });
    }
    res.send('');
})
```

## 5. ทดสอบด้วย POSTMan

## ไฟล์ index.js

```js
const express = require('express');
const dbpool = require('./db');
let app = express();

app.use(express.json());
app.use(express.urlencoded({ extended: true }));


app.get('/', (request, respond) => {
    respond.send('Hello');
});


app.get('/employees', async (req, res) => {
    let pool = await dbpool;
    let sql = 'SELECT * FROM Employee';
    let items = await pool.query(sql,[]);
    console.log(items);
    res.json(items);
})

app.post('/employees/create', async (req, res) => {

    let newEmployee = req.body;
    console.log(newEmployee);

    let pool = await dbpool;
    let sql = 'INSERT INTO Employee (first_name, last_name, email) VALUES (?,?,?)';
    let result = await pool.query(sql,[newEmployee.first_name, newEmployee.last_name, newEmployee.email]);
    console.log(result);

    if(result.affectedRows > 0){
        res.json({ success: true })
    } else {
        res.json({ success: false });
    }
    res.send('');
})



app.listen(3000, ()=>{
    console.log('server is running at port 3000');
})
```