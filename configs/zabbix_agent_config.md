## Configure zabbix agent on host

The Zabbix agent is needed because it allows the Zabbix server to monitor a host in real time. Without it, the server can only monitor devices via indirect methods (like SNMP, ICMP/ping, or external scripts), which are more limited

---

### Specs

host:kali linux OS on VM
hostname:linux
host IP address: 192.168.0.109
zabbix_server IP:192.168.0.137
default listening port:10050

>hostname must be the same as hostname in host configuration in zabbix gui

## Step by step guide

1. Zabbix Agent is not included by default in Kali, so the official Zabbix repo must be added
```bash
wet https: //repo.zabbix.com/zabbix/7.0/debian-arm64/pool/main/z/zabbix-release/zabbix-release_latest_7.0+debian12_all.deb
dpkg -i zabbix-release_latest_7.0+debian12_all.deb
sudo apt update
```
2. Install zabbix agent
```bash
sudo apt install zabbix-agent -y
```
3. Configure zabbix agent
```bash
sudo nano /etc/zabbix/zabbix_agentd.conf
Server=192.168.0.137
ServerActive=192.168.0.137
Hostname=linux
```
4. Allow Firewall, as ufw is being used 
```bash
sudo ufw allow 10050/tcp
sudo ufw reload
```
5. Enable and check zabbix agent status
```bash
sudo systemctl enable zabbix-agent
sudo systemctl start zabbix-agent
sudo systemctl status zabbix-agent
```
