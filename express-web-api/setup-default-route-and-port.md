
# กำหนด Route URL และเริ่มกำหนด port เพื่อเริ่มการทำงาน

1. เปิดไฟล์ `index.js`
2. เขียนกำหนดการทำงานของ Web API

```js
// เรียกใช้งาน environment variable
require('dotenv').config();

// เรียกใช้งาน express module 
const express = require('express');
let app = express();
const PORT = process.env.PORT

// กำหนด route url 
app.get('/', (request, respond) => {
    respond.send('hello');
});

// กำหนด port และเริ่มการทำงาน
app.listen(PORT, ()=>{
    console.log(`server is running at port http://localhost:${PORT}`);
})
```

3. ทดสอบรันการทำงาน ด้วยคำสั่ง 

```bash
nodemon index
```