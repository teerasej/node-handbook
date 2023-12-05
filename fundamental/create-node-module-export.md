
# การเขียน JavaScript เพื่อนำไปใช้งานนอก module

โดยปกติ Node จะถือว่า code ในไฟล์ JavaScript แต่ละไฟล์ (หรือ Module) จะไม่สามารถอ้างถึงกันและกันได้ 

> ในเชิง Object-Oriented Programming เหมือนกับทุกอย่างเป็น private นั่นเอง

## วิธีการส่งผ่าน Code ออกไปใช้นอก module

เราสามารถกำหนดค่าให้กับตัวแปรพิเศษ ที่ Node เตรียมไว้ให้เราได้

```ts
export ...
```

## Export เป็นตัวแปร

ทดสอบสร้างไฟล์ config.ts และ export ตัวแปร url ออกไปใช้งาน

```ts
// config.ts
export const url: string = 'https://www.nextflow.in.th/api';
```

นำค่าตัวแปร url ออกมาใช้งาน ในไฟล์ index.ts

```ts
// index.ts

// การ import ตัวแปร url จากไฟล์ config.ts
import { url } from './config';

// การ import ตัวแปร url และตั้งชื่อตัวแปรใหม่เป็น ENDPOINT
import { url as ENDPOINT } from './config';

console.log(`Url: ${url}`);
console.log(`Endpoint: ${ENDPOINT}`);
```

## Export เป็น Function

สร้างไฟล์ greeting.ts และ export ฟังก์ชัน greeting ออกไปใช้งาน

```ts
// greeting.ts

// สร้างฟังก์ชัน greeting และ export ออกไปใช้งาน
export const greeting = function(name: string): string {
    return `Hello, ${name}`;
}

// สร้างฟังก์ชัน goodbye แบบ Arrow function และ export ออกไปใช้งาน
export const goodbye = (name: string): string => `Goodbye, ${name}`;
```

นำฟังก์ชัน greeting และ  ออกมาใช้งาน ในไฟล์ index.ts

```ts

// index.ts
import { greeting, goodbye } from './greeting';
console.log(greeting('pon'));
console.log(goodbye('pon'));
```

## Export เป็น Object

```js
// auth.js
module.exports = {
    login: (username, password) => {
        console.log('Logging in: ' + username);
    }
}


// index.js
const auth = require('auth');
auth.login('pon','nextflow');
```

## Export เป็น Class 

```js
// user.js
module.exports = class User {
    constructor(username){
        this.username = username;
    }

    display() {
        console.log('Username: ' + this.username );
    }
}


// index.js
const User = require('user');
let userA = new User('pon');
userA.display();
```



