# WebLogic-on-Kubernetes Modernization Project

## Executive Summary
This project demonstrates the end-to-end containerization and modernization of a Java application. It transitions a legacy WebLogic-based middleware stack to a cloud-native Kubernetes environment, utilizing the **Oracle WebLogic Kubernetes Operator** for automated lifecycle management and **WebLogic Deploy Tooling (WDT)** for declarative configuration.

## Technical Architecture
* **Orchestration:** Kubernetes (Minikube)
* **Middleware Lifecycle:** Oracle WebLogic Kubernetes Operator
* **Infrastructure-as-Code:** WDT (WebLogic Deploy Tooling) & Auxiliary Image pattern
* **CI/CD Pipeline:** Jenkins (Kubernetes-native agent pods)
* **Observability:** Prometheus & Grafana (via WLS-Exporter & PodMonitor)
* **Traffic Management:** NGINX Ingress Controller (Session Affinity enabled)

## Key Technical Achievements
* **Automated Lifecycle Management:** Implemented an Auxiliary Image pattern to decouple WebLogic binaries from application models/binaries.
* **Declarative Infrastructure:** Leveraged WDT and Kubernetes Operators to eliminate manual configuration and reduce configuration drift.
* **CI/CD Pipeline Integration:** Developed a dynamic Jenkins pipeline that executes automated image builds and triggers rolling updates of the WebLogic domain.
* **Observability Stack:** Configured a sidecar-free monitoring approach using the `wls-exporter` and Kubernetes `PodMonitor` for real-time metrics.

## Project Structure
* `domain.yaml`: Primary Domain resource definition for the WebLogic Operator.
* `bank-cluster.yaml`: Cluster configuration including readiness and liveness probes.
* `Jenkinsfile`: Pipeline for automated build and deployment cycles.
* `bank-aux-image/`: Dockerfile for custom auxiliary image creation and WDT dependency injection.
* `ingress.yaml`: Network ingress configuration enforcing sticky sessions for stateful session replication.
* `mysql.yaml`: Database deployment configuration for the application backend.
* `secrets.yaml`: Kubernetes secrets management for DB credentials and WebLogic domain access.
* `configmap.yaml`: Externalized configuration properties for datasource management.
* `pod-monitor.yaml`: Observability integration for Prometheus/Grafana monitoring.
