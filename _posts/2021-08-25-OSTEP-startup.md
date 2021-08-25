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
After creating your entity, click on the "Connect" button and choose "EC2-INSTANCE-CONNECT", even without configuring your private key.

### Tips:
1. It is acceptable to write programs directly through the terminal, but it will be better if you can write them in an editor (e.g., VSCode) and then send them to the cloud. Download PuTTY and follow the guidance here: [Connect to your Linux instance from Windows using PuTTY](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html). 
   Here is the only one-line code needed:`pscp -i C:\path\my-key-pair.ppk C:\path\Sample_file.txt my-instance-user-name@my-instance-public-dns-name:/home/my-instance-user-name/Sample_file.txt`
2. If you want to open a 2nd terminal, just click the "Connect" button twice.
