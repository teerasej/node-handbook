
# Interface as concrete structure

## 1. สร้าง Interface ชื่อ IUserTypeCheck 

สร้างไฟล์ `IUserTypeCheck.ts` และกำหนด interface ชื่อ `IUser` ดังนี้:

```typescript
interface IUserTypeCheck {
  isAdmin(): boolean;
  isAnonymous(): boolean;
  isRegistered(): boolean;
}

export default IUserTypeCheck;
```

## 2. นำ interface มากำหนด implements กับ class User


```typescript
// user.ts

// import interface ที่สร้างไว้
import IUserTypeCheck from "./IUserTypeCheck";

import { UserType } from "./user-type";

// นำ interface มากำหนด implements กับ class User
class User implements IUserTypeCheck {
    username: string;
    email: string;
    userType: UserType;

    constructor(username: string, email: string, userType: UserType) {
        this.username = username;
        this.email = email;
        this.userType = userType;
    }
    
    // สร้าง method ตามที่กำหนดใน interface ไม่งั้นจะเกิด error
    isRegistered(): boolean {
        if (this.userType === UserType.Registered) {
            return true;
        } else {
            return false;
        }
    }

    // ก่อนหน้านี้ มีการสร้าง method ตามที่กำหนดใน interface ชื่อ isAdmin() อยู่แล้ว เลยไม่ต้องทำอะไรเพิ่ม
    isAdmin(): boolean {
        if (this.userType === UserType.Admin) {
            return true;
        } else {
            return false;
        }
    }

    // ก่อนหน้านี้ มีการสร้าง method ตามที่กำหนดใน interface ชื่อ isAnonymous() อยู่แล้ว เลยไม่ต้องทำอะไรเพิ่ม
    isAnonymous(): boolean {
        if (this.userType === UserType.Anonymous) {
            return true;
        } else {
            return false;
        }
    }

    hasEmail(): boolean {
        if (this.email) {
            return true;
        } else {
            return false;
        }
    }
}

export default User;
```

## 3. ทดสอบการใข้งานผ่าน index.ts

แก้ไขโค้ดใน `index.ts` ดังนี้ และรันคำสั่ง `npm start` เพื่อทดสอบ

```typescript

// import IUserTypeCheck มาใช้งาน
import IUserTypeCheck from "./IUserTypeCheck";
import User from './user';
import { UserType } from './user-type';

// สร้าง instance ของ class User โดยเก็บไว้ในตัวแปร user1 ที่เป็น type IUserTypeCheck
let user1: IUserTypeCheck = new User('nextflow','training@nextflow.in.th', UserType.Admin);

// เราสามารถเขียนเรียกใช้ method ของ Interface ได้เลย เพราะ class User ได้ implement มันไว้แล้ว
if(user1.isAdmin()) {
    console.log('User 1 is admin');
}

// ถึงแม้ว่า user1 จะมี type เป็น interface แต่เราก็สามารถเขียนเรียกใช้ method ของ class User ได้ โดยใช้ type casting
// เพราะเราทราบว่า user1 จริงๆแล้วเป็น instance ของ class User
if((user1 as User).hasEmail()) {
    console.log('User 1 has email');
}
```
