# Introduction to Resource Management

Resource Management is an HL-only topic. It deals with the various ways your computer handles the fact 
that system resources are limited. In this introduction we will focus on the types of resources a computer 
might manage and the consequences if they run out.

## Common Resources and their roles

| Resource Type             | What it does                                                          | Types of limits                                                        | What happens if it runs out or is low                                                                                                                     |
| ------------------------- | --------------------------------------------------------------------- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Primary Memory            | Stores the current state of applications                              | Amount of RAM, speed of RAM                                            | Applications crash or, more likely, slow down as the computer uses slow secondary memory instead.                                                         |
| Cache                     | Speeds up primary memory significantly                                | Amount of cache, speed of cache                                        | Slower access to apps                                                                                                                                     |
| Secondary Storage         | Stores data for long-term storage, such as documents or settings      | Amount of secondary storage, speed of secondary storage                | New files and applications cannot be created and installed                                                                                                |
| Processor (CPU)           | Does most of the calculations that make a computer or application run | Number of cores, clock speed, instruction set                          | Applications will have to take turns and sometimes wait a long time before their next calculations can be done, resulting in slow or unresponsive devices |
| Network Bandwidth         | Determines how much data can be transferred over a network            | Speed, consistency                                                     | Network-based applications will be slower                                                                                                                 |
| Graphics Processor  (GPU) | Does the calculations involved in generating and displaying graphics  | Number of cores, amount of dedicated RAM, clock speed, instruction set | The frame rate of your computer may slow down, resulting in stuttering display                                                                            |

## Role of the Operating System

Every application running on a computer wants access to these resources. Managing who gets access when
is one of the primary roles of the **operating system**:star:  Every computer, no matter how small or simple,
contains an operating system of some kind. Some examples of common operating systems are:

* Mac OS X
* Microsoft Windows
* Android OS
* iOS
* Tizen
* Linux
* BSD

The operating system is in charge of knowing what resources are available, what resources applications
want, and finding the best way to distribute the limited resources among the apps. 