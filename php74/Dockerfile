FROM centos:7
ENV TZ=Asia/Shanghai

RUN yum -y install epel-release --nogpgcheck && \
    yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm && \
    yum -y install git && yum -y install supervisor && \
    yum install -y php74 php74-php-fpm php74-php-cli php74-php-bcmath php74-php-gd php74-php-json php74-php-mbstring php74-php-mcrypt php74-php-mysqlnd php74-php-opcache php74-php-pdo php74-php-pecl-crypto php74-php-xml php74-php-pecl-redis5 php74-php-pecl-mongodb php74-php-openssl php74-php-pecl-zip && \
    cp /usr/bin/php74 /usr/bin/php && \
    ln -sf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo '$TZ' > /etc/timezone && \
    php -r "readfile('https://getcomposer.org/installer');" | php && \
    groupadd -r www && useradd -r -g www -s /bin/bash www && \
    mv composer.phar /usr/local/bin/composer && yum clean all

COPY .config/php/php.ini /etc/opt/remi/php74/php.ini
COPY .config/php/php-fpm.conf /etc/opt/remi/php74/php-fpm.conf
COPY .config/php/www.conf /etc/opt/remi/php74/php-fpm.d/www.conf
COPY .supervisor/supervisord.conf /etc/supervisord.conf
COPY .supervisor/supervisord.d/php-worker.ini /etc/supervisord.d/php-worker.ini

WORKDIR /var/www/html
EXPOSE 9000
CMD ["/usr/bin/supervisord","-c","/etc/supervisord.conf"]