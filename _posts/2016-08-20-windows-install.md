---
layout: post
title: "Windows: Postgres 9.5 install"
date: 2016-08-20 20:08:06
categories: Intro to SQL, GDIRDU
---

#### Postgres 9.5 install for GDIRDU Intro to SQL

* Download the [installer for Version 9.5.4](http://www.enterprisedb.com/products-services-training/pgdownload#windows).
* If you're not sure which installer you need, open System Information (Windows 10) or Control Panel > System and Security > System (Windows 8) and look for an entry in System Summary titled System Type. If the entry is "x86-based PC", download the 32-bit installer. If it is "x64-based PC", download the 64-bit installer. 
* Once the download is complete, click Run
* You may be asked whether you want to allow changes to your machine; click Yes
* Proceed through installer. Accept defaults. Set the superuser password to 'admin' (or something else you will remember!) 
* You will have the option to launch Stack Builder after install. You don't need to do this.
* Find "SQL Shell (psql)" in the Start menu or by searching for it.
* Click enter to accept defaults for Server, Database, Port, and Username. When you see the prompt `Password for user postgres`, enter the superuser password.

Once you have entered the password, you should see something like:

    psql (9.5.4)
    [Possibly a warning like "Console code page differs from Windows code page"]
    Type "help" for help. 
    
    postgres=#

You may exit by typing `\q`, then Enter.
