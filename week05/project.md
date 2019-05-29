![](../images/banner.jpg)

# Prepare 05 : Threads Lab

##### Due Monday night at Midnight MST

This week, you will be implementing a program to perform matrix multiplication using threads.

### A. Start with the provided code

You will write the code for this project basically from scratch. There will be some sample code and a makefile provided, however:

<pre>/home/cs345/week05/</pre>

Here you will find several files:

*   `makefile` : compile the files and create a TAR for submission
*   `lab05.cpp` : all your code will go here
*   `sampleHello.cpp` : the simplest example of code to spawn a thread
*   `sampleParam.cpp` : an example that passes a parameter from the parent thread to the child, and that passes a parameter from the child back to the parent thread
*   `sampleGlobal.cpp` : an example where multiple child threads and the parent thread share the same global data-structure
*   `sampleSum.cpp` : a more complex example showing how to spawn a number of threads

Make sure you update the header in the makefile so it gets submitted to the correct location. The assignment this week will be called `Lab 05, Threads`

### B. Write the code

Write a program that uses threads to do matrix multiplication. Code is provided which will read the matricies from a file and display them on the screen. Your assignment is to write the code to perform matrix multiplication. This must be done with multiple threads: one thread per cell in the destination matrix.

#### Matrix Multiplication

A matrix is a 2 dimensional array of numbers. Many arithmetic operations that can be performed with integers can also be performed with matricies. One of these operations is multiplication. The details of how to perform matrix multiplication will not be presented here. Instead, you will need to conduct some research. One good source Interactive Mathematics:


[Interactive Mathematics : Multiplication of Matricies](http://www.intmath.com/matrices-determinants/4-multiplying-matrices.php)

[Interactive Mathematics : Multiplying matrices - examples](http://www.intmath.com/matrices-determinants/matrix-multiplication-examples.php)

A stub function for `multiply()` is provided:

```c++
/**************************************************
 * MULTIPLY
 * Perform matrix multiplication
 *************************************************/
bool multiply(MatrixMultiplication & m)
{
   int numRowDes = m.numRowLHS;
   int numColDes = m.numColRHS;

   m.arrayDestination = new int[numRowDes * numColDes];
   for (int row = 0; row < numRowDes; row++)
      for (int col = 0; col < numColDes; col++)
         m.arrayDestination[row * numColDes + col] = 0;

   if (m.numRowRHS != m.numColLHS)
      return false;

   /////////////////////////////
   // Your code goes here

   // Your code goes here
   ////////////////////////////

   return true;
}
```

#### Threads

You are required to use threads to solve this problem. In fact, you are required to use one thread per cell of the destination matrix. If, for example, the resulting matrix was 3x4, then 12 threads must be spawned.

#### Examples

Consider a 2x2 matrix.

<table style="border: 1px solid white; border-collapse: collapse;">

<tbody>

<tr style="border-style: solid; border-left: think black; border-right: think black; border-top: white; border-bottom: white">

<td> 2 </td>

<td> 3 </td>

</tr>

<tr style="border-style: solid; border-left: think black; border-right: think black; border-top: white; border-bottom: white">

<td> 5 </td>

<td> 3 </td>

</tr>

</tbody>

</table>

This matrix can be represented with the following file called `2x2.txt`. Note how the first two numbers represent the number of columns and the number of rows:

<pre>2 2

2 3
5 3</pre>

If we execute matrix multiplication with `a.out 2x2.txt 2x2.txt`, the following output would result:

<pre>|  2  3  | X |  2  3  | = |  19  15   |
|  5  3  |   |  5  3  |   |  25  24   |</pre>

You can also multiply non-square matricies. Consider the following two matricies:

<table style="width:100%; padding: 0px;border-collapse: collapse;">

<tbody>

<tr>

<td>

<pre> 2 4

 4  1
 6 -2
 5 -4
 2  3</pre>

</td>

<td>

<pre> 3 2

-1 -3  7
 0 -2  4

 </pre>

</td>

</tr>

</tbody>

</table>

When these are multiplied together, the result is:

<pre>|  4  1  |   | -1 -3  7  |   |  -4 -14  32   |
|  6 -2  | X |  0 -2  4  | = |  -6 -14  34   |
|  5 -4  |                   |  -5  -7  19   |
|  2  3  |                   |  -2 -12  26   |</pre>

Again, for details how to perform matrix multiplication on square or non-square matricies, please see the following:

[Interactive Mathematics : Multiplication of Matricies.](http://www.intmath.com/matrices-determinants/4-multiplying-matrices.php)

#### Hints

A few issues that you may run into:

* **Samples** : Carefully look at both the sample programs. The first (`sampleHello.cpp`) shows how to span threads in the simplest way possible. The second (`sampleParam.cpp`) shows how to send a parameter from the parent to a child thread, as well as how to send a return value from the child back to the parent. The third (`sampleGlobal.cpp`) shows how share data between many threads through a global variable. The final (`sampleSum.cpp`) shows how to manage multiple threads and how to pass information between the parent and child threads.
* **Globals** : The parent and children threads will need to both see the left-hand-side (LHS) and right-hand-side (RHS) matricies. This must be accomplished by using shared memory. In other words, there needs to be a global variable that is shared between all the processes.
* **Parameter** : The parent thread needs to tell each of the child threads which cell it is to work on. This means that there must be a way to pass the cell information from the parent to the client. You can see an example of how this is done in `sampleParam.cpp` and `sampleSum.cpp`. Note that we will need to pass two pieces of information into that function (row and column) but we have only one parameter. You can accomplish this by either defining a structure or combining both variables into one somehow. The choice is up to you.
* **PThreads** : You will need to provide the code to include the PThread library and to modify `makefile` to compile with the PThread library.

### C. Verify

The testBed for this assignment is:

<pre>testBed cs345/lab05 lab05.tar</pre>

Please make sure your program runs without error.

### D. Style

Your program should be well-commented and free of any style-checker errors.

## Submit

Submit your TAR file in your Linux Account.

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
20%</th>

<td>No defects could be found</td>

<td>The code works as designed, including passing testBed</td>

<td>One test failed to pass on testBed or one glaring bug exists in the code</td>

<td>Elements of the solution exist</td>

<td>No attempt was made to solve the problem</td>

</tr>

<tr>

<th>Efficient  
30%</th>

<td>It is difficult to imagine how the code could be made more efficient</td>

<td>No obvious efficiency problems exist</td>

<td>One minor thing could be done to improve the efficiency of the code</td>

<td>Many obvious opportunities exist to increase performance</td>

<td>The code has horrible performance issues</td>

</tr>

<tr>

<th>Elegant  
30%</th>

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
