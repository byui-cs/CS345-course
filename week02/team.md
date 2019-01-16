![](../images/banner.jpg)

# 02 Teach : Linux Commands

##### Please work together in groups of 2 or 3

In this team activity, we will learning some basic Linux commands.

## Command Section

We will be using the following Linux commands in the small problems below.  I will leave it up to you and your team to search the **Internet for examples** on how to use these commands.


**ls** - Use the "ls" command to know what files are in the directory you are in. You can see all the hidden files by using the command “ls -a”.

**wc** - Displays the number of lines, words and bytes of a file or stream of text.

**echo** - The "echo" command helps us move some data, usually text into a file. For example, if you want to create a new text file or add to an already made text file, you just need to type in, “echo hello, my name is alok >> new.txt”. You do not need to separate the spaces by using the backward slash here, because we put in two triangular brackets when we finish what we need to write.

```bash
echo "Hello World"
Hello World
echo {0..9}
0 1 2 3 4 5 6 7 8 9
echo {a..d}{1..4}
a1 a2 a3 a4 b1 b2 b3 b4 c1 c2 c3 c4 d1 d2 d3 d4
```

**sort** - Sort text files

**cut** - Divide a file into several parts

```bash
echo 'baz' | cut -b 2
a
echo 'baz' | cut -b 1-2
ba
echo 'baz' | cut -b 1,3
bz
```

**date** - Display or change the date & time

**grep** - Search file(s) for lines that match a given pattern

**find** - Search for files that meet a desired criteria

**cat** - Use the cat command to display the contents of a file. It is usually used to easily view programs.

**tac** - Concatenate and write files in reverse

**head** - Output the first part of file(s).  You can decide on the number of lines to display.

**tail** - Output the last part of files.  You can decide on the number of lines to display.


## Tasks

For these tasks, you can use any directory in your Linux account.  I would use a directory that has lots of files in it.

1. Display the list of files in ascending order of file size
1. Display the list of files in ascending order of file modification
1. Display the number of files in a directory
1. Display the number of files that start with the letter 'a' in a directory
1. Display the 3 largest files (just the file names) in a directory
1. Display the 2nd largest file name (just the file name) in a directory
1. display the 5th line in a text file
1. use the commands `head` and `tac` to display the last line in a text file.
1. display current time
1. display the current time zone
1. display all of the files that contain "int" (ie., use cpp files)
1. display all of the files that don't contain "double" (ie., use cpp files)
1. Use the echo command to create a text file that contains "hello world"
1. Using the command echo command, create output of all of the combinations of "NAAN" where N is a number, A is a letter.
1. Display the number of combinations that the above echo command creates. Example: "There are N combinations"
1. The submit command on the Linux system was written by the CS department.  It looks for the assignment, professor and course in the CPP header.  Use Linux commands to get that information from one of your old CPP assignments.  You can divide the problem into three parts. (ie., display the assignment number, then use Linux commands to get the professor, etc...).  You need to handle different sized professor names.

For Example:

```
 1 /***********************************************************************
 2 * Program:
 3 *    Assignment 11, Monthly Budget
 4 *    Brother Smith, CS124
```

```
 1 /***********************************************************************
 2 * Program:
 3 *    Assignment 11, Monthly Budget
 4 *    Brother Comeau, CS124
```


displays

```bash
11
Comeau
CS124
```