FROM base

RUN wget https://artifacts.elastic.co/downloads/kibana/kibana-6.2.4-amd64.deb && \
    dpkg -i kibana-6.2.4-amd64.deb

COPY ./etc/kibana/kibana.yml /etc/kibana


CMD ["./usr/share/kibana/bin/kibana"]

EXPOSE 5601
