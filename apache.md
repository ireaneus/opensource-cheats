# Apache

[Back](README.md) to Linux CheatSheets by Ireaneus

### 3 Ways to Check Apache Server Status and Uptime in Linux

[https://www.tecmint.com/check-apache-httpd-status-and-uptime-in-linux/](https://www.tecmint.com/check-apache-httpd-status-and-uptime-in-linux/)

### How to setup free SSL certificate for Apache on Debian 10

[https://www.tecmint.com/setup-free-ssl-certificate-for-apache-on-debian-10/](https://www.tecmint.com/setup-free-ssl-certificate-for-apache-on-debian-10/)

```bash
[user@server1]$ sudo systemctl status apache2    # Debian/Ubuntu
[user@server1]$ systemctl status httpd     # RHEL/CentOS/Fedora
```

#### Apachectl Utilities

```bash
[user@server1]$ sudo vi /etc/apache2/mods-enabled/status.conf
	<Location /server-status>
		SetHandler server-status
		Require local
		# Require ip 192.0.2.0/24
	</Location>

[user@server1]$ vi /etc/httpd/conf.d/server-status.conf
	<Location "/server-status">
		SetHandler server-status
		#Require  host  localhost uncomment to only allow requests from localhost
	</Location>

[user@server1]$ systemctl restart httpd

[user@server1]$ apachectl status
http://localhost/server-status

[user@server1]$ ps -eo comm,etime,user | grep root | grep httpd
```
