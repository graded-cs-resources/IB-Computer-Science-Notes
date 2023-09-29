---
title: Paper 1 lesson 3.4 - Hardware Used int Networks
---

# Measuring Speed

When discussing different types of transmission media, it is common to talk about the "speed". There are two different ways of measuring speed in networks.

## Latency

**Latency**:star: or *ping* is a measure of how long it takes a single piece of data to get from one computer to another. It is measured in milliseconds. High latency is considered "slower". If you have ever encountered voice delay in a phone call or lag in an online game, that is latency! 

Higher latency can come from either physical distance - longer distance will result in more latency, problems with routing, or **interference**:star: that means packets need to get sent multiple times before they actually make it through.

## Bandwidth

**Bandwidth**:star: is a measure of the *rate* of data transfer, usually measured in bits per second (or kilobits or megabits per second). In your daily life, this might be thought of as the download speed - once a download *starts* on your computer, the bandwidth measures how much data you get per second. 

When we say we have "fast internet" this is usually the number we quote.

It is possible to have high latency (slow!) but also have high bandwidth (fast!). Mailing a hard drive through the mail is an extreme example - the latency might be *days*, but the bandwidth would be quite large since the entire terabyte or more of data can be retrieved in just a couple of minutes! 

Similarly, it is possible to have very low latency (fast!) but also have high bandwidth. Back in my childhood, modems could only give 28.8 *kilobits* per second of bandwidth - a song might take 30 minutes to download! - but the latency was no worse than today.

# Networking Hardware

The IB exam expects you to have a general understanding of different types of hardware used in networks. This includes:

* Types of transmission media

  * Metal conductor cables
    * Coaxial cable that connects you to your ISP if you have cable internet
    * "Ethernet" (Cat5 or Cat6) cables
    * Long-distance metal cables
    * **Advantages**: relatively cheap, relatively fast, relatively flexible (literally - you can bend them) - a good "middle" option for lots of purposes. Also simple - transmitting data using electrical signals is an easy process, relatively.
  
  * Fiber optic cables
    * A clear, glass-like tube that carries data by transmitting light.
    * Primarily used over long distances.
    * **Advantages**: EXTREMELY Fast, EXTREMELY high bandwidth for a relatively "thin" cable
    * **Disadvantages**: Expensive, fragile, hard to install, fairly complex to encode and decode.

  * Wireless transmissions using radio waves
    * Signals are converted into shifting radio waves (remember - radio waves are a kind of light!)
    * Different types: Wi-fi, WiMAX, 3G, LTE, 5G, bluetooth, NFC
      * Different types have different ranges and bandwidths
    * **Advantages**: Much more convenient, as you do not need to run a cable, so enables connection where cables can't easily go. Fewer physical parts to break. 
    * **Disadvantage**: Potentially less secure since the signals can be detected by any radio antenna. Lower maximum bandwidth. Lower range - a single signal cannot travel as far as a single wire. The more people using it at once in the same region, the more *interference* there is - this creates "blocking" much like the video we saw about Ethernet.


* Hardware used in wired networking
  * ethernet adapters
    * Convert signals in the ethernet protocol into standard data for a computer to understand
  * hubs
    * Are devices that essentially let you treat multiple cables like one big one. Has no brains, just metal.
  * switches
    * Have a little bit of a brain - just enough to create different **collision domains** in your ethernet connection. See the crash course video for more details. Only have LAN brain.
  * routers
    * Allow for connection between different LANs, using IP and TCP and UDP. Used to connect a LAN to the larger internet, as a common example. Also used to add TCP and IP protocols to an existing LAN.
  * modems
    * Converts digital signals to analog signals, used to convert data from an Internet Service Provider into data a LAN can understand. Contains security features etc.
  
* Harware used in wireless networking
  * wireless network adapters
    * Convert radio signals sent over wifi (or whatever tech) to regular data a computer can understand
  * wireless access points
    * A device that listens to radio signals from computers/devices and converts those signals into ethernet signals to join a larger LAN (basically the wireless version of a switch)
  * wireless routers
    * See the definition for router up above? This is one of those but it also has wireless.
