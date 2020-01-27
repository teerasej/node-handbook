
# กำหนด Route URL และเริ่มกำหนด port เพื่อเริ่มการทำงาน

1. เปิดไฟล์ `index.js`
2. เขียนกำหนดการทำงานของ Web API

```js
// เรียกใช้งาน express module 
const express = require('express');
let app = express();

// กำหนด route url 
app.get('/', (request, respond) => {
    respond.send('hello');
});

// กำหนด port และเริ่มการทำงาน
app.listen(3000, ()=>{
    console.log('server is running at port 3000');
})
```

3. ทดสอบรันการทำงาน ด้วยคำสั่ง 

```bash
node index
```