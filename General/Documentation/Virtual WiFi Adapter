## Virtual WiFi Adapter for Windows - Usage and Configuration
###### Author: Dave-ee Jones

### DESCRIPTION:
The Virtual WiFi Adapter (A.K.A 'hostednetwork') is the adapter that allows Windows PCs to broadcast an SSID so that other devices can connect to a network.
Essentially it allows a PC to 'WiFi-boost' the network they're currently connected to.

### SETTING UP YOUR HOTSPOT
So, let's look at how one would set the SSID and password of a hotspot. Then we'll look at starting it. It's actually very simple.
First, open CMD (or PowerShell, if you prefer) by typing 'cmd' into the Windows Start Menu (or 'Run' program) and press 'Enter'.
You should see a black CMD box pop-up, waiting for you to type some magic. So, why don't we? Type this in:
```powershell
netsh wlan set hostednetwork ?
```
This will show us all the options we can set for the hotspot ('hostednetwork'). We'll start by changing the SSID.
```powershell
netsh wlan set ssid="Hotspot Test"
```
Now the SSID is 'Hotspot Test' (keep in mind the quotation marks will not show in the actual SSID). Now let's set a password.
```powershell
netsh wlan set key="pa55w0rd" keyUsage=persistent
```
Notice the 'keyUsage' paramter. This means that whenever you start the hotspot in future the password will carry over each time. If you don't set this the password will reset when the hotspot stops.
> **Note:** You can setup all parameters at once: `netsh wlan set hostednetwork mode=allow ssid="Hotspot Test" key="pa55w0rd"`
Now that we've setup the hotspot, let's enable it and start it.
```powershell
netsh wlan set hostednetwork mode=allow
netsh wlan start hostednetwork
```
Now if you look at nearby WiFi APs on your phone or another laptop/PC you might notice an SSID called "Hotspot Test". Try connecting to it with the password you set.
You should now be connected to the WiFi!

### CHANGING THE ADAPTER USED BY THE HOTSPOT
So you may have noticed that the adapter broadcasts the currently-connected network, and this may not work well for you in some cases. You might have a USB dongle plugged in for 4G and you might want to broadcast that over the WiFi instead so others can use it.
That's completely fine, and can be done, so don't worry!
The easiest way to do this is via a batch file. A batch file is a file that runs CMD script line-by-line, making it easier on us.

First thing's first. **Check what adapters are currently in use/connected and disable all but the one you want broadcasted**
So, I have 3 adapters in use:
- Local Area Connection (Ethernet)
- Wireless Network Connection (WiFi)
- USB Dongle (Ethernet USB)
So I need to disable LAC and WNC.
Let's open Notepad and type this in it:
```powershell
netsh interface set interface name="Wireless Network Connection" admin=disabled
netsh interface set interface name="Local Area Connection" admin=disabled
```
I just disabled both adapters. Next, I'll start the hostednetwork, which will automatically choose the USB dongle as the adapter.
Enter this into your Notepad file after the previous 2 lines:
```powershell
netsh wlan set hostednetwork mode=allow ssid="USB WiFi" key=password
netsh wlan start hostednetwork
```
Next, we'll re-enable the adapters we disabled earlier. This doesn't take over the WiFi hotspot, so the hotspot will still use the USB dongle. 
So put this in the Notepad file:
```powershell
netsh interface set interface name="Wireless Network Connection" admin=enabled
netsh interface set interface name="Local Area Connection" admin=enabled
```
Now you're Notepad file should look like this:
```powershell
netsh interface set interface name="Wireless Network Connection" admin=disabled
netsh interface set interface name="Local Area Connection" admin=disabled
netsh wlan set hostednetwork mode=allow ssid="USB WiFi" key=password
netsh wlan start hostednetwork
netsh interface set interface name="Wireless Network Connection" admin=enabled
netsh interface set interface name="Local Area Connection" admin=enabled
```
Save the file as 'USBHotspot.bat' or something along those lines, making sure it doesn't set it to 'USBHotspot.bat.txt', which won't work.
Run the file by clicking on it. If you wish to edit it, right-click on it and click 'Edit'. You should now notice that you're USB dongle is broadcasted on the 'USB WiFi' SSID.

### THAT'S ALL FOLKS!
