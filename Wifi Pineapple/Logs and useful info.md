#log locations on the pineapples are a little spread out so these terminal commands can be 
#useful to find information and issues and give clues to solving them.

dmesg
#Used to find kernel & hardware information for the system.

logread 
#replaces syslogd on the OpenWRT operating system. Can be used to find lots of useful log information

#Examples -

#Find pineapple type
dmesg | grep machine

#See all ssh logins
logread | grep "auth.info ssh"
