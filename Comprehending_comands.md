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

1. 








