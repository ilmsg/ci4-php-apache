# ci4-php-apache

เครื่องมือที่ใช้

    - windows 10 with wsl2
    - vscode
    - docker desktop
    - docker compose
    - composer
    - codeigniter

สำหรับ php:8.3-apache มีส่วน ext, อื่นๆ เพิ่มเข้ามาอีก, มี git, composer ที่ใส่ comment ปิดเอาไว้อยู่ (เผื่อวันไหนอยากใช้อ่ะนะ)

ไพล `docker-compose.yml` 

    - php:8.3-apache
    - mysql:8.4
    - phpmyadmin:5.2-apache

ขั้นตอนที่ 1 - clone repo ลงมา

    $ git clone https://github.com/ilmsg/ci4-php-apache.git <project_name>

ขั้นตอนที่ 2 - รันตัว docker compose

    $ cd <project_name>
    $ docker compose up -d

ขั้นตอนที่ 3 - รันตัว composer install 

    $ cd php/webapp
    $ composer install

หลังจากนั้น ทำตาม step การเริ่มต้นตั้งค่าใช้งาน ci4 แบบปกติได้เลยย

ขั้นตอนที่ 4 - ก๊อปปี้ตัว .env จากตัวอย่าง

    $ cp env .env

ขั้นตอนที่ 5 - เปิดแก้ไขไพล์ .env 

    # CI_ENVIRONMENT = production
    CI_ENVIRONMENT = development

    app.baseURL = 'http://localhost:8000'

---
สร้าง project codeignter จากคำสั่งนี้

    $ composer create-project codeigniter4/appstarter php/webapp

---
มี composer ด้วยนะ ถ้าอยากจะใช้ (อย่าลืมเอา comment ที่เป็นตัว install composer ในตัว Dockerfile ออกก่อน)

    $ docker exec -it ci4-php-apache /bin/bash

ถ้ายังไม่มี composer ก็ลงได้จากตรงนี้

    $ curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

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