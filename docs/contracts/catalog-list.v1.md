# API รายการสินค้า

สถานะ: PROPOSED
รุ่น: v1
เจ้าของข้อเสนอ: Microservice

คำขอ: GET /api/v1/catalog/products

Request body: ไม่ส่ง

Query: available เลือกใส่ได้ รับ true หรือ false

# ผลลัพธ์ของ Query `available`

| Query | คำอธิบาย | สถานะ | Data JSON |
|-------|----------|:-----:|-----------|
| *(ไม่ใส่ `available`)* | ได้ข้อมูลสินค้าทั้งหมด | 200 | `{"data":[{"id":"pencil","name":"ดินสอ","priceSatang":1200,"available":true},{"id":"ruler","name":"ไม้บรรทัด","priceSatang":2000,"available":false},{"id":"eraser","name":"ยางลบ","priceSatang":800,"available":true},{"id":"sharpener","name":"กบเหลาดินสอ","priceSatang":1500,"available":false}]}` |
| `available=true` | ได้ข้อมูลสินค้าที่เหลืออยู่ | 200 | `{"data":[{"id":"pencil","name":"ดินสอ","priceSatang":1200,"available":true},{"id":"eraser","name":"ยางลบ","priceSatang":800,"available":true}]}` |
| `available=false` | ได้ข้อมูลสินค้าที่ไม่เหลือแล้ว | 200 | `{"data":[{"id":"ruler","name":"ไม้บรรทัด","priceSatang":2000,"available":false},{"id":"sharpener","name":"กบเหลาดินสอ","priceSatang":1500,"available":false}]}` |
| `available=yes` | ค่าไม่ถูกต้อง จะได้ error แทน | 422 | `{"error":{"code":"VALIDATION_ERROR","message":"available must be 'true' or 'false'"}}` |

