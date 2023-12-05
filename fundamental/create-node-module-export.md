
# การเขียน TypeScript แยกไฟล์เพื่อจัดการ หรือ Reuse

โดยปกติ Node จะถือว่า code ในไฟล์ TypeScript แต่ละไฟล์ (หรือ Module) จะไม่สามารถอ้างถึงกันและกันได้ ถ้าเราต้องการใช้งาน code ในไฟล์ TypeScript อื่น ๆ เราจะต้องทำการ import ไฟล์นั้นเข้ามาใช้งาน 

> ในมุมมองของการเขียนโปรแกรม Object-Oriented Programming เหมือนกับทุกอย่างเป็น private นั่นเอง

## 1. การ import และ export ใน TypeScript

การ import และ export ใน TypeScript จะมีรูปแบบการเขียนดังนี้

### 1.1 การ Export และ Import แบบ Default

ทดสอบสร้างไฟล์ export-default.ts และ export ฟังก์ชันเป็นค่าเริ่มต้นจากไฟล์นี้ ออกไปใช้งาน

```ts
// lib.ts

// การ export แบบ default
export default function() {
    console.log('my function');
}
```

นำค่าฟังก์ชันที่ export ออกมาใช้งาน ในไฟล์ index.ts

```ts
// index.ts

// การ import แบบ default
import myFunc1 from './lib';

myFunc1();
```

จากนั้นบันทึกไฟล์ และทดสอบรันคำสั่ง tsc เพื่อดูผลลัพธ์


### 1.2 การ Export และ Import แบบกำหนดชื่อ

ให้เพิ่มการ export ฟังก์ชัน export1Function และตัวแปร counter ออกไปใช้งาน

```ts
// lib.ts

export default function() {
    console.log('my function');
}

export function export1Function() {
    console.log('export1 function');
}

export var counter = 0;
```

จากนั้นให้เพิ่มการ import ฟังก์ชัน **export1Function** และตัวแปร **counter** ออกมาใช้งาน ในไฟล์ index.ts

```ts
// index.ts

// การ import แบบ default
import myFunc1 from './lib';

// การ import แบบ named
import { export1Function, counter } from './lib';
import { export1Function as functionA } from './lib';

myFunc1();
export1Function();
console.log(counter);
functionA();
```

ทดสอบรันคำสั่งเพื่อดูผลลัพธ์

```bash
ืnpm start
```


