# VRSMS - Video Rental Store Management System

VRSMS is a Java-based Spring Boot backend for managing a video rental store. The project models the core operations of a rental business, including member management, inventory tracking, rentals, returns, staff workflows, and manager-level administration. It is designed as a modular backend service that can support a web or mobile frontend and is structured around REST APIs, JPA models, and service-oriented business logic.

## Project purpose

The system is built to automate the daily operations of a video rental store, including:

- Managing the movie/video inventory
- Handling customer/member records
- Processing rentals and returns
- Tracking overdue or late items
- Supporting staff and manager actions
- Maintaining member rental history and wishlist records
- Sending notifications such as SMS reminders through Twilio

This repository combines both implementation and engineering documentation, making it a useful example of a software project lifecycle from requirements to design to deployment.

## Technology stack

- Language: Java 17
- Framework: Spring Boot 4.0.4
- Architecture style: Layered web application with REST controllers, services, repositories, and JPA entities
- Persistence: Spring Data JPA with PostgreSQL
- API layer: Spring Web MVC
- Validation: Spring Boot Validation
- External integration: Twilio Java SDK
- Automation/testing support: Selenium Java
- Build tool: Maven
- Containerization: Docker

## Repository structure

```text
.
├── .mvn/
├── 1. SRS/
├── 2. DFD/
├── 3. UC Diagram/
├── 4. Class Diagram/
├── 5. Sequence Diagram/
├── src/
│   ├── main/
│   │   ├── java/com/vrsms/server/
│   │   │   ├── controllers/
│   │   │   ├── models/
│   │   │   ├── repositories/
│   │   │   ├── services/
│   │   │   ├── ServerApplication.java
│   │   └── resources/
│   └── test/
├── Dockerfile
├── pom.xml
├── mvnw
├── mvnw.cmd
├── .gitignore
├── .gitattributes
└── README.md
```

## Main application modules

The server implementation follows a conventional Spring Boot layered structure:

- controllers/: exposes REST endpoints for authentication, rental operations, inventory, staff, manager flows, member history, and wishlists
- services/: contains business logic and orchestration between controllers and repositories
- repositories/: provides persistence access using Spring Data JPA interfaces
- models/: defines the domain entities and data structures for the system
- resources/: holds application configuration and runtime resources

## Key software engineering documents included

This repository contains detailed design and analysis artifacts in dedicated folders, which reflect standard software engineering practices.

### 1. SRS (Software Requirements Specification)

Folder: `1. SRS`

This part describes the problem statement, requirements, scope, functional expectations, and constraints of the system. It captures:

- functional requirements
- non-functional requirements
- user expectations
- system boundaries
- constraints and assumptions

This is the foundation of the project and ensures the implementation is aligned with actual business needs.

### 2. DFD (Data Flow Diagrams)

Folder: `2. DFD`

The DFD documents show how data moves across the system. They help visualize:

- external inputs and outputs
- processes involved in the workflow
- data stores and repositories
- information flow between users and system modules

This is useful for understanding how rental requests, inventory updates, user actions, and reports flow through the application.

### 3. UC Diagram (Use Case Diagrams)

Folder: `3. UC Diagram`

Use case modeling represents the interactions between actors and the system. This folder identifies the major scenarios such as:

- login/authentication
- search or manage inventory
- create rental
- process returns
- review member history
- manage wishlist entries
- staff or manager administrative tasks

Use cases help define the system from a user-centered perspective and drive the API design.

### 4. Class Diagram

Folder: `4. Class Diagram`

The class diagram models the core entities and relationships in the application. It typically identifies:

- domain classes such as Member, Staff, Manager, InventoryItem, RentalTransaction, Wishlist
- associations and multiplicities
- responsibilities and structure of classes
- how business logic is organized around domain objects

This is a key object-oriented design artifact and aligns closely with the Java model classes in `src/main/java/com/vrsms/server/models`.

### 5. Sequence Diagrams

Folder: `5. Sequence Diagram`

Sequence diagrams represent how components interact over time for a given use case. For example, they can show:

- a customer renting a video
- a staff member processing a return
- a manager approving or reviewing store operations
- a login flow involving controller, service, and repository interaction

These diagrams show the runtime message flow and help validate that the controller-service-repository design matches the business process.

## Key software engineering techniques used

This project demonstrates several core software engineering practices:

### Requirement-driven development
The presence of SRS documents shows a requirement-centric approach, making sure the system is designed around user and business needs before coding.

### System modeling
DFD and use case diagrams are used to model the system structure and interactions, making the architecture easier to understand and communicate.

### Object-oriented design
The class diagram reflects object-oriented design principles, including abstraction, encapsulation, association, and modeling of system entities and relationships.

### Behavioral modeling
Sequence diagrams depict runtime behavior and interaction ordering, helping identify responsibilities between modules and ensure the flow of logic is correct.

### Layered architecture
The Java project follows a clear separation of concerns:

- controller layer for API endpoints
- service layer for business logic
- repository layer for persistence access
- model layer for domain definitions

This reduces coupling and keeps the codebase maintainable.

### Data persistence abstraction
Spring Data JPA allows database access to be modeled through repository interfaces rather than raw SQL handling, improving maintainability and reducing boilerplate.

### RESTful API design
Controller classes are organized around resource-oriented endpoints, making the system suitable for integration with front-end applications or external clients.

### Dependency injection and inversion of control
Spring Boot manages application components and dependencies through dependency injection, improving modularity and testability.

### Validation and business rule enforcement
The inclusion of validation libraries and service-based logic indicates attention to data integrity and business rules such as rental conditions, member checks, and item availability.

### Containerized deployment
The Dockerfile makes the application portable and easier to deploy in development, testing, and production environments.

## Typical system flow

A common runtime flow in this project is:

1. A client sends an API request to a controller
2. The controller validates input and passes it to a service
3. The service applies business rules and calls a repository
4. JPA persists or retrieves data from PostgreSQL
5. Results are returned through the REST layer to the client

This flow matches the layered architecture and design documentation included in the repository.

## Quick start

### Prerequisites

- Java 17+
- Maven (or use the included Maven wrapper)
- PostgreSQL database
- Docker (optional)

### Build and run

```bash
git clone https://github.com/bindpratapsingh/VRSMS---Main.git
cd VRSMS---Main
./mvnw clean package
./mvnw spring-boot:run
```

### Running with Docker

```bash
docker build -t vrsms-server .
docker run -p 8080:8080 vrsms-server
```

## Notes

- The repository contains both implementation artifacts and engineering design documents.
- The printed documentation in the `1. SRS`, `2. DFD`, `3. UC Diagram`, `4. Class Diagram`, and `5. Sequence Diagram` folders is an important part of the project and reflects good software engineering practice.
- The project is structured as a backend service, but the documentation clearly shows its design and analysis process from requirements through system behavior modeling.

## Conclusion

VRSMS is more than a basic CRUD project; it demonstrates a complete software engineering workflow from requirements specification to system design and implementation. The repository is a strong example of how formal documentation and modern backend development practices can be combined to build a real-world management system.
