# WordPress Installation Using Docker on Ubuntu

![WordPress Logo](your-image-link-here)

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
git clone https://github.com/yourusername/wordpress-docker-setup.git
cd wordpress-docker-setup
```

### Step 2: Start Docker Services
```bash
docker-compose up -d
```

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

You will see the WordPress installation page.

---

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

---

## 📸 Example Screenshots
> *(Add your screenshots here after each step)*

| Step | Screenshot |
|:----:|:-----------:|
| Docker Services Up | ![docker-compose up](your-image-link-here) |
| WordPress Installation Page | ![wordpress-installation-page](your-image-link-here) |



## 🧐 Notes
- Default WordPress DB username: `wordpress`
- Default WordPress DB password: `wordpress`
- Default MySQL root password: `rootpassword`
- Data persistence is enabled using Docker volumes (`wordpress_data`, `db_data`).



## 📈 Future Improvements
- Add support for SSL with Let's Encrypt.
- Use `.env` file to manage environment variables securely.
- Set up auto backup for database.


# ⭐ Give it a Star!
If you find this project helpful, please give it a ⭐️ on GitHub!
