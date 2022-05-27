+++
title = "Backend thinking"
description = ""
tags = [
    "linux",
    "unix",
    "shell",
    "cdn"
]
date = "2022-05-25"
categories = [
    "Development",
    "system",
]
+++

### Mission of backend
##### What is backend programming?
-> Build code that allows a database and an application to communicate with one another. Backend developers take care and maintain the back-end of a website, Including databases, servers, and apps, and they control what you don't see.
##### What are the differences backend vs frontend programming?
- The term “front-end” refers to the user interface, while “back-end” means the server, application and database that work behind the scenes to deliver information to the user.
- Front end vs. back end: what’s the difference?
  - Front and back end developers work on different sides 
  - Front and back end developers have different strengths 
  - Front and back end developers work in different languages
  
##### What need to be a backend engineer? (Arcording to https://hackr.io/blog/how-to-become-a-backend-developer)
- Some needs to be a backend engineer:
  - Be well versed with the basics of Data Structures & Algorithm.
  - Learn a Programming Language and choose a Framework.
  - Learn the basics of Databases.
  - Learn Framework(s).
  - Start your practical training.
  - Innovate and create something new
  - Hosting.
  

- Road map references to be a backend engineer: [Backend Developer](https://roadmap.sh/backend)
##### Can we deliver our products without a backend?
##### What is backendless?
- Backendless is an amazing, yet effective application development platform which has been designed to serve individual application developers as well as agencies. This solution has the ability to make you efficient in developing your applications. This can provide end to end solutions which are designed for mobile or web development.
- Key Features of Backendless: Database, Cloud Code, Caching, Geolocation, Codeless, Logging, Security features, Real-time Data, User-management.
- References: [What is Backendless?](https://blog.back4app.com/backendless/)
### Environment 
##### Linux vs Unix? Is Linux a Unix?
- **Linux** 
  - Linux is an open source operating system (OS).
  - Linux was designed to be similar to UNIX, but has evolved to run on a wide variety of hardware from phones to supercomputers. Every Linux-based OS involves the Linux kernel - which manages hardware resources - and a set of software packages that make up the rest of the operating system.
  (https://www.redhat.com/en/topics/linux/what-is-linux)

- **Unix**
  - UNIX is an operating system which was first developed in the 1960s, and has been under constant development ever since. By operating system, we mean the suite of programs which make the computer work. It is a stable, multi-user, multi-tasking system for servers, desktops and laptops.

  - UNIX systems also have a graphical user interface (GUI) similar to Microsoft Windows which provides an easy to use environment. However, knowledge of UNIX is required for operations which aren't covered by a graphical program, or for when there is no windows interface available, for example, in a telnet session.
  (http://www.ee.surrey.ac.uk/Teaching/Unix/unixintro.html)
- **So Linux is a Unix?**
 **Linux cannot be said to be Unix** mainly because it was written from scratch. It does not have any original Unix code within. Looking at the two OS, you may not notice much of a difference as Linux was designed to function just like Unix, but it does not contain any of its code. Moreover, it lacks a Unix Certification to satisfy the conditions of being called a Unix OS as aforementioned.
- Further reading: [Unix Vs Linux: What Is Difference Between UNIX And Linux](https://www.softwaretestinghelp.com/unix-vs-linux/)

##### Is Ubuntu a Linux? How about CentOS? What are Linux distros?
- **Ubuntu is a Linux.** 
  Ubuntu is a Linux distribution based on Debian and composed mostly of free and open-source software. 
- **CentOS** 
  Also known as CentOS Linux, is a Linux distribution that provides a free and open-source community-supported computing platform, functionally compatible with its upstream source.
- **Linux distros**
  - A Linux distribution (Distro) is a collection of applications, packages, package managers, and features that run on the Linux kernel, so the Linux kernel is shared among distributions – there are sometimes this kernel is customized according to the organization that maintains the distribution. 
  - Some Distro Linux: Redhat, CentOS, Fedora, Debian, Ubuntu.
- Further reading:
  - [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu)
  - [CentOS](https://en.wikipedia.org/wiki/CentOS)
  - [Linux and Distro Linux](https://xuanthulab.net/gioi-thieu-ve-linux-va-cac-distro-linux.html)
  
##### Is macOS a Linux distro?
- **The answer is not.** 
- Further reading: [Is macOS based on Unix or Linux?](https://www.compuhoy.com/is-macos-based-on-unix-or-linux/)

##### What is Linux file system?
- Linux file system is generally a built-in layer of a Linux operating system used to handle the data management of the storage. It helps to arrange the file on the disk storage. It manages the file name, file size, creation date, and much more information about a file.
- Everything is a file? 
- What is file descriptor?

##### How does Linux file permission work?
- The basic Linux permissions model works by associating each system file with an owner and a group and assigning permission access rights for three different classes of users:
  - The file owner.
  - The group members.
  - Others (everybody else).
- Three file permissions types apply to each class of users:
  - The read permission.
  - The write permission.
  - The execute permission.
- References: [Understanding Linux File Permissions](https://linuxize.com/post/understanding-linux-file-permissions/)
##### Blocking vs Non-blocking I/O?
- Some control over how the wait for I/O to complete is accommodated is available to the programmer of user applications.
- Most I/O requests are considered blocking requests, meaning that control does not return to the application until the I/O is complete.
- Another alternative is to use asynchronous programming techniques with nonblocking system calls. An asynchronous call returns immediately, without waiting for the I/O to complete. 

##### Process vs Thread?
![Process and thread](/posts/process_thread.png)
(https://www.guru99.com/difference-between-process-and-thread.html)
- **Multi-threading**
  - In computer architecture, multithreading is the ability of a central processing unit (CPU) (or a single core in a multi-core processor) to provide multiple threads of execution concurrently, supported by the operating system.
  - Further reading: https://en.wikipedia.org/wiki/Multithreading_(computer_architecture)
- **Parallel vs Concurrent vs Asynchronous**
  - **Race condition, deadlock**
    - Race condition:
    ![Race condition](/posts/race_condition.png)
    - Deadlock:
    ![Deadlock](/posts/dead_lock.png)
    - Further reading: [Race Condition and Deadlock
](https://cloudxlab.com/blog/race-condition-and-deadlock/)
  - **Context switching**
    - Context switching is our tendency to shift from one unrelated task to another. 
    - Further reading: [Context Switching Is Destroying Your Workday: Here's How to Fix It](https://reclaim.ai/blog/context-switching#:~:text=%E2%80%8DContext%20switching%20is%20our%20tendency,move%20to%20a%20new%20task.)
  - **Mutex vs Semaphore**
  - 
##### Memory layout: stack, heap
![Compare stack and heap](/posts/stack_heap.png)
(https://www.geeksforgeeks.org/stack-vs-heap-memory-allocation/)
##### The Shell
- **Bash vs Zsh vs Terminal vs Sh vs...**
  - **Bash** is the abbreviation of the Bourne-again shell. In 1971, the UNIX operating system was released along with the Thompson shell. In 1979, the Thompson shell was modified and released as a Bourne shell. Brian Fox released Bash in 1989 for his project that provided improvements from its previous versions. Bash release enhanced its use as a scripting language. 
  - **Zsh** is called Z Shell, which is an extension of Bash that has many new features and themes. Zsh was released in 1990 by Paul Falstad. Zsh has similarities with Korn shell as well. Linux and Mac OS use Bash as their default shell.
  - **Terminal** A terminal is a text input and output environment. A terminal window, also known as a terminal emulator, is a text-only window that emulates a console in a graphical user interface (GUI).
  - **Sh** utility is a command language interpreter/a command that executes commands read from a command line string, the standard input, or a specified file. The application ensures that the commands to be executed are expressed in the language described in Shell Command Language.
  - Further reading: [Difference between Terminal, Console, Shell, and Command Line](https://www.geeksforgeeks.org/difference-between-terminal-console-shell-and-command-line/)
  
- **Login shell vs Interactive shell**
  - A login shell is typcally the top-level shell in the "tree" of processes that starts with the init process. Many characteristics of processes are passed from parent to child process down this "tree" - especially environment variables, such as the search path.
  - Interactive shell handles commands that you type at a prompt. 
  - References: https://docstore.mik.ua/orelly/unix3/upt/ch03_04.htm
- **Settings**
- **Variables**

### Know tools
##### The commands
##### Handy tools to help out
##### Scripting
##### Git


### Mission of backend
##### What is backend programming?
-> Build code that allows a database and an application to communicate with one another. Backend developers take care and maintain the back-end of a website, Including databases, servers, and apps, and they control what you don't see.
##### What are the differences backend vs frontend programming?
- The term “front-end” refers to the user interface, while “back-end” means the server, application and database that work behind the scenes to deliver information to the user.
- Front end vs. back end: what’s the difference?
  - Front and back end developers work on different sides 
  - Front and back end developers have different strengths 
  - Front and back end developers work in different languages
  
##### What need to be a backend engineer? (Arcording to https://hackr.io/blog/how-to-become-a-backend-developer)
- Some needs to be a backend engineer:
  - Be well versed with the basics of Data Structures & Algorithm.
  - Learn a Programming Language and choose a Framework.
  - Learn the basics of Databases.
  - Learn Framework(s).
  - Start your practical training.
  - Innovate and create something new
  - Hosting.
  

- Road map references to be a backend engineer: [Backend Developer](https://roadmap.sh/backend)
##### Can we deliver our products without a backend?
##### What is backendless?
- Backendless is an amazing, yet effective application development platform which has been designed to serve individual application developers as well as agencies. This solution has the ability to make you efficient in developing your applications. This can provide end to end solutions which are designed for mobile or web development.
- Key Features of Backendless: Database, Cloud Code, Caching, Geolocation, Codeless, Logging, Security features, Real-time Data, User-management.
- References: [What is Backendless?](https://blog.back4app.com/backendless/)
### Environment 
##### Linux vs Unix? Is Linux a Unix?
- **Linux** 
  - Linux is an open source operating system (OS).
  - Linux was designed to be similar to UNIX, but has evolved to run on a wide variety of hardware from phones to supercomputers. Every Linux-based OS involves the Linux kernel - which manages hardware resources - and a set of software packages that make up the rest of the operating system.
  (https://www.redhat.com/en/topics/linux/what-is-linux)

- **Unix**
  - UNIX is an operating system which was first developed in the 1960s, and has been under constant development ever since. By operating system, we mean the suite of programs which make the computer work. It is a stable, multi-user, multi-tasking system for servers, desktops and laptops.

  - UNIX systems also have a graphical user interface (GUI) similar to Microsoft Windows which provides an easy to use environment. However, knowledge of UNIX is required for operations which aren't covered by a graphical program, or for when there is no windows interface available, for example, in a telnet session.
  (http://www.ee.surrey.ac.uk/Teaching/Unix/unixintro.html)
- **So Linux is a Unix?**
 **Linux cannot be said to be Unix** mainly because it was written from scratch. It does not have any original Unix code within. Looking at the two OS, you may not notice much of a difference as Linux was designed to function just like Unix, but it does not contain any of its code. Moreover, it lacks a Unix Certification to satisfy the conditions of being called a Unix OS as aforementioned.
- Further reading: [Unix Vs Linux: What Is Difference Between UNIX And Linux](https://www.softwaretestinghelp.com/unix-vs-linux/)

##### Is Ubuntu a Linux? How about CentOS? What are Linux distros?
- **Ubuntu is a Linux.** 
  Ubuntu is a Linux distribution based on Debian and composed mostly of free and open-source software. 
- **CentOS** 
  Also known as CentOS Linux, is a Linux distribution that provides a free and open-source community-supported computing platform, functionally compatible with its upstream source.
- **Linux distros**
  - A Linux distribution (Distro) is a collection of applications, packages, package managers, and features that run on the Linux kernel, so the Linux kernel is shared among distributions – there are sometimes this kernel is customized according to the organization that maintains the distribution. 
  - Some Distro Linux: Redhat, CentOS, Fedora, Debian, Ubuntu.
- Further reading:
  - [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu)
  - [CentOS](https://en.wikipedia.org/wiki/CentOS)
  - [Linux and Distro Linux](https://xuanthulab.net/gioi-thieu-ve-linux-va-cac-distro-linux.html)
  
##### Is macOS a Linux distro?
- **The answer is not.** 
- Further reading: [Is macOS based on Unix or Linux?](https://www.compuhoy.com/is-macos-based-on-unix-or-linux/)

##### What is Linux file system?
- Linux file system is generally a built-in layer of a Linux operating system used to handle the data management of the storage. It helps to arrange the file on the disk storage. It manages the file name, file size, creation date, and much more information about a file.
- Everything is a file? 
- What is file descriptor?

##### How does Linux file permission work?
- The basic Linux permissions model works by associating each system file with an owner and a group and assigning permission access rights for three different classes of users:
  - The file owner.
  - The group members.
  - Others (everybody else).
- Three file permissions types apply to each class of users:
  - The read permission.
  - The write permission.
  - The execute permission.
- References: [Understanding Linux File Permissions](https://linuxize.com/post/understanding-linux-file-permissions/)
##### Blocking vs Non-blocking I/O?
- Some control over how the wait for I/O to complete is accommodated is available to the programmer of user applications.
- Most I/O requests are considered blocking requests, meaning that control does not return to the application until the I/O is complete.
- Another alternative is to use asynchronous programming techniques with nonblocking system calls. An asynchronous call returns immediately, without waiting for the I/O to complete. 

##### Process vs Thread?
![Process and thread](/posts/process_thread.png)
(https://www.guru99.com/difference-between-process-and-thread.html)
- **Multi-threading**
  - In computer architecture, multithreading is the ability of a central processing unit (CPU) (or a single core in a multi-core processor) to provide multiple threads of execution concurrently, supported by the operating system.
  - Further reading: https://en.wikipedia.org/wiki/Multithreading_(computer_architecture)
- **Parallel vs Concurrent vs Asynchronous**
  - **Race condition, deadlock**
    - Race condition:
    ![Race condition](/posts/race_condition.png)
    - Deadlock:
    ![Deadlock](/posts/dead_lock.png)
    - Further reading: [Race Condition and Deadlock
](https://cloudxlab.com/blog/race-condition-and-deadlock/)
  - **Context switching**
    - Context switching is our tendency to shift from one unrelated task to another. 
    - Further reading: [Context Switching Is Destroying Your Workday: Here's How to Fix It](https://reclaim.ai/blog/context-switching#:~:text=%E2%80%8DContext%20switching%20is%20our%20tendency,move%20to%20a%20new%20task.)
  - **Mutex vs Semaphore**
  - 
##### Memory layout: stack, heap
![Compare stack and heap](/posts/stack_heap.png)
(https://www.geeksforgeeks.org/stack-vs-heap-memory-allocation/)
##### The Shell
- **Bash vs Zsh vs Terminal vs Sh vs...**
  - **Bash** is the abbreviation of the Bourne-again shell. In 1971, the UNIX operating system was released along with the Thompson shell. In 1979, the Thompson shell was modified and released as a Bourne shell. Brian Fox released Bash in 1989 for his project that provided improvements from its previous versions. Bash release enhanced its use as a scripting language. 
  - **Zsh** is called Z Shell, which is an extension of Bash that has many new features and themes. Zsh was released in 1990 by Paul Falstad. Zsh has similarities with Korn shell as well. Linux and Mac OS use Bash as their default shell.
  - **Terminal** A terminal is a text input and output environment. A terminal window, also known as a terminal emulator, is a text-only window that emulates a console in a graphical user interface (GUI).
  - **Sh** utility is a command language interpreter/a command that executes commands read from a command line string, the standard input, or a specified file. The application ensures that the commands to be executed are expressed in the language described in Shell Command Language.
  - Further reading: [Difference between Terminal, Console, Shell, and Command Line](https://www.geeksforgeeks.org/difference-between-terminal-console-shell-and-command-line/)
  
- **Login shell vs Interactive shell**
  - A login shell is typcally the top-level shell in the "tree" of processes that starts with the init process. Many characteristics of processes are passed from parent to child process down this "tree" - especially environment variables, such as the search path.
  - Interactive shell handles commands that you type at a prompt. 
  - References: https://docstore.mik.ua/orelly/unix3/upt/ch03_04.htm
- **Settings**
- **Variables**

### Know tools
##### The commands
##### Handy tools to help out
##### Scripting
##### Git