## Synchronization between Ubuntu Touch and Nextcloud

To automatically syncronize your data, folders with another device like is your raspberrypi you will need at the moment to install on your Ubuntu Touch Synctching app from OpenStore and also the same app on your raspberrypi. 

Your raspberrypi it is an ARM achitecture and it is based on Debian. This makes the installation on your raspberrypi much easier. To install the stable version just follow bellow commands for stable channel on raspberrypi terminal:

Add the release PGP keys:
- `curl -s https://syncthing.net/release-key.txt | sudo apt-key add -`

Add the "stable" channel to your APT sources:
- `echo "deb https://apt.syncthing.net/ syncthing stable" | sudo tee /etc/apt/sources.list.d/syncthing.list`

Update and install syncthing:
- `sudo apt-get update`
- `sudo apt-get install syncthing`

- for more information, errors or candidate channel visit: https://apt.syncthing.net/
- another linux distributions packages: https://syncthing.net/ 
## Setting up Synctching on Raspberry PI and Ubuntu Touch device

First of all we need to run the synctching package, you can do so directly on Raspebery PI Terminal, this will open your browser. 

[TODO]

- for more information about Synctching visit: https://syncthing.net/
- for documentation, getting started guiede download: https://docs.syncthing.net/intro/getting-started.html
