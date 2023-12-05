
# Interface as Data object

## 1. สร้าง Interface ชื่อ IUserInfo 

สร้างไฟล์ `IUserInfo.ts` และกำหนด interface ชื่อ `IUserInfo` ดังนี้:

```typescript
// IUserInfo.ts

import { UserType } from "./user-type";

export default interface IUserInfo {
    username: string;
    email: string;
    userType: UserType;
}
```

## 2. นำ interface มาสร้างเป็น data object ใน index.ts


แก้ไขโค้ดใน `index.ts` ดังนี้ และรันคำสั่ง `npm start` เพื่อทดสอบ

```typescript
// index.ts

// นำเข้า interface จากไฟล์ IUserInfo.ts
import IUserInfo from "./IUserInfo";
import { UserType } from './user-type';


// สร้าง object จาก interface และกำหนดข้อมูลให้กับ property ต่างๆ
var user3: IUserInfo = { 
    username: 'teerasej',
    email: 'teerasej@nextflow.in.th',
    userType: UserType.Registered
};

console.log(user3.username);
console.log(user3.email);
console.log(user3.userType);

```
