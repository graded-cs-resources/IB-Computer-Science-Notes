# How computers store and interpret data

## Memory in a computer

Every computer has multiple places where data can be stored. 

### Secondary Memory

**Secondary Memory**:star:, also called *persistent storage* is the part of a computer where data lives when its not being directly used. In most computers this will be a *hard drive* or *solid-state storage.* This could also be exterior storage such as CDs, DVDs, USB Flash drives, SD Cards, video game cartridges, and so forth. Slow, but permanent (or mostly permanent)<sup><small>[2.1.5](../unit0_resources/syllabus.md#215)</small></sup>
   
### Primary Memory

1. **ROM**:star: or *Read Only Memory* is a tiny piece of medium-fast memory built into the main structure of the computer (but not directly into the main processor chip). It is usually small and contains only the tiny bit of software needed to actually start a computer, before the *operating system* takes over. If you've ever "flashed a firmware update" on your computer, router, or phone, you have edited the ROM. <sup><small>[2.1.2](../unit0_resources/syllabus.md#212)</small></sup>
   
2. **RAM**:star:, or *Random Access Memory* is the part of the computer where data is stored that is being actively used by running programs. It is much smaller than the persistant storage, but much faster. Most computer programs work primarily on RAM, except when saving or loading.<sup><small>[2.1.2](../unit0_resources/syllabus.md#212)</small></sup>
   
3. **Cache**:star: is an even faster and smaller section of memory that is used by the computer to store things it knows it may need again soon. It is the fastest part of the computer that isn't directly connected to the computer's "brain" (CPU). From the perspective of a programmer, the cache and RAM are essentially interchangeable, but they make a difference at the low level.<sup><small>[2.1.3](../unit0_resources/syllabus.md#213)</small></sup>
   
4. **CPU Registers**:star: are extremely tiny, extremely fast places in memory that exist directly on the CPU. They are used only to store the values needed for the current *operation* of the CPU.
   
As a programmer, we mostly only worry about the persistent storage (which we tend to call the *disk* or the *files*) and the RAM (which we tend to call the *memory*.) The CPU and programming language handle the movement between RAM, cache, and registers for us.

![The hierarchy of memory](media/02/memory_heirarchy.jpg)

<small>Image credit: https://www.slideshare.net/rahulbandhe/basics-of-semiconductor-memories-presentation</small>

## What goes in the memory?

Though the different storage types all works very differently at a physical or chemical level (hard drives use magnets, dvds use lasers, etc), for a programmer it is reasonable to think of memory as holding a giant series of `0`'s and `1`s. This is an example of an **abstraction**:star:, or a simplified way of thinking about a concept that works well enough to do necessary work.<sup><small>[4.1.17](../unit0_resources/syllabus.md#4117)</small></sup>

Each `0` or `1` is called a **bit**:star:.<sup><small>[2.1.9](../unit0_resources/syllabus.md#219)</small></sup> By itself, a bit can't convey a lot of meaning, since there are only two options. But if you combine the `0`s and `1`s into groups, you can get more interesting combinations. A group of 8 bits is called a **byte**:star: and provides $2^8=256$ possible values, from `0000 0000` to `1111 1111`. 

Given a single byte (or more than one) we can train our programs to *interpret* it in different ways. For example, the byte `0011 1011` might be interpreted as the integer `59`, or the text character `a` or the percentage `23.13%`, depending on the interpretation instructions we are using. Later in this course we will explore some of these encoding schemes in detail.

## Check your Understanding

1. What is the difference between RAM and ROM?
   
2. How many bits are in one byte?
   
3. What are types of primary memory?

## Study Materials

Create flash cards or a [quizlet](http://quizlet.com) deck with the following words on one side and a quick summary on the other.
* Primary Memory
* Secondary Memory
* RAM
* ROM
* Cache
* Registers
* bit
* byte

We have a quizlet class at https://quizlet.com/join/S8XGx3k93 and you can add your decks there if you make them, but you REALLY should make your own deck before using those of others. You learn as much from making the flashcards as using them, if not more.