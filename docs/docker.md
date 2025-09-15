## Docker

### Build Image
First, build the JAR:
```bash
mvn clean package -DskipTests
```

Then build the image (from repo root):
```bash
docker build -t numeric-app:local .
```

### Run Container
```bash
docker run --rm -p 8080:8080 --name numeric numeric-app:local
```

### Notes
- The image runs as a non-root user and exposes port 8080.
- Healthcheck hits `/actuator/health`. If actuator is not enabled, the healthcheck may fail but the app can still run; you can remove or adjust this for local use.


