
# การใช้งาน docker compose ในการรัน multi-container

ในการทำงานจริงเราสามารถรัน container หลายๆ ตัวพร้อมกันเป็นระบบใหญ่ได้ โดยที่ container แต่ละตัวสามารถอ้างอิงถึงกันภายใน เหมือนระบบ computer ที่อยู่ใน network เดียวกัน

เราสามารถทำแบบนี้ได้ด้วย dockercompose

ให้สร้างไฟล์ `docker-compose.yml` และระบุ configuration ลงไปด้านล่าง

```dockerfile
version: '3'

services:

    # ชื่อของ service ที่ต้องการกำหนดอ้างอิงในกลุ่มเดียวกัน
    # ในที่นี้เรากำหนด container ของ mongoDB image ในชื่อ db
    db:
        # หากต้องการกำหนดชื่อ container
        # container_name: database_mongo

        # ให้แน่ใจว่าได้ระบุ image ที่ต้องการ รวมถึง tag ที่ถูกต้องจริงๆ
        image: mongo

    # ชื่อของ service ที่ต้องการกำหนดอ้างอิงในกลุ่มเดียวกัน
    api:
        # หากต้องการกำหนดชื่อ container
        # container_name: api_main

        # ให้แน่ใจว่าได้ระบุ image ที่ต้องการ รวมถึง tag ที่ถูกต้องจริงๆ 
        image: teerasej/web_api

        # สามารถกำหนด environment variable จาก compose ได้ด้วย
        environment:
            - PORT=3000
            - MONGO_DB_HOST=db
            - MONGO_DB_PORT=27017

        # กำหนดอ้างอิงถึง db
        depends_on:
            - db

        # map port
        ports:
          - "3100:3000"
```

จากนั้นทดสอบการทำงานโดยใช้คำสั่งด้านล่างใน Terminal

```
docker-compose up
```