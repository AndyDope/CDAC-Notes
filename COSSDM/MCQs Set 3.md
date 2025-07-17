### **Comprehensive MCQ Review: COSSDM (Set 2 - Hard)**

Practice these questions to challenge your in-depth understanding of OS and SDM concepts. For best results, attempt to answer them before checking the key.

---

### **Topic 1: OS Fundamentals & Linux Basics (Sessions 1-2)**

1.  **When a user program attempts to execute a privileged instruction (e.g., direct I/O access) while in User Mode, what is the most likely outcome?**
    - [ ] The OS promotes the program to Kernel Mode to execute the instruction.
    - [ ] The instruction is ignored, and the program continues.
    - [ ] The hardware generates a trap, transferring control to the OS kernel, which will likely terminate the program.
    - [ ] The instruction is placed in a queue to be executed by the kernel later.
    <br>

2.  **Which component of a basic computer organization is primarily responsible for fetching and executing instructions?**
    - [ ] Main Memory (RAM)
    - [ ] I/O Modules
    - [ ] System Bus
    - [ ] Central Processing Unit (CPU)
    <br>

3.  **What is the purpose of the shell command `ln -s /data/original.txt /home/user/link.txt`?**
    - [ ] It copies the content of `original.txt` to `link.txt`.
    - [ ] It creates a hard link, where both files share the same inode.
    - [ ] It creates a symbolic (or soft) link named `link.txt` that points to the path of `original.txt`.
    - [ ] It moves the `original.txt` file to the user's home directory.
    <br>

4.  **In Linux, a user's permissions for a file are determined by the OS in which order of precedence?**
    - [ ] Group -> Others -> Owner
    - [ ] Others -> Group -> Owner
    - [ ] Owner -> Group -> Others
    - [ ] The OS checks all three simultaneously.
    <br>

5.  **Which statement accurately describes the difference between an interrupt and a system call?**
    - [ ] Interrupts are synchronous events, while system calls are asynchronous.
    - [ ] Interrupts are typically triggered by hardware events, while system calls are explicitly invoked by software.
    - [ ] System calls have higher priority than hardware interrupts.
    - [ ] Only system calls cause a switch from user mode to kernel mode.
    <br>

6.  **What does the command `ps -ef > processes.log` do?**
    - [ ] It displays the content of `processes.log` on the screen.
    - [ ] It searches for the string "ef" in the `ps` command.
    - [ ] It appends the list of all running processes to the file `processes.log`.
    - [ ] It overwrites the file `processes.log` with the list of all running processes.
    <br>

7.  **A "microkernel" OS architecture differs from a "monolithic kernel" architecture in that:**
    - [ ] A microkernel is hardware-dependent, while a monolithic kernel is not.
    - [ ] A microkernel includes all OS services like file systems and device drivers within the kernel space.
    - [ ] A microkernel provides only essential services (like IPC and scheduling) in the kernel, with other services running as user-space processes.
    - [ ] A monolithic kernel is smaller and faster than a microkernel.
    <br>

8.  **What information is stored in a file's inode in a Unix-like filesystem?**
    - [ ] The file's name.
    - [ ] The file's content.
    - [ ] The file's metadata, such as permissions, owner, size, and pointers to its data blocks.
    - [ ] The path to the file's directory.
    <br>

9.  **Which shell meta-character is used to indicate that a command should be run in the background?**
    - [ ] `*`
    - [ ] `&`
    - [ ] `!`
    - [ ] `$`
    <br>

10. **A user's `PS1` environment variable typically controls:**
    - [ ] The user's default shell.
    - [ ] The appearance of the primary command prompt.
    - [ ] The search path for executable files.
    - [ ] The user's password settings.
    <br>

**Answer Key (1-10)**
1.  **Answer:** ||(C) Privileged instructions can only be executed in Kernel Mode. An attempt to run one in User Mode is a hardware-level fault that generates a trap, allowing the OS to take over and handle the security violation, usually by terminating the offending process.||
2.  **Answer:** ||(D) The CPU's control unit is responsible for the fetch-decode-execute cycle, which is the fundamental process of running a program.||
3.  **Answer:** ||(C) `ln -s` creates a symbolic link. It's essentially a pointer file that contains the path to the original file. This is different from a hard link, which is a direct reference to the same inode.||
4.  **Answer:** ||(C) The system first checks if the user is the owner of the file. If so, only the owner permissions apply. If not, it checks if the user belongs to the file's group. If so, only the group permissions apply. If neither, the "others" permissions apply.||
5.  **Answer:** ||(B) This is the key distinction. Interrupts are asynchronous, hardware-driven events (e.g., disk I/O complete). System calls are synchronous, intentional requests from a program for a kernel service. Both cause a mode switch to kernel space.||
6.  **Answer:** ||(D) The `>` is the standard output redirection operator. It takes the output of the command on its left (`ps -ef`) and writes it to the file on its right, overwriting the file if it already exists. `>>` is used for appending.||
7.  **Answer:** ||(C) The microkernel approach aims for higher security and modularity by moving as many services as possible out of the privileged kernel space and into user space. This contrasts with a monolithic kernel (like traditional Linux) where most services run in kernel space.||
8.  **Answer:** ||(C) The inode (index node) is the data structure that stores all metadata about a file except for its name and actual data content. The file's name is stored in the directory entry that points to the inode.||
9.  **Answer:** ||(B) Appending an ampersand (`&`) to the end of a command tells the shell to execute the command in the background, immediately returning the command prompt to the user without waiting for the command to finish.||
10. **Answer:** ||(B) `PS1` (Prompt String 1) is a shell environment variable that defines the structure and appearance of the main interactive command prompt (e.g., `[user@hostname ~]$ `).||
<br>

### **Topic 2: Shell Programming & Processes (Sessions 3-5)**

11. **In a shell script, what is the purpose of the command `read username`?**
    - [ ] To read the content of a file named `username`.
    - [ ] To set the `username` environment variable.
    - [ ] To read a line from standard input and assign it to the shell variable `username`.
    - [ ] To check if a user named `username` exists.
    <br>

12. **A context switch between two processes is more expensive than a context switch between two threads of the same process because:**
    - [ ] Threads have higher priority than processes.
    - [ ] Switching processes requires the OS to save and load the entire memory management context (e.g., page tables), which is not necessary when switching between threads that share the same memory space.
    - [ ] The OS kernel is not involved in thread switching.
    - [ ] Threads run in kernel mode, while processes run in user mode.
    <br>

13. **Which process scheduling algorithm provides the best average waiting time for a set of processes, but is impossible to implement in a real general-purpose OS?**
    - [ ] First-Come, First-Served (FCFS)
    - [ ] Round Robin (RR)
    - [ ] Non-preemptive Shortest Job First (SJF)
    - [ ] Multi-level Feedback Queue
    <br>

14. **In shell scripting, what does the `until` loop do?**
    - [ ] It executes a block of code as long as a condition is false.
    - [ ] It is a synonym for the `while` loop.
    - [ ] It executes a block of code a fixed number of times.
    - [ ] It executes a block of code until the user presses Ctrl+C.
    <br>

15. **A process that has been terminated by the OS, but whose parent process has also terminated without collecting its exit status, is called a(n):**
    - [ ] Zombie Process
    - [ ] Sleeping Process
    - [ ] Orphan Process
    - [ ] Daemon Process
    <br>

16. **The Long-Term Scheduler (or Job Scheduler) controls:**
    - [ ] Which process gets the CPU next.
    - [ ] The degree of multiprogramming (how many processes are loaded into main memory).
    - [ ] The swapping of processes between main memory and disk.
    - [ ] The allocation of I/O devices.
    <br>

17. **In a Round Robin (RR) scheduling algorithm, what is the effect of a very large time quantum?**
    - [ ] It leads to excessive context switching.
    - [ ] It causes starvation for short processes.
    - [ ] The RR algorithm behaves like the First-Come, First-Served (FCFS) algorithm.
    - [ ] The RR algorithm behaves like the Shortest Job First (SJF) algorithm.
    <br>

18. **After a `fork()` system call, the child process:**
    - [ ] Starts execution from the beginning of the `main` function.
    - [ ] Replaces the parent process.
    - [ ] Continues execution from the instruction immediately following the `fork()` call, just like the parent.
    - [ ] Remains in a waiting state until the parent calls `exec()`.
    <br>

19. **Which of the following is a non-preemptive scheduling algorithm?**
    - [ ] Round Robin (RR)
    - [ ] First-Come, First-Served (FCFS)
    - [ ] Shortest Remaining Time First (SRTF)
    - [ ] Multi-level Feedback Queue
    <br>

20. **What is a "wildcard symbol" (e.g., `*`) in the context of a shell?**
    - [ ] A special character that is ignored by the shell.
    - [ ] A symbol that represents the root user.
    - [ ] A character used by the shell to match patterns in filenames (pathname expansion).
    - [ ] A symbol for redirecting output.
    <br>

**Answer Key (11-20)**
11. **Answer:** ||(C) The `read` command is a shell built-in used to get user input from standard input (the keyboard) and store it in one or more shell variables.||
12. **Answer:** ||(B) Threads share the same address space. Processes do not. When switching between processes, the OS must perform a complete context switch, which includes saving the state of memory management units, flushing caches like the TLB, and loading the context for the new process. This is a much heavier operation.||
13. **Answer:** ||(C) SJF is provably optimal in minimizing the average waiting time. However, it's impossible to implement in a general-purpose OS because you cannot know the exact execution time (the "burst time") of a process in advance.||
14. **Answer:** ||(A) The `until` loop is the logical inverse of a `while` loop. A `while` loop continues as long as its condition is true. An `until` loop continues as long as its condition is false (i.e., until it becomes true).||
15. **Answer:** ||(C) An orphan process is one whose parent has terminated. In Unix/Linux, such processes are "adopted" by the `init` process (process ID 1), which will then collect their exit status when they terminate, preventing them from becoming zombies.||
16. **Answer:** ||(B) The Long-Term Scheduler decides which jobs from the job pool to bring into the ready queue in main memory. By controlling how many processes are active at once, it controls the degree of multiprogramming.||
17. **Answer:** ||(C) If the time quantum is very large (e.g., larger than any process's CPU burst), a process will always complete its burst and relinquish the CPU voluntarily before the timer interrupt goes off. This makes the algorithm behave just like non-preemptive FCFS.||
18. **Answer:** ||(C) The `fork()` call is unique in that it is called once but returns twice—once in the parent and once in the newly created child. Both processes start their execution at the line immediately after the `fork()` call.||
19. **Answer:** ||(B) FCFS is a simple non-preemptive algorithm. Once a process is given the CPU, it runs to completion (or until it blocks for I/O) without being forcibly removed by the OS. All other options are preemptive.||
20. **Answer:** ||(C) Also known as "globbing," these characters (`*`, `?`, `[]`) are interpreted by the shell itself to expand into a list of matching filenames before the command is even executed. `ls *.txt` becomes `ls file1.txt file2.txt ...`.||
<br>

### **Topic 3: Memory Management & Virtual Memory (Sessions 6-8)**

21. **The memory management scheme that suffers from external fragmentation is:**
    - [ ] Paging
    - [ ] Pure Segmentation
    - [ ] Inverted Page Tables
    - [ ] Buddy System
    <br>

22. **What does a "page fault" signify?**
    - [ ] A hardware error in the memory module.
    - [ ] An attempt by a process to access a page that is not currently in its assigned physical memory frames.
    - [ ] A security violation where a process tries to access another process's memory.
    - [ ] A calculation error in a page replacement algorithm.
    <br>

23. **The "Working Set" of a process is defined as:**
    - [ ] The set of all pages allocated to the process.
    - [ ] The set of pages that the process is currently and actively using.
    - [ ] The set of pages that have been modified.
    - [ ] The total memory size required by the process.
    <br>

24. **Which page replacement algorithm is a reasonable approximation of the Optimal algorithm and is often implemented in practice?**
    - [ ] FIFO (First-In, First-Out)
    - [ ] LRU (Least Recently Used)
    - [ ] LFU (Least Frequently Used)
    - [ ] Random Replacement
    <br>

25. **What is a primary advantage of paging?**
    - [ ] It allows processes to have a logical address space larger than the physical memory available.
    - [ ] It completely eliminates the overhead of address translation.
    - [ ] It is simpler for programmers to manage than a contiguous memory space.
    - [ ] It suffers from no fragmentation.
    <br>

26. **"Reentrant code" is code that:**
    - [ ] Can be executed by multiple processes simultaneously without interfering with each other because it does not modify itself.
    - [ ] Re-enters the CPU queue after being executed.
    - [ ] Is stored in the re-entry section of memory.
    - [ ] Must be re-compiled before each execution.
    <br>

27. **What is the purpose of the "Translation Lookaside Buffer" (TLB)?**
    - [ ] To buffer I/O data from slow devices.
    - [ ] To act as a cache for frequently used page table entries to accelerate virtual-to-physical address translation.
    - [ ] To look up which process a memory page belongs to.
    - [ ] To store swapped-out pages.
    <br>

### **Topic 4: Deadlock & Concurrency (Session 9)**

28. **Breaking the "Hold and Wait" condition to prevent deadlock involves:**
    - [ ] Forcibly taking a resource away from a process.
    - [ ] Requiring a process to request all of its required resources at once, or release all held resources before requesting a new one.
    - [ ] Enforcing a strict ordering for resource requests.
    - [ ] Allowing resources to be shared simultaneously.
    <br>

29. **What is a "mutex"?**
    - [ ] A synchronization primitive that acts as a counter for a resource with multiple instances.
    - [ ] A lock that can be acquired by multiple threads at the same time.
    - [ ] A mutual exclusion lock, typically used to protect a critical section, ensuring only one thread can execute it at a time.
    - [ ] A hardware instruction for preventing deadlocks.
    <br>

30. **Which of the following is a deadlock prevention strategy?**
    - [ ] If a deadlock is detected, terminate one of the processes.
    - [ ] Before granting a resource, check if doing so would lead to an unsafe state.
    - [ ] Ensure that the "Circular Wait" condition can never occur by enforcing a strict ordering of resource requests.
    - [ ] Periodically check the system for deadlocked processes.
    <br>

**Answer Key (21-30)**
21. **Answer:** ||(B) In pure segmentation, memory is allocated in variable-sized blocks. Over time, this can lead to small, scattered free blocks (external fragmentation) that are unusable for larger requests. Paging avoids external fragmentation by using fixed-size pages but can suffer from internal fragmentation.||
22. **Answer:** ||(B) A page fault is a normal, expected event in a demand-paged virtual memory system. It's a trap to the OS, which then handles loading the required page from disk into a physical frame.||
23. **Answer:** ||(B) The working set model is a memory management concept which states that for a process to run efficiently, its working set (the pages it needs for its current phase of execution) must be resident in main memory. If not, thrashing will occur.||
24. **Answer:** ||(B) The Optimal algorithm is impossible to implement as it requires future knowledge. LRU is based on the principle of locality, which suggests that pages used recently are likely to be used again soon. Thus, replacing the least recently used page is a good approximation of replacing the one that won't be needed for the longest time.||
25. **Answer:** ||(A) This is the core benefit of virtual memory, which is typically implemented using demand paging. It allows the logical address space of a process to be much larger than the physical RAM installed on the machine.||
26. **Answer:** ||(A) Reentrant code (or pure code) is code that does not modify itself or rely on static variables. This allows multiple processes to share a single copy of the code in memory (e.g., a shared library), as each process has its own separate data section.||
27. **Answer:** ||(B) The TLB is a hardware cache that is part of the Memory Management Unit (MMU). It stores recent page-to-frame translations. If a translation is found in the TLB (a TLB hit), it's very fast. If not (a TLB miss), a slower lookup from the page table in main memory is required.||
28. **Answer:** ||(B) This strategy breaks the "Hold and Wait" condition. A process is either holding the resources it needs and running, or it is waiting for resources but holding none.||
29. **Answer:** ||(C) A mutex (mutual exclusion) is a simple lock. A thread acquires the mutex to enter a critical section and releases it upon exiting, allowing another thread to enter.||
30. **Answer:** ||(C) Deadlock prevention works by ensuring at least one of the four necessary conditions for deadlock can never occur. Enforcing a global order for acquiring resources (e.g., always lock A before B) is a common way to break the Circular Wait condition.||
<br>

### **Topic 5: Software Engineering & SDLC (Sessions 1-5 of SDM)**

31. **Which software process model is designed to handle risk by developing the software in a series of incremental releases?**
    - [ ] Waterfall Model
    - [ ] Spiral Model
    - [ ] V-Model
    - [ ] Prototyping Model
    <br>

32. **A "function-oriented" design approach primarily focuses on:**
    - [ ] The objects and classes that make up the system.
    - [ ] The flow of data through a system and the transformations applied to it.
    - [ ] The user interface and user experience.
    - [ ] The deployment and maintenance of the system.
    <br>

33. **In the context of software design, "modularity" refers to:**
    - [ ] The use of modern programming languages.
    - [ ] The practice of dividing a software system into separate, independent modules that can be developed and tested individually.
    - [ ] The number of lines of code in the project.
    - [ ] The aesthetic quality of the user interface.
    <br>

34. **What is the primary output of the Requirements Engineering phase?**
    - [ ] A fully functional software product.
    - [ ] A detailed architectural design document.
    - [ ] A Software Requirements Specification (SRS) document.
    - [ ] The source code for the application.
    <br>

35. **UML (Unified Modeling Language) is used for:**
    - [ ] Writing software source code.
    - [ ] Creating a standard, visual modeling language to specify, visualize, construct, and document the artifacts of a software system.
    - [ ] Managing project timelines and resources.
    - [ ] Automating software testing.
    <br>

### **Topic 6: Agile, DevOps & Testing (Sessions 6-13)**

36. **Which of the following is NOT a value of the Agile Manifesto?**
    - [ ] Working software over comprehensive documentation.
    - [ ] Responding to change over following a plan.
    - [ ] Processes and tools over individuals and interactions.
    - [ ] Customer collaboration over contract negotiation.
    <br>

37. **In the Scrum framework, who is responsible for prioritizing the product backlog?**
    - [ ] The Scrum Master
    - [ ] The Development Team
    - [ ] The Product Owner
    - [ ] The Stakeholders
    <br>

38. **What is the purpose of a "git merge" command?**
    - [ ] To create a new branch in the repository.
    - [ ] To combine the changes from a different branch into the current branch.
    - [ ] To discard all recent changes in the current branch.
    - [ ] To upload the code to a remote repository.
    <br>

39. **What does a Docker image contain?**
    - [ ] A running instance of an application.
    - [ ] A lightweight virtual machine.
    - [ ] A set of instructions for building a container.
    - [ ] A read-only template that includes the application code, libraries, and dependencies needed to run an application.
    <br>

40. **"Verification" in software testing refers to:**
    - [ ] "Are we building the product right?" (Does it meet the design specifications?)
    - [ ] "Are we building the right product?" (Does it meet the customer's needs?)
    - [ ] The process of testing the software with real users.
    - [ ] The final stage of testing before release.
    <br>

**Answer Key (31-40)**
31. **Answer:** ||(B) The Spiral Model is a risk-driven process model. Each loop in the spiral represents a phase of the software process and includes risk analysis, making it suitable for large, complex, and high-risk projects.||
32. **Answer:** ||(B) Function-oriented (or structured) design decomposes a system into a hierarchy of functions. Its main focus is on data flow and the processes that transform the data. This contrasts with object-oriented design, which focuses on objects.||
33. **Answer:** ||(B) Modularity is a fundamental design principle. A modular system is easier to understand, maintain, and test because changes in one module are less likely to affect other parts of the system (i.e., it promotes low coupling).||
34. **Answer:** ||(C) The SRS document is the official statement of what the system developers should implement. It clearly and precisely describes the functions, performance, and constraints of the system.||
35. **Answer:** ||(B) UML provides a set of graphical notations to create visual models of software systems, such as use case diagrams, class diagrams, sequence diagrams, and activity diagrams.||
36. **Answer:** ||(C) The Agile Manifesto explicitly states that it values "Individuals and interactions OVER processes and tools." This emphasizes communication and collaboration.||
37. **Answer:** ||(C) The Product Owner is the voice of the customer and stakeholders. They are solely responsible for managing the product backlog, which includes creating user stories, prioritizing them, and ensuring the backlog is clear and visible to the team.||
38. **Answer:** ||(B) `git merge` is a fundamental command for integrating changes. It takes the independent lines of development created by `git branch` and integrates them back into a single branch.||
39. **Answer:** ||(D) An image is a static blueprint. It contains everything needed to run an application. A "container" is a runnable instance of an image.||
40. **Answer:** ||(A) Verification is the process of checking that the software meets its specified functional and non-functional requirements. Validation is checking that the software meets the user's actual needs and expectations.||
<br>

### **Topic 7: Automation & Deployment (Sessions 14-16)**

41. **What is a key difference between manual and automation testing?**
    - [ ] Manual testing is faster than automation testing for regression suites.
    - [ ] Automation testing requires human intervention for every test case execution.
    - [ ] Manual testing can suffer from human error, while automation testing provides consistent and repeatable execution of test scripts.
    - [ ] Automation testing can find more bugs than manual testing.
    <br>

42. **In Selenium, what is a "locator"?**
    - [ ] A command to locate the browser window on the screen.
    - [ ] A way to find and identify a web element on a page (e.g., by ID, name, class, or XPath).
    - [ ] A tool for locating performance bottlenecks.
    - [ ] A type of test assertion.
    <br>

43. **What is a "delivery pipeline" in the context of Jenkins and CI/CD?**
    - [ ] The network path used to deliver software to the user.
    - [ ] A sequence of automated steps (e.g., build, test, deploy) that a code change goes through on its way to production.
    - [ ] The physical assembly line for manufacturing software CDs.
    - [ ] A list of features to be delivered in the next release.
    <br>

44. **Which testing method requires knowledge of the internal code structure, logic, and paths?**
    - [ ] Black-box testing
    - [ ] Grey-box testing
    - [ ] White-box testing
    - [ ] Acceptance testing
    <br>

45. **What is the primary role of a "slave node" in a Jenkins setup?**
    - [ ] To store the source code.
    - [ ] To provide a web interface for Jenkins.
    - [ ] To act as a distributed build agent, taking on build jobs dispatched by the Jenkins master to distribute the workload.
    - [ ] To back up the Jenkins configuration.
    <br>

46. **In Selenium WebDriver, what does the command `driver.findElement(By.xpath("//input[@name='username']"))` do?**
    - [ ] It finds all `<input>` elements on the page.
    - [ ] It finds the first `<input>` element that has a `name` attribute equal to "username".
    - [ ] It finds an element with the ID "username".
    - [ ] It finds an element with the text "username".
    <br>

47. **A "pipeline job" in Jenkins is typically defined using:**
    - [ ] A graphical drag-and-drop interface.
    - [ ] An XML configuration file.
    - [ ] A text file called a `Jenkinsfile`, which defines the stages of the CI/CD pipeline as code.
    - [ ] A Java properties file.
    <br>

48. **Which of the following is an example of non-functional testing?**
    - [ ] Testing if a user can successfully log in with valid credentials.
    - [ ] Testing if the "Add to Cart" button correctly adds an item to the cart.
    - [ ] Testing how the system performs under a high load of concurrent users.
    - [ ] Testing if the user profile page displays the correct information.
    <br>

49. **Integrating Selenium with a build tool like Maven is useful because:**
    - [ ] Maven can write the Selenium test scripts automatically.
    - [ ] It allows you to manage the Selenium WebDriver and other dependencies easily, and to run the tests as part of an automated build process.
    - [ ] Maven provides a better browser for running tests.
    - [ ] Selenium cannot run without Maven.
    <br>

50. **What is the "V-Model" in software testing?**
    - [ ] A model where testing is only performed at the very end of the development cycle.
    - [ ] A sequential development model where each development phase has a corresponding, parallel testing phase.
    - [ ] A type of agile methodology.
    - [ ] A model focused on visual testing of user interfaces.
    <br>

**Answer Key (41-50)**
41. **Answer:** ||(C) Automation testing excels at running large regression suites repeatedly without getting tired or making mistakes, ensuring consistency. Manual testing is better for exploratory testing and usability evaluation.||
42. **Answer:** ||(B) A locator is the strategy Selenium uses to find an HTML element on a web page so that it can interact with it (e.g., click it or type into it).||
43. **Answer:** ||(B) A delivery pipeline (or deployment pipeline) is a core concept in CI/CD. It automates the path that software takes from a developer's commit all the way to production, enforcing quality gates at each stage.||
44. **Answer:** ||(C) White-box (or clear-box) testing leverages knowledge of the internal implementation to design test cases that cover specific code paths, branches, and statements.||
45. **Answer:** ||(C) A Jenkins master-slave architecture allows you to scale your build environment. The master orchestrates the jobs, but the actual compilation and testing work is performed by one or more slave nodes.||
46. **Answer:** ||(B) XPath is a powerful language for navigating elements in an XML/HTML document. This specific expression looks for any `input` tag anywhere in the document that has a `name` attribute with the value 'username'.||
47. **Answer:** ||(C) The modern approach to Jenkins is "Pipeline as Code," where the entire CI/CD process is defined in a text file (`Jenkinsfile`) that is stored in source control along with the application code.||
48. **Answer:** ||(C) Non-functional testing evaluates the characteristics of the system, such as performance, security, reliability, and usability, rather than specific business functions. Load testing is a type of performance testing.||
49. **Answer:** ||(B) Using Maven allows you to declare dependencies like `selenium-java` and `webdrivermanager` in your `pom.xml`. Maven will handle downloading the correct JARs. You can then configure the Maven surefire plugin to run your Selenium tests automatically as part of the `mvn test` build phase.||
50. **Answer:** ||(B) The V-Model illustrates how testing activities are related to analysis and design activities. For every phase in the development lifecycle (the left side of the V), there is a corresponding testing phase (the right side of the V). It emphasizes that testing should start early.||