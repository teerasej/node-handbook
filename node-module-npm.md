
# 6. การติดตั้ง Module ด้วย NPM (Node Package Manager)

เราสามารถหา Node Module ได้จากเว็บไซต์ 

https://npmjs.com

## 1. คำสั่ง `NPM`

คำสั่ง `npm` ใช้ในการจัดการ Node module โดยเฉพาะ

เราสามารถดูคำสั่งของ npm ได้โดยใช้คำสั่ง 

```bash
npm --help
```

## 2. วิธีการติดตั้ง 

รันคำสั่ง

```bash
npm install [ชื่อ node module]
npm i [ชื่อ node module]
```

เช่น 

```bash
npm i express
```

ตัว npm จะดาวน์โหลด และเอา Node module ชื่อ express และที่เกี่ยวข้องทั้งหมดมาที่ directory ที่ชื่อ `node_modules/`

