FROM centos:centos7.8.2003
ENV container docker
RUN yum -y update; yum clean all
RUN yum -y install systemd; yum clean all; \
(cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
MAINTAINER Juan Diego Noguera "juandinogueraide@gmail.com"

RUN yum update -y
RUN rpm -Uvh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-release-5.0-1.el7.noarch.rpm
RUN yum clean all && yum install zabbix-server-pgsql zabbix-agent centos-release-scl -y
COPY zabbix.repo /etc/yum.repos.d/zabbix.repo
RUN yum install zabbix-web-pgsql-scl zabbix-apache-conf-scl -y
COPY zabbix.conf /etc/opt/rh/rh-php72/php-fpm.d/zabbix.conf
COPY zabbix_server.conf /etc/zabbix/zabbix_server.conf
COPY zabbix_agentd.conf /etc/zabbix/zabbix_agentd.conf
COPY zabbix.conf.php /etc/zabbix/web/zabbix.conf.php

EXPOSE 80

ENTRYPOINT ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
