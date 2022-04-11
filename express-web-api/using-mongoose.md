
# การใช้งาน Mongoose 

## 1. ติดตั้ง Package

```bash
npm i mongoose
```

## 2. สร้าง Schema และ Validation Rule

สร้างไฟล์ `models/employee.js`

```js
const mongoose = require('mongoose')

// กำหนด field ให้กับ Schema 
const employeeSchema = new mongoose.Schema({

    // กำหนด type และ rule
    email: {
        type: String,
        required: true
    },
    // กำหนด type อย่างเดียว
    firstName: String,
    lastName: String
});

// สร้าง Model จาก Schema
const EmployeeModel = mongoose.model('Employee', employeeSchema)

module.exports = EmployeeModel
```

## 3. ทำการเชื่อมต่อ MongoDB 

เปิดไฟล์ `index.js`

```js
//...

// ของเดิม monk เราไม่ใช้แล้ว 
// const db = require('monk')(`${MONGO_HOST}:${MONGO_PORT}/employeeDB`)
const mongoose = require('mongoose');
const EmployeeModel = require('./model/employee');

// ทำการเชื่อมต่อผ่าน .connect function 
mongoose.connect(`mongodb://${MONGO_HOST}:${MONGO_PORT}/employeeDB`)

//...
```
## 4. เรียกใช้ Schema ในการเพิ่มข้อมูล

1. ในไฟล์ `index.js` เราจะลงมาที่ `POST /employees` และทำการแก้ไขโค้ดให้มาใช้ mongoose แทน
2. ในที่นี้เราจะลองเพิ่มข้อมูลลง collection employee ตามที่เรากำหนดไว้ตอนสร้าง model 
3. เสร็จแล้วลองส่ง request เข้ามาทดสอบดู

```js
app.post('/employees', async (req, res) => {

    const newEmployee = req.body;

    const newEmployeeModel = new EmployeeModel(newEmployee)
    const createdEmployee = await newEmployeeModel.save()
    res.json(createdEmployee)
   
}
```

เราสามารถใช้ try catch ในการจำ error ที่โยนออกมาจากการ validate โดยตัว model ของ mongoose ได้

```js
app.post('/employees', async (req, res) => {

    const newEmployee = req.body;

    try {
        const newEmployeeModel = new EmployeeModel(newEmployee)
        const createdEmployee = await newEmployeeModel.save()
        res.json(createdEmployee)
    } catch (error) {
        res.status(400).send(error.message)
    }
}
```

## 5. เรียกใช้ Schema ในการอ่านข้อมูล

1. ในไฟล์ `index.js` เราจะลงมาที่ `GET /employees` และทำการแก้ไขโค้ดให้มาใช้ mongoose แทน
2. ในที่นี้เราจะใช้ Model ในการอ่านข้อมูล

```js
app.get('/employees', async (req, res) => {

    const docs = await EmployeeModel.find()
    res.status(200).json(docs)

})
```

## 6. เราสามารถใช้ Schema ในการ search ก็ได้ 

เช่นการหาชื่อที่มีข้อความที่เราสนใจ ด้วย [$regex](https://www.mongodb.com/docs/manual/reference/operator/query/regex/)

```js
app.get('/employees/search', async (req, res) => {

    const searchName = req.query.name

    const docs = await EmployeeModel.find({ "firstName": { "$regex": `${searchName}`, "$options": "i" } })
    res.status(200).json(docs)

})
```

หรือใช้ [$or operator](https://www.mongodb.com/docs/manual/reference/operator/query/or/) ในการสร้างเงื่อนไขการเทียบหลาย field 

```js
app.get('/employees/search', async (req, res) => {

    const searchName = req.query.name

    const docs = await EmployeeModel.find({
        $or: [
            { "firstName": { "$regex": `${searchName}`, "$options": "i" } },
            { "lastName": { "$regex": `${searchName}`, "$options": "i" } },
            { "email": { "$regex": `${searchName}`, "$options": "i" } }
        ]
    })
    res.status(200).json(docs)

})
```