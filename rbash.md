# How to use Restricted Shell to limit user access to a Linux system:
# Can be used to login to a bastion host, then 
# ssh to internal systems.
# Bastion host is accessed externally or through vpn

`[user@server1]$ sudo useradd -m ruser -s /bin/rbash`

`[user@server1]$ sudo passwd ruser`

`[user@server1]$ sudo mkdir /home/ruser/bin`

`[user@server1]$ sudo ln -s /bin/mkdir /home/ruser/bin`

`[user@server1]$ sudo ln -s /bin/ls /home/ruser/bin`

`[user@server1]$ sudo ln -s /bin/ssh /home/ruser/bin`

`[user@server1]$ sudo chown root. /home/ruser/.profile`

`[user@server1]$ sudo chmod 755 /home/vega/.profile`

# Login as ruser:

```sh
[ruser@server1]$ cd /
cd / Permission denied
```
