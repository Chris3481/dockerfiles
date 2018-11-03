FROM base

# install packages
RUN install_package mariadb-server

ENV mysql_user chris
ENV mysql_pass chris1990
ENV mysql_host localhost
ENV mysql_db   sample

RUN chown -R mysql:mysql /var/lib/mysql

# configure mariadb
RUN sed -i -e "s/127.0.0.1/0.0.0.0/g" /etc/mysql/mariadb.conf.d/50-server.cnf && \
  echo "mysqld_safe &" > /tmp/config && \
  echo "mysqladmin --silent --wait=30 ping || exit 1" >> /tmp/config && \
  echo "mysql -e 'CREATE DATABASE ${mysql_db} CHARACTER SET utf8 COLLATE utf8_bin;'" >> /tmp/config && \
  echo "mysql -e 'CREATE USER \"${mysql_user}\"@\"%\" IDENTIFIED BY \"${mysql_pass}\";'" >> /tmp/config && \
  echo "mysql -e 'GRANT ALL PRIVILEGES ON *.* TO \"${mysql_user}\"@\"%\" WITH GRANT OPTION;'" >> /tmp/config && \
  echo "mysql -e 'flush privileges;'" >> /tmp/config && \
  bash /tmp/config && \
  rm -f /tmp/config

COPY ./supervisord/supervisord-mariadb.conf /etc/supervisor/conf.d

CMD ["./start.sh"]

EXPOSE 3306
