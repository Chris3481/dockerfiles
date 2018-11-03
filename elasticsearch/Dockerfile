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

RUN echo 'transport.host: localhost' >> /etc/elasticsearch/elasticsearch.yml && \
    echo 'transport.tcp.port: 9300' >> /etc/elasticsearch/elasticsearch.yml && \
    echo 'http.port: 9200' >> /etc/elasticsearch/elasticsearch.yml && \
    echo 'network.host: 0.0.0.0' >> /etc/elasticsearch/elasticsearch.yml && \

    # this settings is needed for elastic beanstalk
    echo 'http.cors.enabled: true' >> /etc/elasticsearch/elasticsearch.yml  && \
    echo 'http.cors.allow-origin: "*"' >> /etc/elasticsearch/elasticsearch.yml


COPY ./supervisord/supervisord-elasticsearch.conf /etc/supervisor/conf.d

CMD ["./start.sh"]

EXPOSE 9100 9200 9300
