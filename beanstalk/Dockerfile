FROM base

# get php 7.2 package
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg && \
    sh -c 'echo "deb https://packages.sury.org/php/ stretch main" > /etc/apt/sources.list.d/php.list'

# install packages
RUN install_package \
    beanstalkd \
    nginx \
    php7.2-fpm

# install elastic beanstalk
RUN rm -rf /var/www
RUN git clone https://github.com/ptrofimov/beanstalk_console.git /var/www
RUN chown -R www-data:www-data /var/www && \
    chmod -R 775 /var/www


# configure php
ENV nginx_vhost /etc/nginx/sites-available
ENV php_conf /etc/php/7.2/fpm/php.ini
ENV nginx_conf /etc/nginx/nginx.conf

RUN sed -i -e 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' ${php_conf} && \
    echo "\ndaemon off;" >> ${nginx_conf}

RUN mkdir -p /run/php && \
    chown -R www-data:www-data /run/php


COPY nginx/sites-available/beanstalk /etc/nginx/sites-available

RUN rm -rf /etc/nginx/sites-available/default
RUN ln -s /etc/nginx/sites-available/beanstalk /etc/nginx/sites-enabled


COPY supervisord/supervisord-beanstalk.conf /etc/supervisor/conf.d

CMD ["./start.sh"]

EXPOSE 11300 8282









# get php 7.2 package
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg && \
    sh -c 'echo "deb https://packages.sury.org/php/ stretch main" > /etc/apt/sources.list.d/php.list'



