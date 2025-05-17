**common Kubernetes operations** along with essential **kubectl commands and code snippets** for deployment and management.

---

### 🚀 **Kubernetes Operations & Code Snippets**

---

## 🔧 1. **Basic Cluster Operations**

### View cluster info:

```bash
kubectl cluster-info
```

### List nodes:

```bash
kubectl get nodes
```

### List all resources in default namespace:

```bash
kubectl get all
```

---

## 📦 2. **Deployment Operations**

### Create Deployment:

```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: myapp-container
        image: nginx
        ports:
        - containerPort: 80
```

```bash
kubectl apply -f deployment.yaml
```

### Scale Deployment:

```bash
kubectl scale deployment myapp-deployment --replicas=3
```

### Update Image:

```bash
kubectl set image deployment/myapp-deployment myapp-container=nginx:latest
```

---

## 🌐 3. **Service Operations**

### Create Service:

```yaml
# service.yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  selector:
    app: myapp
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: NodePort
```

```bash
kubectl apply -f service.yaml
```

### Get Services:

```bash
kubectl get svc
```

---

## 🔍 4. **Pod Operations**

### Get Pods:

```bash
kubectl get pods
```

### Describe Pod:

```bash
kubectl describe pod <pod-name>
```

### Exec into Pod:

```bash
kubectl exec -it <pod-name> -- /bin/bash
```

---

## 📄 5. **ConfigMap & Secrets**

### ConfigMap:

```bash
kubectl create configmap my-config --from-literal=ENV=dev
kubectl get configmaps
```

### Secret:

```bash
kubectl create secret generic my-secret --from-literal=password=1234
kubectl get secrets
```

---

## 📁 6. **Volumes and Persistent Storage**

```yaml
# pvc.yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

```bash
kubectl apply -f pvc.yaml
```

---

## ⚙️ 7. **Helm Commands (Optional)**

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-release bitnami/nginx
helm ls
helm uninstall my-release
```

---

## 🧪 8. **Monitoring & Logs**

```bash
kubectl logs <pod-name>
kubectl top pods
kubectl get events
```

---

## 🔄 9. **Rollouts & Rollbacks**

```bash
kubectl rollout status deployment/myapp-deployment
kubectl rollout undo deployment/myapp-deployment
```

---

## 🧼 10. **Clean-up Resources**

```bash
kubectl delete deployment myapp-deployment
kubectl delete svc myapp-service
kubectl delete pvc my-pvc
```

---
