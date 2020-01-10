![](../images/banner.jpg)

# Prepare 01 : C++ Program and Submission Lab

##### Due Monday night at Midnight MST

## Outline

For this week will be to familiarize you with the submission process of coding assignments in CS 345. While many components may be familiar to those who took CS 124, CS 165, and CS 235, there are unique features. All coding assignments in CS 345 will follow this system:

- Write and submit your code on the CSEE Linux server.  You are free to implement your code on another system or compiler.  However, you are graded on what you submit through the Linux server.  Your code must compile and run in the Linux server.

## Instructions

The first step in the coding projects is to write the code. This will work just like coding assignments in other CS classes: a) start with the provided template, b) write the code to solve the problem c) verify your solution with testBed if one is provided d) check the style e) submit it.

### A. Start with the template

The standard template for CS 345 is at the expected location:

<pre>/home/cs345/week01/template.cpp</pre>

Make sure you update the header so it gets submitted to the correct location. Submitting your project to the wrong course, professor or project will be **graded as zero**.  The assignment this week will be called `Lab 01, Submission Lab`

### B. Write the code

Write a program to prompt the user for an integer. If the provided number is not zero, then prompt him/her for another integer. This continues until you wear down the user and he/she enters '`0`'. At this point, the program will display how many integers were entered.

An example of the output is the following (user input is <span class="input">underlined</span>):

<pre>Enter an integer: <span class="input">3</span>
Enter an integer: <span class="input">4</span>
Enter an integer: <span class="input">-4</span>
Enter an integer: <span class="input">-456789</span>
Enter an integer: <span class="input">0</span>
You entered 4 integers.</pre>

Note that your program must display "`No non-zero integers were entered.`" in the case where "`0`" is the first entered value. It must display "`You entered 1 integer.`" when only one non-zero value was entered.

### C. Verify

The testBed for this assignment is:

<pre>testBed cs345/lab01 lab01.cpp</pre>

Please make sure your program runs without error.

### D. Style

Your program should be well-commented and free of any style-checker errors. You may need to review the style guidelines from [CS 124 and CS 165](https://webmailbyui-my.sharepoint.com/:b:/r/personal/comeaul_byui_edu/Documents/Shared%20with%20Everyone/cs124/cs124%20TextBook.pdf?csf=1&e=CdquAx) if you are unsure of the guidelines.

You can run style checker with:

<pre>styleChecker lab01.cpp</pre>

### E. Submit

**Online**

You will submit this assignment now. You will need to submit it again after you have had your code reviewed on the discussion board. If you have any questions how this process works, please Chapter 1.0 from [Procedural Programming in C++](https://webmailbyui-my.sharepoint.com/:b:/r/personal/comeaul_byui_edu/Documents/Shared%20with%20Everyone/cs124/cs124%20TextBook.pdf?csf=1&e=CdquAx)


**In class**

Face to face students will submit your project through the Linux Account.

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
10%</th>

<td>It is difficult to imagine how the code could be made more efficient</td>

<td>No obvious efficiency problems exist</td>

<td>One minor thing could be done to improve the efficiency of the code</td>

<td>Many obvious opportunities exist to increase performance</td>

<td>The code has horrible performance issues</td>

</tr>

<tr>

<th>Elegant  
10%</th>

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

<td>The solution is well designed and thoughtout</td>

<td>One aspect of the solution design could be improved</td>

<td>Obvious maintainability problems exist</td>

<td>Support costs on this code would be much greater than necessary</td>

</tr>

<tr>

<th>Readable  
30%</th>

<td>"Anyone" could read and understand this code</td>

<td>The code honors all the style guidelines</td>

<td>One minor style error was found</td>

<td>One obvious style error was found</td>

<td>No obvious attention was spent on readability</td>

</tr>

</tbody>

</table>