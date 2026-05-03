# Complete Banking Project

A full-stack microservices-based banking application built with Spring Boot, Spring Cloud, Angular, and MySQL. The system implements a distributed architecture with service discovery, API gateway, and multiple independent microservices.

## 📋 Project Overview

This project demonstrates a modern banking system with the following features:

- **Microservices Architecture** - Multiple independent services for scalability
- **Service Discovery** - Eureka Server for dynamic service registration
- **API Gateway** - Centralized entry point for all client requests
- **User Management** - User authentication and profile management
- **Account Management** - Create and manage bank accounts
- **Transaction Processing** - Handle financial transactions
- **Analytics** - Analytics and reporting services
- **Notifications** - Send notifications to users
- **Angular Frontend** - Modern, responsive UI for banking operations

## 🏗️ Project Structure

```
Complete-Banking_Project-main/
├── eureka-server/           # Service Discovery Server
├── api-gateway/             # API Gateway (Load Balancer)
├── user-service/            # User Management Service
├── account-service/         # Account Management Service
├── transaction-service/     # Transaction Processing Service
├── analytics-service/       # Analytics & Reporting Service
├── notification-service/    # Notification Service
└── Banking-frontend/        # Angular Frontend Application
```

## 🛠️ Technology Stack

### Backend
- **Java 18** - Programming Language
- **Spring Boot 3.2.5** - Framework
- **Spring Cloud 2023.0.1** - Microservices Framework
- **Spring Data JPA** - Database ORM
- **MySQL** - Database
- **Netflix Eureka** - Service Discovery
- **OpenFeign** - Inter-service Communication
- **JWT** - Authentication

### Frontend
- **Angular 21.2.0** - Framework
- **TypeScript** - Language
- **Bootstrap 5.3** - CSS Framework
- **RxJS** - Reactive Programming

### Build & Deployment
- **Maven** - Build Tool
- **npm** - Package Manager

## 📦 Prerequisites

Before running the project, ensure you have installed:

- **Java 18 or higher** - [Download](https://www.oracle.com/java/technologies/downloads/)
- **MySQL 8.0 or higher** - [Download](https://dev.mysql.com/downloads/mysql/)
- **Maven 3.8.0 or higher** - [Download](https://maven.apache.org/download.cgi)
- **Node.js 18+ & npm 11+** - [Download](https://nodejs.org/)
- **Git** - [Download](https://git-scm.com/)

## 🚀 Getting Started

### 1. Database Setup

Create a MySQL user and databases for the application:

```sql
-- Create user
CREATE USER 'root'@'localhost' IDENTIFIED BY 'Root@7979';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;

-- Databases will be auto-created by JPA (createDatabaseIfNotExist=true)
```

### 2. Clone the Repository

```bash
git clone <your-repository-url>
cd Complete-Banking_Project-main
```

### 3. Start Backend Services

#### Start Eureka Server (Service Discovery)

```bash
cd eureka-server
mvn clean install
mvn spring-boot:run
```

Access Eureka Dashboard at: `http://localhost:8761`

#### Start API Gateway

```bash
cd api-gateway
mvn clean install
mvn spring-boot:run
```

API Gateway runs on port: `8080`

#### Start Individual Services

In separate terminal windows, navigate to each service directory and run:

```bash
# User Service (Port 8081)
cd user-service
mvn clean install
mvn spring-boot:run

# Account Service (Port 8082)
cd account-service
mvn clean install
mvn spring-boot:run

# Transaction Service (Port 8083)
cd transaction-service
mvn clean install
mvn spring-boot:run

# Analytics Service (Port 8084)
cd analytics-service
mvn clean install
mvn spring-boot:run

# Notification Service (Port 8085)
cd notification-service
mvn clean install
mvn spring-boot:run
```

### 4. Start Frontend

```bash
cd Banking-frontend
npm install
npm start
```

Frontend runs on: `http://localhost:4200`

## 🔧 Service Details

| Service | Port | Purpose |
|---------|------|---------|
| Eureka Server | 8761 | Service Discovery & Registration |
| API Gateway | 8080 | Entry point for all requests |
| User Service | 8081 | User authentication & profiles |
| Account Service | 8082 | Bank account management |
| Transaction Service | 8083 | Transaction processing |
| Analytics Service | 8084 | Data analysis & reports |
| Notification Service | 8085 | User notifications |
| Frontend (Angular) | 4200 | Web UI |

## 📊 Database Configuration

Default database credentials (can be modified in `application.properties`):

```properties
Database: MySQL
Host: localhost:3306
Username: root
Password: Root@7979
```

Each service has its own database:
- `db_user` - User Service
- `db_account` - Account Service
- `db_transaction` - Transaction Service
- `db_analytics` - Analytics Service
- `db_notification` - Notification Service

## 🔐 Authentication

The system uses JWT (JSON Web Tokens) for authentication. Default secret key:

```
TmV3U2VjcmV0S2V5Rm9ySldUU2lnbmluZ1B1cnBvc2VzMTIzNDU2Nzg
```

⚠️ **Important**: Change this secret key in production!

## 📝 API Endpoints

All requests should go through the API Gateway at `http://localhost:8080`

Example endpoints:
- `POST /user-service/api/users/register` - Register new user
- `POST /user-service/api/users/login` - User login
- `POST /account-service/api/accounts` - Create account
- `GET /account-service/api/accounts` - Get accounts
- `POST /transaction-service/api/transactions` - Create transaction

*Refer to individual service documentation for complete API specifications.*

## 🔄 Service Communication

- **Synchronous**: Services use OpenFeign for REST-based communication
- **Service Discovery**: All services register with Eureka Server
- **Load Balancing**: API Gateway provides load balancing

## 📁 Key Configuration Files

- `application.properties` - Service-specific configuration
- `pom.xml` - Maven dependencies and build configuration
- `angular.json` - Angular build configuration
- `tsconfig.json` - TypeScript configuration

## 🧪 Testing

Run tests for each service:

```bash
cd <service-name>
mvn test
```

## 📦 Building for Production

### Build Backend Services

```bash
cd <service-name>
mvn clean package
```

JAR files will be generated in the `target/` directory.

### Build Frontend

```bash
cd Banking-frontend
npm run build
```

Production build will be in `dist/` directory.

## 🚨 Troubleshooting

### Services not registering with Eureka
- Ensure Eureka Server is running on `http://localhost:8761`
- Check network connectivity between services

### Database connection errors
- Verify MySQL is running
- Check database credentials in `application.properties`
- Ensure databases are created or auto-creation is enabled

### Port already in use
- Kill the process using the port or change the port in `application.properties`

### Frontend not connecting to backend
- Check if API Gateway is running on port 8080
- Verify CORS settings if frontend and backend are on different domains
- Check browser console for error messages

## 📚 Additional Resources

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Cloud Documentation](https://spring.io/projects/spring-cloud)
- [Angular Documentation](https://angular.io/docs)
- [MySQL Documentation](https://dev.mysql.com/doc/)

## 📄 License

This project is provided as-is for educational purposes.

## 👨‍💼 Author

Created by: Preetham

---

**Last Updated**: May 2026

For questions or issues, feel free to open an issue in the repository.
