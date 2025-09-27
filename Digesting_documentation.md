# Challenge 1 learning from documentation

The typical need you'll have for documentation is just to figure out how to use all these
dang programs, and a specific case of that is figuring out what arguments to specify on 
the command line. This module will mostly dig into that concept, as a proxy for figuring 
out how to use the programs in general. Through the rest of the module, you'll go through
various ways of asking the environment for help for the programs, but first, we'll dig into
the concept of reading documentation.

The correct usage of programs depends, in a large part, on the proper specification of 
arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic
Commands module: that -a was an argument that told ls to list out hidden files as well as 
non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a 
argument was the correct way to use it in our scenario.

## Solution 
1. This challenge was about learning to find the correct arguments for a program by reading its documentation
2. The goal was to find the right argument to pass to the `/challenge/challenge` program to make it give me the flag.
3. ased on this direct instruction, I constructed the final command and got the flag

```sh
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{o4J7zx2ExD8Uh3EhEFoGWinX0MQ.QX0ITO0wCMzAzNzEzW}
```

## Flag

```
pwn.college{o4J7zx2ExD8Uh3EhEFoGWinX0MQ.QX0ITO0wCMzAzNzEzW}
```

### Notes
1. The instructions gave me the exact answer, which was to add the --giveflag argument to the command.
2. This is what I learnt.

# Challenge 2 Learning complex usage 

While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

## Solution 

1.This challenge introduced the concept that some arguments, like `--printfile`, require their own arguments.
2. The goal was to run the `/challenge/challenge` program with the correct arguments to print the flag.
3. The documentation explained that I needed to use the `--printfile argument`.
4. So i constructed the following code to get the flag

```sh
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
```

## Flag

```
pwn.college{AuJZp0OIFi3UGzXjxr-trVeFvbm.QX1IT00wCMzAzNzEzW}
```

### Notes 

1. I learned to think of commands as being built from three parts, the program I'm running, the action I want it to take , and the target of that action.
2. This puzzle showed how important it is to combine new and old information.

# Challenge 3 Reading Manuals

This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):

```sh
hacker@dojo:~$ man yes
```

This will display the manual page for yes, which will look something like this:

```sh
YES(1)                           User Commands                          YES(1)

NAME
       yes - output a string repeatedly until killed

SYNOPSIS
       yes [STRING]...
       yes OPTION

DESCRIPTION
       Repeatedly output a line with all specified STRING(s), or 'y'.

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report any translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/yes>
       or available locally via: info '(coreutils) yes invocation'

GNU coreutils 8.32               February 2022                          YES(1)
The important sections are:

NAME(1)                           CATEGORY                          NAME(1)

NAME
	This gives the name (and short description) of the command or
	concept discussed by the page.

SYNOPSIS
	This gives a short usage synopsis. These synopses have a standard
	format. Typically, each line is a different valid invocation of the
	command, and the lines can be read as:

	COMMAND [OPTIONAL_ARGUMENT] SINGLE_MANDATORY_ARGUMENT
	COMMAND [OPTIONAL_ARGUMENT] MULTIPLE_ARGUMENTS...

DESCRIPTION
	Details of the command or concept, with detailed descriptions
	of the various options.

SEE ALSO
	Other man pages or online resources that might be useful.

COLLECTION                        DATE
```
You can scroll around the manpage with your arrow keys and PgUp/PgDn. When you're done reading the manpage, you can hit q to quit.

Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

## Solution 

1. This challenge introduced the man command, the built-in manual for Linux commands
2. I opened the manual for the program by running man challenge.
3. I carefully read the description section, looking for a way to get the flag. I found an option listed as --wrrepn NUM, which the manual said would print the flag if NUM is 619.
4. I exitted the manual by pressing q and then ran the program to get the flag.

```sh
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --wrrepn 619
```

## Flag

```
pwn.college{Mwrr6CX1eGp-OnUKVZdd9uz9eaz.QX0EDO0wCMzAzNzEzW}
```

### Notes

1. I learned how to use the  `man` command.
2. I also learned how to quit a man page which is by just pressing the q key and the most important information is usually in the synopsis and description sections.
3. I faced a problem while quitting the page, it took me a while.

# Challenge 4 Searching manuals 

You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

## Solution 



## Flag

```

```







