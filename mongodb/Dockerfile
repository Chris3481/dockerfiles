FROM base

# install packages
RUN install_package mongodb

# configure mongodb
RUN chown -R mongodb:mongodb /var/lib/mongodb

RUN sed -i -e "s/127.0.0.1/0.0.0.0/g" /etc/mongodb.conf

RUN chown -R mongodb:mongodb /var/lib/mongodb

COPY ./supervisord/supervisord-mongodb.conf /etc/supervisor/conf.d

CMD ["./start.sh"]

EXPOSE 27017 27018 57428
