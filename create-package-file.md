
# การสร้างไฟล์ package.json 

ไฟล์ `package.json` เป็นไฟล์ที่กำหนดการทำงานของโปรเจค Node นั้น และมีคุณประโยชน์หลายอย่างเช่น

- กำหนดรายการ package ที่ใช้ในโปรเจคนั้นผ่านส่วน `dependencies:`
- สามารถกำหนด shortcut ของคำสั่งที่ใช้ในโปรเจคได้ ผ่านส่วน `scripts:`

## วิธีสร้าง package.json

รันคำสั่งด้านล่างใน terminal ของโปรเจค

```bash
npm init
```

จากนั้นกรอกข้อมูลให้ครบถ้วน จะได้ไฟล์ `package.json` มาได้


## หากต้องการใช้คุณสมบัติ import export 

ดูได้ในส่วน [การใช้ keyword import และ export ใน Node.js](import-export-node-module.md)
