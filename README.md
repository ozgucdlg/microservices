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

3. **Inventory Service** (Port: 8083)
   - Manages product inventory
   - PostgreSQL database for inventory tracking
   - Real-time stock management

4. **Order Service** (Port: 8082)
   - Handles order processing
   - PostgreSQL database for order management
   - Communicates with Product and Inventory services

5. **Eureka Server** (Port: 8761)
   - Service discovery and registration
   - Enables service-to-service communication

## Prerequisites

- Java 17
- Maven
- PostgreSQL
- MongoDB
- Docker (optional)

## Database Configuration

### PostgreSQL Databases:
- security_service
- inventory_service
- order_service

Configuration:
```properties
username=postgres
password=password
```

### MongoDB:
- Database: product_service
- Default port: 27017

## Getting Started

1. Start the databases:
   - PostgreSQL
   - MongoDB

2. Start the services in order:
   ```bash
   # 1. Start Eureka Server
   cd eureka-server
   mvn spring-boot:run

   # 2. Start Security Service
   cd security-service
   mvn spring-boot:run

   # 3. Start Product Service
   cd product-service
   mvn spring-boot:run

   # 4. Start Inventory Service
   cd inventory-service
   mvn spring-boot:run

   # 5. Start Order Service
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

- All services register with Eureka Server
- Order Service depends on Product and Inventory Services
- All services except Eureka Server require Security Service for authentication

## Monitoring and Management

- Each service exposes actuator endpoints for monitoring
- Services register with Eureka for service discovery
- Load balancing is handled by Spring Cloud LoadBalancer

## Development Notes

- Services use Spring Boot 3.0.6
- Spring Cloud for service discovery and configuration
- RESTful APIs with proper error handling
- Transaction management for data consistency
- Reactive programming with WebFlux where applicable
