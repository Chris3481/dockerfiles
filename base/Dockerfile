FROM debian:stretch

# Install base packages
RUN \
  apt-get update && \
  apt-get install -y \
  supervisor \
  curl \
  wget \
  git \
  nano \
  locales \
  iptables


# Add package installation scrpt    
COPY ./install_package /usr/local/bin/
RUN chmod +x /usr/local/bin/install_package


# required for installing php7.2
RUN install_package   \
    apt-transport-https \
    ca-certificates


#Copy supervisor configuration
COPY ./supervisord/supervisord.conf /etc/supervisor/supervisord.conf


COPY start.sh /start.sh
