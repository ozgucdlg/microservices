# Product Service

This service is part of the microservices architecture, responsible for managing product information and inventory.

## Technology Stack

- Java 17
- Spring Boot 3.0.6
- MongoDB
- Docker
- Maven

## Project Structure

```
product-service/
├── docker/                     # Docker related files
│   ├── Dockerfile             # Multi-stage Dockerfile for building and running the service
│   └── docker-compose.yml     # Docker compose for local development
├── src/
│   ├── main/
│   │   ├── java/             # Java source files
│   │   └── resources/        # Application properties and resources
│   └── test/                 # Test files
├── target/                    # Compiled files (gitignored)
├── pom.xml                    # Maven dependencies and build configuration
└── README.md                 # This file
```

## Prerequisites

- Java 17 or higher
- Maven 3.8+
- Docker and Docker Compose
- MongoDB (if running locally)

## Running Locally

### Without Docker

1. Ensure MongoDB is running locally on port 27017
2. Run the application:
   ```bash
   mvn spring-boot:run
   ```

### With Docker

1. Navigate to the docker directory:
   ```bash
   cd docker
   ```

2. Build and run the containers:
   ```bash
   docker-compose up --build
   ```

The service will be available at http://localhost:8080

## API Endpoints

- `GET /api/products` - List all products
- `GET /api/products/{id}` - Get a specific product
- `POST /api/products` - Create a new product
- `PUT /api/products/{id}` - Update a product
- `DELETE /api/products/{id}` - Delete a product

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| SPRING_DATA_MONGODB_HOST | MongoDB host | localhost |
| SPRING_DATA_MONGODB_PORT | MongoDB port | 27017 |
| SPRING_DATA_MONGODB_DATABASE | MongoDB database name | product-service |
| SERVER_PORT | Application port | 8080 |

## Health Check

The service includes Spring Boot Actuator for health monitoring:
- Health check endpoint: http://localhost:8080/actuator/health

## Docker Support

The service includes a multi-stage Dockerfile and docker-compose configuration for easy deployment:

- Multi-stage build for optimized image size
- Non-root user for security
- Health checks for both MongoDB and the service
- Volume mounts for data persistence
- Environment variable configuration
- Network isolation

