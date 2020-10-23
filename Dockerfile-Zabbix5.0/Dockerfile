
FROM debian 
MAINTAINER Juan Diego Noguera "juandinogueraide@gmail.com"

RUN apt-get update && apt-get -y upgrade
RUN apt-get install wget -y
RUN wget https://repo.zabbix.com/zabbix/5.0/debian/pool/main/z/zabbix-release/zabbix-release_5.0-1+buster_all.deb
RUN dpkg -i zabbix-release_5.0-1+buster_all.deb
RUN apt-get update
RUN apt-get install -y zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-agent

COPY apache.conf /etc/zabbix/apache.conf
COPY zabbix_server.conf /etc/zabbix/zabbix_server.conf
COPY zabbix_agentd.conf /etc/zabbix/zabbix_agentd.conf
COPY zabbix.conf.php /etc/zabbix/web/zabbix.conf.php

RUN service zabbix-server restart && service zabbix-agent restart

EXPOSE 80

ENTRYPOINT ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
