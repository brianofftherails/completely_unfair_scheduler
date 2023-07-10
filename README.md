# Completely Unfair Scheduler
In this project, we will learn how to create a custom scheduler for the Linux kernel. We will begin by learning how the Linux scheduler has progressed over time and some considerations we must make while designing a time-sharing general purpose scheduler.

## Round Robin Scheduling
This is one of the most naive scheduler, but also the one we will be writing in this project.  We will discuss this further after we learn how some of the schedulers work.

## Important Concepts
### Terms
- Preemption: The ability for a task to "overtake" another task because it has a higher priority.
- Runtime: The amount of time a process spends on CPU
- Quantum: The assigned "timeslice" a process is given by a scheduler. Note that the scheduler reserves the right to cut this short and may give more time than specified (e.g. MIT's exokernel allows processes to go over their timeslice, but are penalized for doing so)

### Metrics for Determining a Good Scheduler
There are certain properties that are important to us as system designers. We often consider *average completion time* when assessing efficiency of algorithms. This takes a set of tasks, measures the walltime that the tasks are completed, then averages out the total time taken for the task to finish. We consider two types of performance metrics:
- performance (e.g. turnaround time, average completion time)
- fairness (implemented through priority levels)

## Some Schedulers
### Shortest Job First
Assume three processes are scheduled at the same time:
```
P1 --> 2s
P2 --> 5s
P3 --> 10s
```
With a SJF scheduler, ***P1*** will be scheduled first, then ***P2***, while ***P3*** will be scheduled after. This is good for ***P1*** and ***P2***, as they will be completed at 2 and 7 seconds into runtime, but ***P3*** will have to wait all the way until 17 seconds to complete. In the case that ***P3*** is a critical task, we have delayed it to the point of being likely not useful.



## Further Reading
### Operating Systems: Three Easy Pieces
[Operating Systems: Three Easy Pieces, Ch 7: Scheduling Introduction](https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-sched.pdf)  
[Operating Systems: Three Easy Pieces, The Completely Fair Scheduler (9.7)](https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-sched-lottery.pdf)  
### Manpages
[sched(7)](https://www.man7.org/linux/man-pages/man7/sched.7.html)  
[nice(1)](https://www.man7.org/linux/man-pages/man1/nice.1.html)
