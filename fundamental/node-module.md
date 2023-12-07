
# การเรียกใช้ Module (import)
 
ด้วย Node.js ทำให้เราสามารถ แบ่งโค้ด Typescript ออกเป็นไฟล์ต่างๆ และสามารถเรียกใช้งานซึ่งกันและกันได้ เหมือนในภาษาโปรแกรมอื่นๆ 

## 1. คำสั่งในการ import 

```ts
import moduleA from './module/path';
import * as moduleB from 'module package name';
```

เทียบกับภาษาอื่นๆ 

### JavaScript
```js
const moduleA = require('./module/path');
```

### HTML
```html
<script src="app.js"></script>
```

### PHP
```php
include('./module/path.php');
```

### C#
```csharp
using com.nextflow.namespace
```

### Java
```java
import com.nextflow.namespace
```


## 2. การอ้างถึง API และ Package 

ในกรณีที่เราต้องการเรียกใช้ 

1. API ของ Node.js 
2. Node Package ที่ติดตั้งด้วยคำสั่ง `npm`

การเรียกใช้จะไม่ต้องระบุชื่อไฟล์ หรือ path ใดๆ เช่น

### เรียกใช้ os API ของ Node

1. ทดสอบสร้างไฟล์ `test-os.ts` และเขียนโค้ดด้านล่าง

```ts
import * as os from 'os';

console.log(os.platform())
```

2. จากนั้นใช้คำสั่งด้านล่างเพื่อคอมไพล์ และรันไฟล์ใน terminal

```bash
npm run build
```

```bash
node dist/test-os
```
