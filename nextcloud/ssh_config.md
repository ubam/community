## SHH configuration
- go to Preferences - Raspberry Pi Configuration - and Enable SSH interfaces
- by default it is openned port 22
- if you prefer you can do so also with Terminal commands
- open Terminal to verify the SSH service status:
- Run command: `sudo service ssh status` and `hostname -I`
- in case it is not enabled:
- Run command: `sudo systemctl enable ssh` and `sudo systemctl start ssh`
- and again:  `sudo service ssh status` and `ssh localhost`
[TODO]
