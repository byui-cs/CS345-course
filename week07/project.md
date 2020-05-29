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


| Points |	Description |
| ----- | -------- |
| 80	   | Overall functionality |
| 10	   | Software design (Modular, structures, object, etc...) |
| 10	   | Style, code conventions, naming, etc. |
