# Challenge description   

**| That's a lot of layers... where does it even stop??** + a 'tar.gz' archive to download

## Solution

### ..*Extracting the archive
The first thing to do ofcourse is to extract the archive and see what does it contain, is it password protected or not:

``` Bash
    tar xvzf layerZzz.tar.gz
```
### ..*Enumerate the content of the archive

By extracting the archive we'll find a file 'message.txt' and a folder 'find_me/', the message file says the following:

Hello there challenger !
We're looking for a file which has a name that starts with "secret" and ends with b64 extension.
Can you **find** it ??
Flag format : shellmates{}

from here we know that we should find a file that starts with secret and ends with b64 extension. To do this we have two possible methods, the first one and the easiest is to use **find** command:
``` Bash
    find -name "secret*.b64"
```
or by using the **tree** command to view the hierarchy of the archive and find the directory of the file.

ps: the file name is **secret-dumpfile.b64** 

### ..*Decode and convert file 

Since the file is base 64 encoded, the normal thing to do is to decod it, and happily bash has our back:
``` Bash
    base64 -d secret-dumpfile.b64 > secretDump
```

after decoding the file it appears that it's the hexdump of a zip archive ( header : 50 4b ). Let's try to convert it now 
``` Bash
  xxd -r secretDump > secret 
```
after converting back the zip archive and extracting it, I have found an executable file called "nothing to see here", when you execute the file, it prints a message saying **" Nothing to see here 👀"**
so let's see whether the flag is embedded in the file's metadata since this is that last layer we could arrive to.

```Bash 
    strings nothing_to_see_here | grep "shell"
```

shellmates{CONGrATzZzz_U_d3FEa73d_a1l_Layer$!!!}
