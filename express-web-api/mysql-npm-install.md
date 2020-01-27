
# ติดตั้ง และเขียน module ใช้งาน Promise MySQL

## 1. รันคำสั่งติดตั้ง module 

```bash
npm i promise-mysql
```

## 2. สร้างไฟล์ `db.js` เพื่อเขียนรายละเอียดของ Database Connection 

```js
var mysql = require('promise-mysql');

// กำหนด การเชื่อมต่อ 
const config = {
  host: 'localhost',
  port: '3306',
  user: 'root',
  password: 'root',
  database: 'company',
  connectionLimit: 100
};

let pool = mysql.createPool(config);
module.exports = pool;
```

### ค่าเริ่มต้นอ้างอิง

- MySQL Host เริ่มต้น: `localhost`
- MySQL Port เริ่มต้น: `3306`

- XAMPP (Windows)
  - User: `'root'`
  - Password: `''`

- MAMP (MacOS)
  - User: `'root'`
  - Password: `'root'`