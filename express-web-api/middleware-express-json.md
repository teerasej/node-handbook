
# ถอดข้อมูล JSON จาก Request ด้วย Middleware

เราสามารถใช้ Middleware function ของ Express สำหรับการถอดข้อมูล json จาก request

```js
// index.js

const express = require('express');
let app = express();

// ใช้ Express Middleware ในการรับ json 
app.use(express.json());

// ใช้ Express Middleware ในการรับ form data
app.use(express.urlencoded({ extended: true }));

//....

app.post('/employees', async (req, res) => {

    // เราสามารถดึง json จาก request.body ได้
    const body = req.body;
})
```

