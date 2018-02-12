## OpenStore Nextcloud Ogra app

- Ubuntu Touch comes pre-installed with a set of solid core apps that cover your daily needs. This includes everything you expect from a phone, like a dialer, contacts and calendar, but since it's Linux, the OS comes with a fully-featured file browser and terminal as well.

- Ubuntu Touch was created to converge the worlds of mobile- and desktop-computing, and that's also true for its applications. All apps are created with convergence in mind and can automatically adapt to screens from the smallest phone to the biggest tablet, and even work in window-mode on the desktop.

- to acces your Nextcloud from Ubuntu Touch you will need to download and install from OpenStore web or directly from UT OpenStore app in your device Mateo Salta Ubuntu Touch [Nextcloud_Ogra app](https://open.uappexplorer.com/app/nextcloud.mateosalta). This app is still in development and for the latest information visit GitHub page [Nextcloud Ogra](https://github.com/ubam/nextcloud_ogra)

## SSH conect from Ubuntu Touch

- you can use SSH to connect to your Raspberry Pi from your  Ubuntu Touch using the default Terminal app  
- by default your UT device should have the SSH service installed. To make sure, you may check the service status
- Runn command: `service --status-all | grep ssh` 
- you should see ssh service listed, with one of 3 possible statuses, marked by a symbol in square bracket:

    [-] meaning that the service is not running
    [+] meaning that the service is running
    [?] was not possible to determine

- you can see that the ssh service is running (it has the [+] status). If this is also your case, then it means there is nothing for you to do. If it is not your case, then you should either enable the service, or install it. If ssh is installed, just not running, you can control it with the service command:

- to restart (will start it whether it's already running or not):
- Run command: `sudo service ssh restart`
- to start service:
- Run command: `sudo service ssh start`
- to stop service:
- Run command: `sudo service ssh stop`

- if you are running the Pi without a screen (headless), you can also look at the device list on your router or use a tool like nmap.

- to connect to your Pi from a different computer, copy and paste the following command into the terminal window but replace <IP> including the bracket with the IP address of the Raspberry Pi. 
- use Ctrl + Shift + V to paste in the terminal: `ssh pi@<IP>`

- if you receive a connection timed out error it is likely that you have entered the wrong IP address for the Raspberry Pi.

- when the connection works you will see a security/authenticity warning. Type YES to continue. You will only see this warning the first time you connect.

# Clear the record from your list of known devices

- in the event your Pi has taken the IP address of a device to which your computer has connected before (even if this was on another network), you may be given a warning and asked to clear the record from your list of known devices. Following this instruction and trying the ssh command again should be successful.

- next you will be prompted for the password for the pi login: on Raspbian the default password is raspberry. You should now be able to see the Raspberry Pi prompt, which will be identical to the one found on the Raspberry Pi itself.

- if you have set up another user on the Raspberry Pi, you can connect to it in the same way, replacing the username with your own, e.g. eben@192.168.1.5 or eben@10.0.1....

- you should see now: `pi@raspberrypi ~ $`
- you are now connected to the Pi remotely, and can execute commands

## SSH and Ubuntu Touch

- everything you want to ask but you are afraid to, visit [Kris Jacewicz](https://kriscode.blogspot.cz/2017/12/ssh-and-ubuntu-touch.html#SshOnUbuntuTouch) blog

[TODO]
