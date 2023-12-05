
# ตัวแปร และค่าคงที่ (Variable & Constant)

## 1. Variable 

การประกาศตัวแปร

```ts
let username = "Teerasej";
let birthYear = 1985;
```

สังเกตว่าใน TypeScript ถ้าไม่ระบุชนิดของตัวแปร TypeScript จะพยายามกำหนดให้ตัวแปรเป็นชนิดที่เหมาะสม โดยอ้างอิงจากค่าที่กำหนดให้กับตัวแปร

<img width="457" alt="2023-12-05_18-10-12" src="https://github.com/teerasej/node-handbook/assets/85179/c2b6225b-601d-4dfa-8e3e-0f132531a178">

<img width="489" alt="2023-12-05_18-10-18" src="https://github.com/teerasej/node-handbook/assets/85179/5f57d2dc-438e-4302-a655-a67c36ece260">


## 2. Constant

การประกาศค่าคงที่

```ts
const IP = "127.0.0.1";

IP = "192.168.1.1" // ตรงนี้จะเกิด Error เพราะพยายามกำหนดค่าใหม่ให้ const
```
