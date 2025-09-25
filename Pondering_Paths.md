# Challenge 1 The Root

Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, 
programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag.
All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. 
This style of path, one that starts with the root directory, is referred to as an "absolute path".

## Solution 

1. First I understood that the filesystem starts at the root directory and it is represented by ```/```.
2. The challenge stated that the program name pwn was placed directly in this.
3. By combining the root dictonary ```/``` with ```pwn``` I got the correct command and hence the flag was obtained.

```sh
$ /pwn
```

## Flag

```
pwn.college{8bSsiGCfXZxL4jjImpmAFKGp7hz.QX4cTO0wCMzAzNzEzW}
```

### Notes

What I learnt is how we can invoke the path for a program
I learnt to invoke '/pwn'

# Challenge 2 Program and Absolute Path

Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge 
directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge. The name of the challenge program in this level 
is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

## Solution 

1. I started with ```/``` which is the top level of the filesystem as discussed previously.
2. As it was given the program was inside a directory named `challenge`, So I made it ```/challenge```.
3. Finally the program was named ```run``` which was located inside the ```/challenge``` so I added the name to complete the full path.

```sh
$ /challenge/run
```

## Flag 

```
pwn.college{wxuXb0re6xRVrSG3e1gZFjdsYfT.QX1QTN0wCMzAzNzEzW}
```

### Notes 

1. I learned that the filesystem is organized, like a tree.
2. This challenge made the structure of absolute paths /directory/file much clear


# Challenge 3 Position thy self 

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a 
path to it as an argument, as so:
```sh
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
```
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. 
The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

## Solution 

1. First my thought was to run the ```/challenge/run``` program directly to see what would happen.
2. This resulted in an error message but it told me the correct location that I needed to be in.
3. Following this specific instruction I used the ```cd``` command to navigate to path.
4. Once my terminal showed me that I was in the correct directory, I ran the ```/challenge/run``` command the
   second time, this was successful and revealed the flag 

```sh
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /var/lib/apt/lists
hacker@paths~position-thy-self:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
```

## Flag 

```
pwn.college{I8BGndE4b2EtDaJ301u4KH7Ybtw.QX2QTN0wCMzAzNzEzW}
```

### Notes 

1. At first, this challenge was confusing. After I connected to the terminal, I expected it to tell me which directory
   to change my present directory into, but there was no message or instruction on the screen. I wasn't sure how to find the path I was suppose to go to.
2. I decided to experiment by running the ```/challenge/run``` program to see what would happen. At this time the program gave me an incorrect message but
   it also showed the right directory in which I need to cd .
3.What I understood is that Sometimes the solutions comes from trying and spending lots of time.

# Challenge 4 Position elsewhere

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it 
as an argument, as so:

```sh
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The 
reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

## Solution 

1. First I ran the ```/challenge/run``` program directly to see what would happen as before.
2. This resulted in an error message but it told me the correct location that I needed to be in.
3. Following this specific instruction I used the ```cd``` command to navigate to path.
4. Once my terminal showed me that I was in the correct directory, I ran the ```/challenge/run``` command the
   second time, this was successful and revealed the flag

```sh
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/log directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd/var/log
bash: cd/var/log: No such file or directory
hacker@paths~position-elsewhere:~$ cd /var/log
hacker@paths~position-elsewhere:/var/log$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
```

## Flag

```
pwn.college{s1nKZHYW8ZOgkFMLNuisqMGUod0.QX3QTN0wCMzAzNzEzW}
```

### Notes

1. At first, this challenge was confusing. After I connected to the terminal, I expected it to tell me which directory
   to change my present directory into, but there was no message or instruction on the screen. I wasn't sure how to find the path I was suppose to go to.
2. I decided to experiment by running the ```/challenge/run``` program to see what would happen. At this time the program gave me an incorrect message but
   it also showed the right directory in which I need to cd .

# Challenge 5 Position Yet Elsewhere

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing 
a path to it as an argument, as so:

```sh
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out.
The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

## Solution 

1. First I ran the ```/challenge/run``` program directly to see what would happen as before.
2. This resulted in an error message but it told me the correct location that I needed to be in.
3. Following this specific instruction I used the ```cd``` command to navigate to path.
4. Once my terminal showed me that I was in the correct directory, I ran the ```/challenge/run``` command the
   second time, this was successful and revealed the flag

```sh
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /
hacker@paths~position-yet-elsewhere:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
```

## Flag

```
pwn.college{Ez7AX3GCOveDztF4K1cK-SDDy3k.QX4QTN0wCMzAzNzEzW}
```

### Notes

1. At first, this challenge was confusing. After I connected to the terminal, I expected    it to tell me which directory to change my present directory into, but there was no      message or instruction on the screen. I wasn't sure how to find the path I was           suppose to go to.
2. I decided to experiment by running the ```/challenge/run``` program to see what would    happen. At this time the program gave me an incorrect message but
   it also showed the right directory in which I need to cd .

# Challenge 6 Implicit relative paths, from /

Now you're familiar with the concept of referring to absolute paths and changing directories. If you put in absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the previous three challenges.

However, the current working directory does matter for relative paths.

A relative path is any path that does not start at root (i.e., it does not start with /).
A relative path is interpreted relative to your current working directory (cwd).
Your ```cwd``` is the directory that your prompt is currently located at.
This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at ```/tmp/a/b/my_file```.

If my cwd is ```/```, then a relative path to the file is ```tmp/a/b/my_file```.
If my cwd is ```/tmp```, then a relative path to the file is ```a/b/my_file```.
If my cwd is ```/tmp/a/b/c```, then a relative path to the file is ../my_file. The .. refers to the parent directory.

## Solution 

1. I first ran the command cd / to move my shell to the root directory, satisfying the      first condition.
2. I understood that the relative path to ```/challenge/run``` would be ```challenge/run```
3. I then executed the ```challlenge/run``` which gave my flag.

```sh
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
```

## Flag

```
pwn.college{geSS5_4S0wTyY-hoef9AAdvrlPW.QX5QTN0wCMzAzNzEzW}
```

### Notes 

1. I learned that a path starting with / is a full location of a file.
2. A path that doesnt start with / is just to tell the pc to look at something inside the folder we are currently in.

# Challenge 7 explicit relative paths, from /

Previously, your relative path was "naked": it directly specified the directory to descend into from the current directory. In this level, we're going to explore more explicit relative paths.

In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to each other:

```sh
/challenge
/challenge/.
/challenge/./././././././././
/./././challenge/././
```
The following relative paths are also all identical to each other:
```sh
challenge
./challenge
./././challenge
challenge/.
```
Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.

## Solution 

1. This challenge is designed to teach us how to use the ```.``` character.
2. First my current directory needed to be the root so I used the ```cd /``` to move        there.
3. To make it explicit relative path I reconstructed the command to ```./challenge/run```
4. Executing this I got my flag.

```sh
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
```

## Flag

```
pwn.college{Mrb0J7eI2Px5B23cmyVVxT1hZeK.QXwUTN0wCMzAzNzEzW}
```

### Notes

1.I learned that adding ```./``` to the start of the path is a way to be very specific.
2.The ```challenge/run``` and ```./challenge/run``` do the same thing but the ```./```     is to be just more specific.

# Challenge 8 Implicit Relative Path 

In this level, we'll practice referring to paths using . a bit more. This challenge will need you to run it from the /challenge directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:

```sh
hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run
```
This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:
```sh
bash: run: command not found
```

## Solution 

1. This challenge required me to execute the ```run``` program within the ```/challenge``` directory.
2. First I navigated to the challenge directory using ```cd /challenge```.
3. then I used ```./run``` to specifically run the ```run``` program.
4. Executing this I got the flag.

```sh
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
```

## Flag 

```
pwn.college{ADLX-lQP_PE-deDw4Wr2-RkDYWh.QXxUTN0wCMzAzNzEzW}
```

### Notes

1. What I learnt is that the computer doesnt automatically look for programs in the folder we are currently in.
2. Just typing run will fail even if the run file is right there.
3. We must type ```./``` before it's name.

# Challenge 9 Home sweet home 

Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker. The home directory is typically where users store most of their personal files. As you make your way through pwn.college, this is where you'll store most of your solutions.

Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:

```sh
hacker@dojo:~$
```
The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider:
```sh
hacker@dojo:~$ echo LOOK: ~
LOOK: /home/hacker
hacker@dojo:~$ cd /
hacker@dojo:/$ cd ~
hacker@dojo:~$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~
hacker@dojo:~$ cd /home/hacker/asdf
hacker@dojo:~/asdf$
```
Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.

Fun fact: cd will use your home directory as the default destination:
```sh
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ cd
hacker@dojo:~$
```

## Solution 






   

