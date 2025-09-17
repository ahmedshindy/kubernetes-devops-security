## Documentation

This folder contains guides for understanding, running, and deploying the project.

- [Overview](./overview.md)
- [Local Development](./local-development.md)
- [Docker](./docker.md)
- [Kubernetes](./kubernetes.md)


### Run
```
cd ~/kubernetes-devops-security/
mvn -q -DskipTests clean package
nohup java -jar target/numeric-0.0.1.jar --server.port=9090 > app-9090.log 2>&1 &
```

### Verify
```
curl -sS http://localhost:9090/
curl -sS http://localhost:9090/compare/51
```


