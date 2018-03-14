##Rebuilding a click file for an installed application

When installing an application from the Ubuntu store, the corresponding click package isn’t permanently saved on your phone. However, this post aims to show that is relatively easy to rebuild it.

Upon installation, all files from a click package are being extracted into a subdirectory of /opt/clicks.ubuntu.com/. (Yes, that means that you can view the source code of every QML app you have installed! :) ) This is what allows us to create a click package for the application using only the files on your phone.

I will demonstrate how to do this using my Forum Browser app as an example but please be cautious that you don’t violate any copyright when trying this with other apps. This tutorial is meant to be for educational purposes only.

Here you go:

First of all, install the respective application from the Ubuntu Store.
Then open a shell on your device, either using the terminal app or ADB.
Afterwards, copy the source code of the application to your home directory:

$ cp -r /opt/click.ubuntu.com/com.ubuntu.developer.nikwen.forum-app ~
The only file we need to care about separately is the manifest.json:

$ cd ~/com.ubuntu.developer.nikwen.forum-app/current
$ cp .click/info/com.ubuntu.developer.nikwen.forum-app.manifest manifest.json
$ cd ..
Now we can rebuild the click file:

$ click build current
That’s it. :)

You can install the click package using the following command:

$ pkcon install-local com.ubuntu.developer.nikwen.forum-app_0.3.1_all.click --allow-untrusted
Please note that our own click file won’t be signed with the official appstore certificate though, but that shouldn’t really bother anyone. ;)

Have fun!

source:http://nikwen.github.io/ubuntu/2016/02/05/rebuilding-a-click-file-for-an-installed-application.html
