FROM centos
MAINTAINER alberto <alberto@alberto.ws>
LABEL description="Imagen Centos Docker File Abril 2020"
RUN yum install httpd -y && \
    yum clean all
COPY fondo.sh /tmp/fondo.sh
EXPOSE 80
ENTRYPOINT ["/tmp/fondo.sh"]
