# Server install (include agent)

Change default passwords, ports and set listet IP
```bash
docker-compose up -d
```

# Agent install

Download package from repository [https://repo.zabbix.com/zabbix/5.2/ubuntu/pool/main/z/zabbix/](https://repo.zabbix.com/zabbix/5.2/ubuntu/pool/main/z/zabbix/)
```bash
dpkg -i zabbix-agent_5.2.*.deb
```
Change default values in /etc/zabbix/zabbix_agent2.conf

* `Hostname` the same as in the zabbix-server web interface;
* `Server` and `ServerActive` set zabbix server IP or DNS name;
* `ListenIP` to local network IP available from zabbix server or set firewall rules to restrict access to port 10050;
* uncomment `Plugins.Docker.Endpoint=unix:///var/run/docker.sock`.

# Alerts

In WebUI - Administration -> Media types -> Telegram:
```
https://git.zabbix.com/projects/ZBX/repos/zabbix/browse/templates/media/telegram

1. Register bot: send "/newbot" to @BotFather and follow instructions
2. Copy and paste the obtained token into the "Token" field above
3. If you want to send personal notifications, you need to get chat id of the user you want to send messages to:
    3.1. Send "/getid" to "@myidbot" in Telegram messenger
    3.2. Copy returned chat id and save it in the "Telegram Webhook" media for the user
    3.3. Ask the user to send "/start" to your bot (Telegram bot won't send anything to the user without it)
4. If you want to send group notifications, you need to get group id of the group you want to send messages to:
    4.1. Add "@myidbot" to your group
    4.2. Send "/getgroupid@myidbot" in your group
    4.3. Copy returned group id save it in the "Telegram Webhook" media for the user you created for  group notifications
    4.4. Send "/start@your_bot_name_here" in your group (Telegram bot won't send anything to the group without it)
```