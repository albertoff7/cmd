# Comandos Kubernetes

## MAIN:

```
# Ver configuracion (contexto)
kubectl config view

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

### Namespaces

```
# Obtener namespaces
kubectl get namespaces

## CONTEXTOS

# Establecer la preferencia de espacio de nombres. 
# Indicar de forma permanente el namespace para llamadas futuras con kubectl.
kubectl config set-context --current --namespace=<insert-namespace-name-here>
kubectl config view | grep namespace:

# También se podría crear un contexto, para lo cual hay que indicar cluster, usuario etc.
# Si creaste un contexto, para cambiar a el ejecuta
kubectl config use-context contexto_xxx

# Obtener pods de un namespace en concreto
kubectl get pods --namespace namespace_xxx
kubectl get pods -n namespace_xxx

# Crear namespaces
kubectl create namespaces test
```
