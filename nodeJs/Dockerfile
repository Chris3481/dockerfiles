FROM base

# install packages
RUN install_package \
    gnupg \
    gnupg1 \
    gnupg2

RUN curl -sL https://deb.nodesource.com/setup_6.x | bash -

RUN install_package nodejs

# COPY supervisord/supervisord-nodejs.conf /etc/supervisor/conf.d/

CMD ["./start.sh"]