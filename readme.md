# <div align="center">

# 👨‍💼 Admin Management Microservice

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/username/urban-assist)
[![Node.js](https://img.shields.io/badge/Node.js-20-green.svg)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-4.21-lightgrey.svg)](https://expressjs.com/)
[![License](https://img.shields.io/badge/license-MIT-red.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

<img src="https://via.placeholder.com/200?text=Admin+Management" alt="Admin Management Service Logo" width="200"/>

*Administrative service management platform for Urban Assist*

[Getting Started](#-getting-started) •
[Installation](#-installation) •
[Configuration](#-configuration) •
[API](#-api-endpoints) •
[Docker](#-docker) •
[Kubernetes](#-kubernetes) •
[Contributing](#-contributing)

</div>

---

## 📚 Overview

This microservice handles administrative functions within the Urban Assist platform. Built with Node.js and Express, it provides robust integration with MySQL for data persistence and includes comprehensive service management capabilities.

<details>
<summary>✨ Key Features</summary>

- **Service Management** - Complete CRUD operations for platform services
- **JWT Authentication** - Secure endpoints with token-based authentication
- **Role-Based Authorization** - Granular access control for administrators
- **MySQL Integration** - Sequelize ORM with MySQL
- **Kubernetes Ready** - Containerized deployment with full K8s support
- **High Availability** - Support for horizontal scaling
- **Configuration Management** - Externalized configuration via ConfigMaps and Secrets

</details>

---

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have met the following requirements:

- **Node.js** (v20 or higher)
- **npm** (latest version)
- **Git** for version control
- **Docker** for containerization
- **Kubernetes** for orchestration
- **MySQL** database

### 📦 Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   ```

2. **Navigate to the admin service directory**:
   ```bash
   cd urban-assist/admin
   ```

3. **Install dependencies**:
   ```bash
   npm install
   ```

---

## ⚙️ Configuration

### Environment Variables

The service uses Kubernetes secrets and configmaps for configuration. Key variables:

```plaintext
PORT=8086
CORS_ORIGIN=*
JWT_SECRET=e7b03c0c0329ed5a8bbac042d38c6d93f7344516ac51203552476cf58f07b62c
DATABASE_NAME=admin
DATABASE_USER=root
DATABASE_PASSWORD=admindevelopers
DATABASE_HOST=mysql-service
```

---

## 🏃‍♂️ Running the Service

Choose your preferred deployment method:

| Command | Description |
|---------|-------------|
| `npm start` | Run in development mode with nodemon |
| `node src/index.js` | Run the application directly |

---

## 🐳 Docker

Build and run the service using Docker:

```bash
# Build the image
docker build -t handyshare/admin:latest .

# Run the container
docker run -p 8086:8086 handyshare/admin:latest
```

---

## ☸️ Kubernetes

Deploy the service to Kubernetes:

```bash
# Apply all configurations
kubectl apply -f k8s/

# Verify deployment
kubectl get deployments
kubectl get services
kubectl get pods
```

### Kubernetes Features

| Feature | Description | Impact |
|---------|-------------|--------|
| **Deployment Strategy** | Rolling update | Zero-downtime deployments |
| **Service Exposure** | Internal cluster communication | Secure service mesh integration |
| **Config Management** | ConfigMaps and Secrets | Secure and flexible configuration |
| **Resource Management** | CPU/Memory limits | Optimal resource utilization |

---

## 📡 API Endpoints

> **Authentication Note**: Include JWT token in Authorization header:
> ```
> Authorization: Bearer <your-jwt-token>
> ```

### Service Management
| Endpoint | Method | Description | Role Required |
|----------|--------|-------------|---------------|
| `/admin/addService` | POST | Create new service | admin |
| `/admin/getServices` | GET | List all services | admin, provider, user |

<details>
<summary>📋 Request/Response Examples</summary>

#### Create Service
```http
POST /admin/addService
Authorization: Bearer <your-jwt-token>
Content-Type: application/json

Request:
{
    "serviceName": "Plumbing",
    "description": "Professional plumbing services",
    "image": "plumbing.jpg"
}

Response:
{
    "statusCode": 201,
    "data": {
        "serviceName": "Plumbing",
        "description": "Professional plumbing services",
        "image": "plumbing.jpg"
    },
    "message": "Service Plumbing created successfully"
}
```

#### List Services
```http
GET /admin/getServices
Authorization: Bearer <your-jwt-token>

Response:
{
    "statusCode": 200,
    "data": [
        {
            "id": 1,
            "serviceName": "Plumbing",
            "description": "Professional plumbing services",
            "image": "plumbing.jpg"
        }
    ],
    "message": "Services fetched successfully"
}
```
</details>

---

## 🛠 Technologies

<div align="center">

[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)

</div>

---

## 🚢 Deployment Impact Features

| Feature | Description | Business Impact |
|---------|-------------|----------------|
| **JWT Authentication** | Secure endpoint access | Enhanced API security |
| **Role-Based Auth** | Granular access control | Improved security management |
| **Data Persistence** | Sequelize with MySQL | Reliable data storage |
| **API Documentation** | Clear endpoint documentation | Easier integration |
| **Environment Isolation** | Kubernetes namespace separation | Secure multi-environment setup |
| **Scalability** | Horizontal pod scaling | Handles increased load |

---

## 👥 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Urban Assist Platform** • Built with ❤️ by the Urban Assist Team

</div>