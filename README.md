# Habit Tracker – End-to-End DevOps CI/CD & GitOps Project

## Project Overview

An end-to-end DevOps implementation of a Java Spring Boot Habit Tracker application using Jenkins, Maven, SonarQube, Docker, Helm, Kubernetes and Argo CD.

The project demonstrates automated continuous integration, code quality analysis, containerization, Helm-based deployment and GitOps continuous delivery.

## Architecture

GitHub → Jenkins → Maven Build & Test → SonarQube → Docker Build & Push → Docker Hub → Helm → Argo CD → Kubernetes (KIND)

## Technology Stack

| Category | Tools |
|---|---|
| Application | Java 21, Spring Boot |
| Build | Maven |
| CI/CD | Jenkins |
| Code Quality | SonarQube |
| Containerization | Docker |
| Container Registry | Docker Hub |
| Deployment | Kubernetes, Helm |
| GitOps | Argo CD |
| Version Control | Git, GitHub |
| Local Kubernetes | KIND |

## CI Pipeline – Jenkins

The Jenkins declarative pipeline includes:

1. Source code checkout from GitHub.
2. Maven build and test execution.
3. SonarQube code analysis.
4. Docker image build.
5. Docker image push to Docker Hub.
6. JUnit test report publishing and JAR artifact archiving.

**Result:** Jenkins pipeline executed successfully.

## Code Quality – SonarQube

- Integrated SonarQube with Jenkins.
- Executed static code analysis.
- Verified the Quality Gate.

**Result:** Quality Gate passed.

## Docker

- Containerized the Spring Boot application.
- Built and pushed Docker images to Docker Hub.
- Used a non-root container configuration.

Docker Hub repository: https://hub.docker.com/r/manujanaa/habit-tracker

## Kubernetes & Helm

- Created Helm charts for the Habit Tracker application.
- Configured Kubernetes Deployment and Service.
- Configured application probes and resource settings.
- Deployed the application to a local KIND cluster.
- Verified application access through Kubernetes Service.

## GitOps – Argo CD

- Installed Argo CD in the KIND cluster.
- Connected Argo CD to the GitHub repository.
- Created an Argo CD Application using the Helm chart.
- Configured automated synchronization and self-healing.
- Verified successful synchronization and application health.

**Final verification:**
- Sync Status: Synced
- Health Status: Healthy
- Habit Tracker replica: 1/1 Running
- Application tested successfully through the Kubernetes Service.

## Application

The Habit Tracker provides functionality to:
- Create and manage habits.
- Track daily completions.
- Monitor current and longest streaks.
- View completion statistics.

**Note:** The application currently uses in-memory storage. Data is not persistent across application restarts.

## Repository Structure

```text
HabitApp/
├── src/
├── pom.xml
├── Dockerfile
├── Jenkinsfile
├── sonar-project.properties
├── helm/
│   └── habit-tracker/
├── argocd/
│   └── application.yaml
└── README.md
```

## Screenshots

Project execution evidence includes:

- Jenkins successful pipeline execution.
- SonarQube Quality Gate.
- Docker Hub image repository.
- Helm deployment.
- Kubernetes pods and services.
- Argo CD application synchronization.
- Argo CD Healthy status.
- Running Habit Tracker application.

## Key Learning Outcomes

- Building Jenkins declarative CI pipelines.
- Automating Maven builds and tests.
- Integrating SonarQube into CI.
- Building and publishing Docker images.
- Deploying Java applications using Helm.
- Managing Kubernetes workloads.
- Implementing GitOps using Argo CD.
- Troubleshooting Kubernetes application deployments.

---

**Project:** Habit Tracker – DevOps CI/CD & GitOps Implementation  
**Repository:** https://github.com/ManasiAanand/HabitApp

