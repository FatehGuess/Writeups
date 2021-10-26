# Challenge Description

**| Oh no! we lost the first byte of this file!!
Can you still recover it?!**

## Solution

This one is pretty simple, Open the corrupted file with your favourite hex editor, I used an online hex editor **hexed**, by looking at what's normally second byte, and compare it with the known filetype headers I knew the missing byte was **1F** since it's the only one that matches. Add the missing byte and export it, you'll get a tar file, so extract it and **cat** the file ;)

shellmates{woW_YoU_RECOv3rEd_tHe_fIle!!}
