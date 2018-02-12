## CalDAV and CardDAV synchronization

- CalDAV and CardDAV are protocols to syncronize calendars and contacts with a remote server. Many email-hosters provide a CalDAV and CardDAV interface.

- use CalDAV Sync to set up the UT calendar app, all configuration it is based on 2 steps:

1. enable (if not done previously) on Nextcloud the Calendar app and click on the left side menu bar
- create + NEW calendar (if not done previously)
- at the bottom search for icon: Settings and Import
- select and copy the calendar Primary CalDAV URL address

2. open calendar app, click on the little calendar First icon in the top right corner and select “Add internet calendar > Generic CalDAV”. Enter your calendar URL as well as your username and password to complete the process.

- to synchorize your contacts with Ut device use CardDAV set up 

- at the moment, there is no carddav implemention directly accessible from the Ubuntu Touch graphical user-interface, so the only way to sync carddav is by using syncevolution + cron. However, there is a simple way to do that with a script that you can run in the terminal or via phablet SSH connection.

[TODO]
