
# การเรียกใช้ Module 

ด้วย Node.js ทำให้เราสามารถ แบ่งโค้ด Javascript ออกเป็นไฟล์ต่างๆ และสามารถเรียกใช้งานซึ่งกันและกันได้ เหมือนในภาษาโปรแกรมอื่นๆ 

## 1. คำสั่ง

```js
let moduleA = require('./module/path');
const moduleB = require('module package name');
```

เทียบกับภาษาอื่นๆ 

```html
<!-- html --> 
<script src="app.js"></script>
```
```csharp
// C# 
using com.nextflow.namespace
```
```java
// Java
import com.nextflow.namespace
```
```php
// PHP
include('./module/path.php');
```

## 2. การอ้างถึงไฟล์ JavaScript ที่อยู่ในโปรเจค

เช่นเรามีไฟล์ JavaScript ชื่อ `calculator.js` เก็บไว้ใน directory ชื่อ `cal-module` จะสามารถเขียนเรียกได้แบบนี้ 

```js
const calculator = require('./cal-module/calculator');
```

> สังเกตว่าจะไม่มีการใส่ นามสกุลไฟล์ `.js` ตามหลัง

### การอ้างอิงถึงแบบย่อ

ถ้าเราต้องการ เราสามารถตั้งชื่อไฟล์ JavaScript เป็น `index.js` ซึ่งการเรียกใช้ไฟล์ชื่อดังกล่าวด้วยคำสั่ง `require` จะไม่ต้องอ้างถึงชื่อไฟล์ 

เช่นเรามีไฟล์อยู่ที่ `cal-module/index.js` จะเขียนคำสั่ง require ได้แบบด้านล่าง

```js
const calculator = require('./cal-module');
```

ซึ่งรูปแบบนี้นิยมใช้กันจนแพร่หลาย เพราะทำให้การใช้งานง่ายกว่า

## 3. การอ้างถึง API และ Package 

ในกรณีที่เราต้องการเรียกใช้ 

1. API ของ Node.js 
2. Node Package ที่ติดตั้งผ่าน `npm`

การเรียกใช้จะไม่ต้องระบุชื่อไฟล์ หรือ path ใดๆ เช่น

```js
// เรียกใช้ os API ของ Node
const os = require('os')
```
```js
// เรียกใช้ Node module package ชื่อ express **ต้องติดตั้งในโปรเจคก่อน**
const express = require('express')
```