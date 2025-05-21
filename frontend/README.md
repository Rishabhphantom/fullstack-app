**please update the packages in this folder to gain the full benefits**
**npm install**

# React Frontend (Dockerized)

This is a Dockerized React frontend application served via Nginx. It connects to a Node.js backend running on port 4000.

## 📁 Project Structure

nginx-proxy-frontend/
├── Dockerfile
├── nginx.conf # Nginx config with API proxy
├── package.json
├── public/
├── src/
└── .env # Optional: for setting API URL


## 🛠️ Prerequisites

Ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/ )

## 🐳 Build the Docker Image

Run this command in the `nginx-proxy-frontend` directory:

```bash
docker build -t react-frontend .
.
## 🚀 Run the Container
docker run --name frontend \
  -p 80:80 \
  -d react-frontend

🌐 Configure API URL
REACT_APP_API_URL=http://backend:4000

⚙️ Use Nginx Proxy
The app uses an Nginx proxy configured in nginx.conf
location /api/ {
    proxy_pass http://backend:4000/;
}
Set env file
REACT_APP_API_URL=/api


🧪 Test the App
http://localhost
