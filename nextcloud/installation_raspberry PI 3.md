# Installation tutorial for beginners
- quoted links are only for more detailed information in case you will find difficult to understand some of the bellow steps

# Recommended installation requirements
- what you will need: 

## Hardware:
- PC with slot for SD card and adapter for micro SD card
- Internet and local network
- Raspberry Pi 3 with Wifi and bluetooth
- Monitor or TV
- HDMI cable
- Keyboard /USB, bluetooth/
- Mouse /USB, bluetooth/
- Original power supply
- min 8 GB, preferentially 16 GB micro SD card /micro SD card format FAT32 needed to use bellow recomended NOOBS installer/
- [Raspberry Pi hardware setup](https://www.raspberrypi.org/learning/hardware-guide/quickstart/)

- external storage device HDD, SD with USB connection,
- read the manufacturer's documentation to ensure any hard drive you're using will work with the Raspberry Pi
- for more info:[External hard drives](https://www.raspberrypi.org/learning/hardware-guide/storage/)

## Software:
- [SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter_4/index.html) /Windows,MC OS/, Gparted /Linux/
- [Etcher software](https://etcher.io/) for burnnig images to SD cards & USB drives
- NOOBS installer,/New Out Of Box Software/ 
- Raspberry OS: Raspbian, included in NOOBS or as ISO Image 
- [Raspberry downloads page](https://www.raspberrypi.org/downloads/)
- for more details you can also visit: 
- [Raspberry software installation tutorial](https://www.raspberrypi.org/learning/software-guide/quickstart/)

- snapd, the service you need to install to run and manage snaps on Raspbian OS (based on Debian OS)
- [snappy Nextcloud](https://github.com/nextcloud/nextcloud-snap)

Nextcloud server packaged as a snap. It consists of:

    Nextcloud 12.0.4
    Apache 2.4
    PHP 7
    MySQL 5.7
    Redis 4.0
    mDNS for network discovery

All commands written in the form:
`xyz command` should be run from Terminal.

## Install Image following Raspberry tutorial on micro SD card
- copy paste / drag and drop unzipped NOOBS software on micro SD card or
- burn RASPBIAN ISO Image on micro SD card with Etcher software

- using NOOBS you'll have to select an operating system and let it install: choose and install RASPBIAN
- ones installation completed connect your Raspberry Pi to Internet

### Default user and sudo pasword on RASPBIAN OS:
- user: pi
- password: raspberry

### To get back during Raspberry Pi restart to NOOBS: press and hold down the left SHIFT key on your keyboard 

## Install snappy Nextcloud:
- first of all you should open Terminal for update and upgrade and free up space on your micro SD card:
- Run commands: `sudo apt-get update` , `sudo apt-get upgrade` ,`sudo apt-get clean`
- if you want to verify your space on an SD card:
- Run command: `df -h`

- install snapd tool service:
- Run command: `sudo apt install snapd`

- install latest snappy Nextcloud and snap permission to access removable media:
- Run command: `sudo snap install nextcloud`
- ones snappy Nextcloud installed allow permission to removable media:
- Run command: `sudo snap connect nextcloud:removable-media`

## User and password Nextcloud setup
- open Terminal and find your rasperry hostname address on your local network:
- Run command: `hostname -I`
- you should obtain something like this: 192.168. ..., or 10.0.1...
- open raspberry browser and insert your hostname address and press Enter
- you should see your login Nextcloud page
- create your user admin name and password 

## Apps installation
- recomended minimum beside the already installed and enabled apps by default:
- enable in settings following apps: Calendar, Contacts, External storage,Talk, Deck, ...  

## Troubleshooting
[TODO]
### 
```
