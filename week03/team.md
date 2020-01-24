![](../images/banner.jpg)

# Team Activity 03 : Pipes

##### Please work together in groups of 2 or 3

# Pipes section 3.6.3

## Instructions

1. You will be writing your team activity code in your Linux account.
2. Copy the file `/home/cs345/week03/team03.cpp` to your home directory.
3. This program creates a fork and uses a pipe to transmit a simple text message from the parent process to the child process.
4. You will be changing the code to transfer the contents of a file from the parent to the child using a pipe.
5. The parent process will:
    - Open the read the file. (filename1.txt).
    - Send the filename2.txt to the child through the pipe.
    - Read blocks of data from the file and send them through the pipe.
    - Close the file and the pipe
6. The child process will:
   - Receive the filename (filename2.txt) and create that file for writing.
   - Read blocks of data from the pipe. (Note: the function read() returns the number of bytes read from the pipe).
   - Close the file and the pipe.

## Suggestions / Notes

- Try getting the pipe to work without sending the filename to the child process - just transmit the contents of the file.  The child process can see the filename to be used for saving of the contents.
- How will the child process know that the parent process is finished transmitting?
- How would you handle sending the filename before the contents of the file?
- Will your code work for non-text files?
- You can use structs or data types to help with your code.

## Sample code to copy a file

```c++
#include <stdlib.h>
#include <stdio.h>

#define BUFFERSIZE    1024 * 4

int main()
{
   char *filename1 = "filename1.txt";
   char *filename2 = "filename2.txt";

   // copy the file
   int count = 0;

   FILE* srcHandle = fopen (filename1, "r");
   FILE* destHandle = fopen(filename2, "w");

   char buffer[BUFFERSIZE];

   // Read the first buffer block
   size_t amountRead = fread(buffer, 1, BUFFERSIZE, srcHandle);
   printf("%d bytes read\n", amountRead);
   while (amountRead > 0)
   {
      count += amountRead;
      fwrite(buffer, 1, amountRead, destHandle);

      // Keep reading until 0 is returned
      amountRead = fread(buffer, 1, BUFFERSIZE, srcHandle);
      printf("%d bytes read\n", amountRead);
   }
   
   fclose(srcHandle);
   fclose(destHandle);
   
   // display stats
   printf("%d bytes copied\n", count);
   
   return 0;
}
```