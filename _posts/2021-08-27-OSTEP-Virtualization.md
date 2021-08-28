---
categories: 
  - OSTEP
tags:
  - code
---
# Process

The process's machine state contains: memory, registers, I/O information.

## Process Creation
1. load its code and static data into *memory* (from disk or SSDs)  
  > Hint: eager <-> lazy (loading the data only when they are in need)
2. Initialize the *slack*, *heap* and *file descriptions*
3. Jump to the *main()* routine

## Terms
![Key Process Terms](https://github.com/ifatess/my_blog/blob/7672a5b8e9d17e5871e09287d120628a5a95ae0f/pics/2021-08-27-OSTEP-Virtualization/01.png)
