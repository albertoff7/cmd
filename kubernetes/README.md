# Comandos Kubernetes

## MAIN:

```
# Ver nodos
kubectl get nodes

# Ver el estado de un rollout para un deployment
kubectl rollout status deployment deployment-test

# Ver pods filtrados por label
kubectl get pods -l app=front -o wide

# Aplicar una configuracion
kubectl apply -f ejemplo1_nginx.yml 

# Obtener servicios con label front
kubectl get svc -l app=front
```
