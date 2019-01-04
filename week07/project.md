![](../images/banner.jpg)

# Ponder 07 : Producer & Consumer

##### Due Monday night at Midnight MST

This project is a continuation of project 06.

Because of the random nature of the production of cars and because of the unpredictable nature of the thread scheduler, you will have to manually varify that each car is sold only once, that the serial numbers are in order for a given retailer, and that no numbers are missing.

The testBed is:

<pre>testBed cs345/lab07 lab07.tar</pre>

A few hints:

*   You are not allowed to change `cars.h` in any way. It is not thread safe and should not be thread safe. Instead, you need to make `producer()` and `consumer` thread safe.
*   The prototypes of `producer()` and `consumer` will need to change.
*   You will need to use **both** a mutex or binary semaphore as well as a counting semaphore to solve this problem.

### Style

Your program should be well-commented and free of any style errors.

### Submit

Please submit your TAR file to `Lab 07, Producer & Consumer`. Note that **you will need to change the label to "07" from 06" or it will not submit correctly.**

### Grading

Your submission will be graded according to the following criteria:

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
30%</th>

<td>No defects could be found</td>

<td>The code works as designed, including passing testBed</td>

<td>One test failed to pass on testBed or one glaring bug exists in the code</td>

<td>Elements of the solution exist</td>

<td>No attempt was made to solve the problem</td>

</tr>

<tr>

<th>Efficient  
40%</th>

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

</article>

</div>

</div>
