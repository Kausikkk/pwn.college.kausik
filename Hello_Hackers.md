# Challenge 1 Intro To Commands

In this challenge, you will invoke your first command! When you type a command and hit enter, the command will be invoked, as so:

```sh
hacker@dojo:~$ whoami  
hacker
hacker@dojo:~$
```
Here, the user executed the whoami command, which simply prints the username (hacker) to the terminal. When the command terminates, 
the shell once again displays the prompt, ready for the next command.

## Solution:

My approach to this challenge was straight. The instructions said that I needed to invoke the `hello` command to get the flag.
So, I typed `hello` into the terminal and ran it. The command's output was the flag.

```sh
$ hello
```

## Flag:

```
pwn.college{IIQMrQx6-Y7koahFfr0Gyi0w6-7.QX3YjM1wCMzAzNzEzW}
```

### Notes:
1. I learnt that commands in Linux are case sensitive: hello is different from HELLO.
2. ```$``` at the end is a status indicator showing that I am a regular user.

# Challenge 2 Intro To Arguments

Let's try something more complicated: a command with arguments, which is what we call additional data passed to the command. When you type a line of text and hit enter, the shell actually parses your input into a command and its arguments. The first word is the command, and the subsequent words are arguments. Observe:

```sh
hacker@dojo:~$ echo Hello
Hello
hacker@dojo:~$
```
In this case, the command was echo, and the argument was Hello. echo is a simple command that "echoes" all of its arguments back out onto the terminal, like you see in the session above.

Let's look at echo with multiple arguments:

```sh
hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
hacker@dojo:~$
```
In this case, the command was echo, and Hello and Hackers! were the two arguments to echo. Simple!

## Solution:

1. First I read the description to understand what command line arguments are.  
2. Next I identified the specific task, which is to run the `hello` command with `hackers` as the argument.  
3. Finally, I executed the command `hello hackers` in the terminal, which showed the flag.

```sh
$ hello hackers
```

## Flag:

```
pwn.college{MsLIeQj9pecP-t9kxzz0T-Rl-Ch.QX4YjM1wCMzAzNzEzW}
```

### Notes:

1. The `echo` command is a utility whose main function is to display text
2. My main learning was how the shell understands what I type and use the space character to split the line.

# Challenge 3 Command History 

You're going to type a lot of commands, and typing everything from scratch can be annoying. Luckily, the shell saves a history of every command you invoke.

You can scroll through those saved commands with the up/down arrow keys.

## Solution:

The flag is already in the command history 

we need to use `up` arrow to get our flag

## Flag: 

```
pwn.college{4GiVsWLysbS-4umKglSefNifETm.0lNzEzNxwCMzAzNzEzW}
```

### Notes:

Pressing the Up arrow key allows me to go through my previous commands. This saves me a lot of time on retyping.








   
