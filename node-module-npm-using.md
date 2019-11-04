
# 8. การเรียกใช้ Module ที่ติดตั้งในโปรเจค

## 1. ทดลองใช้งาน express 

1. ดาวน์โหลดและติดตั้ง node module ชื่อ `express` 
2. สร้างไฟล์ `index.js` และเขียน code ด้านล่าง

```js
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => res.send('Hello World!'))

app.listen(port, () => console.log(`Example app listening on port ${port}!`))
```

3. รันไฟล์ด้วยคำสั่ง node

```bash
node index
```

4. ทดสอบเข้า Web browser ไปที่ http://localhost:3000/