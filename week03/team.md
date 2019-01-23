![](../images/banner.jpg)

# Team Activity 03 : Pipes

##### Please work together in groups of 2 or 3

# Pipes section 3.6.3

## Instructions

1. You will be writing your team activity code in your Linux account.
2. Copy the file `/home/cs345/week03/team03.cpp` to your home directory.
3. This program creates a fork and uses a pipe to transmit a simple text message from the parent process to the child process.
4. You will be changing the code to transfer the contents of a file from the parent to the child using a pipe.
5. The parent process will open the read the file.  The filename and contents will be sent to the child process using the pipe.
6. The child process will receive the filename and contents of the file and will create that file and save the contents to that file.
7. In main, you will have two filenames. One, for the file to be read and the other a name of the file to be created.

## Suggestions / Notes

- Try getting the pipe to work without sending the filename to the child process - just transmit the contents of the file.  The child process can see the filename to be used for saving of the contents.
- How will the child process know that the parent process is finished transmitting?
- How would you handle sending the filename before the contents of the file?
- Will your code work for non-text files?
- You can use structs or data types to help with your code.

