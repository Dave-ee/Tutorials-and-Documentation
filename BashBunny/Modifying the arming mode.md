## Modifying the arming mode
###### Author: Dave-ee Jones
###### Subject: Bash Bunny

### DISCLAIMER:
This can ruin your arming mode if you aren't careful! Make sure you know how ATTACKMODEs work.

So recently there have been people asking questions like "how do I boot RNDIS_ETHERNET attackmode when I plug the Bunny in arming 
mode?" or "how do I run a script when I plug my Bunny in with arming mode?". It's actually a very simple thing to do, if you know
where to go to do it.

### First, let's configure the arming payload.
Yes! There is an arming payload!
If you go to your Bash Bunny's USB storage (just stick your Bash Bunny in with the switch in arming mode) and go to the 'Payloads'
folder where you configure 'switch1' and 'switch2', you can create a folder there with the name 'arming'. This folder is looked
for everytime the Bash Bunny is booted in arming mode.

Go into the folder you just created and create a 'payload.txt' folder. From here, you should get the gist of where this is going.
**This 'arming/payload.txt' file overrides the arming mode, so be VERY careful with what you do in here!**

If you want your arming mode to run RNDIS_ETHERNET alongside STORAGE, you can put this in the 'payload.txt':
```sh
ATTACKMODE RNDIS_ETHERNET RNDIS_SPEED_10000 STORAGE
```

If you want it to write something in a log file everytime you boot the Bunny in arming mode, you can do something like this:
```sh
echo "Booted into arming mode. Again." >> log.txt
```

You can put anything you want - you could put a payload in the arming mode if you really wanted to, however I wouldn't recommend it,
as you may have to recover your Bunny if you can't access it's files with any of your 3 payloads.

Anyway, I hope this has quenched the questions regarding extending the arming mode!

## And now, resources!
- [Bash Bunny Wiki](https://wiki.bashbunny.com/#!index.md)
- [Changelog for fw1.3](https://storage.googleapis.com/bashbunny_updates/ch_fw_1.3-changelog.txt)
  - 'Arming' payload was introduced in this version
