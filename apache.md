# Apache

- 3 Ways to Check Apache Server Status and Uptime in Linux:

[https://www.tecmint.com/check-apache-httpd-status-and-uptime-in-linux/](https://www.tecmint.com/check-apache-httpd-status-and-uptime-in-linux/)

- How to setup free SSL certificate for Apache on Debian 10

[https://www.tecmint.com/setup-free-ssl-certificate-for-apache-on-debian-10/](https://www.tecmint.com/setup-free-ssl-certificate-for-apache-on-debian-10/)

```bash
[user@server1]$ sudo systemctl status apache2    # Debian/Ubuntu
[user@server1]$ systemctl status httpd     # RHEL/CentOS/Fedora
```

- Apachectl Utilities

```bash
[user@server1]$ sudo vi /etc/apache2/mods-enabled/status.conf
```

```config
	<Location /server-status>
		SetHandler server-status
		Require local
		# Require ip 192.0.2.0/24
	</Location>
```

```bash
[user@server1]$ vi /etc/httpd/conf.d/server-status.conf
```

```config
	<Location "/server-status">
		SetHandler server-status
		#Require  host  localhost uncomment to only allow requests from localhost
	</Location>
```

```bash
[user@server1]$ systemctl restart httpd

[user@server1]$ apachectl status
http://localhost/server-status

[user@server1]$ ps -eo comm,etime,user | grep root | grep httpd
```

---

# 📄 Apache Log Rotation with `logrotate`

This guide explains how to safely rotate Apache application logs using `logrotate` with the `copytruncate` option, **without restarting the Apache service**.

---

## 🔧 Configuration: `/etc/logrotate.d/apache`

```conf
/path/to/HTTPServer/logs/*.log {
    daily                 # Rotate logs daily
    rotate 14             # Keep 14 old log files
    compress              # Compress rotated logs
    delaycompress         # Delay compression until next rotation
    missingok             # Ignore if file is missing
    notifempty            # Skip if file is empty
    copytruncate          # Copy and truncate in-place (no restart needed)
    create 644 apache apache  # Set file mode and ownership
}
```

> 💡 Replace `/path/to/HTTPServer/logs` with your actual Apache logs path.

---

## 🛠️ How `copytruncate` Works

- Copies the log file to a new file.
- Truncates the original log file to zero bytes.
- Keeps the Apache process writing to the same file descriptor.
- **No need to restart Apache**.

---

## ⚠️ Limitations of `copytruncate`

- Small chance of **data loss** if writing occurs during truncation.
- Not ideal for **high-frequency logging environments**.

---

## ✅ Best Use Case

Apache HTTP Server, especially when:
- Restarting the service is not feasible.
- Log files are not written extremely rapidly.

---

## 🧪 Test Your Setup

To test your logrotate config:
```bash
sudo logrotate -f /etc/logrotate.d/apache
```

To see logs being rotated and compressed:
```bash
ls -lh /path/to/HTTPServer/logs/
```

---

## 🔁 Optional: Automate via Cron

Logrotate typically runs daily via `/etc/cron.daily/logrotate`.

---

# ✅ Summary

| Setting         | Purpose                            |
|----------------|------------------------------------|
| `copytruncate` | Rotate logs without restart        |
| `rotate 14`    | Retain logs for 14 rotations       |
| `compress`     | Save space on older logs           |
| `notifempty`   | Avoid rotating empty logs          |

Keep your Apache log rotation safe, efficient, and downtime-free.

---

**Suggestions:**
**a.** Add `size` directive to rotate based on file size, e.g. `size 100M`.
**b.** Include log archiving to external storage or S3 as next step.

