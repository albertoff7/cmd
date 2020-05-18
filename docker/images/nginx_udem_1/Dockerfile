FROM centos:7

COPY . /tmp

COPY ./conf/nginx.repo /etc/yum.repos.d/nginx.repo

RUN                                                                          \
  yum -y install nginx --enablerepo=nginx                                 && \
  yum -y install php

EXPOSE 80 443

VOLUME /var/www/html /var/log/nginx /var/log/php-fpm /var/lib/php-fpm

COPY ./conf/nginx.conf /etc/nginx/conf.d/default.conf

COPY ./bin/start.sh /start.sh

COPY index.php /var/www/html/index.php

RUN chmod +x /start.sh

ENTRYPOINT ["bash", "/start.sh"]
