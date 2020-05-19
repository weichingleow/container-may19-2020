FROM mysql:5.7

# set the mysql root password
ENV MYSQL_ROOT_PASSWORD=changeit

# copy *.sql files into /docker-entrypoint-initdb.d
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

# health check
HEALTHCHECK --interval=60s --timeout=30s --start-period=15s --retries=3 \
    CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1

# explicitly sets where mysql stores the database
VOLUME /var/lib/mysql