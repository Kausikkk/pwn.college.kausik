# Challenge 1 Printing variables 

Let's start with printing variables out. The /challenge/run program will not, and cannot, give you the flag, but that's okay, because the flag has been put into the variable called "FLAG"! Just have your shell print it out!

You can accomplish this using a number of ways, but we'll start with echo. This command just prints stuff. For example:
```sh
hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
```
You can also print out variables with echo, by prepending the variable name with a $. For example, there is a variable, PWD, that always holds the current working directory of the current shell. You print it out as so:
```sh
hacker@dojo:~$ echo $PWD
/home/hacker
```
Now it's your turn. Have your shell print out the FLAG variable and solve this challenge!

## Solution 

1. The goal of this challenge was to print the value of a shell variable named FLAG.

2. I learned that to get the value of a variable, you must put a dollar sign ($) in front of its name.

3. I used the echo command to print the variable's value to the screen.

4. The final command, echo $FLAG, successfully read the FLAG variable and printed its content.
   
```sh
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{g3MSFax4oHaLdiUO8pr5J9YOPOU.QX3UTN0wCMzAzNzEzW}
```

## Flag

```
pwn.college{g3MSFax4oHaLdiUO8pr5J9YOPOU.QX3UTN0wCMzAzNzEzW}
```

### Notes 

1. The main lesson was learning about shell variables, which are like named boxes for storing text.

2. The key syntax to remember is that you must use a dollar sign ($) in front of a variable's name to get the value that is stored inside it.


# Challenge 2 Setting variables 

Naturally, as well as reading values stored in variables, you can write values to variables. This is done, as with many other languages, using =. To set variable VAR to value 1337, you would use:
```sh
hacker@dojo:~$ VAR=1337
```
Note that there are no spaces around the =! If you put spaces (e.g., VAR = 1337), the shell won't recognize a variable assignment and will, instead, try to run the VAR command (which does not exist).

Also note that this uses VAR and not $VAR: the $ is only prepended to access variables. In shell terms, this prepending of $ triggers what is called variable expansion, and is, surprisingly, the source of many potential vulnerabilities (if you're interested in that, check out the Art of the Shell dojo when you get comfortable with the command line!).

After setting variables, you can access them using the techniques you've learned previously, such as:
```sh
hacker@dojo:~$ echo $VAR
1337
```
To solve this level, you must set the PWN variable to the value COLLEGE. Be careful: both the names and values of variables are case-sensitive! PWN is not the same as pwn and COLLEGE is not the same as College.

## Solution 

1.The goal of this challenge was to create a shell variable named PWN and give it the value COLLEGE.
2.I learned the correct syntax for this is VARIABLE=VALUE, with absolutely no spaces around the equals sign.
3.I also remembered not to use a dollar sign ($) when setting a variable.
4.I ran the command PWN=COLLEGE, which correctly set the variable and immediately solved the challenge.

```sh
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UkxVeF51jtvXdb4N5HNOqadQFKW.QX5UTN0wCMzAzNzEzW}
```

## Flag 

```
pwn.college{UkxVeF51jtvXdb4N5HNOqadQFKW.QX5UTN0wCMzAzNzEzW}
```

### Notes 

1. The most important rule I learned is that you cannot have any spaces around the = when you set a variable.

# Challenge 3 Multi-word variables 

In this level, you will learn about quoting. Spaces have special significance in the shell, and there are places where you can't use them spuriously. Recall our variable setting:
```sh
hacker@dojo:~$ VAR=1337
```
That sets the VAR variable to 1337, but what if you wanted to set it to 1337 SAUCE? You might try the following:
```sh
hacker@dojo:~$ VAR=1337 SAUCE
```
This looks reasonable, but it does not work, for similar reasons to needing to have no spaces around the =. When the shell sees a space, it ends the variable assignment and interprets the next word (SAUCE in this case) as a command. To set VAR to 1337 SAUCE, you need to quote it:
```sh
hacker@dojo:~$ VAR="1337 SAUCE"
```
Here, the shell reads 1337 SAUCE as a single token, and happily sets that value to VAR. In this level, you'll need to set the variable PWN to COLLEGE YEAH. Good luck!

## Solution 

1.The goal of this challenge was to set a variable (PWN) to a value that contained a space (COLLEGE YEAH).
2.I learned that to include spaces in a variable's value, the entire value must be wrapped in quotes.
3.I ran the command PWN="COLLEGE YEAH", which correctly assigned the multi-word string to the variable.
4.This immediately solved the challenge and printed the flag.

```sh
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{M8nSuq2_O7hoKxPsW7ssyyFrZLd.QXwYTN0wCMzAzNzEzW
```

## Flag 

```
pwn.college{M8nSuq2_O7hoKxPsW7ssyyFrZLd.QXwYTN0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was that we must use quotes (like " ") when we want to put a value with spaces into a variable.
2.This is because the shell uses the space character to separate commands and arguments.

# Challenge 4 Exporting variables 

By default, variables that you set in a shell session are local to that shell process. That is, other commands you run won't inherit them. You can experiment with this by simply invoking another shell process in your own shell, like so:
```sh
hacker@dojo:~$ VAR=1337
hacker@dojo:~$ echo "VAR is: $VAR"
VAR is: 1337
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
```
VAR is: 
In the output above, the $ prompt is the prompt of sh, a minimal shell implementation that is invoked as a child of the main shell process. And it does not receive the VAR variable!

This makes sense, of course. Your shell variables might have sensitive or weird data, and you don't want it leaking to other programs you run unless it explicitly should. How do you mark that it should? You export your variables. When you export your variables, they are passed into the environment variables of child processes. You'll encounter the concept of environment variables in other challenges, but you'll observe their effects here. Here is an example:
```sh
hacker@dojo:~$ VAR=1337
hacker@dojo:~$ export VAR
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
VAR is: 1337
```
Here, the child shell received the value of VAR and was able to print it out! You can also combine those first two lines.
```sh
hacker@dojo:~$ export VAR=1337
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
VAR is: 1337
```
In this challenge, you must invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported (e.g., not inherited by /challenge/run). Good luck!

## Solution 

1.The goal of this puzzle was to set two variables, PWN and COLLEGE, based on specific export rules. 
2.I needed to set the PWN variable to COLLEGE and export it so that other programs could see it. 
3.The COLLEGE variable had to be set to PWN but not exported, keeping it as a private, local variable. 
4.I set the variables correctly using export PWN=COLLEGE and then COLLEGE=PWN. 
5.Finally, running /challenge/run verified that the variables were set properly and gave me the flag.

```sh
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{UxLt0YvTt3st8ngp6XEEuZ6lgiL.QXyYTN0wCMzAzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

## Flag 

```
pwn.college{UxLt0YvTt3st8ngp6XEEuZ6lgiL.QXyYTN0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was the difference between a local variable and an environment variable.
2.Local variables are private to our current shell, while environment variables  are passed down to any programs we run.

# Challenge 5 Printing exported variables 

There are multiple ways to access variables in bash. echo was just one of them, and we'll now learn at least one more in this challenge.

Try the env command: it'll print out every exported variable set in your shell, and you can look through that output to find the FLAG variable!

## Solution 

1.The goal of this challenge was to find the value of an exported environment variable named FLAG.
2.The lesson introduced the env command, which lists all currently set environment variables.
3.I ran the env command, which printed a list of all the variables.
4.I then looked through this list manually and found the line that started with FLAG=, which contained the correct flag.

```sh
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=47173e1e252138a46e161bfcb2595945565847c651da530838db087cc27f0598
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{IVi8IFrOEoLdHTrH21XciQLEeSp.QX4UTN0wCMzAzNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

## Flags 

```
pwn.college{IVi8IFrOEoLdHTrH21XciQLEeSp.QX4UTN0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning the env command, which gives a full list of all active environment (exported) variables.

# Challenge 6 Storing command output 

In the course of working with the shell, you will often want to store the output of some command into a variable. Luckily, the shell makes this quite easy using something called Command Substitution! Observe:
```sh
hacker@dojo:~$ FLAG=$(cat /flag)
hacker@dojo:~$ echo "$FLAG"
pwn.college{blahblahblah}
hacker@dojo:~$
```
Neat! Now, you practice. Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag!

Trivia: You can also use backticks instead of $(): FLAG=`cat /flag` instead of FLAG=$(cat /flag) in the example above. This is an older format, and has some disadvantages (for example, imagine if you wanted to nest command substitutions. How would you do $(cat $(find / -name flag)) with backticks? The official stance of pwn.college is that you should use $(blah) instead of `blah`.

## Solution 

1.The goal of this challenge was to capture the output of the /challenge/run program and store it directly into a variable named PWN.
2.My first command, PWN=$(/challenge/run), ran the program and saved its output into the PWN variable.
3.The challenge then instructed me to print the variable, so my second command was echo "$PWN", which displayed the flag.

```sh
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{o-VfLR76y5y5wKzCS3lBzgb850-.QX1cDN1wCMzAzNzEzW}
```

## Flag 

```
pwn.college{o-VfLR76y5y5wKzCS3lBzgb850-.QX1cDN1wCMzAzNzEzW}
```

### Notes 

1.The instructions mentioned an older way to do this using backticks (`command`), but said that the $(command) way is better.

# Challenge 7 Reading input 

We'll start with reading input from the user (you). That's done using the aptly named read builtin, which reads input into a variable!

Here is an example using the -p argument, which lets you specify a prompt (otherwise, it would be hard for you, reading this now, to separate input from output in the example below):
```sh
hacker@dojo:~$ read -p "INPUT: " MY_VARIABLE
INPUT: Hello!
hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
You entered: Hello!
```
Keep in mind, read reads data from your standard input! The first Hello!, above, was inputted rather than outputted. Let's try to be more explicit with that. Here, we annotated the beginning of each line with whether the line represents INPUT from the user or OUTPUT to the user:
```sh
 INPUT: hacker@dojo:~$ echo $MY_VARIABLE
OUTPUT:
 INPUT: hacker@dojo:~$ read MY_VARIABLE
 INPUT: Hello!
 INPUT: hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
OUTPUT: You entered: Hello!
```
In this challenge, your job is to use read to set the PWN variable to the value COLLEGE. Good luck!

## Solution 

1.he goal of this challenge was to use the read command to get input from the keyboard and set a variable.
2.I needed to set the variable PWN to the value COLLEGE.
3.I first ran the command read PWN, which made the shell pause and wait for me to type something.
4.I then typed COLLEGE and pressed Enter.
5.This saved my input into the PWN variable, which solved the challenge and printed the flag.

```sh
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{0QgcqdmIGOvJtpLZxOt2zy72OMD.QX4cTN0wCMzAzNzEzW}
```

## Flag 

```
pwn.college{0QgcqdmIGOvJtpLZxOt2zy72OMD.QX4cTN0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning the read command, which is the standard way to get user input from the keyboard and save it into a variable.

# Challenge 8 Reading Files 

Often, when shell users want to read a file into an environment variable, they do something like:
```sh
hacker@dojo:~$ echo "test" > some_file
hacker@dojo:~$ VAR=$(cat some_file)
hacker@dojo:~$ echo $VAR
test
```
This works, but it represents what grouchy hackers call a "Useless Use of Cat". That is, running a whole other program just to read the file is a waste. It turns out that you can just use the powers of the shell!

Previously, you read user input into a variable. You've also previously redirected files into command input! Put them together, and you can read files with the shell.
```sh
hacker@dojo:~$ echo "test" > some_file
hacker@dojo:~$ read VAR < some_file
hacker@dojo:~$ echo $VAR
test
```
What happened there? The example redirects some_file into the standard input of read, and so when read reads into VAR, it reads from the file! Now, use that to read /challenge/read_me into the PWN environment variable, and we'll give you the flag! The /challenge/read_me will keep changing, so you'll need to read it right into the PWN variable with one command!

## Solution 

1.The goal of this challenge was to read the contents of the /challenge/read_me file into a variable named PWN in a single, efficient command.
2.I learned to do this by combining the read command with input redirection (<).
3.The single command read PWN < /challenge/read_me read the file's content directly into the PWN variable, which solved the challenge.

```sh
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{YnsMpOtoaifbZFzQsghELdtmEP8.QXwIDO0wCMzAzNzEzW}
```

## Flag 

```
pwn.college{YnsMpOtoaifbZFzQsghELdtmEP8.QXwIDO0wCMzAzNzEzW}
```

### Notes 

1.The main lesson was learning the most efficient way to read the contents of a file into a variable, which is read VARIABLE < filename.



