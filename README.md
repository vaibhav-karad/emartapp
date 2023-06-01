# emartapp
# Containerizing Microservice Project

This project demonstrates the containerization of a microservice-based application, consisting of an Angular client app, Java API, Node.js API, and Nginx as a reverse proxy.

## Project Structure

The project structure is organized as follows:

```
.
├── angular-client-app
├── java-api
├── node-api
└── nginx
```

- `angular-client-app`: Contains the source code for the Angular client application.
- `java-api`: Contains the source code for the Java API.
- `node-api`: Contains the source code for the Node.js API.
- `nginx`: Contains the configuration files for Nginx.

## Prerequisites

Before running this project, ensure you have the following dependencies installed on your machine:

- Docker: [Install Docker](https://docs.docker.com/get-docker/)
- Node.js: [Install Node.js](https://nodejs.org)

## Getting Started

To get started with this project, follow the steps below:

1. Clone the repository:

   ```bash
   git clone https://github.com/vaibhav-karad/emartapp.git
   ```

2. Build and run the Angular client app:

   ```bash
   cd angular-client-app
   npm install
   npm start
   ```

   The client app will be available at `http://localhost:4200`.

3. Build and run the Java API:

   ```bash
   cd java-api
   # Build the Java API
   ./gradlew build

   # Run the Java API
   java -jar build/libs/java-api.jar
   ```

   The Java API will be available at `http://localhost:8080`.

4. Build and run the Node.js API:

   ```bash
   cd node-api
   npm install
   npm start
   ```

   The Node.js API will be available at `http://localhost:3000`.

5. Build and run Nginx as a reverse proxy:

   ```bash
   cd nginx
   docker build -t my-nginx .
   docker run -p 80:80 my-nginx
   ```

   Nginx will be available at `http://localhost`.

## Containerization

To containerize each component of the microservice project, Docker is used. Each component (Angular client app, Java API, Node.js API) has its own Dockerfile in its respective directory.

To build and run the containers, follow these steps:

1. Build the Docker images for each component:

   ```bash
   cd angular-client-app
   docker build -t angular-client .

   cd ../java-api
   docker build -t java-api .

   cd ../node-api
   docker build -t node-api .
   ```

2. Run the containers:

   ```bash
   docker run -d -p 4200:80 angular-client
   docker run -d -p 8080:8080 java-api
   docker run -d -p 3000:3000 node-api
   ```

   The Angular client app will be available at `http://localhost:4200`, the Java API at `http://localhost:8080`, and the Node.js API at `http://localhost:3000`.

3. (Optional) Build and run the Nginx container:

   ```bash
   cd nginx
   docker build -t my-nginx .
   docker run -d -p 80:80 my-nginx
   ```

   Nginx will be available at `http://localhost`.

## Additional Configuration

If you need to modify the configuration of Nginx, you can edit the `nginx.conf` file located in the