# Challenge 1 cat : not the pet, but the command!

One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:
```sh
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
```
cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:
```sh
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
```

## Solution 

1. This challenge introduced ```cat``` command which is used to read and display the contents of file
2. The instructions stated that the challenge would create a file named `flag` and place it in my home directory.
3. What I needed to do was to execute the `cat flag` command in order to get the flag.

```sh
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
```
## Flag 

```
pwn.college{M5ENv_hKSnIj89G59RbXgrExD0A.QXxcTN0wCMzAzNzEzW}
```

### Notes 

1. What I learnt is that `cat` command is the standard tool for quickly viewing the contents of a file
2. I learned that `cat` means `concatenate` from google.This is called so because we can give it a list of multiple files.

# Challenge 2 Catting absolute paths 

In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:
```sh
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
```
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
...

## Solution 

1. This challenge continued the lesson on the cat command, showing how it can be used to read files from anywhere on the system.
2. The instructions stated that the challenge would create a file named flag, but this time it would be placed at the absolute path , not in my home directory.
3. what I  did was execute the `cat /flag` command to read the file from its full path and get the flag.

```sh
hacker@commands~catting-absolute-paths:~$ cat /flag
```

## Flag
```
pwn.college{AUaEO4PBfNdCT0oqL5GGotOZw6s.QX5ETO0wCMzAzNzEzW}
```

### Notes 

1. As long as we give `cat` a valid path, it doesnt matter if the file is in current directory or somewhere else on the system.
2. the main flag for every challenge is technically always stored at `/flag` in pwn.collage.
3. This challenge shows the difference between a relative path and an absolute path.

# Challenge 3 More catting practice 

You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, 
and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.

## Solution

1. This is a straight challenge to practice using `cat` command with a full absolute path.
2. When I connected the instructions in the terminal gave me the exact path to the flag file
   `/lib/ruby/vendor_ruby/flag`
3. I simply used the cat commanf to get the flag

```sh
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /lib/ruby/vendor_ruby/flag. Go cat it out **without** cding into 
that directory!
hacker@commands~more-catting-practice:~$ cat /lib/ruby/vendor_ruby/flag
```

## Flag 

```
pwn.college{8vYpjGwMje08hnQ8DdPkzrAdVj7.QXwITO0wCMzAzNzEzW}
```

### Notes

1. I learned that a files location does not matter as long as we know its full absolute path.
2. I learned to use cat to read any file directly without using cd command.

# Challenge 4 grepping for a needle in a haystack

Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.

There are many ways to grep, and we'll learn one way here:
```sh
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

## Solution 

1. This challenge presented a very large file which was too big to read with `cat`.
2. The goal of this was to find the flag thats stored inside this huge text.
3. The chammenge introduced a new command called ```grep``` which is used to search for specific text within files.
4. In the instructions I was given that the text was inside `/challenge/data. txt`.
5. It also gave a hint that the flag starts with pwn.collage.
6. So I ran the code  grep 'pwn.college' /challenge/data.txt to get the flag.

```sh
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep 'pwn.college' /challenge/data.txt
```

## Flag

```
pwn.college{IEVeTP55lHZhSRVegQNbVg9Io_S.QX3EDO0wCMzAzNzEzW}
```

### Notes 

1. First I though of trying with cat command but it was said that it had 1000s of lines of text.
2. So then I used the grep command to search for the text inside the file.
3. The hint said to search for the text `pwn.collage`.
4. The correct command was ```grep 'pwn.college' /challenge/data.txt```.

# Challenge 5 Comparing files 

When looking for changes between similar files, eyeballing them might not be the most efficient approach! This is where the diff command becomes invaluable.

diff compares two files line by line and shows you exactly what's different between them. For example:

```sh
hacker@dojo:~$ cat file1
hello
world
hacker@dojo:~$ cat file2
hello
universe
hacker@dojo:~$ diff file1 file2
2c2
< world
---
> universe
```
The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

Sometimes, when new lines are added, you'll see something like:

```sh
hacker@dojo:~$ cat old
pwn
hacker@dojo:~$ cat new
pwn
college
hacker@dojo:~$ diff old new
1a2
> college
```
This tells us that after line 1 in the first file, the second file has an additional line (1a2 means "after line 1 of file1, add line 2 of file2").

## Solution 

1. This challenge presented me two files ```decoys_only.txt``` which contained 100 fake flags, and ```decoys_and_real.txt``` which contained the same 100 fake flags and also the one real flag. My goal was to find that single flag .
2. For this the challenge introduced me the `diff` command. I understood that it comapres two files and shows the lines that have been added.
3. I used the `diff` command and gave it full paths to the two files.
4. The command ignored all the identical lines of fake flags and printed only the unique flag from the second file which was the real one.

```sh
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
85a86
> pwn.college{49mwd3l92eyVCycS-t3rf2Wwv01.01MwMDOxwCMzAzNzEzW}
```

## Flag

```
pwn.college{49mwd3l92eyVCycS-t3rf2Wwv01.01MwMDOxwCMzAzNzEzW}
```

### Notes

1. The main lesson that I learned is about the ```diff``` command. Its a tool that spots the difference between two files.
   instantly showing the only lines that are different.
2. ```diff``` command is a real useful command as counting all the lines which are over 100 one by one would have been almost impossible.
3. Another thing that I learned is that while using this command the output, the `>` symbol points to the line that was added to the second file.

# Challenge 6 Listing files 

So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:

```sh
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
```

## Solution 

1. The goal was the find the new random name of the `run` program located in the `/challenge` directory.
2. First I used the `ls` command to list the conetents inside the /challenge.
3. The output to this showed me the new file name that was `28287-renamed-run-1887  DESCRIPTION.md`.
4. Finally I executed the program using its full absolute path to get the flag.

```sh
hacker@commands~listing-files:~$ ls /challenge
28287-renamed-run-1887  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/28287-renamed-run-1887  DESCRIPTION.md
```

## Flag

```
pwn.college{sxi3epkLt8DR_XwcMaOAcG_o0z9.QX4IDO0wCMzAzNzEzW}
```

### Notes

1. I learnt the `ls` command. Its basically a took for looking inside a directory to see what files and folders are there.
2. When I dont know the exact name of the file, I should first use `ls` to find it, and then use that information in my next command.
3. I also learned that `ls` works with paths. I can use the `ls` by itself to see my current folder or I can give a path like `ls/challenge` to get inside a different folder without having to use the `cd` command.

# Challenge 7 Touching files 

Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:

```sh
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
```

## Solution 

1. The challenge introduced me `touch` command, which is used for creating new empty files.
2. This challenge was a three step process.
3. First I had to create two empty files at `/tmp/pwn` and `/tmp/collage`.
4. after creating this I had to run `/challenge/run` program to verift that the files existed.
5. So I executed the following commands which got me the flag

```sh
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
```

## Flag 

```
pwn.college{sh71_hP1FNtDpMKpjvCCK14GrcX.QXwMDO0wCMzAzNzEzW}
```

### Notes 

1. What I learned is the `touch` command which can create a new empty file anywhere in the filesystem by giving it a full path.
2. This challenge made me first create two new files which took a lot of time for me to understand and write it down.
3. At the end upon googling I also learned a new trick that `touch` command can create multiple files at one,
   instead of running two seperate commands, Icould have done the same job in a single step with the command
   `touch /tmp/pwn /tmp/college`.

# Challenge 8 removing files 

Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:

```sh
hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
```

## Solution 

1. This challenge explains the `rm` command which is used to permanently delete files.
2. The task was done in two steps.
3. First I was asked to delete the `delete_me` file from my home directory.
4. Then I was asked to run the `/challenge/check` program to verify if the file got deleted.
5. So first I ran `rm delete_me` and then `/challenge/check` which gave me the flag.

```sh
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
```

## Flag 

```
pwn.college{gm4QjDs9q-kjalQ1PlRIMzYuYYt.QX2kDM1wCMzAzNzEzW}
```

### Notes 

1. I learnt how to use the `rm` command which is used to delete the files.
2. Whats important is that this command deletes the files permanently.
3. If the file hadnt been in my home directory I would have had to type the exact path of the file.
4. This command took me some time to understand how it works.

# Challenge 9 Moving files 

You can also move files around with the mv command. The usage is simple:

```sh
hacker@dojo:~$ ls
my-file
hacker@dojo:~$ cat my-file
PWN!
hacker@dojo:~$ mv my-file your-file
hacker@dojo:~$ ls
your-file
hacker@dojo:~$ cat your-file
PWN!
hacker@dojo:~$
```

## Solution 

1. This challenge introduced the `mv` command used for moving or renaming files.
2. This has two steps first is to move the `/flag` file to a new directory.
3. second step is to run and check the program.
4. I followed the instructions using the correct format and ran `mv /flag /tmp/hack-the-planet` to move the file to its new location.
5. After this I ran the `/challenge/check` which confirmed the file was moved successfully and then this gave me the flag.

```sh
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
```

## Flag 

```
pwn.college{0BfHPQlb-XSmGQXAre07tX0q_im.0VOxEzNxwCMzAzNzEzW}
```

### Notes

1. I learned how the `mv` command works. By this I understood how to move files from one location to another using the simple format.
2. I also learned that `mv` is used to rename files from googling it.

# Challenge 10 hidden files

Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:

```sh
hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$
```

## Solution 

1. This challenge introduced hidden files in Linux—files whose names begin with a dot, The goal was to find and read a hidden flag file located in the root directory.
2. I know a normal `ls` wouldn't work, so I used the `ls -a` command to list all files in the root directory.
3. This revealed the hidden flag file name which was `.flag-1147927078874`.

```sh
hacker@commands~hidden-files:~$ ls -a /
.   .dockerenv           bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-1147927078874  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-1147927078874
```

## Flag

```
pwn.college{UaGzBCWutPQSm_p5wpRVYrhnfuR.QXwUDO0wCMzAzNzEzW}
```

### Notes

1.The main lesson was learning about hidden files. I now know that any file starting with a dot (.) is hidden by default, and we must use the ls -a command to see it.
2.I learned that files are often hidden to protect important configuration files.

# Challenge 11 An epic filesystem quest

With your knowledge of cd, ls, and cat, we're ready to play a little game!

We'll start it out in /. Normally:

```sh
hacker@dojo:~$ cd /
hacker@dojo:/$ ls
```
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file and the challenge directory.

## Solution 
1.This challenge was a long, multi-step treasure hunt across the filesystem. The goal was to follow a trail of clues by repeating a simple pattern of commands using `ls` to LOOK for a clue file, `cat` to READ the clue inside it, and `cd` to GO to the next location.
2.The quest involved several tricks, including "trapped" directories that I couldn't cd into, and files that were just distractions. By carefully investigating files with `ls -l` and identifying the most likely clue files, I navigated through many different directories.
3.The final few steps of my journey are logged below. After following a clue from a HINT file, I navigated to the `/usr/local/lib/python3.8/dist-packages/pytz/zoneinfo/Arctic `directory. There, I used ls to find one last clue file named DOSSIER, and reading it with cat revealed the final flag.

```sh
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
MEMO  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin   challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat MEMO
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/tools/power/cpupower/utils/idle_monitor
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/tools/power/cpupower/utils/idle_monitor
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/cpupower/utils/idle_monitor$ ls
INSIGHT            cpupower-monitor.c  idle_monitors.def  nhm_idle.c
amd_fam14h_idle.c  cpupower-monitor.h  idle_monitors.h    snb_idle.c
cpuidle_sysfs.c    hsw_ext_idle.c      mperf_monitor.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/cpupower/utils/idle_monitor$ cat INSIGHT
Yahaha, you found me!
The next clue is in: /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/NonUnicode

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/cpupower/utils/idle_monitor$ cd /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/NonUnicode
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/NonUnicode$ ls
MESSAGE  Regular
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/NonUnicode$ cat MESSAGE
Congratulations, you found the clue!
The next clue is in: /usr/local/lib/python3.8/dist-packages/pyformlang/fcfg/tests/__pycache__

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/NonUnicode$ ls /usr/local/lib/python3.8/dist-packages/pyformlang/fcfg/tests/__pycache__
SPOILER-TRAPPED          test_fcfg.cpython-38.pyc
__init__.cpython-38.pyc  test_feature_structure.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/NonUnicode$ cat /usr/local/lib/python3.8/dist-packages/pyformlang/fcfg/tests/__pycache__/SPOILER-TRAPPED
Tubular find!
The next clue is in: /usr/share/emacs/26.3/etc

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/NonUnicode$ cd /usr/share/emacs/26.3/etc
hacker@commands~an-epic-filesystem-quest:/usr/share/emacs/26.3/etc$ ls
AUTHORS       GNU         NEWS.20    TERMS              enriched.txt         publicsuffix.txt.gz
CALC-NEWS     GNUS-NEWS   NEWS.21    THE-GNU-PROJECT    forms                refcards
CENSORSHIP    HELLO       NEWS.22    TODO               future-bug           rgb.txt
COPYING       HISTORY     NEWS.23    WHY-FREE           gnus                 schema
CUE           LINUX-GNU   NEWS.24    charsets           gnus-tut.txt         ses-example.ses
DEBUG         MACHINES    NEWS.25    compilation.txt    grep.txt             spook.lines
DISTRIB       MH-E-NEWS   NEXTSTEP   e                  images               srecode
DOC           MORE.STUFF  NXML-NEWS  edt-user.el        nxml                 themes
ERC-NEWS      NEWS        ORDERS     emacs-buffer.gdb   org                  tutorials
ETAGS.EBNF    NEWS.1-17   ORG-NEWS   emacs.appdata.xml  package-keyring.gpg  yow.lines
ETAGS.README  NEWS.18     PROBLEMS   emacs.icon         ps-prin0.ps
FTP           NEWS.19     README     emacs.service      ps-prin1.ps
hacker@commands~an-epic-filesystem-quest:/usr/share/emacs/26.3/etc$ ls -l
total 5472
-rw-r--r--  1 root   root    172098 Sep 10  2019 AUTHORS
-rw-r--r--  1 root   root     36762 Sep 10  2019 CALC-NEWS
-rw-r--r--  1 root   root       191 Sep 10  2019 CENSORSHIP
lrwxrwxrwx  1 root   root        30 Mar 25  2020 COPYING -> ../../../common-licenses/GPL-3
-rw-r--r--  1 hacker hacker     252 Sep 26 17:16 CUE
-rw-r--r--  1 root   root     42198 Sep 10  2019 DEBUG
-rw-r--r--  1 root   root      4615 Sep 10  2019 DISTRIB
-rw-r--r--  1 root   root   2896198 Mar 25  2020 DOC
-rw-r--r--  1 root   root     45170 Sep 10  2019 ERC-NEWS
-rw-r--r--  1 root   root      4139 Sep 10  2019 ETAGS.EBNF
-rw-r--r--  1 root   root      2284 Sep 10  2019 ETAGS.README
-rw-r--r--  1 root   root       312 Sep 10  2019 FTP
-rw-r--r--  1 root   root       172 Sep 10  2019 GNU
-rw-r--r--  1 root   root     12397 Sep 10  2019 GNUS-NEWS
-rw-r--r--  1 root   root      5099 Sep 10  2019 HELLO
-rw-r--r--  1 root   root      5672 Sep 10  2019 HISTORY
-rw-r--r--  1 root   root       185 Sep 10  2019 LINUX-GNU
-rw-r--r--  1 root   root      4731 Sep 10  2019 MACHINES
-rw-r--r--  1 root   root    114771 Sep 10  2019 MH-E-NEWS
-rw-r--r--  1 root   root       208 Sep 10  2019 MORE.STUFF
-rw-r--r--  1 root   root     81564 Mar 25  2020 NEWS
-rw-r--r--  1 root   root     98512 Sep 10  2019 NEWS.1-17
-rw-r--r--  1 root   root     63562 Sep 10  2019 NEWS.18
-rw-r--r--  1 root   root    272638 Sep 10  2019 NEWS.19
-rw-r--r--  1 root   root    188216 Sep 10  2019 NEWS.20
-rw-r--r--  1 root   root    191809 Sep 10  2019 NEWS.21
-rw-r--r--  1 root   root    238292 Sep 10  2019 NEWS.22
-rw-r--r--  1 root   root    102677 Sep 10  2019 NEWS.23
-rw-r--r--  1 root   root    154252 Sep 10  2019 NEWS.24
-rw-r--r--  1 root   root     77261 Sep 10  2019 NEWS.25
-rw-r--r--  1 root   root     12135 Sep 10  2019 NEXTSTEP
-rw-r--r--  1 root   root      7376 Sep 10  2019 NXML-NEWS
-rw-r--r--  1 root   root       187 Sep 10  2019 ORDERS
-rw-r--r--  1 root   root    162315 Sep 10  2019 ORG-NEWS
-rw-r--r--  1 root   root    138785 Sep 10  2019 PROBLEMS
-rw-r--r--  1 root   root       479 Sep 10  2019 README
-rw-r--r--  1 root   root     10055 Sep 10  2019 TERMS
-rw-r--r--  1 root   root       176 Sep 10  2019 THE-GNU-PROJECT
-rw-r--r--  1 root   root     59791 Sep 10  2019 TODO
-rw-r--r--  1 root   root       198 Sep 10  2019 WHY-FREE
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 charsets
-rw-r--r--  1 root   root     19580 Sep 10  2019 compilation.txt
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 e
-rw-r--r--  1 root   root      7015 Sep 10  2019 edt-user.el
-rw-r--r--  1 root   root      8718 Sep 10  2019 emacs-buffer.gdb
-rw-r--r--  1 root   root      1510 Sep 10  2019 emacs.appdata.xml
-rw-r--r--  1 root   root      1933 Sep 10  2019 emacs.icon
-rw-r--r--  1 root   root       560 Sep 10  2019 emacs.service
-rw-r--r--  1 root   root     10626 Sep 10  2019 enriched.txt
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 forms
-rw-r--r--  1 root   root      1574 Sep 10  2019 future-bug
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 gnus
-rw-r--r--  1 root   root     10596 Sep 10  2019 gnus-tut.txt
-rw-r--r--  1 root   root      4701 Sep 10  2019 grep.txt
drwxr-xr-x 13 root   root      4096 Sep  7 01:22 images
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 nxml
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 org
-rw-r--r--  1 root   root      2069 Sep 10  2019 package-keyring.gpg
-rw-r--r--  1 root   root      5326 Sep 10  2019 ps-prin0.ps
-rw-r--r--  1 root   root     23235 Sep 10  2019 ps-prin1.ps
-rw-r--r--  1 root   root     58744 Mar 25  2020 publicsuffix.txt.gz
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 refcards
-rw-r--r--  1 root   root     19044 Sep 10  2019 rgb.txt
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 schema
-rw-r--r--  1 root   root      8629 Sep 10  2019 ses-example.ses
-rw-r--r--  1 root   root     12777 Sep 10  2019 spook.lines
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 srecode
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 themes
drwxr-xr-x  2 root   root      4096 Sep  7 01:22 tutorials
-rw-r--r--  1 root   root       400 Sep 10  2019 yow.lines
hacker@commands~an-epic-filesystem-quest:/usr/share/emacs/26.3/etc$ cat CUE
Yahaha, you found me!
The next clue is in: /usr/share/racket/pkgs/drracket-tool-lib/drracket/private/syncheck/compiled

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/emacs/26.3/etc$ cd /usr/share/racket/pkgs/drracket-tool-lib/drracket/private/syncheck/compiled
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/drracket-tool-lib/drracket/private/syncheck/compiled$ ls -a
.                 colors_rkt.dep              syncheck-intf_rkt.zo                 xref_rkt.dep
..                colors_rkt.zo               syncheck-local-member-names_rkt.dep  xref_rkt.zo
.SNIPPET          contract-traversal_rkt.dep  syncheck-local-member-names_rkt.zo
annotate_rkt.dep  contract-traversal_rkt.zo   traversals_rkt.dep
annotate_rkt.zo   syncheck-intf_rkt.dep       traversals_rkt.zo
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/drracket-tool-lib/drracket/private/syncheck/compiled$ cat .SNIPPET
Tubular find!
The next clue is in: /usr/lib/R/library/stats4/Meta

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/drracket-tool-lib/drracket/private/syncheck/compiled$ cat /usr/lib/R/library/stats4/Meta
cat: /usr/lib/R/library/stats4/Meta: Is a directory
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/drracket-tool-lib/drracket/private/syncheck/compiled$ ls /usr/lib/R/library/stats4/Meta
INFO-TRAPPED  Rd.rds  features.rds  hsearch.rds  links.rds  nsInfo.rds  package.rds
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/drracket-tool-lib/drracket/private/syncheck/compiled$ cat /usr/lib/R/library/stats4/Meta/INFO-TRAPPED
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/tools/testing/selftests/powerpc/primitives/linux
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/drracket-tool-lib/drracket/private/syncheck/compiled$ cd /opt/linux/linux-5.4/tools/testing/selftests/powerpc/primitives/linux
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/testing/selftests/powerpc/primitives/linux$ ls
HINT  stringify.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/testing/selftests/powerpc/primitives/linux$ cat stringify.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/testing/selftests/powerpc/primitives/linux$ cat HINT
Tubular find!
The next clue is in: /usr/local/lib/python3.8/dist-packages/pytz/zoneinfo/Arctic
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/testing/selftests/powerpc/primitives/linux$ cd /usr/local/lib/python3.8/dist-packages/pytz/zoneinfo/Arctic
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/pytz/zoneinfo/Arctic$ ls
DOSSIER  Longyearbyen
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/pytz/zoneinfo/Arctic$ cat DOSSIER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{YxFkh4MttFpKK5xBcPwtBrK8k0H.QX5IDO0wCMzAzNzEzW}
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/pytz/zoneinfo/Arctic$
```

## Flag

```
pwn.college{YxFkh4MttFpKK5xBcPwtBrK8k0H.QX5IDO0wCMzAzNzEzW}
```

### References

`youtube`

### Notes 

1. I learnt how to use the ls, cat, cd commands a lot perfect.
2. This challenge taught me not just to look at filenames but to even use `ls -l` to get more details.
3. The quest used several tricks like the trapped directory where i couldnt use cd.
4. This challenge took me a lot of time probably more than an hour 20 minutes to get till the end and claim the flag.
5. I really learned a lot from this challenge.

# Challenge 12 making directories 

We can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

Watch:
```sh
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
```

## Solution

1.This challenge introduced the `mkdir` command for making new directories and required me to use it along with the `touch` command.
2. First, I needed to create a new directory at `/tmp/pwn`. Second, I had to create a new, empty file named college inside that new directory. Finally, I had to run the /challenge/run program to check my work.
3. I followed the instructions in order. I used `mkdir /tmp/pwn` to create the directory, then touch `/tmp/pwn/college` to create the file inside it. The last step was to run `/challenge/run`, which confirmed the structure was correct and gave me the flag.

```sh
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
```

## Flag

```
pwn.college{wxLbGxG5el4f0Rw9_4_zBoGIfA6.QXxMDO0wCMzAzNzEzW}
```

### Notes 
1.I learned the `mkdir` command which is the standard tool for creating new, empty folders.
2. we use `mkdir` to build the folder structure first and then we place files inside those folders.
3. This challenge was good practice for creating things using full absolute paths.

# challenge 13 finding files

So now we know how to list, read, and create files. But how do we find them? We use the find command!

The find command takes optional arguments describing the search criteria and the search location. If you don't specify a search criteria, find matches every file. If you don't specify a search location, find uses the current working directory (.). For example:
```sh
hacker@dojo:~$ mkdir my_directory
hacker@dojo:~$ mkdir my_directory/my_subdirectory
hacker@dojo:~$ touch my_directory/my_file
hacker@dojo:~$ touch my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find
.
./my_directory
./my_directory/my_subdirectory
./my_directory/my_subdirectory/my_subfile
./my_directory/my_file
hacker@dojo:~$
```
And when specifying the search location:
```sh
hacker@dojo:~$ find my_directory/my_subdirectory
my_directory/my_subdirectory
my_directory/my_subdirectory/my_subfile
hacker@dojo:~$
```
And, of course, we can specify the criteria! For example, here, we filter by name:
```sh
hacker@dojo:~$ find -name my_subfile
./my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find -name my_subdirectory
./my_directory/my_subdirectory
hacker@dojo:~$
```
You can search the whole filesystem if you want!
```sh
hacker@dojo:~$ find / -name hacker
/home/hacker
hacker@dojo:~$
```

## Solution 

1. This challenge introduced the find command to search the entire filesystem.
2.  The goal was to find a file named flag hidden in a random directory.
3.  my first attempt `find / -name flag` produced thousands of permission denied errors which made it impossible to see the actual results but then after some time some more files came.
4.  upon using cat on each of this path I found the flag

```sh
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.4mK6TfTSUV’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
   
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/share/racket/pkgs/plai-lib/gc2/private/compiled/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ 
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/share/racket/pkgs/plai-lib/gc2/private/compiled/flag
pwn.college{gmt3F4dSvyGPuyDTSqLtMKdUEzQ.QXyMDO0wCMzAzNzEzW
```

## FLag 

```
pwn.college{gmt3F4dSvyGPuyDTSqLtMKdUEzQ.QXyMDO0wCMzAzNzEzW}
```

### Notes

1. The main tool I learned was the `find` command which can search the entire computer for a file.
2. This challenge taught me a full workflow for finding a file.
3. This one tool me some time to search for the flag in each and every path but eventually I got it and understood how useful the find command is.

# Challenge 14 linking files

If you use Linux (or computers) for any reasonable length of time to do any real work, you will eventually run into some variant of the following situation: you want two programs to access the same data, but the programs expect that data to be in two different locations. Luckily, Linux provides a solution to this quandary: links.

Links come in two flavors: hard and soft (also known as symbolic) links. We'll differentiate the two with an analogy:

A hard link is when you address your apartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
A soft link is when you move apartments and have the postal service automatically forward your mail from your old place to your new place.
In a filesystem, a file is, conceptually, an address at which the contents of that file live. A hard link is an alternate address that indexes that data --- accesses to the hard link and accesses to the original file are completely identical, in that they immediately yield the necessary data. A soft/symbolic link, instead, contains the original file name. When you access the symbolic link, Linux will realize that it is a symbolic link, read the original file name, and then (typically) automatically access that file. In most cases, both situations result in accessing the original data, but the mechanisms are different.

Hard links sound simpler to most people (case in point, I explained it in one sentence above, versus two for soft links), but they have various downsides and implementation gotchas that make soft/symbolic links, by far, the more popular alternative.

In this challenge, we will learn about symbolic links (also known as symlinks). Symbolic links are created with the ln command with the -s argument, like so:
```sh
hacker@dojo:~$ cat /tmp/myfile
This is my file!
hacker@dojo:~$ ln -s /tmp/myfile /home/hacker/ourfile
hacker@dojo:~$ cat ~/ourfile
This is my file!
hacker@dojo:~$
```
You can see that accessing the symlink results in getting the original file contents! Also, you can see the usage of ln -s. Note that the original file path comes before the link path in the command!

A symlink can be identified as such with a few methods. For example, the file command, which takes a filename and tells you what type of file it is, will recognize symlinks:
```sh
hacker@dojo:~$ file /tmp/myfile
/tmp/myfile: ASCII text
hacker@dojo:~$ file ~/ourfile
/home/hacker/ourfile: symbolic link to /tmp/myfile
hacker@dojo:~$
```

## Solution

1.This challenge introduced symbolic links created with the `ln -s` command.
2. The puzzle involved a program, `/challenge/catflag`, that was coded to only read the file `/home/hacker/not-the-flag`.
3.My goal was to make the program to read the real flag located in `/flag`.
4.I created a symbolic link at the location the program expected `/home/hacker/not-the-flag`.
5. Finally I ran the `/challenge/catflag` and retrived the flag.

```sh
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
```

## Flag

```
pwn.college{EfwBwJeEDwFbPxr7J5Kr-REErnG.QX5ETN1wCMzAzNzEzW}
```

### Notes

1. I learned a symbolic link is just a shortcut to a real file
2. The command to make a shortcut is `ln -s`.
3. I used this trick to make a program open the real flag file when it thought it was opening a fake one.
