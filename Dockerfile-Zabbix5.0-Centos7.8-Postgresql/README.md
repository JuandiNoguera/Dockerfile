# Dockerfile

- Arrancar contenedor:

>docker run -d -it --name zabbix -p 80:80 --network zabbix-net --privileged juandi97/zabbix5-centos:2.0 /usr/sbin/init
