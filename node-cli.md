
# 2. การเรียกใช้ Node CLI

เราสามารถเรียกใช้งาน Node CLI ได้ผ่านโปรแกรมจำพวก Command Line 

- Windows จะมี Command Prompt และ Powershell
- MacOS จะมี Terminal

## 1. เช็คเวอร์ชั่นของ Node และ Node Package Manager 

```bash
node -v
```
และ
```bash
npm -v
```

## 2. รันไฟล์ JavaScript (JS)

เราสามารถใช้ Node CLI ในการอ่าน และรันคำสั่งของไฟล์ JavaScript ได้

1. สร้าง Directory ชื่อ **my-node**
2. สร้างไฟล์ไว้ในโฟลเดอร์ โดยตั้งชื่อไฟล์ว่า **index.js**
3. เขียนคำสั่งในไฟล์ดังนี้ 

```js
console.log('Oh Yeah!');
```

4. บันทึกไฟล์
5. เปิด Command Line มาที่ Directory ชื่อ **my-node**
6. รันคำสั่งด้านล่าง 

```bash
node index.js
```

7. สังเกตผล
8. รันคำสั่งด้านล่าง

```bash
node index
```

9. สังเกตว่าได้ผลเหมือนกัน
