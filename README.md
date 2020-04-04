# angularcrud
Production Level of Angular CRUD Operation with FireBase<br>
See Demo : <a href="https://shawon100.github.io/angularcrud/">Angular CRUD</a>

# Docker Images

https://hub.docker.com/repository/docker/shawon10/angularcrud

# Kubernetes Deployment 
```
kubectl apply -f deployment.yaml

```
# deployment.yaml

```
apiVersion: v1
kind: Service
metadata:
  name: angularcrud-service
spec:
  selector:
    app: angularcrud
  ports:
  - protocol: "TCP"
    port: 80
    targetPort: 80
  type: NodePort

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: angularcrud
spec:
  selector:
    matchLabels:
      app: angularcrud
  replicas: 1
  template:
    metadata:
      labels:
        app: angularcrud
    spec:
      containers:
      - name: angularcrud
        image: shawon10/angularcrud
        imagePullPolicy: Always
        ports:
        - containerPort: 80
```
