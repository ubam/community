Mateo Salta Ubuntu Touch app in development:
[Nextcloud Ogra](https://github.com/mateosalta/nextcloud_ogra)

SSH conect from Ubuntu Touch
You can use SSH to connect to your Raspberry Pi from a Linux computer, or Ubuntu Touch, without installing additional software.
If you are running the Pi without a screen (headless), you can also look at the device list on your router or use a tool like nmap.

To connect to your Pi from a different computer, copy and paste the following command into the terminal window but replace <IP> including the bracket with the IP address of the Raspberry Pi. Use Ctrl + Shift + V to paste in the terminal.

ssh pi@<IP>

If you receive a connection timed out error it is likely that you have entered the wrong IP address for the Raspberry Pi.

When the connection works you will see a security/authenticity warning. Type yes to continue. You will only see this warning the first time you connect.

In the event your Pi has taken the IP address of a device to which your computer has connected before (even if this was on another network), you may be given a warning and asked to clear the record from your list of known devices. Following this instruction and trying the ssh command again should be successful.

Next you will be prompted for the password for the pi login: on Raspbian the default password is raspberry. You should now be able to see the Raspberry Pi prompt, which will be identical to the one found on the Raspberry Pi itself.

If you have set up another user on the Raspberry Pi, you can connect to it in the same way, replacing the username with your own, e.g. eben@192.168.1.5

pi@raspberrypi ~ $

You are now connected to the Pi remotely, and can execute commands.


[TODO]
