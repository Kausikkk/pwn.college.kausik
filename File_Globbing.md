# Challenge 1 Matching with *

The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern. It's easier to show you than explain:

```sh
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c
```
Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one. For example:
```sh
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: file_*
Look: file_a
```
When zero files are matched, by default, the shell leaves the glob unchanged:
```sh
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
```
The * matches any part of the filename except for / or a leading . character. For example:
```sh
hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
```

## Solution 

1.The goal was to get to the /challenge directory, but the path typed into the cd command had to be 4 characters or less.
2. I used shell globbing, where the asterisk (*) acts as to match any characters.
3. I found that the short pattern /c*e was only 4 characters and the shell correctly expanded it to the full /challenge path.
4. After the cd /c*e command moved me to the right directory, I ran /challenge/run to get the flag.

## Flag

```
pwn.college{skKJ9sW3NMOwCO6r4K4w9MjZk0d.QXxIDO0wCMzAzNzEzW}
```

### Notes

1. The main lesson was learning about shell globbing
2. The asterisk (*) is a powerful wildcard that can stand in for any number of characters in a filename or path.
3. I learned that the shell expands these patterns before the command is actually run. The cd command never saw /c*e; it only saw the final result, /challenge.

# Challenge 2 Matching with ?

Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. This works like *, but only matches one character. For example:
```sh
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
```

## Solution 

1.The goal was to go to the `/challenge` directory by replacing specific letters with the ?.
2. I learned that the ? matches exactly one character.
3.I created the pattern `/?ha??enge` to match the target directory /challenge.
4.After using cd /?ha??enge to move into the correct directory, I ran /challenge/run to get the flag.

```sh
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
```

## Flag

```
pwn.college{kZiCZ9XT_RFtJ8UViyvM7Dviatb.QXyIDO0wCMzAzNzEzW}
```

### Notes 

1. The main lesson was learning the question mark (?) .
2. It is used to match exactly one of any character in a path or filename.
3. I learned the difference between ? and *, the * can match many characters, but ? is more precise and matches only a single character.

# Challenge 3 Matching with []

Next, we will cover []. The square brackets are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:

```sh
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```

## Solution 

1.The goal was to use a single argument with bracket wildcards [] to represent four files: file_a, file_b, file_s, and file_h.
2.I learned that [] matches any single character provided in the list inside the brackets.
3.I saw that all the filenames started with file_ and the only difference was the last letter.
4.I created the pattern file_[absh] to match only those four required files.
5.First, I used cd to move into the /challenge/files directory, then I ran the program with the glob pattern to get the flag.

```sh
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
```

## Flag 

```
pwn.college{sK_8NJqenbov0AIT3ltZnR60I2h.QXzIDO0wCMzAzNzEzW}
```

### Notes 

1. The main lesson was learning the bracket wildcard [], which is used to match any single character from a specific list.
2. I learned that [] is more specific and powerful than ? because you can control exactly which characters it matches.

# Challenge 4 Matching paths with []

Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:
```sh
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
```

## Solution 

1.The goal was to use a single argument with bracket wildcards [] to represent four full absolute paths.
2.I learned that these can be used as part of an entire path, not just a filename.
3.The common part of the path was `/challenge/files/file_`, and the different letters were a, b, s, and h.
4.I combined these to create the final pattern: `/challenge/files/file_[absh]`.
5.Running the `/challenge/run` program with this single argument solved the challenge.


```sh
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
```

## Flag

```
pwn.college{Yo3xmHKHPWBZvqrP1ZnHLsQE5Jv.QX0IDO0wCMzAzNzEzW}
```

### Notes

1. My main takeaway is that globbing  (*, ?, []) works on entire paths, not just on simple filenames in the current folder.
2.This challenge was a great example of how globbing can save a lot of typing, by replacing four long absolute paths with one short pattern.

# Challenge 5 Multiple Globs

So far, you've specified one glob at a time, but you can do more! Bash supports the expansion of multiple globs in a single word. For example:
```sh
hacker@dojo:~$ cat /*fl*
pwn.college{YEAH}
hacker@dojo:~$
```
What happens above is that the shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).

## Solution 

1.The goal was to find a 3-character pattern with two * wildcards that would match all files containing the letter p.
2.I learned that you can use multiple wildcards in a single pattern for more complex matching.
3.The pattern *p* means "any characters, then the letter 'p', then any characters," which was a perfect fit for the requirements.
4.First, I used cd /challenge/files to move to the correct directory.
5.Then, I ran /challenge/run *p* which the shell expanded into a list of all matching files, solving the challenge.

```sh
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
```

## Flag

```
pwn.college{QDL0WBAWSmIf0vKZfFaeQCPK1PF.0lM3kjNxwCMzAzNzEzW}
```

### Notes

1.The main lesson was that you can combine multiple wildcards in one pattern to create powerful searches.
2.The *p* pattern is a very useful trick for finding any file that contains the letter p somewhere in its name.
3.This challenge showed that globbing can be used as a simple but effective way to search for files in your current directory.


# Challenge 6 Mixing Globs 

Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!

## Solution 

1.The goal was to create a single pattern of 6 characters or less that matched the files challenging, educational, and pwning.
2.I learned that you can mix different wildcards, like [] and *, in the same pattern to be more specific.
3.I noticed the files started with the letters c, e, or p.
4.I created the pattern [cep]*, which means any file starting with c, e, or p, followed by anything. This was 6 characters long and matched the files perfectly.
5.After I used cd /challenge/files, I ran the program with the [cep]* pattern to get the flag.

```sh
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{oXzoME0khaw8wiQvKVrR-149s3i.QX1IDO0wCMzAzNzEzW}
```

## Flag 

```
pwn.college{oXzoME0khaw8wiQvKVrR-149s3i.QX1IDO0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was that you can mix different wildcards (like [] and *) in the same pattern.
2.The pattern [cep]* was a good example of this, where [cep] matched the first letter and * matched the rest of the filename.
3.This showed that globbing is a powerful way to select a very specific group of files with a short command.


# Challenge 7 Exclusionary globbing 

Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:
```sh
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.

## Solution 

1.The goal was to select all files in the directory that did not start with the letters p, w, or n.
2.I learned that starting a bracket wildcard with ! inverts the match, so it finds characters that are not in the list.
3.To solve the puzzle, I created the pattern [!pwn] to match any first letter that was not p, w, or n.
4.I added * to match the rest of the filename, creating the final pattern [!pwn]*.
5.After using cd /challenge/files, I ran the program with this exclusionary pattern to get the flag.

```sh
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{Ag7tkcp3oJ8TR9S53gsnARxcWAx.QX2IDO0wCMzAzNzEzW}
```

## Flag 

```
pwn.college{Ag7tkcp3oJ8TR9S53gsnARxcWAx.QX2IDO0wCMzAzNzEzW}
```

### Notes 

1.The main lesson I  learnt about was exclusionary globbing with !.
2.This is a powerful feature that lets you match files by specifying characters you want to avoid.
3.The pattern [!pwn]* was a good example of combining an exclusionary glob [!pwn] with a normal glob * to create a very specific filter.


# Challenge 8 Tab completion 

As tempting as it might be, using * to shorten what must be typed on the commandline can lead to mistakes. Your glob might expand to unintended files, and you might not spot it until the rm command is already running! No one is safe from this style of error.

A safer alternative when you are trying to specify a specific target is tab completion. If you hit tab in the shell, it'll try to figure out what you're going to type and automatically complete it. Auto-completion is super useful, and this challenge will explore its use in specifying files.

This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename: we used some serious trickery to make sure that you must tab-complete it. Try it out!
```sh
hacker@dojo:~$ ls /challenge
DESCRIPTION.md  pwncollege
hacker@dojo:~$ cat /challenge/pwncollege
cat: /challenge/pwncollege: No such file or directory
hacker@dojo:~$ cat /challenge/pwn<TAB>
pwn.college{HECK YEAH}
hacker@dojo:~$
```
When you hit that tab key, the name will expand and you'll be able to read the file. Good luck!

## Solution 

1.The goal was to read a file, but the filename was tricky and could not be typed by hand.
2. The lesson was to use Tab completion to let the shell fill in the correct name.
3. I started by typing the beginning of the command: cat /challenge/pwnco.
4. I then pressed the Tab key.
5. The shell automatically completed the rest of the unusual filename. After it was complete, I pressed Enter to get the flag.

```sh
hacker@globbing~tab-completion:~$ cat /challenge/pwncolllege​ 
pwn.college{MppZVgWvL96KWAVPgfWxV23FvBe.0FN0EzNxwCMzAzNzEzW}
```

## Flag 

```
pwn.college{MppZVgWvL96KWAVPgfWxV23FvBe.0FN0EzNxwCMzAzNzEzW}
```

### Notes 

1. The most important lesson was how useful Tab completion is. It saves a lot of time and prevents typos.
2. I learned that Tab completion is not just for convenience, it's sometimes necessary. It correctly handles strange filenames with special characters or spaces that are difficult or impossible to type manually.
3.Using Tab is also much safer option.

# Challenge 9 Multiple Options for tab completion 

Consider the following situation:
```sh
hacker@dojo:~$ ls
flag  flamingo  flowers
hacker@dojo:~$ cat f<TAB>
```
There are multiple options! What happens?

What happens varies based on the specific shell and its options. By default bash will auto-expand until the first point when there are multiple options (in this case, fl). When you hit tab a second time, it'll print out those options. Other shells and configurations, instead, will cycle through the options.

This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!

## Solution 

1. This challenge was a 'tab completion quest' to find the correct flag file among many files with similar names.
2. I started by typing `cat /challenge/files/pwn` and pressing Tab twice to see the first list of possible filenames.
3. From that list, I narrowed down my choice by typing `pwncollege-` and pressing Tab twice again to see a shorter list.
4. I then saw `pwncollege-flag` in the list, so I typed fla and pressed Tab a final time, which auto-completed the full path.
5. Pressing Enter on the final, completed command displayed the flag.

```sh
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-
pwncollege-family      pwncollege-flamingo    pwncollege-hacking     
pwncollege-flag        pwncollege-flyswatter  
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-fla
pwncollege-flag      pwncollege-flamingo  
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{QnAOfmVMAk9Qq0p4nEZ8kWCXkbp.0lN0EzNxwCMzAzNzEzW}
```

## Flag 

```
pwn.college{QnAOfmVMAk9Qq0p4nEZ8kWCXkbp.0lN0EzNxwCMzAzNzEzW}
```

### Notes 

1.The main lesson was how to handle situations with multiple tab completion options.
2.I learned that pressing Tab once completes as much as possible, while pressing Tab a second time lists all the possibilities.
3.This challenge showed that tab completion is a very fast way to explore the contents of a directory without needing to use ls.

# Challenge 10 Tab completion on commands 

Tab completion is for more than files! You can also tab-complete commands. This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it!

NOTE: You can auto-complete any command, but be careful: callous auto-completes without double-checking the result can wreak havoc in your shell if you accidentally run the wrong commands!

## Solution 

1. The goal was to use tab completion to find and run a command that started with pwncollege.
2. I started by typing pwn and pressing the Tab key twice.
3. This showed me a list of all available commands that start with pwn.
4. From that list, I identified the correct command, which was pwncollege-6175.
5. I ran the pwncollege-6175 command to get the flag.

```sh
hacker@globbing~tab-completion-on-commands:~$ pwn
pwn              pwncollege-6175  pwndbg           pwnstrip         pwntools-gdb     
hacker@globbing~tab-completion-on-commands:~$ pwncollege-6175 
Correct! Here is your flag:
pwn.college{siHl08eWk8ZGvaRdNwyem8OvOiJ.0VN0EzNxwCMzAzNzEzW}
```

## Flag 

```
pwn.college{siHl08eWk8ZGvaRdNwyem8OvOiJ.0VN0EzNxwCMzAzNzEzW}
```

### Notes 

1.The main lesson was that Tab completion works for command names, not just for file paths.
2.I learned that typing the first few letters of a command and pressing Tab twice is a great way to discover or remember commands.







