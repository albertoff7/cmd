# Comandos OpenShift

LOGS:

Ver logs de CRI-O/kubelet de un nodo
```
oc adm node-logs -u crio my-node-name
oc adm node-logs -u kubelet my-node-name
```

Ver registros journal de un nodo RedHatCoreOS
```
oc adm node-logs my-node-name
```

ACCEDER A UN NODO (alternativa a SSH)
```
[alberto@redhat ~]$ oc debug node/my-node-name
...output omitted...
# chroot /host
# systemctl is-active kubelet
```

COMANDOS SOBRE UN POD
```
oc get pod
oc status
oc get events
oc describe pod
oc logs my-pod-name -c my-container-name
oc get pod --log-level 10
oc whoami -t ### Obtener token
oc adm top node -l node-role.kubernetes.io/worker
oc get pod -n <project_name>
oc adm node-logs --tail 3 -u kubelet ip-10-0-140-84.us-west-1.compute.internal
```

COMANDOS MACHINE
```
# Obtener los machinsets
oc get machinesets -n openshift-machine-api
NAME                          DESIRED   CURRENT   READY   AVAILABLE   ...
ocp-qz7hf-worker-us-west-1b   1         1         1       1           ...
ocp-qz7hf-worker-us-west-1c   1         1         1       1           ...
```

COMANDOS SUELTOS
```
# Ejecutar nginx dentro de un pod
command: ["sh", "-c", "echo VERSION 1.0 desde $HOSTNAME > /usr/share/nginx/html/index.html && nginx -g 'daemon off;'"]

# Crear una app nueva desde un repositorio docker
oc new-app --name mysql --docker-image registry.access.redhat.com/rhscl/mysql-57-rhel7:5.7-47

# Crear secreto
oc create secret generic mysql --from-literal user=myuser --from-literal password=redhat123 --from-literal database=test_secrets --from-literal hostname=mysql 

# Crear un proyecto
* La creación de un proyecto también crea un NS con el mismo nombre *
oc new-proyect desa1

# Ver caracteristicas de un proyecto
oc describe project desa1
oc get project desa1 -o yaml
oc get projects -l tipo=desa 

# Aplicar cambios de un yaml
oc apply -f first.yml

# Crear un namespace
* La creación de un namespace también crea un proyecto *
oc create namespace desa4

# Para conceder privilegios de ROOT a los contenedores
oc adm policy add-scc-to-user anyuid -z default

# Para cambiarse de proyecto
oc project desa1

# Para crear un pod (Generator con las nuevas versiones)
oc run --generator=run-pod/v1 nginx --image=nginx

# Para recuperar los pods
oc get pods
oc get pods -o wide
oc describe pod nginx
oc get pod nginx -o yaml

# Para recuperar logs de un pod
oc logs nginx

# Para recuperar todos los objetos de un proyecto
oc get all

# Para recuperar los servicios
oc get svc
oc get describe svc servicio1

# Para recuperar un imagestream
oc get is

# Parar recuperar las rutas
oc get route blog

# Escalar replicas
oc scale --replicas=3 dc blog

# Borrar un pod
oc delete pod blog-1-g89rd

```

TERMINOLOGIA
```
# Proyectos: Un namespace de kubernetes en el que también entran objetos de openshift como rutas, DC, BC, etc.
# Pod: Objeto mínimo para desplegar un contenedor
# Imagestream: Directorio de imagenes apunta a diferentes versiones de las imagenes que queremos desplegar. Ventaja: al cambiar la imagen, se puede actualizar de una forma automática. 
# DeploymentConfig: Objeto que crea un ReplicationControler que se encarga de mantener las replicas indicadas de un determinado pod (en base a una imagen de nuestra aplicación)


```
