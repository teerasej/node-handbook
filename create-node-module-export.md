
# 9. การเขียน JavaScript เพื่อนำไปใช้งานนอก module

โดยปกติ Node จะถือว่า code ในไฟล์ JavaScript แต่ละไฟล์ (หรือ Module) จะไม่สามารถอ้างถึงกันและกันได้ 

> ในเชิง Object-Oriented Programming เหมือนกับทุกอย่างเป็น private นั่นเอง

## วิธีการส่งผ่าน Code ออกไปใช้นอก module

เราสามารถกำหนดค่าให้กับตัวแปรพิเศษ ที่ Node เตรียมไว้ให้เราได้

```js
module.exports = ...
```

## Export เป็นตัวแปร

```js
// config.js
const url = 'https://www.nextflow.in.th/api';
module.exports = url;


// index.js
const ENDPOINT = require('config');
console.log(ENDPOINT);
```

## Export เป็น Function

```js
// greeting.js
module.exports = (name) => 'Hello, ' + name;


// index.js
const greeting = require('greeting');
console.log(greeting('pon'));
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



