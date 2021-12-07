# Zabbix agent installatino and metrics collection:

These are the steps followed:

- Insallation of zabbix agent

```bash
sudo apt install zabbix-agent

```

![zabbix install](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/installing-zabbix-agent.png)

- Upated the zabbix server credentials in `zabbix-agentd.conf` located at `/etc/zabbix/`:

![updating server and hostname](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/setting-server-active-value-and-hostname.png)

Later the hostname was changed to `server1` in this conf file.

- eanble and restart zabbix-agent:

```bash
systemctl restart zabbix-agent
systemctl status zabbix-agent


```

![zabbix agent running](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/zabbix-agent-running.png)

- Updating firwall rules to allow 10050 tcp port:

```bash
sudo ufw allow 10050/tcp

```

![firewall](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/added-firewall-rule-for-zabbix-agent.png)

- Created a new host `server1` with `Linux by Zabbix agent active` template using the zabbix frontend:

![listing hosts](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/lists-of-hosts.png)
![ping](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/zabix-host-ping-t0-server.png)

- Adding custom log item:
  Creating a sys log item.
  ![sys log](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/adding-log-item.png)

  ![sys log added in server1](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/sys-log-item.png)

Screenshots of differnt metrics:

![image](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/cpu-idle-time-metrics.png)

![image](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/cpu-utilization-and-usage.png)

![image](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/disk-space-usage.png)

![image](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/disk-utilizatino-and-queue.png)

![image](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/memory-metrix.png)

![image](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/3/screenshot/system-loads.png)
