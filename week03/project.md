![](../images/banner.jpg)

# Prepare 03 : Shell Lab

##### Due Monday night at Midnight MST

This week you will be implementing a UNIX shell and history.

### A. Start with the provided code

The standard template for CS 345 is at the expected location:

```as
/home/cs345/week03/
```

In this directory, you will notice several files:

*   `lab03.cpp` : This has `main()` and will probably have all of your code.
*   `sampleHistory.cpp` : Some sample code demonstrating how to do the history feature.
*   `sampleSignal.cpp` : Some sample code demonstrating how to trap Ctrl-C.
*   `sampleSignalANSI.c` : Same as sampleSignal.cpp except in ANSI C.
*   `sample.out` : An executable that demonstrates how the working program will function.

Make sure you update the header so it gets submitted to the correct location. The assignment this week will be called `Lab 03, Shell and History`

### B. Write the code

Your program is to write a shell (a program in the operating-system that launches other programs) that has a history feature.

#### Requirements

1.  Use `fork()` and one of the family of `exec()` calls to execute commands typed in by the user. You are not to use the `system()` function.
2.  Your shell program is to be able to handle processes being put in the background.
3.  The history feature will be invoked by using a `ctrl-\`, in other words, your shell program is to have a signal handler. The history feature is described below along with some error messages to be given when using the history feature.

#### Background and Details

This project consists of writing a C++ program which serves as a shell interface that accepts user commands and then executes each command in a separate process. A shell interface provides the user a prompt after which the next command is entered. The example below illustrates the prompt `sh>` and the user's next command: `cat prog.c`. This command would display the file `prog.c` on the terminal using the UNIX `cat` command.

```as
sh> cat prog.c
```

One technique for implementing a shell interface is to have the parent process first read what the user enters on the command line (i.e. `cat prog.c`), and then create a separate child process that performs the command. Unless otherwise specified, the parent process waits for the child to exit before continuing. This is similar in functionality to what is illustrated in Figure 3.10 in the textbook. However, UNIX shells typically also allow the child process to run in the background — or concurrently — as well, by specifying the ampersand (`&`) at the end of the command. By rewriting the above command as ...

<pre>sh> cat prog.c &</pre>

... the parent and child processes now run concurrently.

The separate child process is created using the `fork()` system call and the user's command is executed by using one of the system calls in the `exec()` family (Section 3.3.1 has example code that used an `execlp()`, this lab will use `execvp()`).

#### Simple Shell

A C++ program that provides the starting point for a command line shell is supplied in `/home/cs345/week03/`. It is called `lab03.cpp`. It is a modified and enhanced version of the code in Figure 3.25 in Operating-System Concepts Seventh Edition. This program is composed of two functions: `main()` and `setup()`. The `setup()` function reads in the user's next command (which can be up to 80 characters), and then parses it into separate tokens that are used to fill the argument vector for the command to be executed. If the command is to be run in the background, it will end with '`&`', and `setup()` will update the parameter background so that the `main()` function can act accordingly. This program is terminated when the user enters `ctrl-d`, which indicates the end of input. With no input, `setup()` invokes `exit()`.

The `lab03.cpp` code given to you handles having white space before an "`&`" and has fixed an error that the book's code has. It has also been re-commented and conforms better to BYU-Idaho style requirements.

The `main()` function, of the code supplied to you, presents the prompt `COMMAND->` and then invokes `setup()`. `setup()` calls the `read()` system call to obtain input from the keyboard. The keyboard input is returned in an array of characters which is terminated with a newline ('`\n`'), not a null character. The `setup()` function then adds a null to the buffer to create a c-string. [You might remember that c-strings are a null terminated array of characters and that functions, such as `strncpy()`, which work with c-strings require a null character to terminate the string.]

The contents of the command entered by the user is modified by the `setup()` function to be a null terminated set of strings (not just a single string) and also creates the `args[]` array in preparation for passing these to the `execvp()` system call. The `args[]` array is an array of character pointers that point to the first character of the command and to the first character of each argument of the command. The `args[]` array has a `NULL` pointer placed in it to indicate the end of the valid pointers. For example, if the user enters `ls -l` at the `COMMAND->` prompt the `read()` system call returns a buffer with the characters: `l s \32 – l \n`. After `setup()` finishes setting up the `args[]` array and modifying the user's input in the input buffer for the example given above, the buffer would contain the characters: `l s \0 – l \0 \0` plus whatever other characters were left over from previous commands or whatever garbage was in the `inputBuffer[]` to begin with. For this example, the `args[0]` array will have three valid values: `args[0]` will point to the string `ls`, `args[1]` will point to the string to `–l`, and `args[2]` will have a null pointer in it.

This project is organized into three parts: (1) creating the child process and executing the command entered in at the command line, (2) adding signal handling to your code, and (3) modifying the shell to allow a history feature.

#### Creating a child Process

The first part of this project is to create a program (a shell program) that accepts commands from the user and executes those commands in a child process. The program `lab03.cpp` is provided to you as a start, or as a guide, for you.

As noted above, the `setup()` function in `lab03.cpp` loads the contents of the `args` array with pointers to the command specified by the user. This `args[]` array may then be passed to the `execvp()` function, which has the following interface ...

```as
execvp(char *command, char *params[]);
```

... where command represents the command to be performed and `params[]` stores the parameters to this command. For this project, the `execvp()` function should be invoked as `execvp(args[0], args);` be sure to check the value of background to determine if the parent process is to wait for the child to exit or not.

As noted above, UNIX shells typically allow the child process to run in the background — or concurrently with the parent process. This is done by adding the ampersand (`&`) at the end of the command. Your shell program is to have this same functionality. System calls are provided that enable a process to wait to execute any more instructions until a child process completes its processing. Two such system calls are `wait()` and `waitpid()`.

Figure 3.10 in the book shows a `wait()` system call being used. However, the functionality of the `wait()` system call has been modified with different versions of Unix/Linux and even with different versions of the kernel for the same type of Unix/Linux. For this program you might want to use `waitpid(pid, NULL, 0)` as opposed to the `wait(NULL)`. To find out more about these system calls use a search engine, the info command or the man command. Note that if you do: man wait to try to find out about waiting for a child process to finish, you will get a man page on the wait command that is built into the bash shell. You want to get the man pages for the `wait()` and `waitpid()` system calls that are in section 2 of the man pages. Do: `man 2 wait` to see those manual pages.

If the user types "`cate prog.c`" instead of "`cat prog.c`" a "`command not found`" error is generated by most shell programs. Your shell program should also print this error (print: `command not found`) when a user tries to execute a non-existent command. To implement this feature you need to understand what happens if an illegal command is given to the `execvp()` system call.

#### Signal Handling

Add a signal handler to your shell program that catches `SIGQUIT`. This signal may be generated by pressing `ctrl-\` on the keyboard. This signal will be used to in your shell to generate a command history listing.

UNIX systems use signals to notify a process that a particular event has occurred. Signals may be either synchronous or asynchronous, depending upon the source and the reason for the event being signaled. Once a signal has been generated by the occurrence of a certain event (e.g., division by zero, illegal memory access, user entering `ctrl-c`, etc.,), the signal is delivered to a process where it must be handled. A process receiving a signal may handle it by one of the following techniques:

*   Ignoring the signal
*   Using the default signal handler, or
*   Providing a separate signal-handling function.

Signals may be handled by first setting certain fields in the C++ structure `struct sigaction` and then passing this structure to the `sigaction()` system call. Signals are defined in the include files `/usr/include/signal.h` and `/usr/include/bits/signum.h`. For example, the signal `SIGINT` represents the signal for terminating a program with the control sequence `ctrl-c`. The default signal handler for `SIGINT` is to terminate the program. Alternatively, a program may choose to set up its own signal-handling function by setting the `sa_handler` field in `struct sigaction` to the name of the function which will handle the signal and then invoking the `sigaction()` function, passing it (1) the signal we are setting up a handler for, and (2) a pointer to the structure that was created.

The code provided to you in `/home/cs345/week03/sampleSignal.cpp` is a program that uses the function `handle_SIGUSR1()` for handling the `SIGUSR1` signal (not `SIGQUIT`). This code is to help you learn about signals in order to add a signal handler to your shell program. `sampleSignal.cpp` displays the message "`Caught Signal USR1`" when it is invoked due to the process being sent a `USR1` signal. The program simply runs an infinite loop printing a message every three seconds. You may desire to play with `sampleSignal.cpp` to understand the behavior of Linux signals. [The program uses the `write()` system call for performing output in the signal handler, rather than the more common `cout`, as the former is known as being signal-safe, indicating it can be called from inside a signal-handling function; such guarantees cannot be made of various implementations of `printf()` and `cout`.]

A signal-handling function should be declared above `main()`, and because control can be transferred to this function at any point, no parameters may be passed to it. Therefore, any data that it must access in your program must be declared globally, i.e. at the top of the source file before your function declarations. You might consider just setting a global flag in the signal handler to indicate that a signal was seen.

A flag that might be of interest is the `SA_RESTART` flag. It is set with: `handler.sa_flags = SA_RESTART;`

An option to using `sigaction()` discussed above, is to use the ANSI C `signal()` system call. A piece of sample code that has the same functionality of `sampleSignal.cpp` that uses this system call is found in `/home/cs345/week03/sampleSignalANSI.c`. This system call should not be used in a multi-threaded process.

#### Creating a History Feature

The next task is to modify the program in `lab03.cpp` so that it provides a history feature that allows the user access up to the 10 most recently entered commands. These commands will be numbered starting at 0 and will continue to grow larger even past 10, e.g. if the user has entered 35 commands, the 10 most recent commands should be numbered 26 to 35. This history feature will be implemented using a few different techniques.

##### `ctrl-\`

First, the user will be able to list these commands when he/she presses `ctrl-\`, which is the `SIGQUIT` signal. Instead of catching `SIGUSR1`, like `sampleSignal.cpp` did, your shell is to catch `ctrl-\`. When your shell sees a `ctrl-\` a signal handler should be invoked that outputs a list of the most recent 10 commands. The history should print with numbers on the left like the bash shell does:

```as
47  ssh 157.201.194.207
48  eixt       #bad command that was put in history
49  ls /home
50  cd /home/jonesro/cs345
51  ls --color
52  sleep 5 &
53  cd ~/cs144-examples
54  ls
55  cd /
56  rm –rf *  #don't try this</pre>
```

Allow three spaces for command numbers up to 999. The last command listed is the most recent command executed. Your code should be able to handle more than one `ctrl-\` being entered at the keyboard.

##### `r` is extra credit

With this list, the user can run any of the previous 10 commands by entering: `r x` where '`x`' is the first letter of one of the ten previous commands. If more than one command starts with '`x`', execute the most recently executed one. Also, the user should be able to run the most recent command again by just entering '`r`'. You can assume that only one space will separate the '`r`' and the first letter of the command that is to be executed from the history buffer and that the letter will be followed by '`\n`'. Again, '`r`' alone will be immediately be followed by the `\n` character if it is desired to execute the most recently executed command. NOTE: this is how the commands will appear in the `inputBuffer[]` right after the call to `read()` and before `setup()` modifies the `inputBuffer[]` and sets up `args[]`. This being said, you should consider the modifications that you might want to do to the `setup()` function and what you want to store in your history buffer. You could store what is returned from the `read()` function in `setup()` or you could store a copy of the `inputBuffer[]` and `args[]` array after the `inputBuffer[]` is processed by the `setup()` function.

Any command that is executed using the `r` command should be echoed on the user's screen and the command is also placed in the history buffer as the next command. A command such as `r d` does not go into the history list; the actual command, if one was found in the history, that is executed, does. If the user attempts to use the history facility to run a command that is not one of the ten most recently executed commands, the error message "`No matching command in history`" should be given to the user and nothing new should be entered into the history list. As you might expect, the `execvp()` function should not be called either. (It would be nice to know about improperly formed commands that are handed off to `execvp()` that appear to look valid and are not, and not include them in the history, but that does not need to be done. If the user types "`cate`" instead of "`cat`" a "`command not found`" error should be generated, however, the command "`cate`" will still be placed in the history and may be re-executed using the `r` command.)

When a signal is received by your shell program, the most likely place that your shell will be executing is in the `read()` function. The signal will be received and the signal handler will be called. The `read()` will terminate and the length variable that is assigned the return value from the `read()` call will be negative indicating that the contents of the `inputBuffer[]` character array is not valid. This (default) behavior may be modified by using the `SA_RESTART` flag.

You might want to modify `setup()` so it returns an `int` signifying if it has successfully created a valid `args[]` list. `main()` should be updated to check the return value of `setup()` if you do this.

#### Helps

1.  If you start this lab and are having problems with your history being printed multiple times or garbage being printed, re-read the problem description.
2.  A shell history program has been provided for your use. It is found at: `/home/cs345/week03/sampleHistory.cpp`.
3.  Doing some review of pointers and c-strings, if you haven't used them for some time, will probably save you a great deal of time on this lab. You might review a few sections of a CS 124 / CS 165 textbook, look at the files in the `/home/cs345/pointer_pointers` directory, or take a look at tutorials such as Norman Matloff's Unix and Linux Tutorial Center which includes sections on pointers, makefiles and signals.
4.  Another source (suggested and used by a student) is the book Advanced Linux Programming by Mark Mitchell. This book may be accessed through the "Safari Books Online" service through which BYU-Idaho makes hundreds of books available. [http://proquest.safaribooksonline.com](http://proquest.safaribooksonline.com)
5.  You might want to take a look at `shell_ptr_type.c` that is also in the `labHandouts` directory.
6.  If `cout` output a newline as part of the text being output, then a flush is done, otherwise you need to do a `cout.flush()`.
7.  It might be interesting to learn about the history feature of the bash shell or other shells. The `man` or `info` commands may be used to do this. You might be interested in the bash shell `fc` command.
8.  The `ps` command is used to see what commands are running. There is also a `sleep` command that can be helpful in testing your shell. The following was done with a bash shell:

    <pre>[jonesro@aus213l5 ~]$ sleep 5 &
    [1] 5266
    [jonesro@aus213l5 ~]$ sleep 7 &
    [2] 5267
    [jonesro@aus213l5 ~]$ ps
      PID TTY          TIME CMD
     5154 pts/2    00:00:00 bash
     5266 pts/2    00:00:00 sleep
     5267 pts/2    00:00:00 sleep
     5268 pts/2    00:00:00 ps
    [jonesro@aus213l5 ~]$
    [1]-  Done                    sleep 5
    [jonesro@aus213l5 ~]$
    [2]+  Done                    sleep 7
    [jonesro@aus213l5 ~]$</pre>

Here are some sample test sequences for your shell:

<pre>ls
date
uptime
pwd
^\
^d</pre>

Another test runthrough of the shell:

<pre>ls
ls -s
ls -l
df
df -i
df -h
who -i
who -d
who
pwd
uptime
^\              #should not show the first ls
r w             #execute who (not who -d or who -i)
r l             #execute ls -l
touch shell
ps
^\              #history back to: df –h
r               #repeat last command given
^d

#Test #3
sleep 3         #should wait for completion
sleep 5&        #should not wait for completion
sleep 15&       #should not wait for completion
ls
pwd
ps
r s             #execute: sleep 15&
^\              #history listing
r p             #execute: ps
^\
now
now is the
r n
r a
^\
^d</pre>

### C. Verify

There is no test-bed for this assignment. You will have to manually verify the program by-hand.

### D. Style

Your program should be well-commented and free of any style-checker errors.

## 4\. Submit - Due Monday midnight

Submit your code using the submit program in your Linux Account.  Since there is not header in the code file, submit will prompt you for the instructor, course and lab.

## 5\. Rubric

<table class="rubric">

<tbody>
<tr>
<th> </th>

<th>Exceptional  
100%</th>

<th>Good  
90%</th>

<th>Acceptable  
70%</th>

<th>Developing  
50%</th>

<th>Missing  
0%</th>

</tr>

<tr>

<th>Correct  
40%</th>

<td>No defects could be found</td>

<td>The code works as designed</td>

<td>One aspect of the code failed or one glaring bug exists in the code</td>

<td>Elements of the solution exist</td>

<td>No attempt was made to solve the problem</td>

</tr>

<tr>

<th>Efficient  
10%</th>

<td>It is difficult to imagine how the code could be made more efficient</td>

<td>No obvious efficiency problems exist</td>

<td>One minor thing could be done to improve the efficiency of the code</td>

<td>Many obvious opportunities exist to increase performance</td>

<td>The code has horrible performance issues</td>

</tr>

<tr>

<th>Elegant  
20%</th>

<td>The most elegant solution imaginable was found</td>

<td>The code design is "professional"</td>

<td>One minor inelegancy was found</td>

<td>One obvious inelegancy remains in the code</td>

<td>The code was thrown together</td>

</tr>

<tr>

<th>Maintainable  
10%</th>

<td>The code lends itself to reuse and extension</td>

<td>The solution is well designed and thought out</td>

<td>One aspect of the solution design could be improved</td>

<td>Obvious maintainability problems exist</td>

<td>Support costs on this code would be much greater than necessary</td>

</tr>

<tr>

<th>Readable  
20%</th>

<td>"Anyone" could read and understand this code</td>

<td>The code honors all the style guidelines</td>

<td>One minor style error was found</td>

<td>One obvious style error was found</td>

<td>No obvious attention was spent on readability</td>

</tr>

</tbody>

</table>

An additional 10% will be allocated if the `r` command is correctly implemented.
