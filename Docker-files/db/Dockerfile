FROM mysql:8.0.33
ENV "MYSQL_ROOT_PASSWORD" = "vprodbpas"
ENV "MYSQL_DATABASE" = "accounts"
COPY db_backup.sql docker-entrypoint-initdb./db_backup.sql