## Project Overview

**Name**: numeric (Spring Boot) — Kubernetes DevSecOps demo

**Purpose**: Simple Java Spring Boot service exposing endpoints for numeric operations and demonstrating DevSecOps practices across CI (Jenkins), containerization (Docker), security scanning, and Kubernetes deployment.

### Key Components
- Spring Boot REST API in `src/main/java/com/devsecops/`:
  - `/` returns a welcome message.
  - `/compare/{value}` compares an integer to 50.
  - `/increment/{value}` proxies to an external Node service `http://node-service:5000/plusone`.
- Build tooling: Maven (`pom.xml`) with Spring Boot, JaCoCo, Sonar, and PITest plugins.
- Containerization: `Dockerfile` runs the built JAR as non-root with a healthcheck.
- CI: `Jenkinsfile` builds and archives the artifact.
- Kubernetes:
  - `k8s_deployment_service.yaml` for deploying the app as a Deployment and Service.
  - `kube-scan.yaml` to deploy a cluster risk scanning tool (kube-scan) and config.
  - `kubesec-scan.sh` script to scan K8s manifests with Kubesec.

### Notable Behavior
- The `/increment/{value}` endpoint requires the Node service (`node-service:5000/plusone`) to be reachable; otherwise the call will fail. For local development without Kubernetes, this dependency is not available unless you run a compatible Node service locally and adjust `random.service.url`.
- Default app port is 8080 (`application.properties`).


