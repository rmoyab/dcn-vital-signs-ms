# Vital Signs Service

A Spring Boot microservice for ingesting, managing, and distributing patient vital signs. Vital signs are persisted in an Oracle database, and the service integrates with Kafka and RabbitMQ for messaging.

## Features

- Produces patient vital signs data to Kafka (`vital_signs` topic)
- Sends summary reports to RabbitMQ (`vitalSignsSummaryQueue`)
- Stores vital signs records in Oracle DB
- Simulates vital signs data at scheduled intervals
- REST API to manage and retrieve vital signs

## Stack

- Java 23
- Maven
- Docker
- Oracle Database (with wallet for secure connection)
- Kafka
- RabbitMQ
- Spring Boot 3
- Lombok

## API Endpoints

- `POST /api/vital-signs` Create new vital signs for a patient.

- `GET /api/vital-signs/{id}` Retrieve vital signs by ID.

- `GET /api/vital-signs/patient/{patientId}` Retrieve all vital signs for a patient.

- `PUT /api/vital-signs/{id}` Update vital signs by ID.

- `DELETE /api/vital-signs/{id}` Delete vital signs by ID.

## Project Structure

```text
src/
├── config
│   └── Config.java
├── controller
│   └── VitalSignsController.java
├── init
│   └── DataInitializer.java
├── model
│   ├── VitalSigns.java
│   ├── VitalSignsMessage.java
│   └── Patient.java
├── repository
│   └── VitalSignsRepository.java
├── service
│   ├── VitalSignsProducer.java
│   ├── VitalSignsService.java
│   ├── VitalSignsServiceImpl.java
│   ├── VitalSignsSimulator.java
│   └── VitalSignsSummaryProducer.java
├── utils
│   └── Utils.java
└── App.java
```

## Best Practices

- **Layered Architecture:** Clear separation of concerns between controller, service, repository, and configuration layers.
- **Dependency Injection:** Uses Spring's constructor injection for loose coupling and easier testing.
- **Configuration Management:** Sensitive data and environment-specific settings are externalized using `application.yml` and environment variables.
- **Exception Handling:** Centralized exception handling for REST endpoints.
- **Logging:** Uses SLF4J for consistent and configurable logging.
- **DTOs and Models:** Distinct model classes for data transfer and persistence.
- **Unit and Integration Testing:** Testable service and repository layers.
- **Externalized Secrets:** Database credentials and sensitive information are not hardcoded.
- **Containerization:** Docker support for consistent deployment environments.
- **Code Quality:** Follows Java naming conventions and code organization for readability and maintainability.
