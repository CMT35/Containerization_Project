FROM mysql:8.0.33
LABEL "Project"="Containerization_Project"
LABEL "Author"="CMT35"

ENV MYSQL_ROOT_PASSWORD="devprodpass"
ENV MYSQL_DATABASE="accounts"

ADD db_backup.sql docker-entrypoint-initdb.d/db_backup.sql