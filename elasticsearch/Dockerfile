FROM base

# get elastic search package
RUN wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.2.4.deb && \
    dpkg -i elasticsearch-6.2.4.deb

# install packages
RUN install_package \
  openjdk-8-jdk-headless \
  net-tools \
  elasticsearch

RUN rm -rf elasticsearch-6.2.4.deb

RUN chown -R elasticsearch:elasticsearch /var/lib/elasticsearch

COPY ./elasticsearch.yml /etc/elasticsearch

COPY ./supervisord/supervisord-elasticsearch.conf /etc/supervisor/conf.d

CMD ["./start.sh"]

EXPOSE 9100 9200 9300
