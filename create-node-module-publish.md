## 1. สมัคร NPM account

เปิดเว็บ https://npmjs.com 

และสมัครเปิดบัญชีผู้ใช้ และกด activate link ใน Email ที่ส่งเข้ามาตามที่สมัคร (ถ้ามี)

## 2. Publish Node Module

1. กลับมาที่ Command Line ที่อยู่ในโปรเจค
2. รันคำสั่ง 

```bash
npm login
```

3. กรอก username, password, และ email **ที่ใช้สมัครบัญชี npmjs.com** ให้เรียบร้อย

4. รันคำสั่ง เพื่อ publish ขึ้น npmjs.com

```bash
npm publish 
```

5. กลับเข้าเว็บ npmjs.com และดู Profile > Package เพื่อ check ว่า package ขึ้นไปแล้ว

6. แลก link ของ node package ให้เพื่อนลองเอา node module เราไปลองใช้ดู

## 3. Update Node Module: README.md

1. สร้างไฟล์ `README.md` ขึ้นมาในโปรเจค
2. เขียน Markdown ในไฟล์ตามข้อมูลด้านล่าง

```md
# My Shopdee Data Class

ส่วนประกอบของข้อมูลสินค้า
```

3. บันทึกไฟล์
4. เปิดไฟล์ `package.json` และปรับเวอร์ชั่นเพิ่มขึ้น 
5. บันทึกไฟล์
6. รันคำสั่ง เพื่อ publish ขึ้น npmjs.com

```bash
npm publish 
```

7. เข้าไปเช็คความเปลี่ยนแปลงในหน้า package ของเว็บไซต์ npmjs.com

