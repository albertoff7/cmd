# DOCKER

## Instalación Centos
```
yum-config-manager --add-repo  https://download.docker.com/linux/centos/docker-ce.repo
dnf install https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.2.6-3.3.el7.x86_64.rpm -y
dnf install docker-ce -y
systemctl enable --now docker
curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o docker-compose
mv docker-compose /usr/bin && chmod +x /usr/bin/docker-compose
```

## Comandos Docker
```
# Crear contenedor con utilizando red del host
docker build --network host -t <tag_name:v1.0> .

# Ver la IP de un contenedor
podman inspect -f "{{.NetworkSettings.IPAddress}}" nginx 
```
