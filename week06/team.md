![](../images/banner.jpg)

# Teach 06 : Threads

##### Please work together in groups of 2 or 3


## Instructions

- Copy the files from the directory below to your personal account on the Linux account. 
 
```
mkdir week06team
cd week06team
cp /home/cs345/comeau/week06/* .
```

- The source file bossworker.c contains two threads.  The first thread "boss" will add values to a common queue.  The "worker" threads will take values off of the queue.
- You will have one boss thread and many worker threads.
- Use the makefile to build your program.
- Review queue.h to understand the functions that you can do on a queue.


## Suggestions / Notes

What is the purpose of a semaphore and a mutex?

Here are the following semaphore functions/structures that you need to use:

- sem_t
- sem_init()
- sem_wait()
- sem_post()
- pthread_mutex_t
- pthread_mutex_lock()
- pthread_mutex_unlock()
  
