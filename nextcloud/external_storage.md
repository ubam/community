## External Data storage and External storage

## External storage configuration
- connect your external storage to Raspberry Pi and ones it is detected open it
- copy the external storage adress you will see now in the top bar window of file browser something like this: ## /media/pi
- click on settings button in Nextcloud screen and select: Admin
- click on the left side menu on: external storage and paste the address inside second empty cell
- save with click on save symbol on the right side of the line behind the basket symbol (you may need scroll right the screen)
- click on Files symbol beside Nextcloud logo
- click on left menu line with External storages and select the Local file as Favorite

## Move your datastorage permanently to External drive in fstab

[TODO]

- possible issues:
- updating nextcloud with updater may crash the usb-device permanently mounted in fstab to a folder on external data storage.
- updating crash also creates problems with booting the PI as the usb is not able to get mounted
- solutions:

[TODO]

## Spin Down and Manage Hard Drive Power on Raspberry Pi
- tutorial source: https://www.htpcguides.com/spin-down-and-manage-hard-drive-power-on-raspberry-pi/
- on Linux systems you often have to configure power saving parameters for your hard drive manually
- most users wanting to manage hard drive power consumption on the Raspberry Pi may use hdparm, hd-idle or sdparm
- find out your device name on your Raspberry Pi, usually: /dev/sda, in case of multiple drivers also /dev/sdb ...
- update your repository list before installing:
- Run command: `sudo apt-get update`

## Install and Configure hdparm on Raspberry Pi
- Run command: `sudo apt-get install hdparm -y`
- Make sure your drive supports hd parm, modify bellow driver name in accordance to yours: sda,sdb,sdb1, ...
- Run command:  `sudo hdparm -y /dev/sda` or
                `sudo /usr/sbin/hdparm -y /dev/sda`

- there should appear bellow outpout indicating a successful standby command:
```
/dev/sda:
    issuing standby command
```
- If you see bellow output you will need to use hd-idle or sdparm tools instead of hdparm

```
/dev/sda:
    issuing standby command
    SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```

- Check if your drive supports write cache, run command:

- `sudo hdparm -I /dev/sda | grep 'Write cache'` or
- `sudo /usr/sbin/hdparm -I /dev/sda | grep 'Write cache'`

- If you see a * (asterix) then you are good to go.
```
*   Write cache
```
- If you don’t see a star (asterix) then write cache is not possible for your drive
```
    Write cache
```
- To make hdparm spindown the device you can use the -B flag Values between 1 and 127 allow spinning down of the hard drive
- Run command: `sudo hdparm -B127 /dev/sda`

- Time to make hdparm configurations permanent edit the configuration file
- Run command: `sudo nano /etc/hdparm.conf`

- The spindown_time value is multiplied by 5 and you have the total time in seconds
- So a value of 120 yields 10 minutes (120*5=600)
- enable write cache and spindown time by adding this text to the bottom of the file
```
/dev/sda {write_cache = on spindown_time = 120}
```
- Restart the hdparm service
- Run command: `sudo service hdparm restart`

## Install and Configure hd-idle on Raspberry Pi

- If hdparm didn’t work or you just would rather use hd-idle, remove hdparm
- Run command: `sudo apt-get remove hdparm -y`

- hd-idle uses a special system file for detecting disk activity, if it doesn’t exist it won’t work
- Run command: `cat /proc/diskstats`

- You should see some output including the lines below, if you get no such file or directory you cannot use hd-idle
```
   8       0 sda 342 0 2759 260 0 0 0 0 0 250 250
   8       1 sda1 102 0 815 90 0 0 0 0 0 80 80
```
- You have to build hd-idle so make sure you have compilation tools
- Run command: `sudo apt-get install build-essential fakeroot debhelper -y`

- Grab the hd-idle source
- Run command: `wget http://sourceforge.net/projects/hd-idle/files/hd-idle-1.05.tgz`

- Unpack hd-idle and enter the folder
- Run command: `tar -xvf hd-idle-1.05.tgz && cd hd-idle`

- Build the hd-idle package and install it
- Run command: `dpkg-buildpackage -rfakeroot` and `sudo dpkg -i ../hd-idle_*.deb`

- Double check hd-idle works with your hard drive
- Run command: `sudo hd-idle -i 0 -a sda -i 300 -d`

- You should see output like this
```
probing sda: reads: 2759, writes: 0
probing sda: reads: 2759, writes: 0
probing sda: reads: 2759, writes: 0
```
- Use Ctrl+C to stop hd-idle in the terminal
- Open the hd-idle configuration file to enable the service to automatically start and spin down drives
- Run command: `sudo nano /etc/default/hd-idle`

- Change this line to enable hd-idle
```
START_HD_IDLE=true
```
- Adjust this line to enable sleeping on the drive every 10 minutes (60 seconds * 10)
- `HD_IDLE_OPTS="-i 0 -a sda -i 600"`
- Ctrl+X, Y and Enter to save.

- Restart the service
- Run command: `sudo service hd-idle restart`
- By default hd-idle will spin down drives ever 10 minutes which should be sufficient for most users.

- If all else fails you can use sdparm

## Install and Configure sdparm on Raspberry Pi

- First remove hdparm and remove hd-idle
- Run command: `sudo apt-get remove hdparm -y` and `sudo dpkg -r hd-idle`

- Install sdparm
- Run command:`sudo apt-get install sdparm -y`

- Test sdparm works
- Run command: `sdparm --flexible --command=stop /dev/sda`

- You should see output like this
```
/dev/sda: ATA       FUJITSU MHW2160B  891F
```
- Listen carefully, if it starts spinning up again immediately then you are going to need to find another option. Some users have had success with autofs for mounting and using the eject command. If the hard drive stays stopped add the cronjob below.
- Now we can set up a cron job to ask the usb hard drive to spin down ever hour at 5 past. This will run as the root user. /dev/sda is typically the first hard drive but you may have others, you will have to add additional cronjobs for /dev/sdb or whatever else you find by using the blkid command.
- Run command: `sudo crontab -l | { cat; echo "5 * * * * sdparm --command=stop /dev/sda"; } | sudo crontab -`

- If youw ant to run the same cronjob every 10 minutes you would add a / before the number, so this example will spin the drive down every 10 minutes
- Run command: `sudo crontab -l | { cat; echo "/10 * * * * sdparm --command=stop /dev/sda"; } | sudo crontab -`

- Now your Raspberry Pi device will spin down your usb hard drive to save power and hopefully extend the life of your hard drive.
