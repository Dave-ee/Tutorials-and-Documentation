## WabbitWeb usage
###### Author: Dave-ee Jones
###### Payload Github: [Link](https://github.com/Dave-ee/WabbitWeb)
###### Forum thread: [Link](https://forums.hak5.org/index.php?/topic/40941-payload-wabbitweb/)

**Category: Tool/General
Target: Windows 7+
Attackmodes: ETHERNET (default: RNDIS), HID**

### LED Configuration
| STATE  | COLOUR      | ACTION                                  |
| ------ | ----------- | --------------------------------------- |
| SETUP  | M (SOLID)   | Performing checks                       |
| FAIL2  | R (FAST)    | Directory 'ww' not found                |
| FAIL3  | R (VFAST)   | Failed to mount directory 'mfs'         |
| STAGE1 | Y (SINGLE)  | Starting webserver/attackmode           |
| NONE   | B (SOLID)   | Payload started                         |
| NONE   | B (SLOW     | Webserver started/Waiting for commands  |
| FAIL1  | R (SLOW)    | Impacket wasn't found                   |
| NONE   | C (SOLID)   | SMB server launching                    |
| NONE   | C (SLOW)    | SMB server running/Waiting for commands |
| NONE   | G (SOLID)   | Shutdown sequence initiated             |
| FINISH | G (SUCCESS) | Shutdown sequence finished              |
| NONE   | NO COLOUR   | Payload complete                        |
