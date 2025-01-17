---
categories: 
  - OSTEP
tags:
  - code
---
# Brief-intro

This is a post based on the online book [OSTEP](https://pages.cs.wisc.edu/~remzi/OSTEP/), and its [code](https://github.com/remzi-arpacidusseau/ostep-code) on Github, where users can find required *.h* files and *.c* codes in the e-book.

In the following chapters, the author aims at recording and reflecting on the process of learning OSTEP, and collect useful tricks for future use.

# Pre-start

## Environment build-up
According to the *preface* of the book, projects and practices involved are based on **C** and **Unix**. Unfortunately, I'm currently using the *Windows* OS and I'm not about to set up a virtual machine through *VMWare* or other similar softwares.
At the beginning, I set up GCC and VS Code on my PC and it **does** work. However, it's pretty complicated to do so.

Due to my laziness, I turned to a quicker and no less more reliable way to fit in the course's requirement.
I use the t2-micro device from **AWS** service. It is completely free of charge and easy to use.
After creating your instance, click on the "Connect" button and choose "EC2-INSTANCE-CONNECT", even without configuring your private key.

### Tips:
1. It is acceptable to write programs directly through the terminal, but it will be better if you can write them in an editor (e.g., VSCode) and then send them to the cloud. Download PuTTY and follow the guidance here: [Connect to your Linux instance from Windows using PuTTY](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html). Here is the only one-line code needed:`pscp -i C:\path\my-key-pair.ppk C:\path\Sample_file.txt my-instance-user-name@my-instance-public-dns-name:/home/my-instance-user-name/Sample_file.txt`
2. AWS provides a convenient way to install gcc and many other development tools in linux instance, refer to [Prepare to compile software on an Amazon Linux instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/compile-software.html). Use the command: `sudo yum groupinstall "Development Tools"`
3. If you want to open a 2nd terminal, just click the "Connect" button twice.
4. **Cloning the [code repository](https://github.com/remzi-arpacidusseau/ostep-code) directly and "make" it will save your time!**

## Blog set-up
From my perspective, it's necessary for programmers/cs students to have their own blogs. As I mentioned in the *Brief-intro* section, blog can bring us a sense of control and persistence, which will foster our learning efficiency. I decided not to blog in a big community like *csdn*, because it's incompatible with my nature of introspection and freedom.

This blog is set up with *Github Pages* and a Jekyll theme [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/). Just follow the instructions and revise the configurations slightly. I'm used to this mode: it's easy-to-start for almost anyone on the earth.

# Introduction
## Virtualizing the CPU
The author of OSTEP shows us a timer program to point out the ability of OS to operate CPU.
> Hint: Use **&** to run multiple processes at the same time.

This chapter introduces the OS as several roles:
- CPU Virtualizer
- API Provider
- Resource Manager

## Virtualizing Memory
Understand the usage of *malloc()*, *getpid()*, *assert()*. Through running the given program, we realized that the memory assigned to each process is *virtual memory*, i.e., the address returned from *malloc()* isn't the **real** address of data.

## Concurrency
Unserstand the usage of *volatile* (yet not thoroughly...). The author gives an example of how multiple threads being interrupted while processing.

## Persistence
The memory cannot store your data persistently. Therefore, we need I/O devices such as hard drives or SSDs to save the information we need. OS provides a file system to manage the writing/reading process among I/O devices and CPU. We also need to pay attention to the mechanism that OS acquires to recover from unexpectable problems.

> So now you have some idea of what an OS actually does: it takes physical resources, such as a CPU, memory, or disk, and virtualizes them. It handles tough and tricky issues related to concurrency. And it stores files persistently, thus making them safe over the long-term.

## Design Goals
- Raise abstractions
- Provide high performance with minimized overheads
- Give protection (isolation) and reliability
- Others: energy-efficiency, security, mobility...
