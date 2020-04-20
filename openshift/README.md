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

COMANDOS SUELTOS
```
# Ejecutar nginx dentro de un pod
command: ["sh", "-c", "echo VERSION 1.0 desde $HOSTNAME > /usr/share/nginx/html/index.html && nginx -g 'daemon off;'"]
```
