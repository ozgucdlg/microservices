# Stage 1: Build the application
FROM maven:3.8.4-openjdk-17-slim AS builder

# Set working directory
WORKDIR /build

# Copy the parent POM
COPY pom.xml .

# Copy the project files
COPY product-service/pom.xml product-service/
COPY product-service/src product-service/src

# Build the application
RUN mvn clean package -DskipTests -f product-service/pom.xml

# Stage 2: Create the runtime image
FROM openjdk:17-slim

# Set working directory
WORKDIR /app

# Add maintainer info
LABEL maintainer="ozgucdalga@gmail.com"

# Add metadata labels
LABEL version="1.0.0" \
      description="Product Service for Microservices Architecture" \
      project="microservices-demo"

# Create a non-root user
RUN useradd -m -s /bin/bash -u 1001 appuser

# Copy the built artifact from builder stage
COPY --from=builder /build/product-service/target/*.jar app.jar

# Set ownership to non-root user
RUN chown -R appuser:appuser /app

# Use non-root user
USER appuser

# Expose the application port
EXPOSE 8080

# Set the startup command
ENTRYPOINT ["java", "-jar", "app.jar"] 