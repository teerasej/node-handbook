
# การเรียกใช้ Module ที่ติดตั้งในโปรเจค

## 1. ทดลองใช้งาน express 

1. ดาวน์โหลดและติดตั้ง node module ชื่อ `express` ด้วยคำสั่ง

```bash
npm i express
```

2. สร้างไฟล์ `index.ts` และเขียน (หรือแทนที่ด้วย) code ด้านล่าง

```ts
import express, { Request, Response } from 'express';
const app = express();
const port = 3000;

app.get('/', (req: Request, res: Response) => res.send('Hello World!'));

app.listen(port, () => console.log(`Example app listening on port ${port}!`));
```

3. คอมไพล์ TypeScript ไฟล์ด้วยคำสั่ง tsc

```bash
tsc
```

4. รันไฟล์ JavaScript ที่ได้จากการคอมไพล์ด้วยคำสั่ง node

```bash
node index.js
```

5. ทดสอบเข้า Web browser ไปที่ http://localhost:3000/
6. เราควรจะเห็นข้อความ `Hello World!` ขึ้นมาบน Web Browser