
## Exercise 2: Export/import Function

สร้างไฟล์ **greeting.ts** และ export ฟังก์ชัน greeting ออกไปใช้งาน

```ts
// greeting.ts

// สร้างฟังก์ชัน greeting และ export ออกไปใช้งาน
export const greeting = function(name: string): string {
    return `Hello, ${name}`;
}

// สร้างฟังก์ชัน goodbye แบบ Arrow function และ export ออกไปใช้งาน
export const goodbye = (name: string): string => `Goodbye, ${name}`;
```

นำฟังก์ชัน **greeting** และ **goodbye** ออกมาใช้งาน ในไฟล์ **index.ts**

```ts
// index.ts

import { greeting, goodbye } from './greeting';
console.log(greeting('pon'));
console.log(goodbye('pon'));
```
