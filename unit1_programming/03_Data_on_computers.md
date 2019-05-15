# How computers store and interpret data

## Memory in a computer
Every computer has multiple locations where data can be *stored*. 
1. **Persistent Storage**:star: also called **secondary memory**, is the part of a computer where data lives when its not being directly used. In most computers this will be a *hard drive* or *solid-state storage.* This could also be exterior storage such as CDs, DVDs, USB Flash drives, SD Cards, video game cartridges, and so forth. In laptops or desktop computers, the hard disk is usually meaured in hndreds of gigabytes or even terabytes (more on these terms later.)<sup>2.1.5</sup>
2. **RAM**:star:, or *Random Access Memory* is part of the **primary memory** of a computer. It is the part of the computer where data is stored that is being actively used by running programs. It is much smaller than the persistant storage, but much faster. Most computer programs work primarily on RAM, except when saving or loading.<sup>2.1.2</sup>
3. **Cache**:star: is an even faster and smaller section of memory that is used by the computer to store things it knows it may need again soon. It is the fastest part of the computer that isn't directly connected to the computer's "brain" (CPU). From the perspective of a programmer, the cache and RAM are essentially interchangeable, but they make a difference at the low level.<sup>2.1.3</sup>
4. **ROM**:star: or *Read Only Memory* is a tiny piece of medium-fast memory computers come with that is persistent but never user-editable. It contains only the tiny bit of software needed to start a computer. If you've ever "flashed a firmware update" on your computer, router, or phone, you have edited the ROM . <sup>2.1.2</sup>

As a programmer, we mostly only worry about the persistent storage (which we tend to call the *disk* or the *files*) and the RAM (which we tend to call the *memory*.)

## What goes in the memory?
Though the different storage types all works very differently at a physical or chemical level (hard drives use magnets, dvds use lasers, etc), for a programmer it is reasonable to think of memory as holding a giant series of `0`'s and `1`s. This is an example of an **abstraction**:star:, or a simplified way of thinking about a concept that works well enough to do necessary work.<sup>4.1.17</sup>

Each `0` or `1` is called a **bit**:star:.<sup>2.1.9</sup> By itself, a bit can't convey a lot of meaning, since there are only two options. But if you combine the `0`s and `1`s into groups, you can get more interesting combinations. A group of 8 bits is called a **byte**:star: and provides $2^8=256$ possible values, from `0000 0000` to `1111 1111`. 

Given a single byte (or more than one) we can train our programs to *interpret* it in different ways. For example, the byte `0011 1011` might be interpreted as the integer `59`, or the text character `a` or the percentage `23.13%`, depending on the interpretation instructions we are using. Later in this course we will explore some of these encoding schemes in detail.

## Check your Understanding
1. What is the difference between RAM and ROM?
2. How many bits are in one byte?
3. What is the fastest type of memory mentioned so far?

