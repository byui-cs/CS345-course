![](../images/banner.jpg)

# Ponder 02 : System Call Paper

##### Due Monday night at Midnight MST

The project this week will be to explore what system calls are made when we execute simple programs.

## System Calls

Think what needs to happen to put "Hello World" on the screen. Your program needs to figure out 1) which display device is associated with the user, 2) how to send the necessary data across whatever network exists between the CPU and the display device, 3) where on the display device the text is to appear, 4) which font to use, and 5) many other things. Imagine how difficult it would be to write anything if the programmer had to work through all these details with every single program! Fortunately, we don't need to. The system calls provided by the operating-system are a convenient abstraction hiding all these implementation details allowing the programmer to focus on other things.

Every operating-system has a different set of system calls. Those for Linux are quite different than those for Windows systems which are quite different than iOS. Nevertheless, a cross-platform language such as C++ must work with all of these. Thus the libraries (such as `iostream` in C++) provide yet another abstraction on top of that provided by the operating-system.

This begs the question: what system calls correspond to simple high-level language constructs? This question is the focus of our assignment.

## Example

Consider the following C program:

```as
void _start()
{
   const char text[] = "Hello World\n";

   long rv = 0;
   long exit_code = 0;

   // write system call to standard output
   asm volatile ("push %%ebx ; movl %2,%%ebx ; int $0x80 ; pop %%ebx"
      : "=a" (rv) \
      : "0" (4), "ri" ((long)1), "c" ((long)text), "d" ((long)(12))
      : "memory");

   // exit system call -  exit with exit code 0
   rv = 0;
   asm volatile ("push %%ebx ; movl %2,%%ebx ; int $0x80 ; pop %%ebx"
      : "=a" (rv)
      : "0" (1), "ri" (exit_code)
      : "memory");
}
```

When you compile this program with the following:

<pre>gcc -m32 -nostdlib -nostdinc -static sampleAssembly.c -o sampleAssembly.out</pre>

This code will display "Hello World" on the screen as you would expect:

<pre>Hello World</pre>

We can now run `strace` on this executable to see exactly which system calls are executed. The syntax is `strace sampleAssembly.out`. When this code is run, we can see that three system calls are executed:

<pre>execve("./sampleAssembly.out", ["sampleAssembly.out"], [/* 74 vars */]) = 0
[ Process PID=85764 runs in 32 bit mode. ]
write(1, "Hello World\n", 12)           = 12
_exit(0)                                = ?
+++ exited with 0 +++
</pre>

These system calls are:

1.  **execve()**: Execute the program called `sampleAssembly.out`. Note that `strace` executes this system call.
2.  **write()**: Put the text "`Hello World\n`" on the screen.
3.  **_exit()**: Terminate this process.

## Assignment

Your assignment is to write three programs in different languages that displays "`Hello World`" on the screen. This involves four steps:

1.  Write a "Hello World" program in three languages.  For compiled languages, create an executable.
2.  Run `strace` to see which system calls are executed
3.  Conduct some research to see what these system calls do and theorize why they were called.
4.  Write a one paragraph essay summarizing what you have learned from this experiment.

### 1\. Three Languages

Please write "Hello World" in three different languages. One of these languages must be C++. Please try to select languages that are very different. For example, you may try a language that is higher-level than C++ such as Python.

You can use any languages you like. Note that interpreted languages, especially those hosted in a web browser or another application container, will yield very large trace files. This can be expected; one of the main points of this assignment is to realize that different languages have very different efficiencies due to their use of system calls.

### 2\. Trace

Once you have written the three programs, run `strace` on the executable. Probably the best way to do this is to "pipe" the results into a file:

<pre>strace sampleAssembly.out 2> file.txt</pre>

Note that the text `"Hello World\n"` will be sent to standard out. The result of the strace will be sent to standard error. You can "catch" this by using the "second" pipe with `2>`.

### 3\. Research

With trace files for all of your executables, it is now time to analyze the output. You will need to describe what each system call does. To do this, you will need to find a reference online describing the various Linux system calls, describe the function of each system call in the trace, and finally try to explain why that particular system call was used.

There are many sources online describing the various Linux system calls. When you have found one, please make sure to cite is somewhere in your paper. Note that all sources are not created equal. Spending a few extra minutes to locate the best source will probably save you a great deal of time.

Next, describe what each system call is doing. If the system call does not take any parameters, this description can come directly from your online reference. Otherwise, you will need to describe each parameter.

Finally, make an educated guess as to why the compiler generated code to make that system call. Sometimes you simply cannot figure it out. For example, you may notice that the file `/mnt/local/lib/libc.so.6` is being opened. A bit of research on the web will reveal that this file is a standard C library which was loaded from `#include <stdio.h>`. It was not directly by our `printf()` statement but loading the stdio library included a great deal of unused code.

### 4\. Summary

The final part of this paper is to describe what you learned from this experiment. Specifically, answer the question: "How has this experiment made me a better programmer?" This should be approximately one paragraph though you will not be graded on length.

## Turning it in

You will turn in a single document containing the code used in your experiments, the trace results, your analysis of the trace results, and the final summary.  Upload your document (Word, TXT, PDF) into Canvas for this project.

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

<th>Experiments  
20%</th>

<td>The three languages chosen illustrate are unique enough to offer interesting insights</td>

<td>It appears that some thought went into the language choices</td>

<td>Three programs and three stack traces exist</td>

<td>At least one experiment was done</td>

<td>Missing source code or stack trace</td>

</tr>

<tr>

<th>Analysis  
50%</th>

<td>Interesting insights are present in the analysis showing that you went "the extra mile"</td>

<td>Every system call was accurately described</td>

<td>One trace was completely analyzed</td>

<td>Some trace analysis exists for at least one of the experiments</td>

<td>No attempt was made to analyze a trace</td>

</tr>

<tr>

<th>Summary  
20%</th>

<td>Several interesting insights are present in the summary</td>

<td>It is clear that real thought went into the summary</td>

<td>There are no factual errors present in the summary</td>

<td>Little thought or effort was put in the summary part of the paper.</td>

<td>The summary part of the paper is missing</td>

</tr>

<tr>

<th>Professionalism  
10%</th>

<td>The paper is easy to read and ideas are clearly communicated</td>

<td>Everything is properly cited, no grammar or spelling errors, writing style is "professional"</td>

<td>One instance of a spelling error, grammar error, incomplete citation, or poor writing</td>

<td>A citation is missing where one is needed (plagiarism alert!)</td>

<td>Gross spelling/grammar errors or other aspects of the writing that make the paper difficult to read</td>

</tr>

</tbody>

</table>

</article>

</div>

</div>