Download the latest UPDATE file from https://downloads.lanturtle.com/

Verify that the MD5 checksums match

Manually SCP the file to the LAN Turtle in /tmp (ex: scp turtle-2.bin root@172.16.84.1:/tmp/)

From the LAN Turtle, exit shell to the bash prompt and issue: sysupgrade -n /tmp/turtle-2.bin

Wait about 5 minutes for the LAN Turtle to flash the firmware and reboot 
