
# ติดตั้งและเปิดการใช้งาน CORS

ในการเรียกใช้งานข้าม domain เช่น Web Application ที่เป็น SPA (React, Angular, Vue) อาจจะมีการส่ง request มาที่ Web API ที่อยู่อีก domain เช่น 

- React Web App ทำงานอยู่ที่ http://localhost:8080
- Web API ทำงานอยู่ที่ http://localhost:3000 

ในส่วนของ React ที่ทำงานจะมีกลไกของ Web Browser ที่กันการส่ง request ลักษณะนี้ไว้ ต้องมีการกำหนดเปิด CORS ในฝั่่ง client และ Server ถึงจะเรียกหากันได้

## ติดตั้ง Module 

```bash
npm i cors
```

## ติดตั้ง Cors เป็น middleware 

1. เปิดไฟล์ **index.js**
2. เพิ่ม `cors()` เป็น middleware

```js
let app = express();
let cors = require('cors');

app.use(cors());
```