FROM mariadb:10.3.24

ARG GROUP_ID=1000
ARG USER_ID=1000

# Fix permissions to match host user
RUN usermod -u ${USER_ID:-1000} mysql && groupmod -g ${GROUP_ID:-1000} mysql

# Append config to defaults
COPY conf/esco-strict-server.cnf /etc/mysql/conf.d/custom.cnf

# set locales
RUN apt-get update && apt-get install -y \
    apt-utils \
    locales
RUN locale-gen fr_FR.UTF-8
ENV LANG fr_FR.UTF-8
ENV LC_CTYPE fr_FR.UTF-8

# Set TIMEZONE
ENV TZ=Europe/Paris
RUN echo $TZ > /etc/timezone && \
    apt-get update && apt-get install -y tzdata && \
    rm /etc/localtime && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    dpkg-reconfigure -f noninteractive tzdata && \
    apt-get clean

EXPOSE 3306

ENTRYPOINT ["docker-entrypoint.sh"]

CMD ["mysqld"]
