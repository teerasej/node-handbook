
# กำหนด Route สำหรับแสดงข้อมูลพนักงาน และเพิ่มพนักงานใหม่

1. เปิดไฟล์ `index.js`
2. เพิ่ม route GET และ POST
   
```js
app.get('/employees', async (req, res) => {
    res.json({});
})

app.post('/employees', async (req, res) => {
    res.json(req.body);
})
```

## ไฟล์ index.js

```js
const express = require('express');
let app = express();

app.get('/', (request, respond) => {
    respond.send('Hello');
});

app.get('/employees', async (req, res) => {
    res.json({});
})

app.post('/employees', async (req, res) => {
    res.json(req.body);
})


app.listen(3000, ()=>{
    console.log('server is running at port 3000');
})
```
