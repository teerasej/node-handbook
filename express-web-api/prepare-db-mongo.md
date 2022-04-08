
# เตรียมการเชื่อมต่อ Mongo


## ติดตั้ง package 

ในที่นี้เราจะติดตั้ง package 

```
npm i monk
```

## กำหนดค่า environment

เพิ่มค่า variable ในไฟล์ `.env`

```
MONGO_DB_HOST=localhost
MONGO_DB_PORT=27017
```

และเราจะทำการดึงค่า environment มาใช้ในไฟล์ `index.js`

```js
require('dotenv').config();

const express = require('express');
let app = express();
const PORT = process.env.PORT

// เรียกค่า environment variable สำหรับใช้กับ MongoDB
const MONGO_HOST = process.env.MONGO_DB_HOST
const MONGO_PORT = process.env.MONGO_DB_PORT
```


