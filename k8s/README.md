# <div align="center">

# 🚀 Urban Assist Kubernetes Configuration

[![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.25+-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Ingress Nginx](https://img.shields.io/badge/Ingress-Nginx-009639?logo=nginx&logoColor=white)](https://kubernetes.github.io/ingress-nginx/)
[![Docker](https://img.shields.io/badge/Docker-20.10+-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

*Enterprise-grade Kubernetes configurations for the Urban Assist microservices platform*

[Overview](#-overview) •
[Architecture](#-architecture) •
[Services](#-services) •
[Database](#-database) •
[Installation](#-installation) •
[Configuration](#-configuration)

</div>

---

## 📚 Overview

This repository contains the complete Kubernetes configuration for deploying and managing the Urban Assist microservices platform. It includes configurations for service deployments, database management, load balancing, and service mesh integration.

### Key Features

- **Centralized Database Management** with MySQL containerization
- **Advanced Load Balancing** using Nginx Ingress Controller
- **Service Mesh Architecture** with microservices integration
- **Secure Configuration Management** using Secrets and ConfigMaps
- **Persistent Storage** with dynamic provisioning
- **High Availability** setup for critical services

---

## 🏗 Architecture

### Infrastructure Components

| Component | Purpose | Configuration |
|-----------|---------|---------------|
| **MySQL Database** | Central data store | Containerized with persistent storage |
| **Nginx Ingress** | Load balancing & routing | Path-based routing with CORS support |
| **Service Mesh** | Inter-service communication | Internal DNS resolution |
| **Storage** | Persistent data | Dynamic provisioning with StorageClass |

### Microservices

- User Authentication Service (Port: 8081)
- User Management Service (Port: 8083)
- Email Service (Port: 8084)
- Payment Service (Port: 8085)
- Admin Service (Port: 8086)
- Reviews Service (Port: 8089)
- Frontend Service (Port: 80)

---

## 💾 Database Configuration

### MySQL Deployment Highlights

```yaml
# Key Features
- Image: MySQL 8.0
- Persistent Storage: Dynamic provisioning
- Port: 3306 (internal)
- Service Port: 5151 (cluster access)
- Initial Databases: auth, user_management, reviews, admin, payments
```

### Database Security

- Secrets management for credentials
- Isolated storage class
- ConfigMap for initialization scripts
- Resource limits and requests

### High Availability Features

- Persistent Volume Claims
- Storage Class configuration
- Data persistence across pod restarts
- Initialization scripts for database setup

---

## 🔀 Ingress Configuration

### Load Balancing Features

- Path-based routing
- CORS support
- SSL configuration
- Health check integration
- Timeout configurations

### Service Routes

```yaml
Frontend: /
Auth API: /auth-api
Email Service: /mail
User Management: /api
Payments: /payments
Admin: /admin
Reviews: /reviews
```

---

## 🚀 Installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd k8s-config
   ```

2. **Create namespaces:**
   ```bash
   kubectl create namespace urban-assist
   ```

3. **Deploy infrastructure components:**
   ```bash
   # Deploy MySQL
   kubectl apply -f database/

   # Deploy RabbitMQ
   kubectl apply -f rabbitmq/

   # Deploy Ingress Controller
   kubectl apply -f api-gateway/
   ```

4. **Deploy microservices:**
   ```bash
   kubectl apply -f user-auth/
   kubectl apply -f usermanagement/
   kubectl apply -f payment/
   kubectl apply -f email/
   kubectl apply -f admin/
   kubectl apply -f reviews/
   kubectl apply -f frontend/
   ```

---

## ⚙️ Configuration

### Environment Variables

Managed through Kubernetes Secrets and ConfigMaps:

- Database credentials
- API keys
- Service endpoints
- Application configurations

### Resource Management

```yaml
# Example resource limits
resources:
  limits:
    cpu: "500m"
    memory: "512Mi"
  requests:
    cpu: "200m"
    memory: "256Mi"
```

---

## 🔍 Monitoring

### Health Checks

- Readiness probes
- Liveness probes
- Startup probes

### Logging

- Container logs
- System metrics
- Performance monitoring

---

## 🛡 Security

### Features

- JWT Authentication
- Secure communication
- CORS policies
- Network policies
- Secret management

---

## 🔧 Maintenance

### Scaling

```bash
# Scale a deployment
kubectl scale deployment <deployment-name> --replicas=3
```

### Updates

```bash
# Update image
kubectl set image deployment/<deployment-name> container=new-image:tag
```

---

## 📝 Contributing

1. Fork the repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

---

<div align="center">

**Urban Assist Platform** • Built with ❤️ by the Urban Assist Team

</div>
