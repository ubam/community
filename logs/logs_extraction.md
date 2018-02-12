## How to extract logs from your Ubuntu Device

- to report any bugs you find, when your device displays anomalous behaviour. 

## What are logs?

- logs are records of all system events. They are recorded in real time and they contain real-time information on how the system operates.
- they are a powerful tool to detect the precise moment at which the error took place, when the app or scope crashed, and so on.
- the information they provide is used to study the context of the bug, the factors which influence it, and how to stop it happening again.

## What do you need to extract logs from your device?

on your device:
- you need to enable Developer mode in order to access the device via adb, which is the method you will use to connect and extract the logs. You can find this mode at the following location: System settings > About this device > Developer mode (you must then activate it).
- you also need to have set some type of security code to lock the device.

on your PC:
- you need a package with the necessary tools (drivers adb, normally) in order to launch extraction commands. 
- Ubports recommends installing the following tools:

- Run command: `sudo add­-apt-­repository ppa:phablet-­team/tools`
- Run command: `sudo apt­-get update`
- Run command: `sudo apt-get install phablet-tools`

## Classifying the incident: What is the bug’s behaviour?

- to know which logs you need in each case, below listed extraction paths depending on the behaviour of the device. 
- this will make it easier to remember and deal with.

## the bug restarted the device, what type of restart was it?

- soft reboot: the session or app closes, and the Ubuntu Touch loading animation appears. In this case, select syslog, unity8 logs and crash logs.
- hard reboot: the device reboots completely and the white BQ or black Google welcome screen appears when the device is switched on. Select last logs.

##  the app shut down or freeze suddenly?

- select the logs of the app in question.
- select crash logs

## was the system directly affected?

- select syslog (this one is always essential)

## did it affect the graphical interface

- select unity8 logs

## does it affect the Wi-Fi connection?

- enable special Wi-Fi logs for the syslog and reproduce the bug:

- `sudo nmcli general logging level debug domains wifi,wifi_scan (enable logs)`
- `sudo nmcli general logging level info domains DEFAULT (disable logs)`

 ## does it affect Bluetooth?
 - select syslog
 
 - also enable special Bluetooth logs. [Go to this page to see how:](https://wiki.ubuntu.com/DebuggingBluetooth)

 ## Extraction routes

- syslog: /var/log/syslog
- unity8: /home/phablet/.cache/upstart/unity8.log
- /home/phablet/.cache/upstart/unity8-dash.log

- crash logs: /var/crash (in order for these logs to generate you need to activate Application crashes and errors at the following location: System settings > Security and privacy)
- last logs: /var/log/lastlog

- /proc/last_kmsg*
- application log : /home/phablet/.cache/upstart/*

Note: to verify the full route of the application which caused the bug, you can perform these steps:
- connect your device via USB with developer mode enabled
- open a terminal on a PC with Ubuntu and open an adb session with $ adb shell.
- list the content of the route: /home/phablet/.cache/upstart/
- copy the name of the app and add it to the end of the path. For example, if the gallery app crashed, the full path would be:

 - Run command: 
 - `sudo adb pull /home/phablet/.cache/upstart/application-click-com.ubuntu.gallery_gallery_2.9.1.1260.log.1.gz`

Every time you want to report a bug which is easy to reproduce, it is recommended that you delete previous logs relating to the bug in question. This will avoid confusing Ubports and make it easier for them to identify the bug.  To delete old logs, you can launch a command like the one below in a shell session with your Ubuntu PC or from the Terminal app:

- Run command: `sudo rm <route where logs are stored>`

Once deleted, you can reproduce the bug and then extract the logs. 
This will make the bug much easier to find (as the syslog logs events in chronological order) and the file will be much smaller when you upload it to GitHub.
If you include the time at which you reproduced the bug in the logs that you upload, you will make life much easier for Ubports.

## Extracting logs

- once you have reproduced the bug, connect your USB to the computer to extract the files. 
- the basic command to use is the following:
- `sudo adb pull <extraction route> <destination route>`

For example:
- sudo adb pull /var/log/syslog /home/”Your user”/Downloads` 

This procedure will allow you to fully complete a bug report, with a description of the error and all of the evidence confirming the bug’s existence. 
All of this makes bugs easier to resolve, and the solution can then be included in future OTA updates.
