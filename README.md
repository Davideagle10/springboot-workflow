# Spring Boot Web Application  
### CI/CD with GitHub Actions & GitHub Container Registry (GHCR)

A minimal, production-ready **Spring Boot REST application** with a fully automated **CI/CD pipeline** that builds, tests, containerizes, and publishes Docker images to **GitHub Container Registry (GHCR)** using **GitHub Actions**.

This repository demonstrates modern **Java backend**, **containerization**, and **DevOps** practices in a clean and reproducible setup.

---

## 📌 Overview

- **Framework:** Spring Boot  
- **Build Tool:** Gradle (Wrapper)  
- **Containerization:** Docker  
- **CI/CD:** GitHub Actions  
- **Container Registry:** GitHub Container Registry (GHCR)

The pipeline automatically:

1. Builds the application JAR  
2. Runs unit tests  
3. Builds a Docker image  
4. Authenticates securely to GHCR  
5. Pushes the image to the registry  

---

## 🚀 Application Description

The application exposes a simple REST endpoint:
```http
GET /webapp
```

### Example Request
```http
GET /webapp?name=David
```

### Example Response
```text
Hello David!
```

If no query parameter is provided:
```text
Hello World!
```

---

## 🧪 Testing

The project includes a basic Spring Boot context load test to validate application startup and configuration:
```java
@SpringBootTest
class WebappApplicationTests {

    @Test
    void contextLoads() {
    }

}
```

This ensures:

- Spring context initializes correctly
- Application configuration is valid

---

## 🏗️ Project Structure
```text
.
├── LICENSE
└── webapp
    ├── Dockerfile
    ├── build.gradle
    ├── settings.gradle
    ├── gradlew
    ├── src
    │   ├── main
    │   │   ├── java
    │   │   └── resources
    │   └── test
    └── build
```

The project follows the standard Spring Boot + Gradle layout, making it easy to understand, extend, and deploy.

---

## 🐳 Docker

The application is packaged as a Docker image.

### Image Name
```text
ghcr.io//springboot-webapp:webapp-latest
```

### Run Locally
```bash
docker run -p 8080:8080 ghcr.io//springboot-webapp:webapp-latest
```

Then open:
```text
http://localhost:8080/webapp
```

---

## 🔄 CI/CD Pipeline

The CI/CD pipeline is implemented using **GitHub Actions** and is triggered on every push.

### Pipeline Stages

1. Checkout repository
2. Build JAR with Gradle
3. Run tests
4. Build Docker image
5. Authenticate to GHCR
6. Push image to the registry

### Security Notes

- Uses GitHub ephemeral `GITHUB_TOKEN`
- No long-lived secrets
- Minimal permissions (`packages: write`)

---

## 🔐 GitHub Container Registry Authentication

Authentication to GHCR is handled using GitHub Actions built-in token:

- Token is automatically generated
- Token is scoped to the repository
- Token expires at the end of the workflow

This follows GitHub's official security best practices.

---

## 🧠 Design Principles

- Minimal but realistic application
- Reproducible builds
- Infrastructure-agnostic container image
- Secure CI/CD by default
- Clear separation between application and delivery pipeline
