---
title: Resource management techniques
---

# Resource Management Techniques

These are things the OS does to manage various types of resources.

Most of these management techniques are necessary to allow for the process of **multitasking**, which is where many different programs can be running on a computer "at the same time." To make this possible, the OS needs to manage the processor, memory, and peripheral access for each of the running programs (also known as *processes*)

## Processor Management

In our visual of a processor, only one operation can be performed at a time. It is therefore the job of the processor to decide which process operations are performed and in which order.

### Scheduling

#### Time slicing

In time slicing, each process gets a specific amount of time to run, then the process is paused, and another process runs. this is one of the simplest types of scheduling.