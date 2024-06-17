# ci4-php-apache

สำหรับ php:8.3-apache มีส่วน ext, อื่นๆ เพิ่มเข้ามาอีก, มี git, composer ที่ใส่ comment ปิดเอาไว้อยู่ (เผื่อวันไหนอยากใช้อ่ะนะ)

ไพล `docker-compose.yml` 

    - php:8.3-apache
    - mysql:8.4
    - phpmyadmin:5.2-apache

รันตัว docker compose

    $ docker compose up -d

init ตัว ci project ด้วย composer (จากตัว local ของเราเอง)

    $ cd php/webapp
    $ composer create-project codeigniter4/appstarter .

ในกรณีที่เราจะใช้ composer ภายใน (อย่าลืมเอา comment ที่เป็นตัว install composer ในตัว Dockerfile ออกก่อน)

    $ docker exec -it ci4-php-apache /bin/bash

หลังจากนั้น ทำตาม step การเริ่มต้นตั้งค่าใช้งาน ci4 แบบปกติได้เลยย

๊ก๊อปปี้ตัว .env จากตัวอย่าง

    $ cp env .env

เปิดแก้ไขไพล์ .env 

    # CI_ENVIRONMENT = production
    CI_ENVIRONMENT = development

    app.baseURL = 'http://localhost:8000'

---

- หลังจากใช้ composer สร้าง ci project แล้ว (แต่ยังไม่ได้สร้างไพล์ .env) ไม่ต้องตกใจ! ไปสร้าง .env กันก่อน
![](/images/2024-06-17_091910.png)

---
- หลังจากสร้างไพล์ .env เรียบร้อยแล้ว
![](/images/2024-06-17_091554.png)

แก้ไขด้วย

    $ chmod 777 -R writable

---
- แบบนี้ก็พร้อมลุยโค้ดกันแล้วววว
![](/images/2024-06-17_092523.png)