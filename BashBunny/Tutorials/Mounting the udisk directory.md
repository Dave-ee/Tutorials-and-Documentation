## Mounting the 'udisk' directory
###### Author: Dave-ee Jones
###### Subject: Bash Bunny

### DISCLAIMER:
Requires firmware 1.2+.

Whenever you plug your Bunny with Storage and serial/ethernet, you might notice that when you SSH/serial into your Bunny your 
storage partition (/root/udisk) isn't mounted by default, essentially showing you an empty folder. Here's how you can show
what's actually in that folder. It's pretty easy, basically just a few commands.

The first thing (just to be on the safe side), is to go back to the roots:
```sh
cd /
```
The next thing we can do is mount the directory:
```sh
udisk mount
```
Now we can go to the folder and see how we went:
```sh
cd /root/udisk/
```
Draw all the contents of the folder:
```sh
ls
```
VOILA! There's the contents of your USB storage on the Bunny. Remember, if you do anything with the Bunny's storage you need to
sync the storage. You can do this by using this command (works in 'payload.txt's as well):
```sh
sync
```
