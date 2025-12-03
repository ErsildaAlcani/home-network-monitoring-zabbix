##  Zabbix Server Installation

Follow official Zabbix installation instructions:  
[https://www.zabbix.com/download](https://www.zabbix.com/download?zabbix=7.0&os_distribution=ubuntu_arm64&os_version=24.04&components=server_frontend_agent&db=mysql&ws=apache)

1. Install Zabbix Repository
```bash
sudo -s
wget https://repo.zabbix.com/zabbix/7.0/ubuntu-arm64/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu24.04_all.deb
dpkg -i zabbix-release_latest_7.0+ubuntu24.04_all.deb
apt update
```

2. Install Zabbix server, frontend, agent 
```bash
# apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```
> Check if the services are up and running
```bash
> systemctl status zabbix-server apache2 mysql
```
------
### Database Setup

1. Create initial database
```bash
mysql -uroot -p
1234
mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;
mysql> create user zabbix@localhost identified by '1234';
mysql> grant all privileges on zabbix.* to zabbix@localhost;
mysql> set global log_bin_trust_function_creators = 1;
mysql> quit;
```
2. On Zabbix server host import initial schema and data.
```bash
# zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix
```
>Common error - ERROR 1050 (42S01) at line XXX: Table 'role' already exists. 
>To fix it I dropped the table and created it again. 
3. Disable log_bin_trust_function_creators option after importing database schema.
```bash
mysql -uroot -p
1234
mysql> set global log_bin_trust_function_creators = 0;
mysql> quit;
```
4. Configure the database for Zabbix server
```bash
nano /etc/zabbix/zabbix_server.conf
DBPassword=1234
```
5. Start Zabbix server and agent processes
```bash
systemctl restart zabbix-server zabbix-agent apache2
systemctl enable zabbix-server zabbix-agent apache2
```
------