# Microservices Project

This project implements a microservices-based architecture using Spring Boot and various Spring Cloud components. The system consists of multiple services that work together to provide a complete e-commerce solution.

## Services Architecture

1. **Security Service** (Port: 8084)
   - Handles user authentication and authorization
   - JWT token-based security
   - PostgreSQL database for user management

2. **Product Service** (Port: 8080)
   - Manages product information
   - MongoDB database for product storage
   - RESTful APIs for product operations

3. **Inventory Service** (Port: 8085)
   - Manages product inventory
   - PostgreSQL database for inventory tracking
   - Real-time stock management

4. **Order Service** (Port: 8082)
   - Handles order processing
   - PostgreSQL database for order management
   - Communicates with Product and Inventory services

## Prerequisites

- Java 17
- Maven
- Docker and Docker Compose
- PostgreSQL (if running locally)
- MongoDB (if running locally)

## Database Configuration

### PostgreSQL Databases:
- security_service
- inventory_service
- order_service

Configuration:
```properties
username=postgres
password=postgres
```

### MongoDB:
- Database: product_service
- Default port: 27017

## Getting Started

### Using Docker (Recommended)

1. Build and start all services:
   ```bash
   docker-compose up --build
   ```

2. Access the services:
   - Security Service: http://localhost:8084
   - Product Service: http://localhost:8080
   - Inventory Service: http://localhost:8085
   - Order Service: http://localhost:8082

### Manual Setup

1. Start the databases:
   - PostgreSQL
   - MongoDB

2. Start the services in order:
   ```bash
   # 1. Start Security Service
   cd security-service
   mvn spring-boot:run

   # 2. Start Product Service
   cd product-service
   mvn spring-boot:run

   # 3. Start Inventory Service
   cd inventory-service
   mvn spring-boot:run

   # 4. Start Order Service
   cd order-service
   mvn spring-boot:run
   ```

## API Security

The services are secured using JWT authentication. To access protected endpoints:

1. Register a user:
   ```http
   POST http://localhost:8084/api/auth/register
   Content-Type: application/json

   {
     "username": "user",
     "password": "password",
     "email": "user@example.com"
   }
   ```

2. Login to get JWT token:
   ```http
   POST http://localhost:8084/api/auth/login
   Content-Type: application/json

   {
     "username": "user",
     "password": "password"
   }
   ```

3. Use the JWT token in subsequent requests:
   ```http
   Authorization: Bearer <your_jwt_token>
   ```

## Service Dependencies

- Order Service depends on Product and Inventory Services
- All services require Security Service for authentication

## Monitoring and Management

- Each service exposes actuator endpoints for monitoring
- Prometheus metrics available for all services
- Logging patterns configured for better traceability

## Development Notes

- Services use Spring Boot 3.0.6
- RESTful APIs with proper error handling
- Transaction management for data consistency
- Docker support for all services
- Multi-stage Docker builds for optimized images
