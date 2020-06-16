![](../images/banner.jpg)

# Ponder 09 : MMU Lab

##### Due Monday night at Midnight MST

Our assignment is to implement a memory-management unit (MMU) which will convert logical addresses into physical addresses. This will be accomplished by: 

1. reading a file containing the page table
1. writing the code to convert a logical address to a vertical address, and 
2. implementing a simple driver program to test our MMU.

### 1. Read a page table

Recall from section 7.5 Pages from the reading that a page table consists of a mapping from logical addresses to physical. In our case, the page table will consist of three columns: a logical page number, a valid bit, and a base address otherwise known as the physical page number.

<table class="content">

<tbody>

<tr>

<th>Logical Page Number   </th>

<th>Valid Bit   </th>

<th>Physical Page Number</th>

</tr>

<tr>

<td>0</td>

<td>1</td>

<td>4</td>

</tr>

<tr>

<td>3</td>

<td>1</td>

<td>2</td>

</tr>

<tr>

<td>4</td>

<td>0</td>

<td>0</td>

</tr>

<tr>

<td>2</td>

<td>0</td>

<td>0</td>

</tr>

<tr>

<td>1</td>

<td>1</td>

<td>7</td>

</tr>

<tr>

<td>5</td>

<td>1</td>

<td>0</td>

</tr>

</tbody>

</table>

Our page table will have an additional piece of information: the page size. Normally this is a constant and defined by hardware. Our MMU is designed to be general purpose so it will be provided in our page table file.

Our first task is to read the page table file into our program. The format of this file is first the size of the page, followed by the page table. The following page table file corresponds to the above table.

<pre>1024
0 1 4
3 1 2
4 0 0
2 0 0
1 1 7
5 1 0</pre>

Observe how the page size is 1024 bytes. The first column corresponds to the virtual page number. In the textbook, these are always in order with no gaps. Our page file has no such constraint. The second column is the valid bit where '`1`' corresponds to a valid page and '`0`' corresponds to an unused or invalid page. The final column is the corresponding frame in physical memory.

### 2. Convert address

The next step is to convert a logical address to a physical address. Recall from the reading (Section 7.5.1 Basic Method) that an address consists of two parts, the page number and the page offset. The page number can be computed by dividing the address by the page size and the page offset is the remainder.

For example, consider the address 3851 and the page size of 1024. Here the page number is 3 and the page offset is 779:

<div class="quote">

page number is 3 == 3851 / 1024  
page offset is 779 == 3851 % 1024

</div>

The page offset will remain unchanged in the transformation from logical to physical address. The page number will change, however. The logical page number is 3 which corresponds to the second row on our page table. If the valid bit is set to 1 (true), we can look up the physical page number. Otherwise we must indicate there is a page fault. Since the bit is set to 1, we can see the physical page number is 2.

The equation to compute the physical address is:

<div class="quote">

Physical = (physical page number x page size) + page offset

</div>

We know all three variables. The physical page number is 2, the page size is 1024, and the page offset is 449. Thus the physical address is 2827 == (2 x 1024) + (3851 % 1024).

### 3. Driver program

The final part of the assignment is to create a simple driver program to test our code. This program will prompt the user for the page table, then keep prompting the user for logical addressess until the user indicates he or she is done by specifying the 0 address.

The page table can be given by providing it on the command prompt...

<pre>% <span class="input">a.out lab09.txt</span></pre>

... or by prompt...

<pre>% <span class="input">a.out</span>
What is the filename of the page table? <span class="input">lab09.txt</span></pre>

Next the program will give the user some instructions then prompting the user for a logical address.

<pre>% <span class="input">a.out lab09.txt</span>
Enter logical address and the corresponding physical one will be displayed.
Enter 0 for an address when done.
> <span class="input">3851</span>
        2827
> <span class="input">4932</span>
        Page Fault
> <span class="input">1090</span>
        7234
> <span class="input">0</span></pre>

There are four things to notice from this example:

*   If the valid bit is set to `0` or if there is no entry in the page table for a given logical address, the program displays `Page Fault`.
*   There is a tab before all the physical addresses in the output.
*   Each prompt is preceeded with a greater than and a space: "`>` "
*   Notice how you need to accept both command line input and prompt input.

## Assignment

Please: a) start from the standard template, b) write the code, c) validate it against testbed, d) ensure your style is good, e) and submit it.

### A. Start from scratch

There is no provided code for this lab. Please start from the standard template:

<pre>/home/cs345/week09/template.cpp</pre>

Do not forget to fill in your name, your instructor name, and any relevant comments.

### B. Write the code

Write the code using the best coding practices. This may include containers from the standard template library, or it may not. This may include classes, or it may not. These decisions are up to you.

### C. Validate

Please validate your solution against `testBed`.

<pre>testBed cs345/lab09 lab09.cpp</pre>

Make sure your code passes all the tests without error. The following page table files are provided (Found at `/home/cs345/week09`)

*   **pageFile1.txt** : The page file presented in this document.
*   **pageFile2.txt** : A more complex page table file.

### D. Style

Validate your code style with `styleChecker` as appropriate. Note that `styleChecker` cannot handle all C++ constructs. The most important thing is that all the relevant style guidelines are followed.

### E. Submit

This is `Lab 09, MMU Lab`. Make sure your instrutor name is properly filled out or you will get no credit.

## Assessment

Your submission will be graded according to the following criteria:

| Points |	Description |
| ----- | -------- |
| 80	   | Overall functionality |
| 10	   | Software design (Modular, structures, object, etc...) |
| 10	   | Style, code conventions, naming, etc. |
