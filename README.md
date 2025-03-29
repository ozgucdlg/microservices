# Microservices E-Commerce Application

## Overview
This project implements a microservices-based e-commerce application using Spring Boot. The application consists of three main services that work together to provide a complete e-commerce solution.

## Services Architecture

### Product Service (Port: 8080)
- Manages product information and catalog
- Built with Spring Boot and MongoDB
- Handles product creation and retrieval operations
- Database: MongoDB (Port: 27017)

### Inventory Service (Port: 8083)
- Manages product inventory and stock levels
- Built with Spring Boot and PostgreSQL
- Handles inventory checks and updates
- Database: PostgreSQL (Port: 5432)

### Order Service (Port: 8082)
- Manages customer orders and order processing
- Built with Spring Boot and PostgreSQL
- Communicates with Product and Inventory services
- Database: PostgreSQL (Port: 5432)

## Technical Stack

### Backend Technologies
- Java 17
- Spring Boot 3.0.6
- Spring Data JPA/MongoDB
- Maven (Build Tool)
- RESTful APIs

### Databases
- MongoDB (Product Service)
- PostgreSQL (Inventory and Order Services)

### Additional Tools
- Lombok
- Spring Web
- Spring Boot DevTools
- Spring Boot Actuator

## Getting Started

### Prerequisites
- Java 17 or higher
- Maven 3.x
- MongoDB
- PostgreSQL

### Installation and Setup

1. Clone the repository:
   ```bash
   git clone [repository-url]
   cd microservices-new
   ```

2. Configure Databases:
   - Ensure MongoDB is running on port 27017
   - Ensure PostgreSQL is running on port 5432
   - Create databases:
     - `product-service` (MongoDB)
     - `inventoryService` (PostgreSQL)
     - `orderService` (PostgreSQL)

3. Build the project:
   ```bash
   mvn clean install
   ```

4. Start the services:
   ```bash
   # Start Product Service
   cd product-service
   mvn spring-boot:run

   # Start Inventory Service
   cd ../inventory-service
   mvn spring-boot:run

   # Start Order Service
   cd ../order-servive
   mvn spring-boot:run
   ```

## Service Endpoints

### Product Service
- Base URL: `http://localhost:8080`
- Available endpoints:
  - Product operations (GET, POST, etc.)

### Inventory Service
- Base URL: `http://localhost:8083`
- Available endpoints:
  - Inventory operations (GET, POST, etc.)

### Order Service
- Base URL: `http://localhost:8082`
- Available endpoints:
  - Order operations (GET, POST, etc.)

## Configuration

Each service has its own `application.properties` file with specific configurations:
- Database connections
- Server ports
- Application-specific properties

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
