FROM centos
MAINTAINER alberto <alberto@alberto.ws>
LABEL description="Imagen Centos Docker File Abril 2020"
RUN dnf clean all && rm -r /var/cache/dnf  && dnf install httpd -y
CMD apachectl -DFOREGROUND
