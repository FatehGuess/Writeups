# Challenge Description

 **Our Club's designer -Bob- was acting weird past days.. Our HR team finds out that he was 'somehow' hiding some secrets in our Github repository! but they cannot find anything! just some Logos and a page cover, after i called Bob to meet him asap he said:" hey Boss, i'm so sorry.. it is snowing outside! So i'm going For Skiing, i can't miss this chance! the most important thing in skiing is you have to be having fun. If you’re having fun, then everything else will come easy to you. Call ended"

    | ouff... i can't wait.. so i want you to catch him! i'm wondering how a designer could hide a secret!.**
    
    
 ## Solution
 
 ### 1. Finding the password of the rar archive
 The rar archive contain multiple image files, each of them is protected with a password. Only the readme.md file is open and readable. This file contain a braille ciphetext:
 
 ```
    ⠏⠺⠙⠒⠀⠧⠥⠇⠥⠭⠙⠎⠞⠛⠓⠼⠓⠼⠃⠁⠎⠎⠙⠍⠼⠊⠕⠥⠏⠁⠵⠊
 ```
 
 once this cipher is decoded we obtain the following : 
 ```
    PWD : VULUXDSTGH82ASSDM9OUPAZI
 
 ```
 which appears to be the password of the archive.
 
 ### 2. Extracting embedded data
 
I tried several tools to extract data but using binwalk ``` binwalk -e cover.jpg ``` I've found a hidden file in the **cover.jpg**, the file name is **My Quotes.txt**. As it's name indicate, the file contains a quote talking about snow.
Could mentioning snow & skiing be a clue to the tool used ? since we all know that **stegsnow** is a stegano tool that hides data in a whitespace format, and that's what we are looking at, lot of whitespaces. Well, Let's see! 
```
    stegsnow -C "My Quotes.txt"
```
The data extracted is weired, so there should be a passphrase hidden.

### 3. Fiding the passphrase 

Since bob is a designer, we should play on the contrasts,lighting etc and see .. (the idea came to my mind when I re-read the challenge description, luckily **cover.jpg** hides all needed data the passphrase is **shellmates**

let's now re-try to extract the hidden data from my quotes.txt

```
    stegsnow -C -p "Shellmates" "My Quotes.txt"
```

Bingo the flag is: shellmates{sn0w_is_th3_wint3r_v3rsi0n_0f_st3g4n0}


