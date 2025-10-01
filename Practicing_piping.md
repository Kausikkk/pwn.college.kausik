# Challenge 1 Redirecting output 

First, let's look at redirecting stdout to files. You can accomplish this with the > character, as so:
```sh
hacker@dojo:~$ echo hi > asdf
```
This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to output this file:
```sh
hacker@dojo:~$ cat asdf
hi
```

## Solution 

1. This challenge was about learning output redirection with the > symbol.
2. The goal was to create a file named COLLEGE with the word PWN inside it.
3. I used the echo PWN command to generate the text PWN.
4. I then used the > symbol to redirect that output into the COLLEGE file.
5. After creating the file, I ran the checker program to get the flag.

```sh
hacker@piping~redirecting-output:~$ echo PWN
PWN
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{ENQiIM4sphoTXrdm_u1PKT56G2t.QX0YTN0wCMzAzNzEzW}
```

## Flag 

```
pwn.college{ENQiIM4sphoTXrdm_u1PKT56G2t.QX0YTN0wCMzAzNzEzW}
```

### Notes 

1. The main lesson was learning that > redirects the output of a command into a file.
2. This is a powerful way to save the results of any command for later.


# Challenge 2 Redirecting more output 

Aside from redirecting the output of echo, you can, of course, redirect the output of any command. In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!

You'll notice that /challenge/run will still happily print to your terminal, despite you redirecting stdout. That's because it communicates its instructions and feedback over standard error, and only prints the flag over standard out!

## Solution 

1.The goal of this challenge was to run /challenge/run and redirect its output into a file named myflag.
2.I used the output redirection symbol > to do this.
3.My first command, /challenge/run > myflag, ran the program and successfully saved the flag into the myflag file.
4.My second command, cat myflag, was then needed to read the contents of the myflag file and display the flag on the screen.

```sh
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{s6MNeb8uBrIdf1Vz98PVJ_gJmem.QX1YTN0wCMzAzNzEzW}
```

## Flag

```
[FLAG] pwn.college{s6MNeb8uBrIdf1Vz98PVJ_gJmem.QX1YTN0wCMzAzNzEzW}
```

### Notes 

1.This challenge was good practice to show that output redirection (>) works for the output of any command, not just echo.
2.I learned that programs can have two different kinds of output. 

# Challenge 3 Appending output 

A common use-case of output redirection is to save off some command results for later analysis. Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.

You can redirect input in append mode using >> instead of >, as so:
```sh
hacker@dojo:~$ echo pwn > outfile
hacker@dojo:~$ echo college >> outfile
hacker@dojo:~$ cat outfile
pwn
college
hacker@dojo:$
```
To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag!

## Solution 

1.The goal was to use the append redirector (>>) to correctly save a flag that was output in two separate parts.
2.I learned that >> adds output to the end of a file, whereas > would have erased the first part.
3.My first command, /challenge/run >> /home/hacker/the-flag, ran the program and correctly saved both pieces of the flag to the file.
4.My second command, cat /home/hacker/the-flag, displayed the contents of the file, which contained the full flag.

```sh
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{4z1xT5omOtsP52n48krXhOqCheY.QX3ATO0wCMzAzNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!

```

## Flag 

```
pwn.college{4z1xT5omOtsP52n48krXhOqCheY.QX3ATO0wCMzAzNzEzW}
```

### Notes 

1.The most important lesson was the difference between > and >>.
2.The single > erases and overwrites a file.
3.The double >> adds (appends) to the end of a file without deleting the old content.

# Challenge 4 Redirecting errors 

Just like standard output, you can also redirect the error channel of commands. Here, we'll learn about File Descriptor numbers. A File Descriptor (FD) is a number that describes a communication channel in Linux. You've already been using them, even though you didn't realize it. We're already familiar with three:

FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error
When you redirect process communication, you do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output). Thus, the following two commands are equivalent:
```sh
hacker@dojo:~$ echo hi > asdf
hacker@dojo:~$ echo hi 1> asdf
```
Redirecting errors is pretty easy from this point. If you have a command that might produce data via standard error (such as /challenge/run), you can do:
```
hacker@dojo:~$ /challenge/run 2> errors.log
```
That will redirect standard error (FD 2) to the errors.log file. Furthermore, you can redirect multiple file descriptors at the same time! For example:

hacker@dojo:~$ some_command > output.log 2> errors.log
That command will redirect output to output.log and errors to errors.log.

Let's put this into practice! In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions. You'll notice that nothing will be printed to the terminal, because you have redirected everything! You can find the instructions/feedback in instructions and the flag in myflag when you successfully pull this off!

## Solution 

1.The goal of this challenge was to redirect a program's normal output and its error output into two different files.
2.I learned that > redirects the normal output and 2> redirects the error output .
3.My first command, /challenge/run > myflag 2> instructions, ran the program and saved the flag into myflag and all the info messages into instructions.
4.My second command, cat myflag, was then needed to read the contents of the myflag file and display the flag on the screen.

```sh
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{8BLACuG89hTxE2UMYHnHhCIkCrw.QX3YTN0wCMzAzNzEzW}
```

## Flag 

```
[FLAG] pwn.college{8BLACuG89hTxE2UMYHnHhCIkCrw.QX3YTN0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning about File Descriptors, especially 1 for standard output and 2 for standard error.
2.I learned that the command 2> is used specifically to redirect error and info messages.

# Challenge 5 Redirecting input 

Just like you can redirect output from programs, you can redirect input to programs! This is done using <, as so:
```sh
hacker@dojo:~$ echo yo > message
hacker@dojo:~$ cat message
yo
hacker@dojo:~$ rev < message
oy
```
You can do interesting things with a lot of different programs using input redirection! In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!

## Solution 

1.This challenge required a two-step process: first, create a file with specific content, and second, use that file as input for the main program.
2.I used output redirection to create the file with the command echo COLLEGE > PWN. This created a file named PWN that contained the word COLLEGE.
3.I then used the new input redirection symbol (<) to "feed" the contents of the PWN file into the /challenge/run program.
4.The final command, /challenge/run < PWN, successfully read the file's content and gave me the flag.

```sh
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
```

# Flag

```
pwn.college{QzQ5zeQnoXl0OQWTGkD1NpqpgNP.QXwcTN0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning about input redirection with the less-than symbol (<).
2.This feature lets us use a file as input for a command, which is like the command is typing the file's contents itself.
3.I learned that < and > are opposites: > sends output out to a file, while < takes input in from a file.

# Challenge 6 Grepping stored results 

You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep). Let's put this together!

In preparation for more complex levels, we want you to:

1.Redirect the output of /challenge/run to /tmp/data.txt.
2.This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
3.grep that for the flag!

## Solution 

1.This challenge required me to combine two skills: redirecting output (>) and searching with grep.
2.First, I ran the /challenge/run program and used > to redirect its large output into a file named /tmp/data.txt.
3.Next, I used the grep command to search inside that new file for the line containing the flag.
4.Knowing the flag starts with pwn.college, my final command was grep 'pwn.college' /tmp/data.txt, which found the flag.

```sh
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep 'pwn.college' /tmp/data.txt
pwn.college{giPWj0dXMo3F6L0rGLtFbC8vfyg.QX4EDO0wCMzAzNzEzW}
```

## Flag

```
pwn.college{giPWj0dXMo3F6L0rGLtFbC8vfyg.QX4EDO0wCMzAzNzEzW}
```

### Notes 

1.first, save the output of a command to a file, and second, analyze or search that file with other tools like grep.
2.Saving the results to a file is a good strategy when the original command takes a long time to run.
3.This allows us to search the same data multiple times without having to run the slow command over and over again.

# Challenge 7 Grepping live output 

It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can do this by using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example:
```sh
hacker@dojo:~$ echo no-no | grep yes
hacker@dojo:~$ echo yes-yes | grep yes
yes-yes
hacker@dojo:~$ echo yes-yes | grep no
hacker@dojo:~$ echo no-no | grep no
no-no
```
Now try it for yourself! /challenge/run will output a hundred thousand lines of text, including the flag. grep for the flag!

## Solution 

1.I used the pipe operator (|) to connect the output of /challenge/run directly to the input of the grep command.
2.This allowed me to "cut out the middleman" and avoid saving the output to a temporary file.
3.The final command, /challenge/run | grep 'pwn.college', filtered the live output and instantly showed me the line containing the flag.

```sh
hacker@piping~grepping-live-output:~$ /challenge/run | grep 'pwn.college'
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{8e5nPpu3O2UjfQ8iKLg-8vwBgUX.QX5EDO0wCMzAzNzEzW}
```

## Flag

```
pwn.college{8e5nPpu3O2UjfQ8iKLg-8vwBgUX.QX5EDO0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning to use the pipe (|) to chain the output of one command directly into the input of another.
2.Using a pipe is much more efficient than the previous method of saving output to a file with > and then searching it with grep.

# Challenge 8 Grepping errors 

You know how to redirect errors to a file, and you know how to pipe output to another program, such as grep. But what if you wanted to grep through errors directly?

The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output (file descriptor 1).

Luckily, where there's a shell, there's a way!

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)!

## Solution 

1. The goal of this challenge was to find a flag that was hidden in the program's error messages.
2. I learned that the pipe operator (|) by itself only sends the normal output (stdout), not the error output.
3. The solution was to first use the special redirector 2>&1 to merge the error stream (2) into the normal output stream (1).
4. I then piped this combined stream into grep 'pwn.college' to filter out everything but the flag.

```sh
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep 'pwn.college'
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
```

## Flag 

```
pwn.college{gtJEDc_BeuEuMHCaE_0_XTdfltT.QX1ATO0wCMzAzNzEzW}
```

### Notes 

1. The main lesson was learning how to grep a command's error messages.
2. The 2>&1 operator is the key trick, which merges the error output into the normal output.
3. I now know that the pipe (|) only listens to standard output by default.

# Challenge 9 Filtering with grep -v

The grep command has a very useful option: -v (invert match). While normal grep shows lines that MATCH a pattern, grep -v shows lines that do NOT match a pattern:
```sh
hacker@dojo:~$ cat data.txt
hello hackers!
hello world!
hacker@dojo:~$ cat data.txt | grep -v world
hello hackers!
hacker@dojo:~$
```
Sometimes, the only way to filter to just the data you want is to filter out the data you don't want. In this challenge, /challenge/run will output the flag to stdout, but it will also output over 1000 decoy flags (containing the word DECOY somewhere in the flag) mixed in with the real flag. You'll need to filter out the decoys while keeping the real flag!

## Solution 

1.The goal was to find one real flag hidden in the output among over 1000 decoy flags.
2.I learned to use the grep -v command, which inverts a search to show only the lines that do not match a pattern.
3.The instructions stated that all the decoy flags contained the word DECOY.
4.I piped the output of /challenge/run into the command grep -v "DECOY" to filter out all the decoy lines.
5.This left only the single, real flag, which was then printed to the screen.

```sh
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v "DECOY"
pwn.college{QUoPWugewGsMwOVLuelDC8PEceQ.0FOxEzNxwCMzAzNzEzW}
```

## Flag 

```
pwn.college{QUoPWugewGsMwOVLuelDC8PEceQ.0FOxEzNxwCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning the -v option for grep, which is used to show everything except for lines that match a pattern.
2.This challenge taught a new problem-solving strategy i.e. sometimes the easiest way to find what you want is to filter out all the junk you don't want.

# Challenge 10 Duplicating piped data with tee

When you pipe data from one command to another, you of course no longer see it on your screen. This is not always desired: for example, you might want to see the data as it flows through between your commands to debug unintended outcomes (e.g., "why did that second command not work???").

Luckily, there is a solution! The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line. For example:
```sh
hacker@dojo:~$ echo hi | tee pwn college
hi
hacker@dojo:~$ cat pwn
hi
hacker@dojo:~$ cat college
hi
hacker@dojo:~$
```
As you can see, by providing two files to tee, we ended up with three copies of the piped-in data: one to stdout, one to the pwn file, and one to the college file. You can imagine how you might use this to debug things going haywire:
```sh
hacker@dojo:~$ command_1 | command_2
Command 2 failed!
hacker@dojo:~$ command_1 | tee cmd1_output | command_2
Command 2 failed!
hacker@dojo:~$ cat cmd1_output
Command 1 failed: must pass --succeed!
hacker@dojo:~$ command_1 --succeed | command_2
Commands succeeded!
```

## Solution 

1. This was a debugging challenge where I needed to find out what information the /challenge/pwn program required.
2. I used the tee command in a pipeline (/challenge/pwn | tee output.txt | /challenge/college) to save the output of the pwn program into a file called output.txt.
3. I then read the output.txt file and discovered that the pwn program needed a secret argument: --secret I9v9vYrj.
4. My final command provided this secret to the pwn program and then piped its correct output into the college program to get the flag.

```sh
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee output.txt | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat output.txt
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "I9v9vYrj"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret I9v9vYrj | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{I9v9vYrjIw-DAz87ZW-UbUvt4Wd.QXxITO0wCMzAzNzEzW}
```

## Flag

```
pwn.college{I9v9vYrjIw-DAz87ZW-UbUvt4Wd.QXxITO0wCMzAzNzEzW}
```

### Notes 

1. The main lesson was learning to use the tee command as a debugging tool for command pipelines.
2. tee acts like a "T-splitter", sending data to the next command in the pipe AND saving a copy to a file at the same time.

# Challenge 11 Process substitution for input 

Sometimes you need to compare the output of two commands rather than two files. You might think to save each output to a file first:
```sh
hacker@dojo:~$ command1 > file1
hacker@dojo:~$ command2 > file2
hacker@dojo:~$ diff file1 file2
```
But there's a more elegant way! Linux follows the philosophy that "everything is a file". That is, the system strives to provide file-like access to most resources, including the input and output of running programs! The shell follows this philosophy, allowing you to, for example, use any utility that takes file arguments on the command line and hook it up to the output of programs, as you learned in the previous few levels.

Interestingly, we can go further, and hook input and output of programs to arguments of commands. This is done using Process Substitution. For reading from a command (input process substitution), use <(command). When you write <(command), bash will run the command and hook up its output to a temporary file that it will create. This isn't a real file, of course, it's what's called a named pipe, in that it has a file name:
```sh
hacker@dojo:~$ echo <(echo hi)
/dev/fd/63
hacker@dojo:~$
```
Where did /dev/fd/63 come from? bash replaced <(echo hi) with the path of the named pipe file that's hooked up to the command's output! While the command is running, reading from this file will read data from the standard output of the command. Typically, this is done using commands that take input files as arguments:
```sh
hacker@dojo:~$ cat <(echo hi)
hi
hacker@dojo:~$
```
Of course, you can specify this multiple times:
```sh
hacker@dojo:~$ echo <(echo pwn) <(echo college)
/dev/fd/63 /dev/fd/64
hacker@dojo:~$ cat <(echo pwn) <(echo college)
pwn
college
hacker@dojo:~$
```
Now for your challenge! Recall what you learned in the diff challenge from Comprehending Commands. In that challenge, you diffed two files. Now, you'll diff two sets of command outputs: /challenge/print_decoys, which will print a bunch of decoy flags, and /challenge/print_decoys_and_flag which will print those same decoys plus the real flag.

Use process substitution with diff to compare the outputs of these two programs and find your flag!

## Solution 

1.The goal was to compare the output of two different programs (/challenge/print_decoys and /challenge/print_decoys_and_flag) in a single command.
2.I learned to use process substitution with the <(command) syntax, which lets the shell treat the output of a command as a temporary file.
3.I used the diff command and for its two arguments, I provided the output of each program using this new syntax.
4.The final command compared the two outputs directly and showed the single different line, which was the flag.

```sh
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
55a56
> pwn.college{YOM2SVzBa9UohzcWwEDKPa9rp5_.0lNwMDOxwCMzAzNzEzW}
```

## Flag 

```
pwn.college{YOM2SVzBa9UohzcWwEDKPa9rp5_.0lNwMDOxwCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning about process substitution with the <(command) syntax.
2.This is a powerful feature that lets us use the live output of a command in any place where a filename is expected.
3.This method is much more efficient than saving the output of each command to a separate file and then comparing those files.

# Challenge 12 Writing to multiple programs 

Now you've learned that process substitution can make command output appear as files for reading with <(command). But you can also use process substitution for writing to commands!

You can duplicate data to two files with tee:
```sh
hacker@dojo:~$ echo HACK | tee THE > PLANET
hacker@dojo:~$ cat THE
HACK
hacker@dojo:~$ cat PLANET
HACK
hacker@dojo:~$
```
And you've used tee to duplicate data to a file and a command:
```sh
hacker@dojo:~$ echo HACK | tee THE | cat
HACK
hacker@dojo:~$ cat THE
HACK
hacker@dojo:~$
```
But what about duplicating to two commands? As tee says in its manpage, it's designed to write to files and to standard output:

TEE(1)                           User Commands                          TEE(1)

NAME
       tee - read from standard input and write to standard output and files
But wait! You just learned that bash can make commands look like files using process substitution! For writing to a command (output process substitution), use >(command). If you write an argument of >(rev), bash will run the rev command (this command reads data from standard input, reverses its order, and writes it to standard output!), but hook up its input to a temporary named pipe file. When commands write to this file, the data goes to the standard input of the command:
```sh
hacker@dojo:~$ echo HACK | rev
KCAH
hacker@dojo:~$ echo HACK | tee >(rev)
HACK
KCAH
```
Above, the following sequence of events took place:

bash started up the rev command, hooking a named pipe (presumably /dev/fd/63) to rev's standard input
bash started up the tee command, hooking a pipe to its standard input, and replacing the first argument to tee with /dev/fd/63. tee never even saw the argument >(rev); the shell substituted it before launching tee
bash used the echo builtin to print HACK into tee's standard input
tee read HACK, wrote it to standard output, and then wrote it to /dev/fd/63 (which is connected to rev's stdin)
rev read HACK from its standard input, reversed it, and wrote KCAH to standard output
Now it's your turn! In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands! Scroll back through the previous challenges "Duplicating piped data with tee" and "Process substitution for input" if you need a refresher on this method.
Trivia!

The observant learner will realize that the following are equivalent:
```sh
hacker@dojo:~$ echo hi | rev
ih
hacker@dojo:~$ echo hi > >(rev)
ih
hacker@dojo:~$
```
More than one way to pipe data! Of course, the second route is way harder to read and also harder to expand. For example:
```sh
hacker@dojo:~$ echo hi | rev | rev
hi
hacker@dojo:~$ echo hi > >(rev | rev)
hi
hacker@dojo:~$
```
That's just silly! The lesson here is that, while Process Substitution is a powerful tool in your toolbox, it's a very specialized tool; don't use it for everything!

## Solution 

1.The goal was to send the output of the /challenge/hack program to the input of two other programs, /challenge/the and /challenge/planet, at the same time.
2.I learned to use the tee command to split the output stream and output process substitution >(command) to treat a program's input like a file.
3.My final command started with /challenge/hack, piped its output to tee, which then sent one copy to >(/challenge/planet) and piped the other copy to /challenge/the.

```sh
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/planet) | /challenge/the
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{YpzT2MwJm5WzL7Tk0ph606VVSrA.QXwgDN1wCMzAzNzEzW}
```

## Flag 

```
pwn.college{YpzT2MwJm5WzL7Tk0ph606VVSrA.QXwgDN1wCMzAzNzEzW}
```

### Notes 

1. My main takeaway was learning about output process substitution with >(command), which lets us treat a program's input like a file you can write to.
2. The tee command is a powerful "T-splitter" that can send data to a file (or a process substitution) while also passing it down a pipe to another command.

# Challenge 13 Split-piping stderr and stdout 

Now, let's put your knowledge together. You must master the ultimate piping task: redirect stdout to one program and stderr to another.

The challenge here, of course, is that the | operator links the stdout of the left command with the stdin of the right command. Of course, you've used 2>&1 to redirect stderr into stdout and, thus, pipe stderr over, but this then mixes stderr and stdout. How to keep it unmixed?

You will need to combine your knowledge of >(), 2>, and |. How to do it is a task I'll leave to you.

In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program

## Solution 

1.The goal was to split the output of /challenge/hack, sending its normal output (stdout) to /challenge/planet and its error output (stderr) to /challenge/the.
2.I used a standard pipe (|) to send the stdout of /challenge/hack to the input of /challenge/planet.
3.To handle the error stream, I used the trick 2> >(/challenge/the) to redirect the stderr of /challenge/hack to the input of /challenge/the.
4.I combined both of these techniques into a single line to run all three programs at once and solve the challenge.

```sh
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{M-lrNemr8GqS9inwOKC3JU8ot__.QXxQDM2wCMzAzNzEzW}
```

## Flag 

```
pwn.college{M-lrNemr8GqS9inwOKC3JU8ot__.QXxQDM2wCMzAzNzEzW}
```

### Notes 

1.This was the most advanced redirection lesson, showing how to handle both stdout and stderr at the same time.
2.The key was to use a normal pipe (|) for the normal output and the special combination of error redirection (2>) and process substitution (>(...)) for the error output.

# Challenge 14 Named pipes 

You've learned about pipes using |, and you've seen that process substitution creates temporary named pipes (like /dev/fd/63). You can also create your own persistent named pipes that stick around on the filesystem! These are called FIFOs, which stands for First (byte) In, First (byte) Out.

You create a FIFO using the mkfifo command:
```sh
hacker@dojo:~$ mkfifo my_pipe
hacker@dojo:~$ ls -l my_pipe
prw-r--r-- 1 hacker hacker 0 Jan 1 12:00 my_pipe
-rw-r--r-- 1 hacker hacker 0 Jan 1 12:00 some_file
hacker@dojo:~$
```
Notice the p at the beginning of the permissions - that indicates it's a pipe! That's markedly different than the - that's at the beginning of normal files, such as some_file in the above example.

Unlike the automatic named pipes from process substitution:

You control where FIFOs are created
They persist until you delete them
Any process can write to them by path (e.g., echo hi > my_pipe)
You can see them with ls and examine them like files
One problem with FIFOs is that they'll "block" any operations on them until both the read side of the pipe and the write side of the pipe are ready. For example, consider this:
```sh
hacker@dojo:~$ mkfifo myfifo
hacker@dojo:~$ echo pwn > myfifo
```
To service echo pwn > myfifo, bash will open the myfifo file in write mode. However, this operation will hang until something also opens the file in read mode (thus completing the pipe). That can be in a different console:
```sh
hacker@dojo:~$ cat myfifo
pwn
hacker@dojo:~$
```
What happened here? When we ran cat myfifo, the pipe had both sides of the connection all set, and unblocked, allowing echo pwn > myfifo to run, which sent pwn into the pipe, where it was read by cat.

Of course, this can somewhat be done by normal files: you've learned how to echo stuff into them and cat them out. Why use a FIFO instead? Here are key differences:

No disk storage: FIFOs pass data directly between processes in memory - nothing is saved to disk
Ephemeral data: Once data is read from a FIFO, it's gone (unlike files where data persists)
Automatic synchronization: Writers block until the readers are ready, and vice-versa. This is actually useful! It provides automatic synchronization. Consider the example above: with a FIFO, it doesn't matter if cat myfifo or echo pwn > myfifo is executed first; each would just wait for the other. With files, you need to make sure to execute the writer before the reader.
Complex data flows: FIFOs are useful for facilitating complex data flows, merging and splitting data in flexible ways, and so on. For example, FIFOs support multiple readers and writers.
This challenge will be a simple introduction to FIFOs. You'll need to create a /tmp/flag_fifo file and redirect the stdout of /challenge/run to it. If you're successful, /challenge/run will write the flag into the FIFO! Go do it!

HINT: The blocking behavior of FIFOs makes it hard to solve this challenge in a single terminal. You may want to use the Desktop or VSCode mode for this challenge so that you can launch two terminals.

## Solution 

1. This challenge required using a named pipe (FIFO) and two separate terminals to get the flag.
2. First, I created the pipe in one terminal with mkfifo /tmp/flag_fifo.
3. In that same terminal (Terminal 1), I started the "reader" process by running cat /tmp/flag_fifo. This command then waited.
4. In a second, separate terminal (Terminal 2), I started the "writer" process by running /challenge/run > /tmp/flag_fifo.
5. As soon as the writer started, it sent the flag through the pipe, and the reader in Terminal 1 received it and printed it to the screen.

Terminal-1 

```sh
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at 
/tmp/flag_fifo! Here is your flag:
pwn.college{4YHqFLLSOEJaZQiQtWcpXtrWwIQ.01MzMDOxwCMzAzNzEzW}
```

Terminal-2 

```sh
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!
```

## Flag 

```
pwn.college{4YHqFLLSOEJaZQiQtWcpXtrWwIQ.01MzMDOxwCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning how to create a Named Pipe (FIFO) with the mkfifo command, which allows separate terminals to communicate.
2.The key behavior I learned is that FIFOs block (freeze) until there is a program both reading from and writing to the pipe.






