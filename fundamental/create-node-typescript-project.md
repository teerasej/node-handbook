
# การสร้างโปรเจค Node.js ที่ใช้ TypeScript

## 1. สร้างโปรเจค Node.js ด้วยคำสั่ง `npm init`

1. สร้างโฟลเดอร์ directory ชื่อ `my-node-ts-project` ในเครื่อง และเปิดขึ้นมาใน Visual Studio Code

2. สร้างโปรเจค Node.js ด้วยคำสั่ง `npm init` ใน Terminal

```bash
npm init -y
```

> คำสั่ง `npm init` จะสร้างไฟล์ `package.json` ให้เรา และการกำหนด `-y` จะทำให้ไม่ต้องตอบคำถามต่างๆ ที่มีในการสร้าง `package.json`


## 2. ติดตั้ง TypeScript ในโปรเจค 
   
1. โดยการรันคำสั่งด้านล่างใน Terminal ของ Visual Studio Code

```bash
npm install typescript --save-dev
```

2. รันคำสั่งด้านล่าง เพื่อสร้างไฟล์ `tsconfig.json` ในโปรเจค

```bash
npx tsc --init
```

และเข้าไปแก้ไขบรรทัดที่ 58 ให้เป็นดังนี้

```json
   "outDir": "./dist", 
```

หรือ [copy โค้ดไฟล์ `tsconfig.json` จาก link นี้](https://gist.github.com/teerasej/114dfdf2f8ea1093a62377e65dad3eb1)ไปใช้งานได้เลย โดยให้สร้างไฟล์ `tsconfig.json` ไว้ในโปรเจค

## 3. สร้าง `src` directory 

1. เราจะสร้างโฟลเดอร์ `src` ไว้เก็บไฟล์ TypeScript ที่เราจะเขียนโปรแกรมไว้ในโปรเจค

2. สร้างไฟล์ `index.ts` ในโฟลเดอร์ `src` และเขียนโค้ดด้านล่าง

```ts
console.log('Hello World');
```

## 4. ตั้งค่าการคอมไพล์โค้ดด้วยคำสั่ง `npm run build`

1. แก้ไขค่า `"scripts"` ในไฟล์ `package.json` ให้เป็นดังนี้

```json
  "scripts": {
    "build": "tsc"
  },
```

2. รันคำสั่ง `npm run build` เพื่อคอมไพล์โค้ด TypeScript ให้เป็น JavaScript

```bash
npm run build
```

3. จะเห็นไฟล์ `index.js` ถูกสร้างขึ้นมาในโฟลเดอร์ `dist` และเราสามารถรันโค้ดได้ด้วยคำสั่ง 

```bash
node dist/index.js
```

4. ทดสอบรันโค้ด เราควรจะเห็นข้อความแสดงขึ้นมาบน Terminal ว่า `Hello World`
   
## 5. รันโปรแกรมด้วยคำสั่ง `npm start`

1. แก้ไขค่า `"scripts"` ในไฟล์ `package.json` ให้เป็นดังนี้

```json
  "scripts": {
    "build": "tsc",
    "start": "node dist/index.js"
  },
```

2. รันคำสั่ง `npm start` เพื่อรันโปรแกรม

```bash
npm start
```

3. ทดสอบรันโค้ด เราควรจะเห็นข้อความแสดงขึ้นมาบน Terminal ว่า `Hello World`

## 6. ปรับคำสั่ง script เพื่อให้ build และรันโปรแกรมได้ด้วยคำสั่งเดียว

1. แก้ไขค่า `"scripts"` ในไฟล์ `package.json` ให้เป็นดังนี้

```json
  "scripts": {
    "build": "tsc",
    "start": "npm run build && node dist/index.js"
  },
```

2. รันคำสั่ง `npm start` เพื่อรันโปรแกรม

```bash
npm start
```

3. ทดสอบรันโค้ด เราควรจะเห็นข้อความแสดงขึ้นมาบน Terminal ว่า `Hello World`