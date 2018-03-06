FROM mariadb:10.1.31

ARG GROUP_ID=1000
ARG USER_ID=1000

# Fix permissions to match host user
RUN usermod -u ${USER_ID:-1000} mysql && groupmod -g ${GROUP_ID:-1000} mysql

# Append config to defaults
COPY conf/esco-strict-server.cnf /etc/mysql/conf.d/custom.cnf

EXPOSE 3306

ENTRYPOINT ["docker-entrypoint.sh"]

CMD ["mysqld"]