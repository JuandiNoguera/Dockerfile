# Dockerfile
 
 - Restablecer usuario por Postgresql

INSERT INTO users (userid,alias,name,surname,passwd,url,autologin,autologout,lang,refresh,type,theme,rows_per_page) values ('1','Admin','Zabbix','Administrator','$2y$10$92nDno4n0Zm7Ej7Jfsz8WukBfgSS/U0QkIuu8WkJPihXBb2A1UrEK','','1','0','en_GB','30s','3','default','50');
