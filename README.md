# Containerization of Java Project using Docker

## Overview

This project demonstrates the containerization of a Java-based application using Docker. The architecture includes an Nginx frontend, a Tomcat-based application server, a MySQL backend, and additional services such as RabbitMQ and Memcached. The setup involves multi-stage Docker builds to efficiently manage the application image and reduce its size. The Docker engine runs on an AWS EC2 instance of the `t2.small` type.

## Architecture Diagram
![Vprofile projectsetup Manual](https://github.com/user-attachments/assets/9290a0d2-89ce-461e-b103-992a327124e6)

## Project Structure

- **Frontend**: Nginx
  - The Nginx server serves as the frontend for the application. 

- **Application Server**: Tomcat
  - The backend Java application is deployed on an Apache Tomcat server. A **multi-stage Docker build** is used for the application server:
    - **Stage 1**: Builds the artifact.
    - **Stage 2**: Sets up the Tomcat application server using the built artifact.

- **Backend**: MySQL
  - The database backend is handled by a MySQL server. A custom Dockerfile was written for MySQL to accommodate the specific configuration needs of the application.

- **Additional Services**:
  - **RabbitMQ**: Used for message queuing.
  - **Memcached**: Used for caching.
  - Both RabbitMQ and Memcached utilize standard Docker images from Docker Hub.

## Docker Workflow
![Containerization of Java Project using Docker](https://github.com/user-attachments/assets/201e12ba-113f-4a28-9966-8268dab562e7)

1. **Source**: Write Dockerfiles for Nginx, Tomcat (with multi-stage build), and MySQL. Use standard images for RabbitMQ and Memcached.
2. **Build**: Perform a Docker build using multi-stage builds to create efficient images for Nginx and Tomcat.
3. **Test**: Use Docker Compose to test the entire application stack locally.
4. **Store**: Push the built images to Docker Hub or your private registry.

## Setup and Installation

### Prerequisites

- Docker
- Docker Compose
- AWS EC2 instance (t2.small)

### Steps to Run

1. **Launch an EC2 Instance**
   - Launch an EC2 instance of `t2.small` type.
   - Install Docker Engine on the instance.

2. **Clone the Repository**
   ```bash
   git clone 
   cd vprofile-project
   git checkout containers
   ```

3. **Build and Run the Docker Containers**
   ```bash
   docker compose up 
   ```

4. **Access the Application**
   - The application should now be accessible through the Nginx frontend at `http://<EC2-Instance-Public-IP>:8080`.

### Additional Commands

- **Stop the Containers**
  ```bash
  docker compose down
  ```

- **View Logs**
  ```bash
  docker compose logs -f
  ```
