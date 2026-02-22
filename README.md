# 🚀 Hiring Application – Production-Grade Microservices Platform

A scalable, resilient, and production-ready **Hiring Platform** built using Spring Boot Microservices architecture.

This project demonstrates real-world distributed system design including:

- Microservices Architecture
- Event-Driven Communication
- Circuit Breaker & Retry Mechanisms
- Outbox Pattern for Reliable Messaging
- Distributed Caching with Redis
- Observability & Monitoring
- CI/CD Automation
- Containerized Deployment

---

# 📌 Table of Contents

- Overview
- Architecture
- Services
- Engineering Features
- Technology Stack
- Security
- Event-Driven Design
- Caching Strategy
- Monitoring & Observability
- CI/CD Pipeline
- API Documentation
- How to Run
- Scalability Approach
- Testing Strategy
- Future Improvements

---

# 🏗 Overview

The Hiring Application is a distributed backend system that allows:

- User registration and authentication
- Job category management
- Job creation and search
- Advert posting
- Offer submission
- Notification handling
- File upload and download

The system follows modern backend engineering standards suitable for large-scale applications.

---

# 🏛 Architecture

Client  
→ API Gateway  
→ Microservices  
→ PostgreSQL  
→ Kafka  
→ Redis  
→ Monitoring Stack  

## Core Components

- Config Server – Centralized configuration management
- Eureka Server – Service discovery
- API Gateway – Routing & request filtering
- Auth Service – JWT authentication & authorization
- User Service – User management
- Job Service – Categories, Jobs, Adverts, Offers
- Notification Service – Event-driven notifications
- File Storage Service – File handling
- Redis – Caching layer
- Kafka – Asynchronous messaging
- Prometheus – Metrics collection
- Grafana – Monitoring dashboards

---

# 🔥 Engineering Features

## 1️⃣ Circuit Breaker & Retry

- Prevents cascading failures
- Provides fallback mechanisms
- Configurable retry strategy
- Applied to inter-service communication

Improves system reliability and fault tolerance.

---

## 2️⃣ Outbox Pattern

Solves the dual-write problem in distributed systems.

Implementation:

- Domain entity + event saved in same DB transaction
- Event stored in `outbox` table
- Background scheduler publishes event to Kafka
- Event marked as processed after successful publish

Ensures:
- No message loss
- Eventual consistency
- Reliable event delivery

---

## 3️⃣ Event-Driven Architecture

Kafka events published for:

- Advert Created
- Offer Created
- Job Updated

Notification Service consumes events asynchronously.

Benefits:

- Loose coupling
- Scalability
- Failure isolation
- Improved responsiveness

---

## 4️⃣ Redis Caching Strategy

Implements Cache-Aside Pattern.

Cached Endpoints:

- Get all jobs
- Get categories
- Job search queries

Features:

- TTL-based eviction
- Cache invalidation on updates
- Reduced DB load
- Faster read operations

---

## 5️⃣ Monitoring & Observability

Integrated with:

- Spring Boot Actuator
- Prometheus
- Grafana

Monitored Metrics:

- Request count
- Error rate
- Latency
- JVM memory usage
- Service health

Provides production-level visibility into system behavior.

---

## 6️⃣ CI/CD Pipeline

Automated using GitHub Actions.

Pipeline Steps:

1. Checkout code
2. Build project
3. Run unit tests
4. Build Docker image
5. Push to Docker registry

Triggers on:
- Pull Requests
- Push to main branch

---

# 🛠 Technology Stack

## Backend
- Java 17
- Spring Boot
- Spring Security
- JWT
- Spring Cloud Gateway
- Spring Cloud Config
- Eureka
- Spring Data JPA

## Database
- PostgreSQL

## Messaging
- Kafka

## Caching
- Redis

## Resilience
- Resilience4j

## Monitoring
- Prometheus
- Grafana

## DevOps
- Docker
- Docker Compose
- GitHub Actions

---

# 🔐 Security

- JWT-based authentication
- Role-based access control (ADMIN / USER)
- Method-level authorization
- Gateway-level request filtering
- Secure endpoint protection

---

# 📡 API Overview

## Authentication

POST `/v1/auth/register`  
POST `/v1/auth/login`

## User

GET `/v1/user/getAll`  
GET `/v1/user/getUserById/{id}`  
PUT `/v1/user/update`  
DELETE `/v1/user/deleteUserById/{id}`  

## Job Service

### Category
POST `/v1/job-service/category/create`  
GET `/v1/job-service/category/getAll`  
PUT `/v1/job-service/category/update`  
DELETE `/v1/job-service/category/deleteCategoryById/{id}`  

### Job
POST `/v1/job-service/job/create`  
GET `/v1/job-service/job/getAll`  
PUT `/v1/job-service/job/update`  
DELETE `/v1/job-service/job/deleteJobById/{id}`  

### Advert
POST `/v1/job-service/advert/create`  
GET `/v1/job-service/advert/getAll`  
PUT `/v1/job-service/advert/update`  
DELETE `/v1/job-service/advert/deleteAdvertById/{id}`  

### Offer
POST `/v1/job-service/offer/makeAnOffer`  
GET `/v1/job-service/offer/getOfferById/{id}`  
PUT `/v1/job-service/offer/update`  
DELETE `/v1/job-service/offer/deleteOfferById/{id}`  

## Notification

GET `/v1/notification/getAllByUserId/{id}`  

## File Storage

GET `/v1/file-storage/download/{id}`  

---

# 🐳 How to Run

## 1️⃣ Clone Repository








This starts:

- PostgreSQL
- Kafka
- Redis
- Prometheus
- Grafana

## 3️⃣ Start Services (Order)

1. Config Server  
2. Eureka Server  
3. API Gateway  
4. Auth Service  
5. User Service  
6. Job Service  
7. Notification Service  
8. File Storage Service  

---

# 📊 Access URLs

Prometheus  
http://localhost:9090  

Grafana  
http://localhost:3000  

Swagger UI  
http://localhost:8080/v1/{service-name}/swagger-ui/index.html  

---

# 📈 Scalability Strategy

- Stateless service design
- Horizontal scaling via containers
- Distributed caching
- Asynchronous communication
- Failure isolation with circuit breaker
- Eventual consistency model

---

# 🧪 Testing Strategy

- Unit Testing (Mockito)
- Integration Testing
- Kafka Event Testing
- Security Testing
- API Validation

---

# 🎯 Production-Level Capabilities

✔ Microservices Architecture  
✔ Reliable Messaging  
✔ Resilience Patterns  
✔ Distributed Caching  
✔ Monitoring & Metrics  
✔ CI/CD Automation  
✔ Secure Authentication  
✔ Containerized Deployment  

---

# 🔮 Future Improvements

- Kubernetes deployment
- Distributed tracing
- API rate limiting
- Elasticsearch integration
- Blue-Green deployment strategy

---

# 👨‍💻 Author

Developed to demonstrate advanced backend engineering and distributed system design principles.
