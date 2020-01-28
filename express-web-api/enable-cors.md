
# ติดตั้งและเปิดการใช้งาน CORS

## ติดตั้ง Module 

```bash
npm i cors
```

## ติดตั้ง Cors เป็น middleware 

1. เปิดไฟล์ **index.js**
2. เพิ่ม `cors()` เป็น middleware

```js
let cors = require('cors');
let app = express();

app.use(cors());
```