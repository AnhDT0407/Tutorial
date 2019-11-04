# Install MySQL on Ubuntu

### 1: Update Ubuntu
The first thing you should always do is update your system. You can do so by running the following commands:

```java
apt-get update && apt-get upgrade
```

### 2: Install MySQL

```java
sudo apt-get install mysql-server
```

### 3: Testing MySQL
Regardless of how you installed it, MySQL should have started running automatically. To test this, check its status.

```java
systemctl status mysql.service
```

You'll see output similar to the following:

Output
```java
● mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: en
   Active: active (running) since Wed 2016-11-23 21:21:25 UTC; 30min ago
 Main PID: 3754 (mysqld)
    Tasks: 28
   Memory: 142.3M
      CPU: 1.994s
   CGroup: /system.slice/mysql.service
           └─3754 /usr/sbin/mysqld
```

If MySQL isn't running, you can start it with `sudo systemctl start mysql`.

### To log in to MySQL as the root user:

```java
mysql -u root -p
```

For an additional check, you can try connecting to the database using the `mysqladmin` tool, which is a client that lets you run administrative commands. For example, this command says to connect to MySQL as root (`-u root`), prompt for a password (`-p`), and return the version.

```java
mysqladmin -p -u root version
```
You should see output similar to this:

Output
```java
mysqladmin  Ver 8.42 Distrib 5.7.16, for Linux on x86_64
Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Server version      5.7.16-0ubuntu0.16.04.1
Protocol version    10
Connection      Localhost via UNIX socket
UNIX socket     /var/run/mysqld/mysqld.sock
Uptime:         30 min 54 sec

Threads: 1  Questions: 12  Slow queries: 0  Opens: 115  Flush tables: 1  Open tables: 34  Queries per second avg: 0.006
```

This means MySQL is up and running.


## Reset the MySQL Root Password
If you forget your MySQL root password, it can be reset.

### 1. Stop the current MySQL server instance:
```java
sudo service mysql stop
```

### 2. Use dpkg to re-run the configuration process that MySQL goes through on first installation. You will again be asked to set a root password.
```java
sudo dpkg-reconfigure mysql-server-5.5
```

### 3. Then start MySQL:
```java
sudo service mysql start
```
You’ll now be able to log in again using `mysql -u root -p`.


Refer: [here](https://www.linode.com/docs/databases/mysql/install-mysql-on-ubuntu-14-04/)
