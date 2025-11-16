# Nginx + Certbot Docker Setup

A simple Docker-based setup to serve static websites with **HTTPS** using Nginx and **Let’s Encrypt**.  
Allows full manual control over Nginx configuration while still supporting automatic certificate renewal via Certbot.

---

## Features

- Serve static HTML or React build with Nginx
- HTTPS via Let’s Encrypt certificates
- HTTP → HTTPS automatic redirect
- Manual Nginx configuration for full control
- Automated certificate renewal via Cron

---

## Project Structure



---

## Prerequisites

- Docker & Docker Compose installed on your host
- Domain pointing to your server’s public IP
- Ports **80 (HTTP)** and **443 (HTTPS)** open in firewall/security group

---

## Getting Started

1. **Clone the repository**

```bash
git clone https://github.com/yourusername/nginx-certbot.git
cd nginx-certbot
```
Place your index.html or React build files inside the html/ folder.
Add your domain into the conf.d/default.conf file

```bash
docker compose up -d nginx

docker run --rm \
  -v $(pwd)/certs:/etc/letsencrypt \
  -v $(pwd)/html:/usr/share/nginx/html \
  certbot/certbot certonly \
  --webroot -w /usr/share/nginx/html \
  -d yourdomain.com -d www.yourdomain.com \
  --email youremail@domain.com --agree-tos --non-interactive

docker exec nginx nginx -s reload

```




