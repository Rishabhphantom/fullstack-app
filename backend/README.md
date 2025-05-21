Node.js Backend (Dockerized)

This is a Dockerized Express backend application that connects to a MySQL database running outside of Docker on the local machine.

📁 Project Structure
backend/
├── Dockerfile            # Docker image definition
├── server.js             # Express server with MySQL connection
├── .env.example          # Example environment config
├── package.json          # Node.js dependencies
└── README.md             # This file

🛠️ Requirements

Ensure you have:

Docker
Also ensure:

A MySQL server is running locally or accessible from your host.
The required database and table are already created.

🐳 Build the Docker Image
Run this command in the backend directory:
docker build -t node-backend .
This builds a Docker image named node-backend based on the instructions in the Dockerfile.

🚀 Run the Container
To run the container and connect it to your local MySQL server , use:
docker run --name backend \
  -p 4000:4000 \
  -e DB_HOST=localhost \
  -e DB_PORT=3306 \
  -e DB_USER=root \
  -e DB_PASSWORD=Asher976123@ \
  -e DB_NAME=myapp \
  -d node-backend
  
  
  🗄️ MySQL Setup
  Make sure the required database and table exist before starting the backend.
  CREATE DATABASE myapp;

USE myapp;

CREATE TABLE formData (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  message TEXT
);
We can verify data insertion after submitting the form via the frontend.

🧪 Test the API
After starting the container, test the API endpoint using curl :

Submit Form Data

curl -X POST http://localhost:4000/submit \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@example.com","message":"Hello World"}'
  
  Expected Response
  {
  "message": "Your response has been saved"
}

Check if Data Was Stored

In MySQL CLI:

USE myapp;
SELECT * FROM formData;

You should see the submitted data.

🔍 View Logs
If you need to debug any issues:

docker logs backend

docker compose up --build
