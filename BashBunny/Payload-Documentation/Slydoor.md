## Slydoor usage
###### Author: Dave-ee Jones
###### Payload Github: [Link](https://github.com/Dave-ee/Slydoor)
###### Forum thread: [Link](https://forums.hak5.org/topic/41049-payload-slydoor/)
###### Category: Code Execution
###### Target: Windows 7+
###### Attackmodes: HID, STORAGE

#### LED Configuration
| STATE  | COLOUR      | ACTION                                  |
| ------ | ----------- | --------------------------------------- |
| SETUP  | M (FAST)    | Setting up payload                      |
| FAIL2  | R (SLOW)    | Failed to load 'a.ps1'/mode.ps1 file    |
| FAIL3  | B (FAST)    | Starting attackmode                     |
| STAGE1 | C (Fast)    | Bypassing UAC (PowerShell run)          |
| NONE   | W (FAST)    | Waiting for script                      |
| NONE   | W (SUCCESS) | Payload complete                        |
| NONE   | NO COLOUR   | Bunny off                               |
