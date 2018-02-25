## Synchronization between Ubuntu Touch and Nextcloud

To automatically syncronize your Ubuntu Touch directories and data (photos, files, or backup) with another device like is your Raspberry Pi. In this case Nextcloud on your Raspberry Pi you will need, at the moment, to install on your Ubuntu Touch Syncthing app from OpenStore and also the same package app on your Raspberry Pi. 

Your Raspberry Pi it is an ARM achitecture and it is based on Debian. To install the stable channel version just copy bellow commands and run them on Raspberry Pi terminal:

Add the release PGP keys:
- `curl -s https://syncthing.net/release-key.txt | sudo apt-key add -`

Add the "stable" channel to your APT sources:
- `echo "deb https://apt.syncthing.net/ syncthing stable" | sudo tee /etc/apt/sources.list.d/syncthing.list`

Update and install syncthing:
- `sudo apt-get update`
- `sudo apt-get install syncthing`

- for more information, errors or candidate channel visit: https://apt.syncthing.net/
- another linux distributions packages: https://syncthing.net/ 

## Setting up Syncthing on Raspberry PI and Ubuntu Touch device

First of all we need to run the syncthing package on your Raspberry PI. Open your browser and go to admin GUI that remains available on https://localhost:8384/. Cookies are essential to the correct functioning of the GUI; please ensure your browser accepts them.

Once opened you will see on the left side the default list of “folders”, or directories to synchronize. The default folder was created for you, and it’s currently marked “Unshared” since it’s not yet shared with any other device. On the right side you will see the list of devices. Currently there is only one device: the Raspberry Pi in our case we are running this on.

For Syncthing to be able to synchronize files with another device, it must be told about that device. This is accomplished by exchanging “device IDs”. A device ID is a unique, cryptographically-secure identifier that is generated as part of the key generation the first time you start Syncthing. It is printed in the log above, and you can see it in the web GUI by selecting the “gear menu” (top right) and “Show ID”.

Two devices will only connect and talk to each other if they are both configured with each other’s device ID. Since the configuration must be mutual for a connection to happen, device IDs don’t need to be kept secret. They are essentially part of the public key.

To get your two devices to talk to each other click “Add Device” at the bottom right on both, and enter the device ID of the other device. It means insert the ID of Ubuntu Touch device you will see when you will open the Syncthing app on Ubuntu Touch device as described above. You should also select the folder(s) that you want to share. By default the two devices share an empty directory. Adding files to the shared directory on either device will synchronize those files to the other side. 

In our case we want to share pherhaps our photos made with Ubuntu Touch camera as we want to backup them on our Raspberry PI Nextcloud with mounted external storage.
- ubuntu touch path: /home/phablet/Pictures/com.ubuntu.camera
- nextcloud path: /home/media/pi/... name of the media/...name of your directory you want to share, backup in

This way you can do also with other Ubuntu Touch directories. The device name is optional and purely cosmetic. It can be changed later if required. What it is very important it is the directory ID name: it has to be the same for both above devices directory path: let us call it pherhaps: 'photos_ut' 

Once you click “Save” the new device will appear on right side of the GUI (although disconnected) and a prompt will be shown to indicate the need for a restart.

Syncthing needs to be restarted for some configuration changes to take effect, such as sharing folders with new devices. When you click “Restart” Syncthing will first restart: …and then connect to the new device after a minute or so. Remember to repeat this step for the other device.

Each device scans for changes every 60 seconds, so changes can take a little over a minute to propagate to the other side, although some contributed wrappers include file system “watcher” features to speed this up. The rescan interval can be changed for each folder by clicking on a folder, clicking “Edit” and entering a new value for “Rescan Interval”.

Don’t forget that configuration changes will not be reflected instantly - give Syncthing a little time, especially after a restart.

Keep Syntching running on Raspberry PI: keep open the browser admin GUI on https://localhost:8384/ this way always when you will reopen your app on Ubuntu Touch it will automatically syncronize both directories. In case of any restart of Rasperry PI just go to Raspberry top left icon and select RUN option, type: syncthing and press button return on your keyboard. Than select on admin GUI: rescan.  

- for more information about Syncthing visit: https://syncthing.net/
- for documentation, getting started guide download: https://docs.syncthing.net/intro/getting-started.html
