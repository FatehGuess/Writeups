# Challenge description

**| Speed is the way to go.
    Connect with: ssh -p 6003 ctf@linux.ctf.microclub.net
    Password : ctf**
    
## Solution 

by doing some enumeration you can find a python script **read.py** which we can run as ctf-cracked, this script will create a file in the **/tmp** directory and write the flag in it,then delete the file at the end.
```Bash
  sudo -u ctf-cracked /challenge/read.py
```
so to find the flag we have to read the file **A_flag_that_you_can't_catch**, the creative way to do it is to open a new session and keep reading the file while the python script is running. Here's a script to do it:

```Python
while True:
	print(open("/tmp/A_flag_that_you_can't_catch").read())

```
you can be more creative with the script for example checking whether the file is empty or not to know when to quit.

the flag : shellmates{83C4r3FU11WH3NY0UD341W17H71M317C4N76377r1CKY}
