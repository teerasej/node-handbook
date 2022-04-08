
# สร้างโปรเจค Web API

1. สร้างโฟลเดอร์ **employeeAPI**
2. เปิดโฟลเดอร์ **employeeAPI** ใน Terminal 
3. รันคำสั่งสร้าง `package.json`

```bash
npm init
```

4. สร้างไฟล์ `index.js` 


## ติดตั้ง Package ที่จำเป็น

1. เปิด Terminal
2. รันคำสั่งติดตั้ง package

```bash
// สร้าง API
npm i express

// สามารถเรียกใช้ environment variable ได้
npm i dotenv

// รันและแก้ไข javascript โดยที่ไม่ต้อง restart node
npm install -g nodemon
```

## สร้างไฟล์ .env

เพื่อกำหนดค่า environment ต่างๆ เริ่มจากกำหนด PORT ก่อนเลย
```
PORT=3000
```