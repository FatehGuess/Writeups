# Challenge description   

**| This image is the only evidence we have, we need the hacker's location. 
    Note : the hacker's location is not the flag, dig more and you'll find a normal readable flag** 

## Solution

# Image Metadata

We have an image of a neon hacker, and we should find his location, with some reverse image researching you'de find tone of similar picture from different sources which won't lead us anywhere. So there next thing is to check the metadata informations and see whether there is an interesting information we could use:

``` Bash
    exiftool hacker.jpg
```

some of the informations we've got are the **GPS laptitude** and  **GPS Longtitude**, with those informations we can do some gps position lookup, using https://www.gps-coordinates.net/ for exemple. When searching for the gps location on google maps you'll find the flag.

shellmates{Good_JOb_d3t3cT1VE_H0Lm3s}

