FROM base

# install packages
RUN install_package nginx

# install elastic beanstalk
RUN rm -rf /var/www
RUN git clone git://github.com/mobz/elasticsearch-head.git /var/www
RUN chown -R www-data:www-data /var/www && \
    chmod -R 775 /var/www

COPY nginx/sites-available/head /etc/nginx/sites-available

RUN rm -rf /etc/nginx/sites-available/default
RUN ln -s /etc/nginx/sites-available/head /etc/nginx/sites-enabled


COPY supervisord/supervisord-elastic-head.conf /etc/supervisor/conf.d

CMD ["./start.sh"]

EXPOSE 8080
