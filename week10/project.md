![](../images/banner.jpg)

# Ponder 10 : Page Replacement Lab

##### Due Monday night at Midnight MST

This week will be to write a program to implement the page replacment algorithms discussed in the chapter.


### A. Start with the provided code

Most of the code for this program is provided. You are only to implement the page replacement algorithms, not the user interface. The code is provided in the following location:

<pre>/home/cs345/week10/</pre>

Here you will find several files:

*   `makefile` : compile the files and create a TAR for submission. This should not need to be changed.
*   `lab10.cpp` : defines `main()` and a few user interface functions. This should not need to be changed.
*   `lab10.out` : an executable so you can see how it should work. This is mostly provided for testing purposes.
*   `pr.h` : defines the <span class="code">PageReplacementAlgorithm</span> base-class and should not need to be changed.
*   `pr.cpp` : implements the interfaces for `PageReplacementAlgorithm` and does not need to be changed.
*   `prBasic.h` : contains an implementation for a simple page replacement algorithm. This code is provided. You might want to use it as a reference when implementing the rest of the other algorithms.
*   `prFIFO.h` : a stub for the FIFO algorithm you will have to write. You will have to make changes to this file.
*   `prLRU.h` : a stub for the LRU algorithm you will have to write. You will have to make changes to this file.
*   `prSecond.h` : a stub for the Second Chance algorithm you will have to write. You will have to make changes to this file.
*   `test1.txt` ... `test3.txt` : test files used for `testBed`
*   `test4.txt` : a test file matching the reference string in the textbook

Make sure you update the header in the makefile so it gets submitted to the correct location. The assignment this week will be called `Lab 10, Page Replacement Lab`

### B. Write the code

Implement four scheduling algorithms as mentioned in the textbooks. These algorithms are:

*   **Basic**: Basic Page found in section 8.4.1 FIFO Page Replacement on page 384-387
*   **FIFO**: First-In-First-Out found in section 8.4.2 FIFO Page Replacement on page 387-388
*   **LRU**: Least Recently Used found in section 8.4.4 LRU Page Replacement on page 390-392
*   **Second**: Second-Chance found in section 8.4.5.2 Second-Chance Algorithm on page 392-393

The implementation for a basic page replacement algorithm (random) is provided. Also provided is the code to select the proper page replacement algorithm and to display a report. An example of the output is the following. Consider the following page requests:

<pre>2 3 2 1 5 2 4 5 3 2 5 2</pre>

All of these are in a file called `/home/cs345/week10/test2.txt`. If this were to be executed using First-In-First-Out using 2 slots, the following would be the output:

<pre>How many slots: <span class="input">2</span>
What is the filename of the process file? <span class="input">/home/cs345/week10/test2.txt</span>
Please select one of the following page replacement algorithms:
  1\. Basic Page Replacement
  2\. First-In-First-Out
  3\. Least Recently Used
  4\. Second Chance
< <span class="input">2</span>
2 3 2 1 5 2 4 5 3 2 5 2
+-+-+-+-+-+-+-+-+-+-+-+-+
|2|2|2|1|1|2|2|5|5|2|2|2|
| |3|3|3|5|5|4|4|3|3|5|5|
+-+-+-+-+-+-+-+-+-+-+-+-+
 F F   F F F F F F F F
Hit ratio: 2/12</pre>

You are to implement the constructor and the `run(int pageNumber)` method for the First-In-First-Out, Least-Recently-Used, and Second-Chance algorithms. This `run()` method will simulate a given page request. At the end it must ensure that the passed parameter is somewhere in the `pageFrame` vector. It must also call `PageReplacementAlgorithm::record(pageNumber, true /*pageFaultOccurred*/);` so we can display the nifty report you see in the output example above. You may need to provide additional member variables or methods to accomplish this task.

### C. Verify

The testBed for this assignment is:

<pre>testBed cs345/lab10 lab10.tar</pre>

Please make sure your program runs without error. As a reminder, testBed can accept `.cpp`, `.out`, and `.tar` files.

### D. Style

Your program should be well-commented and free of any style-checker errors.

## Submit

After your code has been reviewed, incorporate your changes back into your code. Make sure it still compiles and passes testBed. When you submit it, double-check that the file was submitted to the correct location.

### Assessment

Your grade for this activity will be according to the following rubric:

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

<td>The code works as designed, including passing testBed</td>

<td>One test failed to pass on testBed or one glaring bug exists in the code</td>

<td>Elements of the solution exist</td>

<td>No attempt was made to solve the problem</td>

</tr>

<tr>

<th>Efficient  
20%</th>

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

<td>The code looks "professional"</td>

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
10%</th>

<td>"Anyone" could read and understand this code</td>

<td>The code honors all the style guidelines</td>

<td>One minor style error was found</td>

<td>One obvious style error was found</td>

<td>No obvious attention was spent on readability</td>

</tr>

</tbody>

</table>