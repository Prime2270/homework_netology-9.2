список команд job1

sudo wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian11_all.deb

sudo dpkg -i zabbix-release_6.4-1+debian11_all.deb

sudo apt update

sudo apt install postgresql -y

sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent2 -y


sudo -u postgres createuser --pwprompt zabbix

#задаем пароль

sudo -u postgres createdb -O zabbix zabbix

zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

sudo nano /etc/zabbix/zabbix_server.conf

DBPassword=123456789

sudo systemctl restart zabbix-server zabbix-agent2 apache2

sudo systemctl enable zabbix-server zabbix-agent2 apache2

sudo systemctl status zabbix-server zabbix-agent2 apache2

список команд job2

wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian11_all.deb

sudo dpkg -i zabbix-release_6.4-1+debian11_all.deb

sudo apt update

sudo apt install zabbix-agent2 zabbix-agent2-plugin-*

sudo nano /etc/zabbix/zabbix_agent2.conf

#Server=добавить адрес zabbix.server

sudo systemctl restart zabbix-agent2

sudo systemctl enable zabbix-agent2

sudo systemctl status zabbix-agent2

tail -f /var/log/zabbix/zabbix_agent2.log

