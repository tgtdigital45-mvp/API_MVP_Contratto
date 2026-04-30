# Project Overview

Backend for the **Contratto MVP** (B2B2C Marketplace). This is a Spring Boot application designed to handle the core business logic, data persistence, and caching for the marketplace platform.

- **Main Technologies:**
    - **Language:** Java 21
    - **Framework:** Spring Boot (Parent: 4.0.3)
    - **Database:** PostgreSQL 15 (Migrations with Flyway)
    - **Caching:** Redis
    - **Build Tool:** Maven
    - **Containerization:** Docker & Docker Compose
    - **Key Libraries:** 
        - [Lombok](https://projectlombok.org/) for boilerplate reduction.
        - [MapStruct](https://mapstruct.org/) for type-safe bean mapping.
        - [Uber H3](https://h3geo.org/) for hexagonal hierarchical geospatial indexing.

# Building and Running

### Prerequisites
- Java 21 JDK
- Docker and Docker Compose (for infrastructure)
- Maven (or use the included `./mvnw` wrapper)

### Infrastructure Setup
To start the required services (PostgreSQL, Redis):
```bash
docker compose up -d
```
*Note: Ensure you have a `.env` file or environment variables set for `DB_USER`, `DB_PASSWORD`, `DB_NAME`, `REDIS_PASSWORD`, and `SNOWFLAKE_NODE_ID`.*

### Running the Application Locally
Using the Maven wrapper:
```bash
./mvnw spring-boot:run
```

### Building the Project
To compile and package the application into a JAR:
```bash
./mvnw clean package
```

### Running Tests
To execute the test suite:
```bash
./mvnw test
```

# Development Conventions

- **Java Version:** Strictly Java 21. Utilize modern features like Records, Sealed Classes, and Pattern Matching where appropriate.
- **Database Migrations:** All schema changes must be implemented via Flyway migration scripts located in `src/main/resources/db/migration`.
- **Mapping:** Use MapStruct for converting between Entities and DTOs. Avoid manual mapping logic in services.
- **Lombok:** Use `@Data`, `@Builder`, `@NoArgsConstructor`, and `@AllArgsConstructor` to keep code concise.
- **Configuration:** Externalize configuration using `application.yaml` and environment variables.
- **Geospatial:** Use Uber H3 for any location-based logic or spatial indexing requirements.

# Project Structure
- `src/main/java/com/contratto/api`: Root package for the application.
- `src/main/resources/db/migration`: SQL migration scripts (Flyway).
- `Dockerfile`: Multi-stage build for containerizing the Spring Boot app.
- `compose.yaml`: Infrastructure and application orchestration.

<!-- SPECKIT START -->
For additional context about technologies to be used, project structure,
shell commands, and other important information, read the current plan
<!-- SPECKIT END -->
