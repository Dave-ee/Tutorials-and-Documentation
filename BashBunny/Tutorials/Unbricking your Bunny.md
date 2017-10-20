## Unbricking your Bunny
###### Author: [Just_a_User](https://forums.hak5.org/profile/53001-just_a_user/)
###### Subject: Bash Bunny
###### [Forum post](https://forums.hak5.org/topic/42021-unbrick-bashbunny-method-not-guaranteed/)

### DISCLAIMER:
This is not guaranteed; it may unbrick your bunny, it may not. **Read the instructions fully before attempting this procedure**.

### ISSUE TO BE FIXED:
User copied firmware file to Bunny storage directory with an incorrect name (e.g. still has (1) at the end of the filename).

### SYMPTOMS:
1. Bash Bunny gets stuck in an infinite update loop
2. Bash Bunny lights up with a green LED on boot but then does nothing and gets very hot (CPU maxed out)

### INSTRUCTIONS:
Firstly, we should revert the Bash Bunny to the initial firmware, 1.0. To do this, select switch 3 (closest to the male end of the USB) and insert the Bunny, pulling it out immediately after the green LED turns off. Do this 3 times, but don't do it a 4th just yet.

Before we plug the Bunny back in for the 4th time, we must know what's about to happen and what we should do. It will light up with the normal flashing process (police-flashing LED or just a red flashing LED) and after this is will reboot, lighting up with a green LED. When it does this we must unplug it as soon as it lights up green. This will stop a retry of the update process.

So, with that in mind, plug the Bunny in a 4th time and do as stated above.

Your Bunny should now be unplugged and should also have firmware 1.0 on it. Before we plug it back in we should keep in mind that it will only attempt to update if your Bunny is in arming mode. So, all we need to do is put the Bunny in another switch position (anything other than 3) and plug it in. Once it's completely booted you should be able to access the Bunny via serial.

Once you've logged on with the default serial creds ('root' is the username, 'hak5bunny' is the password) you can type these following commands:
```sh
cd
mount /dev/nandf udisk
cd udisk
ls
```
What we just did above was tell the Bunny to enable the USB storage partition without telling Windows to mount it.
The output we should get at the end of this should look like:
```sh
Files                      config.txt  loot        tools
System Volume Information  docs        payloads    version.txt
ch_fw_1.3_264 (1).tar.gz   languages   readme.txt  win7-win8-cdc-acm.inf
```
Notice the firmware file: ``ch_fw_1.3_264 (1).tar.gz``
Then type the following to remove the firmware file:
```sh
rm 'ch_fw_1.3_264 (1).tar.gz'
ls
```
Now the output should show the file is gone. From here you can unplug the Bunny, set the switch to 3 and re-insert the Bash Bunny. You should notice that the Bunny has booted with STORAGE mode active, allowing Windows (or whichever OS) to access the filesystem.

Congratulations! Your Bunny is now unbricked!

### IF THIS PROCEDURE DOESN'T FIX YOUR BUNNY THEN YOU MORE THAN LIKELY HAVE A DIFFERENT ISSUE CAUSING YOUR BRICKED BUNNY. IF YOU HAVE NOT ALREADY DONE SO, CONTACT HAK5 SUPPORT!
