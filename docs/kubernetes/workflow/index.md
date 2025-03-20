# Kubernetes Deployment Workflow 🔥

## 1️⃣ Create a Namespace (Optional but Recommended)
Namespaces help organize resources within the cluster.
```sh
kubectl create namespace my-namespace
```

## 2️⃣ Create a Deployment (Manages Pods & Ensures Availability)
A Deployment ensures that the required number of Pods are running.

### Deployment YAML (nginx-example.yaml)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  namespace: my-namespace
spec:
  replicas: 2  # Number of Pods
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
```

**Apply the Deployment**

```sh
kubectl apply -f nginx-example.yaml
```

## 3️⃣ Verify Deployment & Pods

```sh
kubectl get deployments -n my-namespace
kubectl get pods -n my-namespace
```

## 4️⃣ Create a Service (To Expose Deployment Internally or Externally)
A Service allows communication with the application running inside the Pods.

### Service YAML (nginx-service.yaml)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
  namespace: my-namespace
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP  # Change to NodePort or LoadBalancer if external access is needed
```

**Apply the Service**

```sh
kubectl apply -f nginx-service.yaml
```

## 5️⃣ Verify the Service
```sh
kubectl get services -n my-namespace
```

## 6️⃣ (Optional) Expose the Application Externally

### Option 1: Use NodePort (Exposes Service on a Static Node Port)
Modify the `type` in the Service YAML:
```yaml
  type: NodePort
```
Apply changes
```sh
kubectl apply -f nginx-service.yaml
kubectl get services -n my-namespace
```

Check external access
```sh
minikube service nginx-service -n my-namespace
```

### Option 2: Use Ingress (Advanced Routing & HTTPS Support)
Create an Ingress resource for domain-based routing.

### Ingress YAML (nginx-ingress.yaml)

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: nginx-ingress
  namespace: my-namespace
spec:
  rules:
    - host: myapp.local  # Change this to your domain
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: nginx-service
                port:
                  number: 80
```

**Apply the Ingress**
```sh
kubectl apply -f nginx-ingress.yaml
```

Check the Ingress
```sh
kubectl get ingress -n my-namespace
```

## 7️⃣ Scaling & Updating the Deployment

### Scale Up or Down
```sh
kubectl scale deployment nginx-deployment --replicas=4 -n my-namespace
```

### Rolling Update (Update Image Version)
```sh
kubectl set image deployment/nginx-deployment nginx=nginx:1.21 -n my-namespace
```

## 8️⃣ Deleting Resources (Cleanup)
```sh
kubectl delete namespace my-namespace
```

---
