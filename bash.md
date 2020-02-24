# Bash

[Back](README.md) to Linux Cheatsheets by Ireaneus

## To list all bash commands

```bash
[user@server1]$ Esc + y
```

## Executing bash scripts

```bash
#!/usr/bin/env bash
[user@server1]$ bash my.sh
[user@server1]$ chmod +x my.sh
[user@server1]$ ./my.sh
```

## To include a bash script in another bash script

```bash
# config.sh
USERNAME=$USER
EMAIL="username@example.com"

# main.sh
## #!/bin/bash
# Including config.sh, set filename with proper path.
source config.sh

echo Welcome ${USERNAME}!
echo Your email is ${EMAIL}.
```

## To implement a for loop

```bash
for file in [[ "ls -l * | wc -l" ]];
do
    echo $file found;
done
```

## To implement a case command:

```bash
case "$1"
in
    0) echo "zero found";;
    1) echo "one found";;
    2) echo "two found";;
    3*) echo "something beginning with 3 found";;
esac
```

## debugging

```bash
[user@server1]$ set -x	# turn on debugging
[user@server1]$ set +x	# turn off debugging
```

## Environment echo commands

```bash
[user@server1]$ echo $PATH $HOME $UID $(date) $USER

# Brace Expansion
[user@server1]$ echo {1..10..2}
1 3 5 7 9

[user@server1]$ echo {A..Z}
A B C D ..

[user@server1]$ echo a{A{1,2},B{3,4}}b
```

## Make parent directory
```bash
[user@server1]$ mkdir -p Projects/{docker,bash,ansible}
```

### bash cursor movements

| Command | Description |
| --- | --- |
| ctrl-a | Move to beginning of line |
| ctrl-e | Move to end of line |
| ctrl-f | Move forward one character |
| ctrl-b | Move backward one character |
| alt-f | Move forward one word |
| alt-b | Move backward one word |
| ctrl-l | clear screen and move to top left |
| ctrl-xx | Move between the beginning of the |
| | line, return to start of line and |
| | change something then back again |
| | |

## bash command replacement

```bash
[user@server1]$ ls anaconda-ks.cfg
[user@server1]$ vi !!:$

[user@server1]$ cp anaconda-ks.cfg anaconda-ks.bak
[user@server1]$ vi !^
vi anaconda-ks.cfg

[user@server1]$ !grep			# run the last grep command
```

### bash delete text

| Command | Description |
| --- | --- |
| ctrl-d | Delete character under the cursor |
| alt-d | Delete all characters after the cursor |
| ctrl-h | Delet the character before the cursor |
| | |

### Completion commands

| Command | Description |
| --- | --- |
| alt-? | Display list of possible combos |
| alt-* | Insert all possible completions |
| | |

### Declare statements

```bash
[user@server1]$ declare -i NEWVAR=123  			# Integer only
[user@server1]$ declare -r NEWVAR="this is readonly"
[user@server1]$ declare +i NEWVAR="string"
[user@server1]$ declare -p NEWVAR 			# print
```

### Export variables

```bash
[user@server1]$ MYVAR="value"
[user@server1]$ echo ${MYVAR}
value

[user@server1]$ echo 'echo ${MYVAR}' > echo.sh
[user@server1]$ chmod +x echo.sh
[user@server1]$ ./echo.sh
[user@server1]$ export MYVAR="value-exported"
[user@server1]$ ./echo.sh
value-exported
```

## bash alias

```bash
[user@server1]$ echo 'alias webstat="systemctl status httpd.service"' >> /home/user/.bashrc
```

## Running a remote script in bash

```bash
##### remote_check.sh #####
#!/bin/bash

##
# BASH script that checks the following:
#	- Memory usage
#	- CPU load
#	- Number of TCP connections
# 	- Kernel version
##

## 
# Memory check
##
server_name=$(hostname)

function memory_check() {
	echo "#######"
	echo "The current memory usage on ${server_name} is: "
	echo ""
	free -h
	echo "#######"
}

function cpu_check() {
	echo "#######"
	echo "The current CPU load on ${server_name} is: "
	echo ""
	uptime
	echo "#######"
}

function tcp_check() {
	echo "#######"
	echo "Total TCP connection on ${server_name}: "
	echo ""
	cat /proc/net/tcp | wc -l
	echo "#######"
}

function kernel_check() {
	echo "#######"
	echo "The exact Kernel version on ${server_name} is: "
	echo ""
	uname -r
	echo "#######"
}

function all_checks() {
	memory_check
	cpu_check
	tcp_check
	kernel_check
}

all_checks

##### remote_check.sh #####
```

## Running remote_check.sh on remote servers

```bash
[user@server1]$ for server in $(cat servers.txt) ; do ssh root@${server} 'bash -s' < ./remote_check.sh ; done
```
