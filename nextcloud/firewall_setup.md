## Firewall setup
- to install firewall run command: `sudo apt-get update` and `sudo apt-get install ufw`
- to check current status of firewall run command: `sudo ufw status`
- to enable firewall run command: `sudo ufw enable`
- to disable firewall run command: `sudo ufw disable`
- allow port 20 to acces RASPBIAN Terminal by ssh and port 80 to acces Nextcloud from your local network 
- to open a port (SSH in this example): `sudo ufw allow 80`
- to close opened port (SSH in this example): `sudo ufw deny 80`
- to remove a rule, use delete followed by the rule: `sudo ufw delete deny 80`

## Firewall Remote Desktop RDP setup
- allow port 3350 and 3389 to acces RASPBIAN desktop on your local network and install xrdp client
- to open a port (SSH in this example): `sudo ufw allow 3350`and `sudo ufw allow 3389`
- to install xrdp run command on RASPBIAN Terminal: `sudo apt-get install xrdp` and restart your Raspberry PI
- make sure installed xrdp client is running: `sudo service xrdp status` 
- for your IP address to insert in your Remmina RDP client installed on your PC run on RASPBIAN OS Terminal:`hostname -I`
- remember the default RASPBIAN username is: pi and the password: raspberry 
- verify that you are entering correctly your password, each letter, because of the keyboard layout possible changes

[TODO]
