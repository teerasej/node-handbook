
# การสร้าง และเรียกใช้งาน package.json

## การสร้าง package.json

1. จากใน Visual Studio Code ให้เปิดส่วน Terminal ขึ้นมา จากเมนูด้านบนเลือก Terminal > New Terminal
2. พิมพ์คำสั่ง `npm init` แล้วกด Enter
3. ตอบคำถามตามลำดับ อันไหนไม่รู้ก็กด Enter ได้เลย เพราะจะใช้ค่าเริ่มต้นตามที่ node เสนอมาในหน้าจอ
4. ตอนนี้จะเห็นว่ามีไฟล์ชื่อ package.json ถูกสร้างขึ้นมาใหม่ ในโปรเจคของเรา

## การเรียกใช้ package.json

1. เปิดไฟล์ `package.json` ขึ้นมา จะเห็นค่าเริ่มต้นประมาณนี้

```json
{
  "name": "nextflow-blank-typescript",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
}
```
2. ทำการเพิ่มคำสั่ง start ในส่วนของ script ดังนี้

```json
{
  "name": "nextflow-blank-typescript",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",

    "start": "node index.js"

  },
  "keywords": [],
  "author": "",
  "license": "ISC",
}
```

3. ทดสอบรันคำสั่งด้านล่างใน terminal

```bash
npm start
```