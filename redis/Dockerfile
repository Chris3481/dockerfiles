FROM base

# install packages
RUN install_package redis-server


COPY supervisord/supervisord-redis.conf /etc/supervisor/conf.d

CMD ["./start.sh"]

EXPOSE 6379
