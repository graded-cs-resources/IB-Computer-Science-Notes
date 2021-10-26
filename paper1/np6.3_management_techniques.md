---
title: Resource management techniques
---

# Resource Management Techniques

These are things the OS does to manage various types of resources.

Most of these management techniques are necessary to allow for the process of **multitasking**, which is where many different programs can be running on a computer "at the same time." To make this possible, the OS needs to manage the processor, memory, and peripheral access for each of the running programs (also known as *processes*)

## Processor Management

In our visual of a processor, only one operation can be performed at a time. It is therefore the job of the processor to decide which process operations are performed and in which order.

### Scheduling

**Scheduling** is the process by which an OS and processor work together to share calculation space between many different running processes.

#### Time slicing

In time slicing, each process gets a specific amount of time to run, then the process is paused, and another process runs. This behavior will be pre-programmed by the OS. This is one of the simplest types of scheduling.

#### Prioritized time slicing

A better version of time slicing allows the OS to give different process different amounts of time based on their complexity and their priority, so that more important processes, or processes that will finish more quickly, can run before longer ones or less important ones.

#### Interrupts

An **interrupt** is a command that stops the current process from running and gives control back to the operating system so that it can figure out what to do next. Interrupts can be caused by hardware (for example by the user pressing a key on a keyboard or moving a mouse), or they can be set up to run systematically. Most modern OSes and processors use an interrupt-driven system, where any hardware interaction will pause running processes temporarily and give control of the processor back to an OS process called the **scheduler**, which will then figure out how to handle the interrupt and decide which process should go back into the processor. 

To allow for something similar to time slicing, the OS can implement a clock that sends an interrupt once every millisecond or slow, guaranteeting that the OS gets the opportunity to switch processes regularly if necessary.

This is called **preemptive multitasking**.

## Memory Management

The other major thing the operating system needs to manage is the memory - RAM, primarily - in a computer.