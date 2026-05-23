---
publish: true
title: Linux Challenges
created: 2020-02-01
modified: 2026-05-23T23:43:02.777+08:00
tags:
  - Security
  - Cloud
  - Try Hack Me
  - Beginner
---

I thought a good place to start would be to do some writeups of some basic Linux challenges. The way I will structure these posts is by first providing a list of fundamental knowledge that you will require to understand followed by a walkthrough of every challenge.

# Knowledge

I am within the assumption that you what Linux is, however if you don't; Linux is an operating system much like the similarly used Windows and MacOS. There are multiple methods to run Linux and this is either through a virtual machine or to downloaded it for your computer. A recommendation would be to use a distribution called [Ubuntu](https://ubuntu.com/#download) or use the [Kali Tool](https://www.kali.org/downloads/) for this challenge.

Specifically for this set of Linux challenge, there are a few commands that you should be comfortable with and these are:

- ls - Lists folders/files within your current directory (Folder you are currently in).
- cd - Change directory to a specified folder.
- cat - Show content of file within the command-line.
- vi - Text editor to make modifications of a file.
- grep - Search for keywords/regular expressions and print all matching lines.
- history - Show history of previous commands used.
- su - Substitute user which allows using certain privileges by authenticating as a different user.
- sudo - When required to use elevated privileges.
- ps - Show system processes
- tar - Used to compress/decompress files or quickly access a collection of files.

Some of these commands have flags (Command-line flags to specify options) to have a more advanced utility and it is recommended to research through using [Google](https://www.google.com) by typing the commands as listed above.

# Walkthrough

## Task 1 - Linux Challenges Introduction

### How many visible files can you see in Garry's home directory? <br/>

By typing "ls" within the command-line you can see the list of folders/files.

```
  ls
```

> flag1.txt flag24 flag29

This answer is self-explanatory. Just count the number of files. <br/>

**Answer:** 3

## Task 2 - The Basics

### Flag 1 <br/>

To read what is within flag 1, you will have to use a text editor. For this example, I will use VI.

```
  vi flag1.txt
```

> Flag 1: f40dc0cff080ad38a6ba9a1c2c038b2c
>
> Log into bobs account to get flag 2.
>
> Username: bob <br/>
> Password: linuxrules

Flag 1 is listed and the username and password for bob is required for the next flag. To exit out press the "Esc" key and type ":q!". <br/>

**Answer:** f40dc0cff080ad38a6ba9a1c2c038b2c

### Flag 2 <br/>

Log into bob's account using the credentials shown in flag 1 by using the following command:

```
  su -l bob
```

> Password: linuxrules

You are then prompted to type the password as shown in flag 1. After that you can determine the flag by using the same method through obtaining flag 1 or use an easier method using:

```
  cat flag2.txt
```

> Flag 2: 8e255dfa51c9cce67420d2386cede596

**Answer:** 8e255dfa51c9cce67420d2386cede596

### Flag 3 <br/>

Through using the "history" command, you can see the commands you have used. Flag 3 will be at the top of the history.

```
  history
```

> 1    9daf3281745c2d75fc6e992ccfdedfcd

**Answer:** 9daf3281745c2d75fc6e992ccfdedfcd

### Flag 4 <br/>

As stated within the challenge, we will be using crontab. Otherwise, the commands "cat" or "vi" will do the same.

```
  crontab -l
```

> Flag4: dcd5d1dcfac0578c99b7e7a6437827f3

**Answer:** dcd5d1dcfac0578c99b7e7a6437827f3

### Flag 5 <br/>

Using "grep" and the "-rnw" flag, you can find specific file names you want. It shows the location of the file.

```
  grep -rnw 'flag5'
```

> /lib/terminfo/E/flag5.txt

After knowing the location, use the "cat" command to find the contents within.

```
  cat /lib/terminfo/E/flag5.txt
```

> bd8f33216075e5ba07c9ed41261d1703

**Answer:** bd8f33216075e5ba07c9ed41261d1703

### Flag 6 <br/>

Similarly using "grep", find the location of flag 6.

```
  grep -rnw 'flag6'
```

> /home/flag6.txt

Here you are unable to "cat" as it contains other messages unrelated to the flag. Therefore you must use "grep" in conjunction with "cat". As stated within the challenge, we require to find "c9" and this will be highlighted within the text.

```
  cat /home/flag6.txt | grep c9
```

> c9e142a1e25b24a837b98db589b08be5

**Answer:** c9e142a1e25b24a837b98db589b08be5

### Flag 7 <br/>

To check the system processes you use the command "ps". Furthermore, using the flags "-aef" are necessary. After scrolling through the system processes, you can see a line containing flag 7.

```
  ps -aef
```

> root  1388  1 0 01:38 ? 00:00:00  flag7:274adb75b337307bd57807c005ee6358  1000000

**Answer:** 274adb75b337307bd57807c005ee6358

### Flag 8 <br/>

To decompress a "tar.gz" file we require to use the "tar" command with the flags "-xvf".

```
  tar -xvf flag8.tar.gz
```

> flag8.txt

Using "cat" command to read content.

```
  cat flag8.txt
```

> 75f5edb76fe98dd5fc9f577a3f5de9bc

**Answer:** 75f5edb76fe98dd5fc9f577a3f5de9bc

### Flag 9 <br/>

The host file is located within "/etc/hosts" on Linux machines. You can use "cat" to find the contents inside.

```
  cat /etc/hosts
```

> 127.0.0.0 dcf50ad844f9fe06339041ccc0d6e280.com

**Answer:** dcf50ad844f9fe06339041ccc0d6e280

### Flag 10 <br/>

To find all the users within the system, you can use the "/etc/passwd" file to see them (It does not tell the password of each user though as it requires a hash key). The flag will be shown under Bob's account.

```
  cat /etc/passwd
```

> bob:x:1001:1001:BOB,,,:/home/bob:/bin/bash <br/>
> 5e23deecfe3a7292970ee48ff1b6d00c:x:1002:1002:,,,:/home/5e23deecfe3a7292970ee48ff1b6d00c:/bin/bash

**Answer:** 5e23deecfe3a7292970ee48ff1b6d00c

## Task 3 - Linux Functionality

### Flag 11 <br/>

To find the flag, you are required to understand that each time you open the command-line interface (Called Bash on Linux); the ".bashrc" automatically runs with the set of commands contained within the file. The alias is a command that makes other commands more simple each time Bash is initiated and thus is also stored within the ".bashrc" file.

```
  cat .bashrc
```

> alias flag 11='echo "You need to look where the alias are created..."' b4ba05d85801f62c4c0d05d3a76432e0

**Answer:** b4ba05d85801f62c4c0d05d3a76432e0

### Flag 12 <br/>

The MOTD (Message of the Day), sends a common message to all the users when they log into the system. This file is normally located within "/etc/update-motd.d". The script however, is listed as "00-header" and therefore the command "cat" should be used on the file.

```
  cat /etc/update-motd.d/00-header
```

> Flag12: 01687f0c5e63382f1c9cc783ad44ff7f

**Answer:** 01687f0c5e63382f1c9cc783ad44ff7f

### Flag 13 <br/>

As flag 13 is a folder, we would change into the directory and list the file contents. Through using the commands:

```
  cd flag13
  ls
```

> script1 script2

As seen here, there are two files. To check the difference between the two files, we require to use the "diff" command followed by the two files that require checking.

```
  diff script1 script2
```

> Lightroller sees 3383f3771ba86b1ed9ab7fbf8abab531 Smith walking stiffly toward him and quickly goes to him. He yells into the Captain's ear, though cupped hands, over the roar of the steam...

**Answer:** 3383f3771ba86b1ed9ab7fbf8abab531

### Flag 14 <br/>

The log files are normally stored within "/var/log". First it is required to change into the directory and then "cat" the content from "flagtourteen.txt" (Yes, the file is spelt like that).

```
  cd /var/log
  ls
```

> apeche2 flagtourteen.txt  syslog

```
  cat flagtourteen.txt
```

> 71c3a8ad9752666275dadf62a93ef393

**Answer:** 71c3a8ad9752666275dadf62a93ef393

### Flag 15 <br/>

The system information can be found within the "/etc/\*release" file.

```
  cat /etc/*release
```

> FLAG\_15=a914945a4b2b5e934ae06ad6f9c6be45

**Answer:** a914945a4b2b5e934ae06ad6f9c6be45

### Flag 16 <br/>

To check system mounts, you are able to see it within "/media". This challenge required you to change directory (cd) multiple times until you can see the folder containing the actual flag.

```
  cd /media/f/l/a/g/1/6/is
  ls
```

> cab4b7cae33c87794d82efa1e7f834e6

**Answer:** cab4b7cae33c87794d82efa1e7f834e6

### Flag 17 <br/>

Similar to logging in as Bob, now you have Alice's account details. To login use the "su -l" command and type her corresponding password. After inside her account, we are then able to use the "cat" command to find flag 17.

```
  su -l alice
```

> Password: TryHackMe123

```
  cat flag17
```

> 89d7bce9d0bab49e11e194b54a601362

**Answer:** 89d7bce9d0bab49e11e194b54a601362

### Flag 18 <br/>

To list invisible folders/files you are required to use the "ls" command in conjunction with the "-a" flag.

```
  ls -a
```

> .. .bashrc  .flag18 flag22  .lesshst  .viminfo

```
  cat .flag18
```

> c6522bb26600d30254549b6574d2cef2

**Answer:** c6522bb26600d30254549b6574d2cef2

### Flag 19 <br/>

There are a few ways to find a specific line. Originally, I used the "head" command which shows all the lines up to a particular number.

```
  head -n 2345 flag19
```

> ... <br/>
> 490e69bd1bf3fc736cce9ff300653a3b

Through the hint, it said to use the "sed" command which shows the specified line.

```
  sed -n 2345p flag19
```

> 490e69bd1bf3fc736cce9ff300653a3b

**Answer:** 490e69bd1bf3fc736cce9ff300653a3b

## Task 4 - Data Representation, Strings and Permissions

### Flag 20 <br/>

Decode with base64

```
  base64 -d flag20
```

> 02b9aab8a29970db08ec77ae425f6e68

**Answer:** 02b9aab8a29970db08ec77ae425f6e68

### Flag 21 <br/>

```
  su -l bob
```

> Password: linuxrules

```
  less flag21.php
```

> \<?=\`\$ POST\[Flag21\_g00djob]\`?>\<?='MoreToThisFileThanYouThink';?>

**Answer:** g00djob

### Flag 22 <br/>

```
  su -l alice
```

> Password: TryHackMe123

"-r" converts hex into ascii
"-p" use plain format

```
  xxd -r -p flag22
```

> 9d1ae8d569c83e03d8a8f61568a0fa7d

**Answer:** 9d1ae8d569c83e03d8a8f61568a0fa7d

### Flag 23 <br/>

```
  rev flag23
```

> ea52970566f4c090a7348b033852bff5

**Answer:** ea52970566f4c090a7348b033852bff5

### Flag 24 <br/>

```
  su -l garry
```

> Password: letmein

```
  strings flag24
```

**Answer:** hidd3nStr1ng

### Flag 25 <br/>

Does not exist.

### Flag 26 <br/>

Unable to locate.

### Flag 27 <br/>

By running "sudo -l", you are able to see which user is able to access the root flag. In this case it states Alice is able to use Flag 27.

```
  su -l alice
```

> Password: TryHackMe123

```
  sudo cat /home/flag27
```

> 6fc0c805702baebb0ecc01ae9e5a0db5

**Answer:** 6fc0c805702baebb0ecc01ae9e5a0db5

### Flag 28 <br/>

To find the details of the computer software, "uname" command is used. You are able to use the "-a" flag to show all the details, or specifically use the "-r" flag to see the kernel version.

```
  uname -r
```

> 4.4.0-1075-aws

**Answer:** 4.4.0-1075-aws

### Flag 29 <br/>

This can be found if you remove all the spaces within the file. As stated in the question, it is the last element split by the comma.

```
  cat flag29 | tr -d ' '
```

> ,fastidiisuscipitmeaei.

**Answer:** fastidiisuscipitmeaei

## Task 5 - SQL, FTP, Groups and RDP

### Flag 30 <br/>

Through using curl, you want to collect files through the localhost.

```
  curl localhost
```

> flag30: fe74bb12fe03c5d8dfc245bdd1eae13f

**Answer:** fe74bb12fe03c5d8dfc245bdd1eae13f

### Flag 31 <br/>

Firstly, you have to login to mySQL to be able to have assess to the database name.

```
  mysql -u root -p
```

> Password: hello

After logging in, you issue the command to see all the database names:

```
  show databases;
```

> database\_2fb1cab13bf5f4d61de3555430c917f4

**Answer:** 2fb1cab13bf5f4d61de3555430c917f4

### Flag 31 (Bonus)

After finding the name of the database, you must now access it and read inside the contents.

```
  use database_2fb1cab13bf5f4d61de3555430c917f4
  show tables;
```

> | flags |

As you can see, the database only contains one set of data. To read inside, you use the command:

```
  select * from flags:
```

> |1| ee5954ee1d4d94d61c2f823d7b9d733c |

**Answer:** ee5954ee1d4d94d61c2f823d7b9d733c

### Flag 32

This flag is quite difficult. Firstly, you must log in as Alice.

```
  su -l alice
```

> Password: TryHackMe123

After logging in as Alice, we require to send the file "flag32.mp3" from her home directory. Use the "ls" command to ensure you can see the file. After making sure that it exist, we are then required to secure copy (scp command) through the use of SSH. It is assumed that you have connected to the "TryHackMe" server with OpenVPN already.

On Linux and Windows, you are able to find your username (Don't mistaken with computer name) with the command:

```
  whoami
```

Then to find your IP address, you use the command:

```
  LINUX:
    ifconfig
    OR
    ip a
  WINDOWS:
    ipconfig
```

In the command below, between the "<" and ">" you must replace it with your own details. This will save the file to your desktop.

```
  LINUX:
    scp flag32.mp3 <USERNAME>@<IP-ADDRESS>:/home/<USERNAME>/Desktop
  WINDOWS:
    scp flag32.mp3 <USERNAME>@<IP-ADDRESS>:/C:/Users/<USERNAME>/Desktop
```

> Password: <YOUR PASSWORD>

If it doesn't work, make sure SSH service is running on your computer. Finally you can open the file and listen what is in it.

**Answer:** tryhackme1337

### Flag 33

This flag is stored in Bob's directory.

```
  su -l bob
```

> Password: linuxrules

Then to see your profile, use the command:

```
  cat .profile
```

> #Flag 33: 547b6ceee3c5b997b625de99b044f5cf

**Answer:** 547b6ceee3c5b997b625de99b044f5cf

### Flag 34

To list all the system variables, you use the command:

```
  env
```

> flag34=7a88306309fe05070a7c5bb26a6b2def

Otherwise, as the hint also states:

```
  echo $flag34
```

> 7a88306309fe05070a7c5bb26a6b2def

**Answer:** 7a88306309fe05070a7c5bb26a6b2def

### Flag 35

To list all groups on a system, use the command:

```
  getent group
```

> flag35\_769afb6:x:1005:

**Answer:** 769afb6

### Flag 36

```
  getent group hacker
```

> hacker:x:1004:bob

As Bob is within the group hacker, he has permission to read flag 36. The flag is within the path "etc".

```
  cat /etc/flag36
```

> 83d233f2ffa388e5f0b053848caed1eb

**Answer:** 83d233f2ffa388e5f0b053848caed1eb

# Conclusion

In conclusion, this challenge had jogged up my memory and made me understand Linux a bit better. There are a lot of commands that I had no previous knowledge about and this is why [Google](https://www.google.com) is the best tool to use for research and learning concepts.
