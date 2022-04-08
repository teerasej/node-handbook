
# วิธีสร้าง Image และใช้งาน Container

## 1. สร้าง Dockerfile

ตัว Image สามารถสร้างขึ้นมาใช้งานได้ด้วยการเขียนกำหนดขั้นตอนใน `dockerfile`

ให้ทำการสร้าง dockerfile

```dockerfile
# เลือก image เริ่มต้นแบบที่ติดตั้ง node เวอร์ชั่น 16
FROM node:16-alpine

# กำหนด path ไปที่ directory 
WORKDIR /usr/src/app

# สั่ง copy ไฟล์ package.json  ไปก่อน
COPY package*.json ./

# จากนั้นรันคำสั่งติดตั้ง package
RUN npm install
# If you are building your code for production
# RUN npm ci --only=production

# ตามด้วย copy ไฟล์ทั้งหมดใน folder ไป
COPY . .

# กำหนดให้ image มีการเปิด port 3000 ให้ตอนที่สร้างเป็น container 
EXPOSE 3000

# ตอนทำงานให้รันทำสั่งต่อไปนี้
CMD [ "node", "index.js" ]
```

## 2. ละเว้นไฟล์ด้วย `.dockerignore`

- เราสามารถกำหนดให้ docker ละเว้นไฟล์หรือโฟลเดอร์จากคำสั่งใน dockerfile โดยการเขียนไว้ในไฟล์ชื่อ dockerignore 
- วิธีการเขียนจะเป็นแบบเดียวกับ gitignore

ให้เราสร้างไฟล์ `.dockerignore` และระบุโฟลเดอร์ที่ต้องการลงไปใน file

```
node_module
```

## สร้าง Image จาก Dockerfile

จากนั้นเราสามารถรันคำสั่ง dockerfile เพื่อสร้าง image ตามคำสั่งที่เขียนไว้ได้โดยการรันคำสั่งด้านล่างใน terminal

```
docker build . -t <ชื่อ username>/<ชื่อ Image>
```

เช่น

```
docker build . -t teerasej/node-web-app
```

1. docker จะทำตามคำสั่ง เช่นไปโหลด image ต้นฉบับ (node:16) มาไว้ในเครื่อง ต่อด้วยการ copy ไฟล์เข้าไปไว้ใน image 
2. เสร็จแล้ว ให้ตรวจสอบจาก Docker Extension ว่ามี Image ของเราแสดงขึ้นมาไหม

### Tips 

เราสามารถติด tag ให้ docker image ของเราได้ด้วยนะ เช่น 

```
docker build . -t teerasej/node-web-app:1.0
docker build . -t teerasej/node-web-app:production
docker build . -t teerasej/node-web-app:final
docker build . -t teerasej/node-web-app:finalfinal
```

## การรัน Image ขึ้นมาใช้งานเป็น Container 

```
docker run -p 3100:3000 -d <ชื่อ username>/<ชื่อ Image>
```

1. จากนั้นตรวจสอบผ่าน Docker Extension จะเห็น Container แสดงขึ้นมา
2. ทดสอบส่ง Request ไปที่ port 3100 ได้เลย เช่น http://localhost:3100

3. แต่จะเห็นว่าการส่ง request ไปที่ http://localhost:3100/employees จะไม่มีค่าอะไรกลับมาเพราะว่า...

ใน container ไม่มี mongoDB หน่ะสิ!