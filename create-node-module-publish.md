

# การสร้าง Module ใช้งานเอง

การสร้าง Module ใช้งานเองมีหลายระดับ แต่เราสามารถแบ่งออกเป็น 2 กลุ่มใหญ่ๆ นั่นคือ

1. แบบเขียนไฟล์ในโปรเจค
2. แบบแยกเป็น package 

แบบเขียนแยกไฟล์ เราได้ดูในส่วนของ [การใช้งาน Node Module](/node-module.md) แล้ว แต่ในที่นี้เราจะแยกเป็น package กัน

## 1. การใช้คำสั่ง `npm init`

1. สร้าง directory ขึ้นมา ตั้งชื่อว่า `nextflowshop` แล้วต่อท้ายด้วยชื่อของเรา
2. เปิด Command Line มาที่ directory ดังกล่าว และรันคำสั่ง 

```bash
npm init
```

3. กรอกข้อมูลของ module ตามความเหมาะสม (บางข้อมูลถ้าไม่ใส่จะมีการใช้ค่าเริ่มต้น)
4. ยืนยันการสร้าง
5. สังเกตว่าจะมีไฟล์ `package.json` ถูกสร้างขึ้นมาในโปรเจค

ที่คือไฟล์ที่ระบุรายละเอียดของ package เรานั่นเอง

## 2. การติดตั้ง package เพิ่มเติม

เราสามารถอ้างอิง module ของคนอื่น ใน package ของเราได้ด้วย 

เช่น การรันคำสั่ง

```bash
npm i nextflow-calculator --save
```
สังเกตว่าในไฟล์ **package.json** จะมีส่วนที่ชื่อว่า `dependencies` ขึ้นมา 

```bash
npm i nextflow-calculator --save-dev
```

สังเกตว่าในไฟล์ **package.json** จะมีส่วนที่ชื่อว่า `dependencies` ขึ้นมา 

### ความแตกต่างระหว่าง `dependencies` กับ `dev-dependencies`

1. `dependencies` จะเป็นรายชื่อ module ที่ใช้จริงๆ (เรียกว่า Runtime module)
2. `dev-dependencies` จะเป็นรายชื่อ module ที่ใช้ตอน development เท่านั้น (เรียกว่า Development module)






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

