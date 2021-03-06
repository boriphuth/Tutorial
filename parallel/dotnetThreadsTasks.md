# Threads vs. Tasks


You can think about tasks in a variety of ways. 
One is to start from the notion of a thread and state that tasks are like __lightweight threads__, _running on top of a pool of low-level operating system threads_. 
This is quite an _implementation-oriented_ definition that starts from machine-level mechanics and builds an abstraction out of it.
A better way to think about tasks is to see them as __representations of future values__ that get computed by means of a function. 
As such, tasks are sources of *asynchrony* in your code: 
While the task is running, you can do other useful work, until the point you want to await the task’s result. 
Furthermore, tasks can be composed in a variety of ways. 
In the definition in the preceding paragraph, the word future is used intentionally.
Computer science literature often refers to this mechanism as futures (“_in the future, there will be a value_”) or **promises** (“the tasks promise to compute a value”). 
Contrast the _data oriented nature of tasks_ with regular threads to see the difference.
Tasks provide a much nicer abstraction to perform computation in the background, allowing the result to be obtained in a variety of manners at a later point in time.

Tasks should really be thought of as the new threads. 
Disadvantage inherent to threads: _their cost to create_. 
The _thread pool_ is used to reduce such costs and even to **avoid excessive context switching** by _multiplexing multiple units of work onto the same physical operating system thread_ that gets reused.
The introduction of tasks makes direct use of threads largely obsolete because they can be used for **both** _long-running_ work and for _short-lived_ operations. 
The latter case clearly is where you would have been using the thread pool before, although it suffers from limitations such as the ability to return values and compose operations. 
Tasks are a much better abstraction.
_Using the thread pool for long-running work used to be problematic_ because you were stealing away a worker in the thread pool for a long time. 
The engineering done to the task infrastructure (and the underlying revamped thread pool on top of which it’s built) means that tasks can now be used for long-running work, too.

[<<](../parallel.md) 
| 
[home](../README.md) 
| 
[wiki](https://github.com/illegitimis/Tutorial/wiki) 