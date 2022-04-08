


```
FROM node:16-alpine

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm ci --only=production

COPY . .

EXPOSE 3000

CMD [ "node", "index.js" ]
```

## สร้าง Image จาก Dockerfile

```
docker build . -t <ชื่อ username>/<ชื่อ Image>
```

เช่น

```
docker build . -t teerasej/node-web-app
```

ตรวจสอบจาก Docker Extension ว่ามี Image ของเราแสดงขึ้นมาไหม

## การรัน Image ขึ้นมาใช้งานเป็น Container 

```
docker run -p 3100:3000 -d <ชื่อ username>/<ชื่อ Image>
```

จากนั้นตรวจสอบผ่าน Docker Extension จะเห็น Container แสดงขึ้นมา

ทดสอบส่ง Request ไปที่ port 3100 ได้เลย