FROM percona:latest

MAINTAINER peyagodson "peyagodson@gmail.com"

ENV LANG C.UTF-8
#RUN apt-get update
#COPY ./fame-server/src/main/resources/init.sql /docker-entrypoint-initdb.d/init.sql
COPY ./mysqld.cnf /etc/mysql/mysql.conf.d/mysqld.cnf
