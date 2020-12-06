# ServiceCreator
Script that allows quickly creating, enabling and starting linux unit files for services

Just run the script as root, it will prompt you for all the neccessary information.

Currenty, only service files can be created.

## Installation
the following two commands need to be run in order to run the script anywhere
```
sudo wget "https://raw.githubusercontent.com/dakhnod/ServiceCreator/master/servicecreator" -O /usr/bin/servicecreator
sudo chmod 744 /usr/bin/servicecreator
```

## Example
This is how a test invokation looked like:
```
root@home:~# servicecreator
service name (single word): example
executable path and parameters: /bin/true -parameter1
Decription: Example service with no purpose
enable (run at boot)? (yes/no): yes
start service? (yes/no): yes
restart (on error) (always/no): no
unit file:

[Unit]
Description=Example service with no purpose

[Service]
Restart=no
ExecStart=/bin/true -parameter1
RestartSec=1

[Install]
WantedBy=multi-user.target

saving to /etc/systemd/system/example.service
open system file for editing? (yes/no):no
reloading daemon files
enabling unit file
restarting service
● example.service - Example service with no purpose
   Loaded: loaded (/etc/systemd/system/example.service; enabled; vendor preset: enabled)
   Active: inactive (dead) since Sun 2020-12-06 04:27:35 CET; 19ms ago
  Process: 14989 ExecStart=/bin/true -parameter1 (code=exited, status=0/SUCCESS)
 Main PID: 14989 (code=exited, status=0/SUCCESS)

Dez 06 04:27:35 home systemd[1]: Started Example service with no purpose.
Dez 06 04:27:35 home systemd[1]: example.service: Succeeded.
root@home:~#

```
