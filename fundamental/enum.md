
# การใช้งาน Enum 

Enum ใน TypeScript ใช้สำหรับการกำหนดค่าคงที่ที่มีความหมาย เช่น ประเภทของผู้ใช้งาน

## 1. การประกาศ Enum

สร้าง enum ในไฟล์ `user-type.ts` ดังนี้


```ts
export enum UserType {
    Admin = 'Admin',
    Anonymous = 'Anonymous',
    Registered = 'Registered'
}
```

## 2. นำ enum มากำหนดค่าให้กับ property ใน class

```ts
// user.ts

import { UserType } from "./user-type";

class User {
    username: string;
    email: string;

    // กำหนด type ของ property userType เป็น UserType
    userType: UserType;

    // เพิ่ม parameter userType ใน constructor
    constructor(username: string, email: string, userType: UserType) {
        this.username = username;
        this.email = email;
        this.userType = userType;
    }

    // เพิ่ม method ใน class เพื่อเช็คว่าเป็น Admin หรือไม่
    isAdmin(): boolean {
        if(this.userType === UserType.Admin) {
            return true;
        } else {
            return false;
        }
    }

    // เพิ่ม method ใน class เพื่อเช็คว่าเป็น Anonymous หรือไม่
    isAnonymous(): boolean {
        if(this.userType === UserType.Anonymous) {
            return true;
        } else {
            return false;
        }
    }

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

## 3. ทดสอบการใช้งาน

ปรับปรุงไฟล์ `index.ts` ดังนี้ เพื่อทดสอบการใช้งาน enum ที่เป็น property ของ class

เสร็จแล้ว ให้รันคำสั่ง `npm start` เพื่อทดสอบการทำงาน

```ts
// index.ts

import User from './user';

// import enum UserType จากไฟล์ user-type.ts
import { UserType } from './user-type';

//  สร้าง instance ของ class User โดยระบุ email และ userType เป็น UserType.Admin
let user1 = new User('nextflow','training@nextflow.in.th', UserType.Admin);

// เรียกใช้ method isAdmin() จาก instance ของ class User ที่สร้างขึ้น โดยจะได้ผลลัพธ์เป็น true
if(user1.isAdmin()) {
    console.log('User 1 is admin');
}

if(user1.hasEmail()) {
    console.log('User 1 has email');
} else {
    console.log('User 1 has no email');
}

// สร้าง instance ของ class User โดยไม่ระบุ email และ userType เป็น UserType.Anonymous
let user2 = new User('nextflow','', UserType.Anonymous);

// เรียกใช้ method isAnonymous จาก instance ของ class User ที่สร้างขึ้น โดยจะได้ผลลัพธ์เป็น false
if(user2.isAnonymous()) {
    console.log('User 2 is Anonymous');
}

if(user2.hasEmail()) {
    console.log('User 2 has email');
} else {
    console.log('User 2 has no email');
}


```