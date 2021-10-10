---
categories: 
  - OSTEP
tags:
  - code
---
# Process

The process's machine state contains: memory, registers, I/O information.

## Creation
1. load its code and static data into *memory* (from disk or SSDs)  
  > Hint: eager <-> lazy (loading the data only when they are in need)
2. Initialize the *slack*, *heap* and *file descriptions*
3. Jump to the *main()* routine

## API
1. *fork()*: call a child process which is exactly the copy of current process, but it comes to life only when *fork()* has been called.  
   > Difference: *fork()* in the child process returns 0 rather than the PID of its child process.  
   However, directly call *fork()* will cause non-determinism, because we cannot predict what the CPU scheduler's decision.
2. *wait()*: execute in the parent process to wait until the child process has run and exited. It provide determinism to the program.
3. *exec()*: call if you want to run a program that is different from the calling program. It does not call a new process, instead, it loads code and data from executable and overwrites its current code segment.  
  As if *exec()* runs, it seems like the former child process never runs.
  > The separation of fork() and exec() is essential in building a UNIX shell.
4. *pipe()*: look for free file descriptors and assign one to the program. Hence the output is sent to the **pipe** rather than printed on the screen for the next input. Try `grep -o include p4.c | wc -l` to count "include" in p4.c.  
  > Implement:   
    `close(STDOUT_FILENO);`  
    `open("./p4.output", O_CREAT|O_WRONLY|O_TRUNC, S_IRWXU);`

## Homework 05 Takeaways
1. The child process shallow copies data structures from its parent, but shares the same file descriptions. However, one cannot write in a file in the child process and try to read it in the parent process. Not until the whole program ends will the data be written into the file.  
  > In task 3, simply add `sleep(1)` in the child process.
2. The key difference between the parent and child is **the value** *fork()* returns. In child processes, it returns 0.
3. How to create two child processes? Refer to [this article](https://www.cnblogs.com/yfceshi/p/7066407.html). Pay attention to the `return 0`.

# Efficiently Virtualize the CPU with Control
Reason to virtualize the CPU:
1. Control the behavior of programs;
2. Switch among programs to make the PC more efficient.
Otherwise the OS would become a simple library👎.
## System v.s. User
System mode: user mode & kernel mode (trap)
Pay attention to user input: OS runs a trap handler, and user calls should call for a system call and then transfer it into a number. Thus, the system doesn't run the specific code the user provides.
