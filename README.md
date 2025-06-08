![e2e-2](https://github.com/user-attachments/assets/58fa994b-8d4f-43dc-8b27-a7d36464225e)

# Java Hello World Application with CI/CD Pipeline

This project demonstrates a Java Spring Boot application with a complete CI/CD pipeline using GitHub Actions, Docker, and GitOps principles.
Works with 2 repos - application code repo and gitops_repo [Helm charts, argocd configs etc]

## Overview

The application is a simple "Hello World" Spring Boot service that:
- Runs on port 8081
- Returns "Hello, World!" at the root endpoint
- Is containerized using Docker
- Has an automated CI/CD pipeline that builds, tests, and deploys the application

## Architecture Components

1. **Application Code**:
   - Spring Boot Java application
   - Single endpoint at `/` returning a greeting
   - Configured to run on port 8081

2. **Docker Image**:
   - Based on OpenJDK 11 JRE slim image
   - Copies built JAR file into container
   - Exposes port 8081

3. **CI/CD Pipeline** (defined in `.github/workflows/ci-cd.yaml`):
   - Triggered on pushes to `main` branch and pull requests
   - Builds the application with Maven
   - Builds and pushes a Docker image to Docker Hub
   - Updates the GitOps repository with the new image tag
   - Creates a PR in the GitOps repository for deployment

## Prerequisites

- Java 11+
- Maven
- Docker
- GitHub account
- Docker Hub account
- GitHub Personal Access Token (PAT) with repo permissions
- Self-hosted GitHub Actions runner
