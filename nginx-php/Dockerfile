FROM base

# get php 7.2 package
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg && \
    sh -c 'echo "deb https://packages.sury.org/php/ stretch main" > /etc/apt/sources.list.d/php.list'

# install packages
RUN install_package \
  nginx \
  php7.2-fpm \
  php7.2-mysql \
  php7.2-mongodb \
  php7.2-gd \
  php7.2-imagick \
  php7.2-dev \
  php7.2-curl \
  php7.2-opcache \
  php7.2-cli \
  php7.2-intl \
  php7.2-tidy \
  php7.2-imap \
  php7.2-json \
  php7.2-common \
  php7.2-sybase \
  php7.2-sqlite3 \
  php7.2-bz2 \
  php7.2-common \
  php7.2-apcu-bc \
  php7.2-redis \
  php7.2-xml \
  php7.2-shmop \
  php7.2-mbstring \
  php7.2-zip \
  php7.2-bcmath

#Define the ENV variable
ENV nginx_vhost /etc/nginx/sites-available
ENV php_conf /etc/php/7.2/fpm/php.ini
ENV nginx_conf /etc/nginx/nginx.conf


RUN sed -i -e 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' ${php_conf} && \
    echo "\ndaemon off;" >> ${nginx_conf}


RUN mkdir -p /run/php && \
    chown -R www-data:www-data /var/www && \
    chown -R www-data:www-data /run/php


COPY ./supervisord/supervisord-nginx.conf /etc/supervisor/conf.d


CMD ["./start.sh"]

# EXPOSE 80 443
