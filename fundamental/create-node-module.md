
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




