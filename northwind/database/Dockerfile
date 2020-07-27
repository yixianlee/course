#FROM mysql@sha256:bf17a7109057494c45fba5aab7fc805ca00ac1eef638dfdd42b38d5a7190c9bb
FROM mysql:5.7

# ENV MYSQL_ROOT_PASSWORD=changeit MYSQL_DATABASE=northwind 
ENV MYSQL_ROOT_PASSWORD=changeit MYSQL_PORT=3306

ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

#add healthcheck

HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \  
    CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} > /dev/null || exit 1



EXPOSE 3306
VOLUME /var/lib/mysql





