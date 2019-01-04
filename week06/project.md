![](../images/banner.jpg)

# Ponder 06 : Producer & Consumer

##### Due Monday night at Midnight MST

This week, you will be implementing a program that with producer and consumer threads.

### Producer and Consumer

[McLaren Cars](http://cars.mclaren.com/home) is a small British manufacturer that produces race cars and sports cars. In 1992, they decided to produce a limited edition sports car called the [F1](http://cars.mclaren.com/F1-the-story). All 106 cars were custom ordered, meaning McLaren did not have to keep a stock of cars in inventory. Another way of saying this is that there was just one producer (one shop produced all 106 cars) and one consumer (all the cars reached customers through the same avenue).

In 2009, McLaren decided to make a medium production sports car called the [MP4 12C or "12C"](http://cars.mclaren.com/12C) for short. In order to accommodate the larger volume (about 4,000 were produced), McLaren created a dealer network. All 4,000 cars were built on the same assembly line. This meant that there was one producer and several consumers. Inventory of cars rolling off the production line was maintained in a queue because McLaren was constantly refining their design and did not want older copies sitting in the inventory to be considered obsolete.

Today McLaren has many models in production (540, 570S, 570GT, 650S Coupe, 650S Spider, 675LT, 675LT Spider, the P1, and the P1 GTR). Each major model (540, 570, 650, and P1) roll off different assembly lines. In other words, there is one inventory, four assembly lines, and 17 retailers in the US alone. Thus there are four producers and several consumers with one centralized queue.

During the early days, it was possible to manage this flow synchronously. However, with the growing demand for their cars, with the larger number of models, and with their expanding retailer network, it has become necessary to move to a threaded design.

**This system has several properties:**

*   Cars take an unpredictable amount of time to sell. Each retailer can have only one car in their showroom at a time and the length of time it spends there varies. Sometimes several will sell in quick succession, sometimes there is a significant wait.
*   It takes an unpredictable amount of time to build a car. Some roll off the assembly line quickly, some take a long time.
*   Each car must be sold exactly once. A car cannot leave the inventory without being sold and it cannot be sold more than once.
*   Each retailer can have only one car in the showroom at a time.
*   The cars sold by a given retailer must be sold in order.
*   There can be no more than 6 cars in the inventory.

To make this happen as smoothly as possible, we must create several thread to represent the production lines of the various models. We will call these the producers. We will then create a number of threads to represent the different retailers. These will be called the consumers. Of course they need to operate in a thread-safe way.

#### Producers

The producer threads will have a static local variable representing the serial number of the next car to roll off the production line. This number starts at 1 and continues to 50. At random intervals of time, the producer will place a car in the inventory queue. This will include the model which will be specified by which car is sent. This queue will be visible to all the consumers.

#### Consumers

Each consumer thread will wait patiently for a car to appear in the inventory queue. When one arrives, it will grab that customer and wait on it for a random amount of time. When the wait is over, it will then look for another customer to service. Note that there may be more than one car in the queue if manufacturing gets ahead of sales.

#### Synchronization

As you can well imagine, synchronizing between these many processes is going to be challenging. If two consumers attempt to grab the same car from the queue, bad things are going to happen. Similarly, if the producer and a consumer attempt to manipulate the queue at the same time, the integrity of the queue might be compromised.

### Assignment

Please start with the provided `lab06.cpp` which does not use threads. Extend the program to call multiple producer and consumer threads. Finally make the program thread-safe by introducing critical sections.

#### Start

All the code needed to manage the McLaren Car inventory is provided:

<pre>/home/cs345/week06/lab06.cpp</pre>

There is just one problem with the code: it does not work very well. If more than one producer is specified, then all 50 cars of the run are created by one producer and the other producers create nothing. Furthermore, all the cars are sold by one retailer. This happens after the last car rolled off the assembly line. As this one retailer does its best to sell the cars, all the other retailers wait empty-handed. Clearly something needs to be done.

#### Threads

Using what we learned about threads last week, modify the program to spawn one thread for each producer and one thread for each consumer. If, for example, there are 3 producers and 6 consumers, we would expect 9 threads to be created.

You may notice that the provided code for the producer does not match the prototype needed for thread functions:

<pre>void producer(const char * model);</pre>

The same is also true for the consumer function:

<pre>string * consumer(const char * retailer);</pre>

You will need to modify these functions so the necessary information is passed.

#### Critical Sections

The final part of the assignment is to introduce critical sections in the code so it behaves the way we expect. Please put the minimal amount of code in the critical section possible. This means you should not put I/O code in the critical section. You should also not put `usleep()` code in the critical section. In other words, only the required code should be in the critical section; nothing else!

### Assessment

For this submission point, you will not need to handle the case of multiple producers or multiple consumers. Also, we are not handling the case of a limited inventory size. That will be tested next week. That being said, you may choose to try that now.

#### testBed

The testBed for this assignment is:

<pre>testBed cs345/lab06 lab06.tar</pre>

Note that this testBed will only check the condition of 1 producer and 1 consumer. Next week's testBed will handle the more difficult cases of many producers and many consumers.

#### Style

Your program should be well-commented and free of any style errors.

## Submit

Please submit your TAR file to `Lab 06, Producer & Consumer`.

#### Hints

A few hints to help you with the assignment:

*   Please see `/home/cs345/week06/sampleMutex.cpp` for code demonstrating how to use a mutex.
*   Please see `/home/cs345/week06/sampleBinarySem.cpp` for code demonstrating how to use a binary semaphore.
*   Please see `/home/cs345/week06/sampleCountSem.cpp` for code demonstrating how to use a counting semaphore.
*   You are not allowed to change `cars.h` in any way. It is not thread safe and should not be thread safe. Instead, you need to make `producer()` and `consumer` thread safe.
*   The prototypes of `producer()` and `consumer` will need to change.
*   You will need to use **both** a mutex or binary semaphore as well as a counting semaphore to solve this problem.

Your submission will be graded according to the following criteria:

<table class="rubric">

<tbody>

<tr>

<th> </th>

<th>Exceptional 100%</th>

<th>Good 90%</th>

<th>Acceptable 70%</th>

<th>Developing 50%</th>

<th>Missing 0%</th>

</tr>

<tr>

<th>Correct 30%</th>

<td>No defects could be found</td>

<td>The code works as designed, including passing testBed</td>

<td>One test failed to pass on testBed or one glaring bug exists in the code</td>

<td>Elements of the solution exist</td>

<td>No attempt was made to solve the problem</td>

</tr>

<tr>

<th>Efficient 40%</th>

<td>It is difficult to imagine how the code could be made more efficient</td>

<td>No obvious efficiency problems exist</td>

<td>One minor thing could be done to improve the efficiency of the code</td>

<td>Many obvious opportunities exist to increase performance</td>

<td>The code has horrible performance issues</td>

</tr>

<tr>

<th>Elegant 10%</th>

<td>The most elegant solution imaginable was found</td>

<td>The code looks "professional"</td>

<td>One minor inelegancy was found</td>

<td>One obvious inelegancy remains in the code</td>

<td>The code was thrown together</td>

</tr>

<tr>

<th>Maintainable 10%</th>

<td>The code lends itself to reuse and extension</td>

<td>The solution is well designed and thought out</td>

<td>One aspect of the solution design could be improved</td>

<td>Obvious maintainability problems exist</td>

<td>Support costs on this code would be much greater than necessary</td>

</tr>

<tr>

<th>Readable 10%</th>

<td>"Anyone" could read and understand this code</td>

<td>The code honors all the style guidelines</td>

<td>One minor style error was found</td>

<td>One obvious style error was found</td>

<td>No obvious attention was spent on readability</td>

</tr>

</tbody>

</table>
