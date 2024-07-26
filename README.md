# Soccer Data Publisher

## Description

A microservices-based Java Spring Boot application to fetch and publish soccer tournament data. Integrates with API-Football for data, and publishes updates to Twitter and WhatsApp using Twilio and Twitter APIs. Utilizes Spring Cloud Gateway, Netflix Eureka, Spring Cloud Config, GraphQL, Docker, Kubernetes, and Prometheus for scalability and maintainability.

## High-Level Design

### Overview

The project aims to develop a Java Spring Boot application that fetches football (soccer) tournament data from the API-Football service and publishes this data to Twitter and WhatsApp. The application is designed using microservices architecture to ensure scalability, maintainability, and flexibility.

### High-Level Architecture Diagram

```plaintext
                            +-------------------------+
                            |      API Gateway        |
                            +------------+------------+
                                         |
                                         v
                           +-------------+-------------+
                           |       Service Discovery   |
                           +-------------+-------------+
                                         |
                                         v
                         +---------------+---------------+
                         | Configuration Management     |
                         +---------------+---------------+
                                         |
                                         v
              +-----------+----------------------------+------------+
              |           |                            |            |
              v           v                            v            v
      +-----------+ +-----------+               +------------+ +------------+
      | Data      | | Data      |               |  Twitter   | | WhatsApp   |
      | Fetching  | | Processing|               | Publishing | | Publishing |
      | Service   | | Service   |               | Service    | | Service    |
      +-----------+ +-----------+               +------------+ +------------+
              |
              v
      +-------------+
      |   Database  |
      +-------------+
              |
              v
      +-------------+
      | GraphQL     |
      | Service     |
      +-------------+
              |
              v
      +-------------+
      | Notification|
      | Service     |
      +-------------+
              |
              v
      +-------------+
      | Caching     |
      +-------------+
              |
              v
      +-------------+
      | Logging and |
      | Monitoring  |
      +-------------+
              |
              v
      +-------------+
      | Message     |
      | Broker      |
      +-------------+
              |
              v
      +-------------+
      | Service Mesh|
      +-------------+
              |
              v
      +-------------+
      | Container-  |
      | ization and |
      | Orchestration|
      +-------------+
              |
              v
      +-------------+
      | CI/CD       |
      | Pipeline    |
      +-------------+
```

### Key Components
- API Gateway: Routes incoming requests to appropriate microservices, handles security and authentication.
- Service Discovery: Manages the registration and discovery of microservices.
- Configuration Management: Centralized management of application configurations.
- Data Fetching Service: Periodically fetches football data from the API-Football service.
- Data Processing Service: Processes and filters the fetched data, preparing it for storage and publication.
- Database: Stores processed data.
- GraphQL Service: Provides a flexible and efficient data querying interface.
- Twitter Publishing Service: Publishes processed data to Twitter.
- WhatsApp Publishing Service: Sends processed data to WhatsApp.
- Notification Service: Sends notifications for failures or important events.
- Logging and Monitoring: Centralized logging and monitoring of the application.
- Caching: Improves performance and reduces load on external APIs.
- Containerization and Orchestration: Manages deployment and scaling of microservices.
- Service Mesh: Manages microservices traffic and provides additional security and monitoring.
- Message Broker: Handles inter-service communication and event-driven architecture.
- CI/CD Pipeline: Automates testing, building, and deployment.

### Folder Structure

```plaintext
/football-data-publisher
|-- /api-gateway
|-- /service-discovery
|-- /config-server
|-- /data-fetching-service
|-- /data-processing-service
|-- /database-service
|-- /graphql-service
|-- /twitter-publishing-service
|-- /whatsapp-publishing-service
|-- /notification-service
|-- /logging-and-monitoring
|-- /caching-service
|-- /message-broker-service
|-- /ci-cd-pipeline
|-- /service-mesh
|-- /docker
|-- /kubernetes
|-- README.md
|-- docker-compose.yml
|-- .gitignore
```

### Individual Microservice Folder Structure
Each microservice will follow a similar structure. Here is an example for the data-fetching-service:

```plaintext
/data-fetching-service
|-- /src
|   |-- /main
|   |   |-- /java
|   |   |   |-- /com/example/datafetching
|   |   |       |-- DataFetchingServiceApplication.java
|   |   |       |-- /controller
|   |   |       |   |-- DataFetchingController.java
|   |   |       |-- /service
|   |   |       |   |-- DataFetchingService.java
|   |   |       |-- /model
|   |   |       |   |-- TournamentData.java
|   |   |       |-- /repository
|   |   |           |-- TournamentDataRepository.java
|   |   |-- /resources
|   |       |-- application.yml
|   |       |-- logback-spring.xml
|   |-- /test
|       |-- /java
|       |   |-- /com/example/datafetching
|       |       |-- DataFetchingServiceApplicationTests.java
|       |       |-- /controller
|       |       |   |-- DataFetchingControllerTests.java
|       |       |-- /service
|       |           |-- DataFetchingServiceTests.java
|-- Dockerfile
|-- pom.xml
```

### Tech Stack
- Java Spring Boot
- Spring Cloud Gateway
- Netflix Eureka
- Spring Cloud Config
- Spring Boot with WebClient
- Spring Boot with Jackson
- H2 Database (for development)
- PostgreSQL (for production)
- Spring Boot with GraphQL (GraphQL Spring Boot Starter)
- Twitter4J, Twitter API
- Twilio API
- Spring Cloud Stream
- SLF4J with Logback
- Spring Boot Actuator
- Prometheus and Grafana
- Spring Cache
- Redis
- Docker
- Kubernetes
- Istio
- Apache Kafka
- RabbitMQ
- Swagger/OpenAPI
- GraphiQL
- Spring Boot Micrometer
- Jaeger
- GitHub Actions
- Jenkins


