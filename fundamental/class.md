
# การสร้าง และใช้งาน Class, Property, Method

## 1. การตั้งชื่อ Class

การประกาศ class ใน TypeScript โดยสร้างไฟล์ `user.ts` และประกาศ class ดังนี้

```ts
// user.ts

class User {

}
```

## 2. การกำหนด Property

```ts
// user.ts

class User {

    // ประกาศ property และกำหนด type
    username: string;
    email: string;

}
```

## 3. การประกาศ Constructor 

```ts
// user.ts

class User {

    username: string;
    email: string;

    // ประกาศ constructor และกำหนด type ของ parameter
    constructor(username: string, email: string) {
        this.username = username;
        this.email = email;
    }

}
```

## 4. การประกาศ Method เพื่อเอาไว้ใช้งาน

```ts
// user.ts

class User {
    username: string;
    email: string;

    constructor(username: string, email: string) {
        this.username = username;
        this.email = email;
    }

    // ประกาศ method เพื่อเช็คว่ามี email กำหนดไว้หรือไม่
    hasEmail(): boolean {
        if(this.email) {
            return true;
        } else {
            return false;
        }
    }
}
```

### 5. ใช้คำสั่ง export เพื่อให้สามารถนำ Class User ไปใช้งานได้

```ts   
// user.ts

class User {
    username: string;
    email: string;

    constructor(username: string, email: string) {
        this.username = username;
        this.email = email;
    }

    // ประกาศ method เพื่อเช็คว่ามี email กำหนดไว้หรือไม่
    hasEmail(): boolean {
        if(this.email) {
            return true;
        } else {
            return false;
        }
    }
}

export default User;

```

> หมายเหตุ: การใช้คำสั่ง `export default` จะทำให้สามารถนำ class ไปใช้งานได้โดยไม่ต้องระบุชื่อ class ที่ต้องการ

### 6. ทดสอบสร้าง instance หรือ object

เขียนโค้ดในไฟล์ `index.ts` ดังนี้ และรันคำสั่ง `npm start` เพื่อทดสอบการทำงาน

```ts
// index.ts

// นำเข้า class User จากไฟล์ user.ts
import User from './user';

// สร้าง instance ของ class User
let user = new User('nextflow','training@nextflow.in.th');

// เรียกใช้ method ที่ประกาศไว้ใน class User 
// โดยจะเป็นการเรียกใช้ method ที่มีการเช็คว่ามี email หรือไม่
// ซึ่งจะได้ผลลัพธ์เป็น true
if(user.hasEmail()) {
    console.log('User has email');
} else {
    console.log('User has no email');
}

// สร้าง instance ของ class User โดยไม่กำหนด email
let user2 = new User('nextflow','');

// เรียกใช้ method ที่ประกาศไว้ใน class User
// โดยจะเป็นการเรียกใช้ method ที่มีการเช็คว่ามี email หรือไม่
// ซึ่งจะได้ผลลัพธ์เป็น false
if(user2.hasEmail()) {
    console.log('User has email');
} else {
    console.log('User has no email');
}
```
