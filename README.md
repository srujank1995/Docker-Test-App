Here’s a `README.md` file for the Docker commands you provided:

```markdown
# Docker Node.js Application Setup

This repository contains the necessary steps to containerize a Node.js application using Docker. The following instructions will guide you through creating a Docker image, pushing it to Docker Hub, and running it in a container.

## Prerequisites

- Docker installed on your local machine.
- A Docker Hub account.

## Steps to Containerize and Run the Application

### 1. Create a Dockerfile

First, create a `Dockerfile` in your project directory:

```bash
touch Dockerfile
```

Then, open the `Dockerfile` and add the following content:

```Dockerfile
# Use Node.js version 18 with Alpine Linux
FROM node:18-alpine

# Set the working directory in the container to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . .

# Install dependencies, only production dependencies
RUN yarn install --production

# Command to run the application
CMD ["node", "src/index.js"]

# Expose port 3000 to the outside world
EXPOSE 3000
```

### 2. Build the Docker Image

Build the Docker image using the following command:

```bash
docker build -t test-img1 .
```

### 3. Log in to Docker Hub

Log in to your Docker Hub account:

```bash
docker login
```

### 4. Tag the Docker Image

Tag the image with your Docker Hub username and repository name:

```bash
docker tag test-img1:latest srukinj01/test-img-hub:latest
```

### 5. View Docker Images

You can list all Docker images on your local machine using:

```bash
docker images
```

### 6. Push the Docker Image to Docker Hub

Push the tagged image to your Docker Hub repository:

```bash
docker push srukinj01/test-img-hub:latest
```

### 7. Run the Docker Container

Run the Docker container from the image you just pushed to Docker Hub:

```bash
docker run -dp 3000:3000 srukinj01/test-img-hub:latest
```

### 8. Access the Running Container

To access the running container’s shell, use one of the following commands:

```bash
docker exec -it <container_name> sh
```

or

```bash
docker exec -it <container_id> sh
```

### 9. View Container Logs

To view the logs of the running container:

```bash
docker logs <container_name>
```

## Conclusion

By following these steps, you will successfully containerize your Node.js application, push it to Docker Hub, and run it in a Docker container. Feel free to customize the Dockerfile and commands according to your project's requirements.

# Docker-Test-App
