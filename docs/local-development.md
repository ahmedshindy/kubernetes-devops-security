## Local Development

### Prerequisites
- Java 8 JDK (compatible with Spring Boot 2.2.1)
- Maven 3.6+
- Optional: A local Node service for `/increment` dependency, or disable testing of that endpoint

### Build
```bash
mvn clean package -DskipTests
```

The compiled JAR will be created under `target/` (e.g., `numeric-0.0.1.jar`).

### Run
```bash
mvn spring-boot:run
# or
java -jar target/numeric-0.0.1.jar
```

The app listens on `http://localhost:8080`.

### Test Endpoints
- `GET /` → should return: `Kubernetes DevSecOps`
- `GET /compare/51` → `Greater than 50`
- `GET /compare/10` → `Smaller than or equal to 50`
- `GET /increment/7` → requires the Node service running at `http://node-service:5000/plusone`.

To test `/increment` locally without Kubernetes, either:
1. Run a compatible Node service locally and update `src/main/resources/application.properties` to point to it, or
2. Temporarily mock the service by running a simple local server on `localhost` and editing the controller URL.

### Troubleshooting
- If port 8080 is in use, set `server.port` in `application.properties` or run with `--server.port=9090`.
- If `/increment` fails, verify connectivity to the Node service or skip testing that endpoint.


