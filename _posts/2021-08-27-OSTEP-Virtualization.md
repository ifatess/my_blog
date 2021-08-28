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
