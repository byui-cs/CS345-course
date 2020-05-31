![](../images/banner.jpg)

# Teach 07 : QuickSort

##### Please work together in groups of 2 or 3


## Instructions

- Copy the files from the directory below to your personal account on the Linux account. 
 
```
mkdir week07team
cd week07team
cp /home/cs345/comeau/week07/* .
```

- The source file main.cpp contains code to load the values.txt file into memory and sort the values using quicksort.
- the "values.txt" file contains random values to be sorted.

To compile:
```bash
g++ main.cpp
```

## Part 1

- Add threads to the quicksort function.
- Make sure you create and join them correctly.  
- You should end up with the same sorted results without threading.

## Part 2

- Limit the number of threads to 10.

## Suggestions / Notes

1) Is there a limit to the number of threads for a process?
2) How many semaphores and/or mutexes do you need?

Here are the following semaphore functions/structures that you need to use:

- sem_t
- sem_init()
- sem_wait()
- sem_post()
- pthread_mutex_t
- pthread_mutex_lock()
- pthread_mutex_unlock()
  
