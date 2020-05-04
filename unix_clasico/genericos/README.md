# Comandos UNIX/LINUX Generic

## PS (monitorizacion de procesos):

```
# Ver la jerarquia de procesos con ps auxf
root      2023  0.2  2.6 1373708 103560 ?      Ssl  17:12   0:04 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
root      8528  0.0  0.2 479084  9512 ?        Sl   17:21   0:00  \_ /usr/bin/docker-proxy -proto tcp -host-ip 0.0.0.0 -host-port 8001 -container-ip 172.19.0.5 -container-port 80
root      2027  0.0  0.2  92312  7756 ?        Ss   17:12   0:00 /usr/sbin/sshd -D -oCiphers=aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes256-ctr,aes256-cbc,aes128-gcm@openssh.com,aes128-ctr,aes128-cb
root      5138  0.0  0.2 159480  9652 ?        Ss   17:12   0:00  \_ sshd: ec2-user [priv]
ec2-user  5370  0.0  0.1 159480  5256 ?        S    17:12   0:00  |   \_ sshd: ec2-user@pts/1
ec2-user  5436  0.0  0.0  23256  3616 pts/1    Ss   17:12   0:00  |       \_ -bash
root      5973  0.0  0.1 135232  7140 pts/1    S    17:12   0:00  |           \_ sudo -i
root      5975  0.0  0.1  25484  4044 pts/1    S    17:12   0:00  |               \_ -bash
root     14064  0.0  1.6 641852 64992 pts/1    Sl+  17:41   0:00  |                   \_ docker logs kimai2_kimai_1 -f

# Encontrar procesos que más consumo tienen en linux
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head
  PID  PPID CMD                         %MEM %CPU
 5562  5550 /usr/lib/jvm/java-7-openjdk 24.7  3.1
 5550  5523 java -jar /usr/local/glassf 10.1  0.2
 1822     1 /usr/bin/dockerd -H fd:// -  6.6  0.1
 1433     1 /usr/bin/containerd          2.9  0.0
 1107     1 /usr/libexec/platform-pytho  2.5  0.0
 1420     1 /usr/libexec/platform-pytho  2.0  0.0
 1421     1 /usr/sbin/libvirtd           1.3  0.0
 5834  1828 sshd: ec2-user [priv]        1.1  0.2
 1464  1419 /usr/sbin/httpd -DFOREGROUN  1.1  0.0

# Limpiar la cache en un sistema linux. Cuidado REVISAR casos de uso!!
echo 1 > /proc/sys/vm/drop_caches
echo 2 > /proc/sys/vm/drop_caches
echo 3 > /proc/sys/vm/drop_caches
```
