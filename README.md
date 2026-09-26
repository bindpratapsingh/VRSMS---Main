# VRSMS — Video Rental Store Management System

VRSMS is a Java 17 and Spring Boot backend for managing the operations of a video rental store. It provides a layered REST application for inventory, members, rentals, returns, staff and manager workflows, member history, wishlists, and notification support.

This repository also includes the project's software engineering documentation, covering requirements analysis, data flow, use cases, object-oriented design, and runtime interactions.

## Features

- Authentication and user access management
- Video and inventory management
- Rental and return processing
- Member rental history
- Wishlist management
- Staff operations
- Manager operations
- PostgreSQL-backed persistence
- Twilio integration for notification capabilities

## Technology stack

- **Language:** Java 17
- **Framework:** Spring Boot 4.0.4
- **Web/API:** Spring Web MVC
- **Persistence:** Spring Data JPA
- **Database:** PostgreSQL
- **Validation:** Spring Boot Validation
- **Notifications:** Twilio Java SDK
- **Testing/automation:** Selenium Java dependency
- **Build:** Maven
- **Deployment:** Docker

## Repository structure

```text
.
├── 1. SRS/                 # Software Requirements Specification
├── 2. DFD/                 # Data Flow Diagrams and data dictionary
├── 3. UC Diagram/          # Use case documentation and diagrams
├── 4. Class Diagram/       # Object-oriented class model
├── 5. Sequence Diagram/    # Interaction and runtime sequence diagrams
├── src/
│   ├── main/
│   │   ├── java/com/vrsms/server/
│   │   │   ├── controllers/    # REST API endpoints
│   │   │   ├── models/         # Domain entities and data models
│   │   │   ├── repositories/   # Spring Data JPA repositories
│   │   │   ├── services/       # Business logic
│   │   │   └── ServerApplication.java
│   │   └── resources/          # Application configuration
│   └── test/                   # Test sources
├── Dockerfile
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md
```

## Application architecture

The backend follows a layered architecture:

1. A client sends a request to a REST controller.
2. The controller validates input and delegates to a service.
3. The service applies business rules and coordinates the operation.
4. A repository reads or writes data through Spring Data JPA.
5. The response is returned to the client through the REST API.

This separation of concerns keeps API handling, business logic, persistence, and domain models independently maintainable.

## Software engineering documentation

The numbered documentation folders represent the project lifecycle from requirements to design and implementation.

### 1. Software Requirements Specification (SRS)

[`1. SRS/Group 23_VSRSMS_ SRS-v1.2.pdf`](<1.%20SRS/Group%2023_VSRSMS_%20SRS-v1.2.pdf>)

The SRS defines the system's purpose, scope, functional requirements, non-functional requirements, users, assumptions, constraints, and expected behavior. It establishes the baseline against which the design and implementation can be evaluated.

### 2. Data Flow Diagrams (DFD)

[`2. DFD/Group23_DFD.pdf`](<2.%20DFD/Group23_DFD.pdf>)  
[`2. DFD/Dictionary.pdf`](<2.%20DFD/Dictionary.pdf>)

The DFD documentation models how information moves through the system. It includes context and decomposed process views, data stores, external entities, process boundaries, and a data dictionary. The additional Level 0, Level 1, and Level 2 diagrams provide progressively more detailed views of system processing.

### 3. Use Case (UC) Diagrams

[`3. UC Diagram/Group23_UCdocument.pdf`](<3.%20UC%20Diagram/Group23_UCdocument.pdf>)  
[`3. UC Diagram/Group23_Use-Case.drawio.pdf`](<3.%20UC%20Diagram/Group23_Use-Case.drawio.pdf>)

The use case documentation describes how actors interact with the system. It provides a user-centered view of capabilities such as authentication, inventory operations, rentals, returns, member history, wishlists, and staff or manager activities.

### 4. Class Diagram

[`4. Class Diagram/Group23 class diagram.pdf`](<4.%20Class%20Diagram/Group23%20class%20diagram.pdf>)

The class diagram presents the static, object-oriented structure of the application. It documents domain classes, relationships, responsibilities, and associations that correspond to the Java model and service design.

### 5. Sequence Diagrams

[`5. Sequence Diagram/Group 23_SequenceDiagram.pdf`](<5.%20Sequence%20Diagram/Group%2023_SequenceDiagram.pdf>)

The sequence diagrams describe the order of interactions between actors and system components during key workflows. They help connect use cases to implementation by showing how controllers, services, repositories, and external integrations collaborate at runtime.

## Software engineering techniques used

### Requirement-driven development

The SRS is used to define the system before implementation. This supports traceability from business needs to features, design decisions, and code.

### Structured system modeling

DFDs provide multiple levels of process decomposition, making data movement and system boundaries easier to analyze and communicate.

### Use case analysis

Use cases identify system actors, goals, and interactions. They provide a practical basis for defining functional requirements and REST API behavior.

### Object-oriented design

The class diagram models the domain using classes, attributes, responsibilities, and relationships. This supports encapsulation, abstraction, and maintainable Java code.

### Behavioral modeling

Sequence diagrams model time-ordered interactions and clarify which component is responsible for each step of a workflow.

### Separation of concerns

Controllers, services, repositories, and models have distinct responsibilities. This reduces coupling and makes the system easier to test and extend.

### Dependency injection and inversion of control

Spring manages application components and their dependencies, allowing classes to depend on abstractions and improving modularity and testability.

### Persistence abstraction

Spring Data JPA provides repository-based data access, reducing database boilerplate and keeping persistence concerns separate from business logic.

### Validation and business rules

Spring validation support and service-layer processing help protect data integrity and enforce rules around members, inventory availability, rentals, and returns.

### Containerized deployment

The included `Dockerfile` provides a repeatable way to package and run the Spring Boot service across development, testing, and deployment environments.

## Getting started

### Prerequisites

- Java 17 or later
- PostgreSQL
- Maven, or use the included Maven Wrapper
- Docker (optional)

### Clone the repository

```bash
git clone https://github.com/bindpratapsingh/VRSMS---Main.git
cd VRSMS---Main
```

### Build the application

On Linux or macOS:

```bash
./mvnw clean package
```

On Windows:

```bat
mvnw.cmd clean package
```

### Run the application

```bash
./mvnw spring-boot:run
```

The packaged JAR can also be started with:

```bash
java -jar target/server-0.0.1-SNAPSHOT.jar
```

### Run tests

```bash
./mvnw test
```

### Run with Docker

```bash
docker build -t vrsms-server .
docker run -p 8080:8080 vrsms-server
```

## Database and configuration

The application includes the PostgreSQL JDBC driver and Spring Data JPA. Configure the datasource using Spring Boot application properties or environment-specific configuration.

Typical settings include:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/vrsms
spring.datasource.username=<database-user>
spring.datasource.password=<database-password>
```

If notification functionality is enabled, configure the required Twilio credentials securely through the application's expected configuration mechanism. Do not commit credentials or secrets to the repository.

## Project status

This repository contains the Spring Boot server implementation together with its supporting software engineering deliverables. API details, request models, and business rules should be verified against the controller, service, model, and repository classes under `src/main/java/com/vrsms/server/`.

## License

No license file is currently included. Add a `LICENSE` file before distributing the project under an open-source license.
