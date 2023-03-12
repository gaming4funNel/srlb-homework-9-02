# Домашнее задание к занятию "9.2 Zabbix. Часть 1" - Иванов Игорь


### Задание 1

Установите Zabbix Server с веб-интерфейсом.

Приложите скриншот авторизации в админке. Приложите текст использованных команд в GitHub.

 wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian11_all.deb
 dpkg -i zabbix-release_6.4-1+debian11_all.deb
 apt update
 
 apt install postgresql
 
 apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-nginx-conf zabbix-sql-scripts zabbix-agent
 
 sudo -u postgres createuser --pwprompt zabbix
 sudo -u postgres createdb -O zabbix zabbix
 
 zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
 
 nano /etc/zabbix/zabbix_server.conf
 
 nano /etc/zabbix/nginx.conf

![Zabbix](https://github.com/gaming4funNel/srlb-homework-9-02/blob/main/img/zabbix_auth.png)
---

### Задание 2

Установите Zabbix Agent на два хоста.

Приложите скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу. 

![Zabbix](https://github.com/gaming4funNel/srlb-homework-9-02/blob/main/img/hosts.png)

Приложите скриншот лога zabbix agent, где видно, что он работает с сервером. 

![Zabbix](https://github.com/gaming4funNel/srlb-homework-9-02/blob/main/img/log_zabbix_agent.png)

Приложите скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные. 

![Zabbix](https://github.com/gaming4funNel/srlb-homework-9-02/blob/main/img/latest_data_zabbix.png)

![Zabbix](https://github.com/gaming4funNel/srlb-homework-9-02/blob/main/img/latest_data_zabbix2.png)

Приложите текст использованных команд в GitHub.

 wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian11_all.deb
 dpkg -i zabbix-release_6.4-1+debian11_all.deb
 apt update
 
 apt install zabbix-agent2 zabbix-agent2-plugin-*
 
 systemctl restart zabbix-agent2
 systemctl enable zabbix-agent2

## Дополнительные задания (со звездочкой*)

### Задание 3*

Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.

Приложите скриншот раздела Latest Data, где видно свободное место на диске C:

![Zabbix](https://github.com/gaming4funNel/srlb-homework-9-02/blob/main/img/windows_c.png)
