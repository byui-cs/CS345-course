![](../images/banner.jpg)

# Prepare 08 : Parallelism

## Reading

The reading this week will consist of a half chapter from the textbook.  It should take two hours to complete the reading and an hour to complete the reading quiz.

## Reading

The reading this week will consist of seven chapters from a [Lawrence Livermore National Laboratory article](https://computing.llnl.gov/tutorials/parallel_comp/) plus two reference documents.

### Abstract

Very short introduction but worth a read.

[Introduction to Parallel Programming : Abstract](https://computing.llnl.gov/tutorials/parallel_comp/#Abstract)

### Overview

There are two things I like about this section. The first is that they do a good job of describing what parallel computing really is all about. After all, this is not a concept which is easy to internalize. The second great thing about this section is the pictures they have of real parallel hardware. In my opinion, it makes these abstract concepts seem more approachable when you can see the actual hardware.

[Introduction to Parallel Programming : Overview](https://computing.llnl.gov/tutorials/parallel_comp/#Overview)

### Concepts and Terminology

This section begins with Flynn's taxonomy which we will refer to for the remainder of this lesson. Next under the sub-section titled "Concepts and Terminology," there are several terms and definitions which you may have heard before or, more likely, have used incorrectly. Please spend a few minutes on Amdahl's law and try to internalize its implications.

Speaking of Amdahl's law, there are a few variables which are difficult to understand. "S" is the portion of the code that must be serial and "P" is the portion of the code that can be parallelized. The article just defines "S" as the "serial fraction" not "speedup." Note that S + P = 1\. It is important to note that speedups calculated with Amdahl's Law are theoretical maximum speedups.

[Introduction to Parallel Programming : Concepts and Terminology](https://computing.llnl.gov/tutorials/parallel_comp/#Concepts)

### Parallel Computer Memory Architectures

With this section, we begin to appreciate the complexity of working with massively parallel computers. As each model is presented, try to visualize the implications on hardware design as well as on the software we write.

[Introduction to Parallel Programming : Parallel Computer Memory Architectures](https://computing.llnl.gov/tutorials/parallel_comp/#MemoryArch)

### Parallel Programming Models

This section is very relevant to our job as programmers. This is especially true because hardware is becoming increasingly more parallel with every generation. (Not to make me sound old but...) In my day, even supercomputers were serial. Today, even mobile devices have multiple cores and/or processors. This section discusses the tools we use to take advantage of this hardware.

[Introduction to Parallel Programming : Parallel Programming Models](https://computing.llnl.gov/tutorials/parallel_comp/#Models)

### Designing Parallel Programs

This section presents a collection of design considerations related to parallel computing. Each consideration is largely independent of the others, but all are things we have to think about as we write code.

[Introduction to Parallel Programming : Designing Parallel Programs](https://computing.llnl.gov/tutorials/parallel_comp/#Designing)

### Parallel Examples

This last section provides some examples of how various parallel problems can be solved. The first example will be particularly relevant for our Lab this week.

[Introduction to Parallel Programming : Parallel Examples](https://computing.llnl.gov/tutorials/parallel_comp/#Examples)

### Lawrence Livermore National Laboratory : OpenMP

One reference to OpenMP. Please do not read this entire article (unless you are having trouble sleeping at night). Instead use it as a reference. A couple particularly relevant sections are:

[OpenMP Directives : C / C++ Directives Format](https://computing.llnl.gov/tutorials/openMP/#CFormat)

[OpenMP Directives : PARALLEL Region Construct](https://computing.llnl.gov/tutorials/openMP/#ParallelRegion)

### OpenMP Application Program Interface

Another document for reference rather than for reading. That being said, I did read page 7-13 (skipping the Fortran examples).

[OpenMP.org : OpenMP Application Program Interface](http://openmp.org/mp-documents/OpenMP4.0.0.Examples.pdf)

## Quiz

##### Due Wednesday before class time

Quizzes are found in Canvas for the course. You may take the quiz as many times as you like. Only your highest grade on the quiz will be recorded.  Each week the quiz will close before Monday's class time.

Here is my suggested way to do this:

1.  Take the quiz before doing the reading.
2.  Next, read the chapter all the way through, looking for the items mentioned in the quiz.
3.  Finally take the quiz a second time, looking up the items that are specifically mentioned in the quiz.

Hint: write down your answers before submitting! If you do not get a 100% on this second attempt, you will need to re-take the quiz. If you write down your answers, then you will have to do less work on the re-take.
