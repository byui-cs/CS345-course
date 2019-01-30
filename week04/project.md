![](../images/banner.jpg)

# Prepare 04 : Scheduling Lab

##### Due Monday night at Midnight MST

This week, the project will be to write a program to implement the scheduling algorithms discussed in the chapter. 

### A. Start with the provided code

Most of the code for this program is provided. You are only to implement the scheduling algorithms, not the user interface. The code is provided in the following location:

```as
/home/cs345/week04/
```

Here you will find several files:

* `makefile` : compile the files and create a TAR for submission. This should not be changed.
* `lab04.cpp` : defines `main()`. This should not be changed.
* `lab04.out` : an executable so you can see how it should work. This is mostly provided for testing purposes.
* `process.h` : captures the notion of a single process running on the system. This should not be changed.
* `schedule.h` : defines the <span class="code">Disbatch</span> base-class. This should not be changed.
* `schedule.cpp` : implements the interfaces for `Disbatch`. This should not be changed.
* `scheduleFCFS.h` : contains the First-Come-First-Serve scheduling algorithm. This code is provided. You might want to use it as a reference when implementing the rest of the scheduling algorithms. This should not be changed.
* `scheduleRR.h` : a stub for the Round-Robin algorithm. **Your edits go here.**
* `scheduleSJF.h` : a stub for the Shortest-Job-First algorithm. **Your edits go here.**
* `scheduleSRT.h` : a stub for the Shortest-Remaining-Time algorithm. **Your edits go here.**
* `test1.txt` ... `test4.txt` : a collection of test files. This should not be changed.

Make sure you update the header in the makefile so it gets submitted to the correct location. The assignment this week will be called `Lab 04, Scheduling Algorithm`

### B. Write the code

Implement four scheduling algorithms as mentioned in the textbooks. These algorithms are:

* **FCFS**: First-Come-First-Serve
* **RR**: Round-Robin
* **SJF**: Shortest-Job-First also known as shortest-remaining-time-first
* **SRT**: Shortest-Remaining-Time

The implementation for FCFS (First-Come-First-Serve) is provided. Also provided is the code to select the proper scheduling algorithm and to display a report. An example of the output is the following. Consider five processes:

```as
     A  0 3
     B  2 6
     C  4 4
     D  6 5
     E  8 2
```

Here the first column is the process name, the second is the arrive time, and the third is the service time. If this were to be executed using First-Come-First-Serve, the following would be the output:

```tex
Please select one of the following scheduling algorithms:
  1\. First-Come-First-Serve
  2\. Round-Robin where Time Quanta is 1
  3\. Round-Robin where Time Quanta is 4
  4\. Shortest-Job-First non-preemptive
  5\. Shortest-Remaining-Time
> <span class="input">1</span>
What is the filename of the process file? <span class="input">test1.txt</span>

Process Table
     0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19
 A   #  #  #
 B            #  #  #  #  #  #
 C                              #  #  #  #
 D                                          #  #  #  #  #
 E                                                         #  #

Statistics Table
         Finish Time  Turnaround Time    Running Ratio
 A                 3                3              1.0
 B                 9                7              1.2
 C                13                9              2.2
 D                18               12              2.4
 E                20               12              6.0
               mean:              8.6              2.6

Wait Statistics
Total wait time:   23
Average wait time: 4.6
```

You are to implement the `clock()` and `startProcess()` method for the Round-Robin, Shortest-Job-First, and Shortest-Remaining-Time algorithms. This `clock()` method will determine what is to happen during a given clock cycle. The `startProcess()` method adds a new process to the ready queue (or whatever data structure you need for a given scheduling algorithm). You may need to provide additional member variables or methods to accomplish this task.

### C. Verify

The testBed for this assignment is:

<pre>testBed cs345/lab04 lab04.tar</pre>

Please make sure your program runs without error.

### D. Style

Your program should be well-commented and free of any style-checker errors.

## 4\. Submit - Due Monday midnight

Please submit your TAR file to `Lab 04, Scheduling Lab`.

### Rubric

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
20%</th>

<td>"Anyone" could read and understand this code</td>

<td>The code honors all the style guidelines</td>

<td>One minor style error was found</td>

<td>One obvious style error was found</td>

<td>No obvious attention was spent on readability</td>

</tr>

</tbody>

</table>
