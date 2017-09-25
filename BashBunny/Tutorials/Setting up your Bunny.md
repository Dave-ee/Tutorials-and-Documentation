## Setting up your new Bash Bunny
###### Author: Dave-ee Jones
###### Subject: Bash Bunny

### DISCLAIMER:
This tutorial assumes you've just got your Bunny and are still on firmware 1.0 (comes with the Bunny).

So, you've just got your Bunny and you're ready to do some real pentesting, you shove a payload in a switch folder and nothing happens.
What's going on here?

Well, this tutorial is here to tell you that the Bunny needs to go through some setup steps first.

### First thing's first. Upgrade the firmware.
This step is fairly easy and can be done multiple ways. The most important thing to remember throughout this whole process is
**DO NOT UNPLUG THE BUNNY UNLESS TOLD TO DO SO**! Bad things happen otherwise.

###### Method 1: using the [Bash Bunny Updater](https://forums.hak5.org/topic/41583-beta-release-bash-bunny-updater/).
- For Windows users, this is the easiest option. Simply download the updater, extract the .ZIP file using your favourite ZIP extractor (I myself prefer 7Zip), then drag-and-drop the 'bashbunnyupdater.exe' file to the Bash Bunny's USB storage while it's in arming mode. From there, all you need to do is run it.
- For Linux users, the process is a bit different. Since Linux doesn't properly support FAT32 you cannot execute it by simply moving it to the USB storage of the Bunny and running it. [Sebkinne](https://forums.hak5.org/profile/17160-sebkinne/) advises that you should rename the updater to 'bunnyupdater.exe' and move it to the Bunny's USB storage, then run it. Alternatively, you can setup an environmental variable and run it from there.

The updater will download the required files once you have gotten through the CLI menu. Once the Bunny is flashing red **DO NOT UNPLUG IT!**
It will automatically restart once it is finished (~10-15m) and you'll be on the latest firmware.

###### Method 2: manually updating the Bunny.
This method is similar to method 1, in terms of downloading a file, dragging and dropping it to the Bunny in arming mode and watching the red button flash. 

Head over to the Bash Bunny Wiki's 'Downloads' section (found [here](https://wiki.bashbunny.com/#!downloads.md)), and download the latest firmware version (currently it is 1.3). Once you've downloaded the file, **make sure you compare the SHA256 checksums**. There have been multiple instances of broken Bunnies because of people trying to upgrade a broken firmware file. Once you've verified the file, drop it in your Bunny's USB storage partition while it's in arming mode. Once it has finished copying, **eject** the Bunny and unplug it. Plug it back in and then the Bunny should boot and start upgrading the firmware (red flashing). It should automatically reboot, so don't do anything with it **INCLUDING UNPLUGGING IT** until it has booted into arming mode and USB storage has popped up.

You can verify that the firmware upgrade was successful by checking the 'version.txt' file on the USB storage partition.

> **NOTE:** If either of these methods didn't work for you then please say so in the '[Issues](https://github.com/Dave-ee/Tutorials-and-Documentation/issues)' section or on the [forum post](https://forums.hak5.org/topic/41853-tutorials-and-documentation/)!

### Next thing's next. Grab the newest version of the Payloads library!

The Github repo for the Bash Bunny can be found [here](https://github.com/hak5/bashbunny-payloads/tree/master/).

Navigate to the 'payloads/library/' folder. This is the folder that you need to move to your Bunny's 'payloads/library/' folder,
but to do that you first need to download the whole .ZIP of the repo (sad, I know..). So, download the .ZIP of the repo and extract it. Copy the whole 'payloads' folder (make sure you're current switch folders are backed up!) to your Bunny's 'payloads' folder, giving you the whole library and extensions with it.

Now that you've got your library updated you can choose what payloads you want, when you want. 

### Good luck and have fun using your new Bunny! If you have any questions, be sure to ask at the Bash Bunny [subforum](https://forums.hak5.org/forum/92-bash-bunny/) or refer to the [Bash Bunny Wiki](https://wiki.bashbunny.com/#!index.md)!
