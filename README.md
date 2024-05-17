# Rutgers: CS518 - Operating Systems Design

## Abstract

This project implements a user-level thread library using the pthread library as a template. The library includes functions for creating and managing threads, scheduling their execution, and implementing mutual exclusion using mutexes. The project helps understand the challenges and concepts involved in scheduling and managing threads, similar to operating system processes and kernel-level threads.

## Introduction

Threads are logical sequences of instructions within a process that can run concurrently. This project implements a user-level thread library, where threads are managed in user space without direct kernel support. The library includes functionalities for creating threads, yielding execution, joining threads, and using mutexes for mutual exclusion. The scheduler supports different algorithms like Round Robin, Preemptive Shortest Job First, and Multi-level Feedback Queue.

## Requirements

- Implement functions for creating, managing, and scheduling threads.
- Implement mutual exclusion using mutexes.
- Scheduler should support Round Robin, Preemptive Shortest Job First (SJF), and Multi-level Feedback Queue (MLFQ) scheduling algorithms.
- Ensure proper memory management and signal handling.

## Files

- `mypthread.c`: Implementation of the user-level thread library.
- `mypthread.h`: Header file for the thread library.
- `Makefile`: Makefile to compile the library and test programs.

## Functions Implemented

### Thread Management

- `int mypthread_create(mypthread_t *thread, pthread_attr_t *attr, void *(*function)(void*), void *arg);`
  - Creates a new thread.
  - Parameters:
    - `thread`: Pointer to the thread identifier.
    - `attr`: Pointer to thread attributes (ignored, pass NULL).
    - `function`: Pointer to the function to be executed by the thread.
    - `arg`: Argument to be passed to the function.
  - Returns 0 on success, -1 on failure.

- `int mypthread_yield();`
  - Yields the execution of the current thread.

- `void mypthread_exit(void *value_ptr);`
  - Terminates the current thread and optionally returns a value.

- `int mypthread_join(mypthread_t thread, void **value_ptr);`
  - Waits for the specified thread to terminate and retrieves the return value.

### Mutex Management

- `int mypthread_mutex_init(mypthread_mutex_t *mutex, const pthread_mutexattr_t *mutexattr);`
  - Initializes a mutex.

- `int mypthread_mutex_lock(mypthread_mutex_t *mutex);`
  - Locks a mutex. If the mutex is already locked, the calling thread is blocked until the mutex becomes available.

- `int mypthread_mutex_unlock(mypthread_mutex_t *mutex);`
  - Unlocks a mutex.

- `int mypthread_mutex_destroy(mypthread_mutex_t *mutex);`
  - Destroys a mutex.

## Scheduler

- `void schedule();`
  - Invokes the appropriate scheduling algorithm based on the configuration.

### Scheduling Algorithms

- `static void sched_RR();`
  - Implements Round Robin scheduling.

- `static void sched_PSJF();`
  - Implements Preemptive Shortest Job First scheduling.

- `static void sched_MLFQ();`
  - Implements Multi-level Feedback Queue scheduling.

## Building and Running

### Compilation

Use the provided `Makefile` to compile the library and test programs.
