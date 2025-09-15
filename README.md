# kubernetes-devops-security

## Fork and Clone this Repo

## Clone to Desktop and VM

## NodeJS Microservice - Docker Image -
`docker run -p 8787:5000 siddharth67/node-service:v1`

`curl localhost:8787/plusone/99`
 
## NodeJS Microservice - Kubernetes Deployment -
`kubectl create deploy node-app --image siddharth67/node-service:v1`

`kubectl expose deploy node-app --name node-service --port 5000 --type ClusterIP`

`curl node-service-ip:5000/plusone/99`



### Run
```
cd kubernetes-devops-security/
mvn -q -DskipTests clean package
nohup java -jar target/numeric-0.0.1.jar --server.port=9090 > app-9090.log 2>&1 &
```

Verify
```
curl -sS http://localhost:9090/
curl -sS http://localhost:9090/compare/51
```
