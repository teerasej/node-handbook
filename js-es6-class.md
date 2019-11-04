
# 5. JavaScirpt ES6 - Class, Property, Method 

การประกาศ class ใน JavaScript

```js
class User {

}
```

## 1. การประกาศ Constructor และกำหนด Property

```js
class User {

    constructor(username, password) {
        this.username = username;
        this.password = password;
    }

}
```

## 2. การประกาศ Method


```js
class User {

    // ประกาศ method และ return ค่า
    validate() {
        return true;
    }

    isSameAccount(user) {
        return false;
    }
}
```

## 3. การประกาศ Getter และ Setter

```js
class User {

    get username() {
        return this.username;
    }

    set username(username) {
        this.username = username;
    }
}
```

### เวลาใช้งาน

```js
let user = new User('nextflow','1234');

// setter
user.username = 'admin';

// getter
console.log(user.username);
```