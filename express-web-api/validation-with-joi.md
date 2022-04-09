
# Validate JSON ด้วย Joi

## 1. ติดตั้ง package 

```bash
npm i joi 
```

## 2. สร้าง Validation Schema

เปิดไฟล์ `index.js` เราจะทำการเพิ่มการใช้งาน Joi ใน Route `POST /employees`

```js
const Joi = require('joi');

//...

app.post('/employees', async (req, res) => {
    
    //...

    // สร้าง Object validation rule โดยการกำหนด field และ validation rule ให้แต่ละ field
    const objectSchema = Joi.object({
        firstName: Joi.string().min(3).required(),
        lastName: Joi.string().min(3).required(),
        email: Joi.string().email().required()
    })

    // ทำการ validate object และนำค่า error มาตรวจสอบ
    const { error } = objectSchema.validate(newEmployee)

    // ถ้ามี error เราจะส่ง Status code 400 พร้อมข้อความ error กลับไป
    if(error) {
        console.log(error)
        res.status(400).json({ message: error.details[0].message })
    }

    console.log('New employee:', newEmployee);

    //...
}
```

## 3. กำหนด error message ตามเงื่อนไข

rule ใน joi มีหลากหลายแบบ ซึ่งแต่ละแบบจะมี[ชื่อที่สามารถอ้างอิงได้จากที่นี่](https://joi.dev/api/?v=17.6.0#errors)

```js
app.post('/employees', async (req, res) => {
    
    //...

    const objectSchema = Joi.object({
        // กำหนดข้อความ Error ตาม
        firstName: Joi.string().min(3).required().messages({
            "string.min": "Must more than 3 characters",
            "any.required":"Email is required!"
        }),
        lastName: Joi.string().min(3).required(),
        email: Joi.string().email().required().messages({
            "any.required":"Email is required!"
        })
    })
    const { error } = objectSchema.validate(newEmployee)


    if(error) {
        console.log(error)
        res.status(400).json({ message: error.details[0].message })
    }

    console.log('New employee:', newEmployee);

    //...
}
```