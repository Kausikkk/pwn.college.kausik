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

1. At first, this challenge was confusing. After I connected to the terminal, I expected it to tell me which directory
   to change my present directory into, but there was no message or instruction on the screen. I wasn't sure how to find the path I was suppose to go to.
2. I decided to experiment by running the ```/challenge/run``` program to see what would happen. At this time the program gave me an incorrect message but
   it also showed the right directory in which I need to cd .
