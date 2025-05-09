# WordPress Installation Using Docker on Ubuntu

## 📖 Project Overview
This project demonstrates **how to install and run WordPress using Docker and Docker Compose** on an Ubuntu server.  
It simplifies the setup of a full WordPress environment (WordPress + MySQL) in a few commands.

---

## 🛠️ Technologies Used
- **Docker** (Containerization)
- **Docker Compose** (Multi-container orchestration)
- **Ubuntu 20.04+** (Linux Distribution)
- **WordPress** (CMS)
- **MySQL** (Database)

---

## 📋 Prerequisites
Before starting, make sure you have:

- A Linux machine (Ubuntu 20.04+, or compatible).
- Docker installed.
- Docker Compose installed.

If not installed yet, follow these commands:

### Install Docker
```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
docker --version
```

### Install Docker Compose
```bash
sudo apt install -y docker-compose
docker-compose --version
```

---

## 📂 Project Structure

```
wordpress-docker-setup/
├── docker-compose.yml
├── README.md
└── .env (optional for environment variables)
```

---

## 📝 docker-compose.yml Content

```yaml
version: '3.8'

services:
  wordpress:
    image: wordpress:latest
    container_name: wordpress
    restart: always
    ports:
      - "8000:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - wordpress_data:/var/www/html

  db:
    image: mysql:5.7
    container_name: wordpress_db
    restart: always
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
      MYSQL_ROOT_PASSWORD: rootpassword
    volumes:
      - db_data:/var/lib/mysql

volumes:
  wordpress_data:
  db_data:
```

---

## 🚀 Setup Instructions

### Step 1: Clone the Repository
```bash
git clone https://github.com/obidahalqudah/wordpress-docker-setup.git
cd wordpress-docker-setup
```

### Step 2: Start Docker Services
```bash
docker-compose up -d
```
![image](https://github.com/user-attachments/assets/af125046-acc3-477d-a58d-63e92ca27eb1)

This will:
- Download WordPress and MySQL images if they are not already present.
- Create two containers (`wordpress`, `wordpress_db`).
- Map WordPress on port `8000`.

### Step 3: Access WordPress
Open your browser and go to:

```
http://localhost:8000
```
or if you are using a server:

```
http://your-server-ip:8000
```
![image](https://github.com/user-attachments/assets/dc25e0f2-0daa-4d24-8d5f-029228fd1ce3)

You will see the WordPress installation page.

---
![image](https://github.com/user-attachments/assets/ef255cb6-0aef-40dd-b786-7eecc15d72dd)

## 🔥 Managing Containers

### To View Running Containers
----bash
docker ps
```

### To Stop Containers
```bash
docker-compose down
```

### To Restart Containers
----bash
docker-compose restart
```




## 🧐 Notes
- Default WordPress DB username: `wordpress`
- Default WordPress DB password: `wordpress`
- Default MySQL root password: `rootpassword`
- Data persistence is enabled using Docker volumes (`wordpress_data`, `db_data`).




# ⭐ Give it a Star!
If you find this project helpful, please give it a ⭐️ on GitHub!
