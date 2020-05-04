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
```
