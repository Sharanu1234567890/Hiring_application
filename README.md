Hiring Application – Spring Boot Microservices Architecture

A production-grade Spring Boot Microservices Hiring Platform built with modern backend engineering principles including resilience patterns, event-driven architecture, caching strategy, monitoring, and CI/CD automation.

This project demonstrates scalable, secure, and fault-tolerant distributed system design suitable for enterprise-level applications.

 Architecture Overview

The system follows a microservices architecture pattern with the following components:

Config Server – Centralized configuration management

Eureka Server – Service discovery

API Gateway – Routing, filtering, authentication

Auth Service – Authentication & JWT authorization

User Service – User management

Job Service – Categories, Jobs, Adverts, Offers

Notification Service – Event-driven notifications

File Storage Service – Image/file upload and download

Redis – Distributed caching

Kafka – Event streaming

Prometheus + Grafana – Monitoring & observability

Resilience4j – Circuit breaker & retry mechanism

Docker – Containerization

GitHub Actions – CI/CD pipeline

🏗 High-Level Architecture

Client → API Gateway → Microservices
↓
Eureka (Service Discovery)
Config Server (Centralized Config)
Kafka (Event Streaming)
Redis (Caching)
PostgreSQL (Database)
Prometheus (Metrics)
Grafana (Dashboards)

 Key Engineering Features
1️⃣ Circuit Breaker & Retry (Resilience4j)

Prevents cascading failures between services

Automatic fallback methods

Configurable retry with exponential backoff

Applied between:

Job Service → Notification Service

Gateway → Downstream services

2️⃣ Outbox Pattern (Reliable Event Publishing)

To solve the Dual Write Problem:

Domain data and event are saved in the same database transaction

Events are stored in an outbox table

Background scheduler publishes events to Kafka

Events marked as processed after successful publish

Ensures:

No lost messages

Exactly-once processing

Eventual consistency

3️⃣ Redis Caching Strategy

Implements Cache-Aside Pattern

Cached Endpoints:

Get all jobs

Get categories

Job search queries

Features:

TTL based eviction

@Cacheable and @CacheEvict

Cache invalidation on updates

Reduced DB load

Improved performance

4️⃣ Monitoring & Observability

Integrated with:

Spring Boot Actuator

Prometheus

Grafana

Monitored Metrics:

Request count

Error rate

Latency

JVM memory usage

Kafka metrics

Access dashboards through Grafana UI after Docker startup.

5️⃣ CI/CD Pipeline (GitHub Actions)

Automated pipeline includes:

Code checkout

Maven build

Unit tests execution

Docker image build

Push to Docker Hub

Runs on:

Pull requests

Push to main branch

🛠 Technology Stack
Backend

Java 17

Spring Boot

Spring Security

JWT Authentication

Spring Cloud Gateway

Spring Cloud Config

Eureka Service Discovery

Database

PostgreSQL

Spring Data JPA

Messaging

Kafka

Caching

Redis

Resilience

Resilience4j

Monitoring

Prometheus

Grafana

DevOps

Docker & Docker Compose

GitHub Actions

🔐 Authentication & Authorization

JWT-based authentication

Role-based access control (ADMIN / USER)

Method-level security

Secure endpoints through API Gateway

📡 Event-Driven Architecture

Events Published:

Advert Created

Offer Created

Job Updated

Notification Service consumes Kafka events asynchronously.

Benefits:

Loose coupling

Improved scalability

Better failure isolation

Eventual consistency

📂 REST API Endpoints
Authentication

POST /v1/auth/register
POST /v1/auth/login

User Management

GET /v1/user/getAll
GET /v1/user/getUserById/{id}
PUT /v1/user/update
DELETE /v1/user/deleteUserById/{id}

Job Service
Category

POST /v1/job-service/category/create
GET /v1/job-service/category/getAll
PUT /v1/job-service/category/update
DELETE /v1/job-service/category/deleteCategoryById/{id}

Job

POST /v1/job-service/job/create
GET /v1/job-service/job/getAll
PUT /v1/job-service/job/update
DELETE /v1/job-service/job/deleteJobById/{id}

Advert

POST /v1/job-service/advert/create
GET /v1/job-service/advert/getAll
PUT /v1/job-service/advert/update
DELETE /v1/job-service/advert/deleteAdvertById/{id}

Offer

POST /v1/job-service/offer/makeAnOffer
GET /v1/job-service/offer/getOfferById/{id}
PUT /v1/job-service/offer/update
DELETE /v1/job-service/offer/deleteOfferById/{id}

Notification

GET /v1/notification/getAllByUserId/{id}

File Storage

GET /v1/file-storage/download/{id}

🐳 Running the Application
1️⃣ Clone Repository
git clone https://github.com/your-username/hiring_application.git
cd hiring_application
2️⃣ Start Infrastructure
docker compose up

This starts:

PostgreSQL

Kafka

Redis

Prometheus

Grafana

3️⃣ Start Services

Run in order:

Config Server

Eureka Server

API Gateway

Auth Service

User Service

Job Service

Notification Service

File Storage

4️⃣ Swagger UI
http://localhost:8080/v1/{service-name}/swagger-ui/index.html
Monitoring Access

Prometheus:

http://localhost:9090

Grafana:

http://localhost:3000
 Engineering Highlights

✔ Microservices Architecture
✔ Circuit Breaker & Retry
✔ Event-Driven Design
✔ Outbox Pattern Implementation
✔ Redis Caching Strategy
✔ Observability & Metrics
✔ CI/CD Automation
✔ Dockerized Deployment
✔ Role-Based Security
✔ Distributed System Design Principles

📈 Scalability Strategy

Stateless services

Horizontal scaling via containers

Caching for read-heavy operations

Asynchronous communication via Kafka

Failure isolation using Circuit Breaker

Testing Strategy

Unit testing (Mockito)

Integration testing

Kafka event validation

Security testing

API testing via Swagger

 Future Enhancements

Kubernetes deployment

Distributed tracing (Zipkin)

API rate limiting

Advanced search with Elasticsearch

Blue-Green deployment strategy

👨‍💻 Author

Developed as a production-level backend system to demonstrate advanced microservices architecture, resilience patterns, and distributed system design principles.
