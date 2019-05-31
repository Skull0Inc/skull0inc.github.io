---
layout: post
title: "Only copy files that don't exist to new destination folder"
description: "How to copy only new files without overwriting ones that already exist in Windows"
categories: [Files, Windows]
tags: [windows,command-line]
---

### Windows: Copying only files that do not already exist to a destination folder.

One day, I was copying 400+GB of data in Windows GUI(just drag and drop) copier and while switching between different windows; managed to accidentially close the copying window, therefore cancelling my operation. Yikes! I had waited one-and-a-half hours out of a two hour process. It was very frustrating as it was late at night, and didnt have another 2 hours to spare before getting to go to bed. Anyway did a bit of digging and managed to find this :

~~~ console
robocopy a:\sourcePath b:\destinationPath /E /XC /XN /XO
~~~

* /E - recursively copy sub-directories, including empty ones.
* /XC - excludes existing files with the same timestamp, but different file sizes. 
* /XN - excludes existing files newer than the copy in the destination directory . 
* /XO - excludes existing files older than the copy in the destination directory . 

> see robocopy /? for full list on options. All of the above /x* options would normally be overwritten.

So basically this utility was able to help me continue where the copying was cancelled and did so until completion and I was able to sleep
at a relatively decent time not too long past 2am.

