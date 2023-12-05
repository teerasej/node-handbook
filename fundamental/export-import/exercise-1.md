

# Exercise 1: Export/Import ตัวแปร

ทดสอบสร้างไฟล์ **config.ts** และให้สร้าง และ export ตัวแปรชื่อ **url** ออกไปใช้งาน

```ts
// config.ts
export const url: string = 'https://www.nextflow.in.th/api';
```

นำค่าตัวแปร url ออกมาใช้งาน ในไฟล์ **index.ts**

```ts
// index.ts

// การ import ตัวแปร url จากไฟล์ config.ts
import { url } from './config';

// การ import ตัวแปร url และตั้งชื่อตัวแปรใหม่เป็น ENDPOINT
import { url as ENDPOINT } from './config';

console.log(`Url: ${url}`);
console.log(`Endpoint: ${ENDPOINT}`);
```

เสร็จแล้วให้รันคำสั่งเพื่อดูผลลัพธ์

```bash
ืnpm start
```
