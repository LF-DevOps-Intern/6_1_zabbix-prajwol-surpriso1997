# Installation of zabbix server and its configurations:

These are the steps followed:

- Downloading zabbix's .deb file(for debian based distro) using `wget`:

```bash

wget https://repo.zabbix.com/zabbix/5.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_5.4-1+ubuntu20.04_all.deb
```

![downlaod zabbix](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/1/screenshot/download-zabbix-deb-file.png)

- Install zabbix with `dpkg -i` command:

```bash

dpkg -i zabbix-release_5.4-1+ubuntu20.04_all.deb
```

- Installing other dependencies for zabbix:

1. zabbix-mysql-server
2. zabbix-frontend-php
3. zabbix-apache-conf
4. zabbix-sql-scripts

```bash
Sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts

```

![isntall azbbix other pakckatge](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/1/screenshot/installing-zabbix's-server,mysql,apache,scripts.png)

- Mysql was already isntalled in the system prior to this assignment.
  Logged into mysql root user with :

```bash
mysql -uroot -p

```

- Created zabbix user, zabbix database and given priveleges to the zabbix user.

```sql
create database zabbix character set utf8 collate utf8_bin;

create user zabbix@localhost identified by 'Manish@1';

grant all privileges on zabbix.* to zabbix@localhost;

flush privileges;

quit;


```

![create zabbix db and user](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/1/screenshot/created-database-and-user-for-zabbix.png)

- located the dowloaded sql scripts to create tables for zabbix. The script file `create.sql.gz` was found in `/usr/share/doc/zabbox-sql-scripts/mysql` directory. The sql file was run with:

```bash
zcat /usr/share/doc/zabbix-server-mysql/create.sql.gz | mysql -uzabbix -p zabbix
```

![run sql commands](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/1/screenshot/run%20-create-sql%20-command.png)

- Edited and updated the `zabbix-server.conf` file located at `/etc/zabbix` and updated DBPassword field to the password of zabbix user created earlier.

![password](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/1/screenshot/set-db-password-in-zabbix-config.png)

- Eanaled and restarted `apache2` and `zabbix-server` services:

```bash
sudo systemctl enable apache2
sudo systemctl enable zabbix-server

sudo systemctl status apache2
sudo systemctl status zabbix-server


```

![zabbix server running](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/1/screenshot/zabbix-server-running.png)

![apache running](https://github.com/surpriso1997/6_1_ZABBIX-Prajwol/blob/main/1/screenshot/apach2-running.png)
