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
   Difference: *fork()* in the child process returns 0 rather than the PID of its child process.
