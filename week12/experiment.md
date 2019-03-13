![](../images/banner.jpg)

# Teach 12 : Experimentation for White Paper

We will be working on the Gather step here of the white paper.

Your white paper must report on actual data you collected. To facilitate this, two programs will be provided: `experimentCPU.c` and `experimentIO.cpp`. Run these programs and collect data for your paper.

### Experiment CPU

The first program is designed to be CPU heavy. The source is provided at:

<pre>/home/cs345/week12/experimentCPU.c</pre>

There is also an executable in the same location called `experimentCPU.out`.

This is a more general version of the threaded matrix multiplication program that you wrote for a previous lab. This program may need to be compiled on each different type of system you want to run it on due to 32 bit vs. 64 bit issues and library issues.

The usage of this program is:

```as
experimentCPU.out <matrix A rows> <A cols> <B rows> <B cols> <# threads>
```

This program populates matrices A and B with random integers with values from 0 to 99 and then calculates the product matrix by using the number of threads specified on the command line.

### Experiment I/O

The second program is designed to be I/O heavy. The source is provided at:

<pre>/home/cs345/week12/experimentIO.cpp</pre>

There is also an executable in the same location called `experimentIO.out`.

```as
experimentIO.out <# threads from 1 to 1000>
```

This program simulates completing a bunch of I/O jobs that need to be done. Instead of doing actual I/O, sleeps are done instead. The I/O jobs are done by a user specified number of threads.

### Collect Data

Do some testing, individually, and develop your own answers to questions such as those listed here. Back up your answers to these questions with performance data and examples from running the threaded programs experimentIO and experimentCPU, on a few different types of systems. You may obtain performance data by using the `time` command. Some things to be considered:

*   What factors should be taken into account when determining the number of threads that a CPU intensive program should use?
*   What factors should be taken into account when determining the number of threads that an I/O intensive program should use?

### Hints

A large amount of testing could be done to gather data to analyze — with the analysis of the data hopefully producing the insights that you would be excited to share with others — however, you should not spend hours and hours producing data. Here are some hints:

#### Be deliberate about your experimentation

Use what you have already learned (from class or from your research) to help determine what testing to do.

#### There are four main variables

There are four main “knobs” that can be used in producing data:

1.  The type of system
2.  The type of workload (CPU intensive or I/O intensive)
3.  The size of workload
4.  How many threads are used

#### Know when to stop

Do some testing, analyze the data and determine the appropriate amount of testing to do. Don’t overwhelm yourself with data.

#### Use the Time command

You may time the execution of a program using the bash shell command `time` or the `/usr/bin/time` command, like:

<pre>time ./some_command arg1 arg2 ...</pre>

To understand what real/elapsed, user, and sys/system times are, you might start with doing the command: `man 7 time`.

If you are using the bash `time` command to gather performance data, you may write a script that puts the results in a file by doing the following:

<pre>#The way to get the results of a time command put into a file is:
    (time someCommand) 2>results</pre>

A script might include lines like:

<pre>echo "Results of ... threads test ..." >>results.txt
(time someCommand) 2>>results.txt
echo "Results of ... threads test ..." >>results.txt
(time someCommand) 2>>results.txt</pre>

There are various tools or ways to take the results of `time` commands and put the data in a different format. The following is some `awk` code that takes a file with time output in it and reformats the data such that it could more easily be put in a spreadsheet.

<pre>awk '{
   if ( $2 != "" )
   {
      split($2, a, "[ms]");
      printf("%s\t%d\t%f\n", $1, a[1], a[2])
   }
   else
      printf("\n")
}' file_of_time_ouput.txt</pre>

Input looks like:

<pre>real    0m54.714s
user    0m0.000s
sys     0m0.002s

real    0m37.053s
user    0m0.001s
sys     0m0.001s

real    0m23.319s
...</pre>

Output looks like:

<pre>real    0       54.714000
user    0       0.000000
sys     0       0.002000

real    0       37.053000
user    0       0.001000
sys     0       0.001000

real    0       23.319000
...</pre>

There is also the possibility that you have time commands other than your shell’s that has some nice options. The following uses formatting options of `/usr/bin/time`:

<pre>COUNT=1
while [ $COUNT -lt 5 ]; do
  /usr/bin/time -ao times4myCode.txt --format="$COUNT,%e,%U,%S" myCode
  let COUNT=COUNT+1
done</pre>

