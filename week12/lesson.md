![](../images/banner.jpg)

# Prepare 12 : File-Systems

##### Due Monday before class time

## Reading

The reading this week will consist of two chapter from the textbook.

### Chapter 10\. File-System Interface

File-systems are operating-system abstractions turning the storage resources of a mass-storage device into a useful programming asset. This week we will learn how these assets appear to programmers and what properties they have. As you do the reading, pay particular attention to the following:

*   File attributes, file operations, and file types.
*   How directories are presented to the user and how they are implemented internally.
*   What is access control and how it is presented to the user.

### Chapter 11\. File-System Implementation

We will be reading only some of Chapter 11\. While it is unlikely that you will ever have the opportunity to implement a File-System or even work with File-System source-code, having a working knowledge of how they are built does help us make better use of File-System assets.

Please read the following sections:

#### Section 11.1 File-System Structure

Focus on the notion of a file-control-block and the layered File-System.

#### Section 11.2 File-System Implementation

Skim this section but take a good look at Figure 11.3 and Figure 11.4.

#### Section 11.3 Directory Implementation

Another section to skim.

#### Section 11.4 Allocation Methods

This section does have implications for how our programs use the File-System. Pay particular attention to the performance implications of contiguous, linked, and index allocation.

#### Section 11.5 Free-Space Management

This is interesting from a general programming perspective. Can you think of a way to use these various implementations (bit vector, linked list, grouping, counting, and space maps) in other programming contexts?

#### Section 11.6 Efficiency and Performance

Another section for skimming. While we certainly have seen caching appear in other contexts, this provides another context.

### File Permissions in Linux

Please read this webpage on [file permissions](https://www.linux.com/training-tutorials/understanding-linux-file-permissions/).


## Quiz

##### Due Wednesday before class time

Quizzes are found in Canvas for the course. You may take the quiz as many times as you like. Only your highest grade on the quiz will be recorded.  Each week the quiz will close before Monday's class time.

Here is my suggested way to do this:

1.  Take the quiz before doing the reading.
2.  Next, read the chapter all the way through, looking for the items mentioned in the quiz.
3.  Finally take the quiz a second time, looking up the items that are specifically mentioned in the quiz.

Hint: write down your answers before submitting! If you do not get a 100% on this second attempt, you will need to re-take the quiz. If you write down your answers, then you will have to do less work on the re-take.
