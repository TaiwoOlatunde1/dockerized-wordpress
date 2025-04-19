
---

```markdown
# 🐳 WordPress + MySQL + Ngrok Docker Setup

[![Docker](https://img.shields.io/badge/docker-ready-blue?logo=docker&logoColor=white)](https://www.docker.com/)
[![WordPress](https://img.shields.io/badge/wordpress-dev-blueviolet?logo=wordpress&logoColor=white)](https://wordpress.org/)
[![MySQL](https://img.shields.io/badge/mysql-5.7-blue?logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Ngrok](https://img.shields.io/badge/ngrok-enabled-orange?logo=ngrok&logoColor=white)](https://ngrok.com/)

---

This project sets up a local WordPress development environment using Docker Compose. It includes:
- WordPress (latest version)
- MySQL 5.7
- Ngrok for public HTTPS tunneling

Everything was built **from scratch in VS Code**, including:
- `.env` for local configuration
- `.env.example` as a safe template for environment variables
- `.gitignore` to prevent sensitive files from being tracked
- `docker-compose.yml` to define and run the services

---

## 📦 Requirements

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Ngrok account](https://ngrok.com/) (for your auth token)

---

## 🚀 Getting Started

### 1. Create a `.env` File

Start by creating a `.env` file in the root of your project using the provided `.env.example`:

```bash
cp .env.example .env
```

Then fill in your actual values:

```env
MYSQL_DATABASE=wordpress
MYSQL_USER=wpuser
MYSQL_PASSWORD=wppassword
MYSQL_ROOT_PASSWORD=rootpassword
NGROK_TOKEN=your_ngrok_authtoken
```

> 💡 Get your Ngrok token from [https://dashboard.ngrok.com/get-started/your-authtoken](https://dashboard.ngrok.com/get-started/your-authtoken)

---

### 2. Start the Containers

```bash
docker-compose up -d
```

---

### 3. Access Your Site

- **Local WordPress**: [http://localhost:8080](http://localhost:8080)
- **Ngrok Public URL**: Go to [http://localhost:4040](http://localhost:4040) and find the public HTTPS link

---

## 📁 Project Structure

```
.
├── .env             # Your local environment config (not committed)
├── .env.example     # Template with required environment variables
├── .gitignore       # Prevents .env and other local files from being tracked
└── docker-compose.yml  # WordPress, MySQL, and Ngrok service definitions
```

---

## 📁 Volumes

Docker volumes are used for persistent data:

- `wp_data`: WordPress files
- `db_data`: MySQL database

---

## 🔄 Restart Policy

All services use `restart: always` to automatically restart on failure or system reboot.

---

## 📡 Networking

All services are connected through a shared custom network `wp_network` for secure and isolated communication.

---

## 🧹 Stopping and Cleaning Up

To stop and remove all services, volumes, and the custom network:

```bash
docker-compose down -v
```

---

## ⚠️ Notes

- This setup is for **development purposes only** — not production ready as-is.
- Ngrok exposes your local WordPress site to the public internet — share responsibly.

---

## 🛠 Troubleshooting

- Make sure your `.env` file exists and has valid values.
- If you encounter issues with Ngrok, double-check your token or visit your [Ngrok dashboard](https://dashboard.ngrok.com).

---
```