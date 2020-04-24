# Comandos UNIX/LINUX REDES

## MAIN:

```
# Ver tabla de rutas Kernel IP routing table
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG        0 0          0 enp0s3
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 enp0s3
172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0

# Como ver la IP publica de mi server desde consola bash
dig TXT +short o-o.myaddr.l.google.com @ns1.google.com | awk -F'"' '{ print $2}'

```
