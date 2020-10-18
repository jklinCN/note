#### Chapter 1 Introduction

1. An operating system is software that manages the computer hardware, as well as providing an environment for application programs to run.

   操作系统是一种管理计算机硬件和提供应用程序运行环境的软件。

2. A number of device controllers connected through a common bus that provides access between components and shared memory.

   系统总线（system bus）提供计算机组件访问共享内存的渠道。（除系统总线外还有很多总线）

3. Interrupts are a key way in which hardware interacts with the operating system. A hardware device triggers an interrupt by sending a signal to the CPU to alert the CPU that some event requires attention.

   中断是硬件与操作系统交互的关键。一个硬件设备通过给cpu发送信号触发一个中断，来警示cpu一些事件需要关注。

   具体过程：The CPU hardware has a wire called the interrupt-request line that the CPU senses after executing every instruction. When the CPU detects that a controller has asserted a signal on the interrupt-request line, it reads the interrupt number and jumps to the interrupt-handler routine by using that interrupt number as an index into the interrupt vector. It then starts execution at the address associated with that index. The interrupt handler saves any state it will be changing during its operation, determines the cause of the interrupt, performs the necessary processing, performs a state restore, and executes a return_from_interrupt instruction to return the CPU to the execution state prior to the interrupt.

4. For a computer to do its job of executing programs, the programs must be in main memory, which is the only large storage area that the processor can access directly.

   程序只有在处理器可以直接访问的主内存中才能执行。

5. Volatile storage will be referred to simply as memory.

   主内存通常是易失性存储设备，当电源关闭或者消失时，会丢失存储的内容。

6. Nonvolatile storage is an extension of main memory and is capable of holding large quantities of data permanently. Nonvolatile storage retains its contents when power is lost. It will be referred to as NVS. The vast majority of the time we spend on NVS will be on secondary storage. 

   非易失性存储是主存的扩展，能够永久地保存大量数据。当电源消失时，非易失性存储会保留其存储的内容，称作NVS。我们花在NVS的时间大部分是在辅助存储上，分为两种类型：1.机械的，像机械硬盘、光盘、磁带；2.电子的，像闪存、FRAM、NRAM、SSD。

7. Modern computer architectures are multiprocessor systems in which each CPU contains several computing cores.

   当代计算机体系结构是多处理器系统，每个cpu都包含多个计算核心。

8. To best utilize the CPU, modern operating systems employ multiprogramming, which allows several jobs to be in memory at the same time, thus ensuring that the CPU always has a job to execute.

   为了最大化利用cpu，现代操作系统会采用多程序设计，允许一些工作同时处于内存中，以此确保cpu总有工作去执行。

9. Multitasking is an extension of multiprogramming where in CPU scheduling algorithms rapidly switch between processes, providing users with a fast response time.

   多任务处理是多程序设计的一种扩展，其中的调度算法在进程之间快速切换，为用户提供更快的响应时间。

10. To prevent user programs from interfering with the proper operation of the system, the system hardware has two modes: user mode and kernel mode.

    为了防止用户程序干扰系统的正常运行，系统硬件有两种模式:用户模式和内核模式。

11. A process is the fundamental unit of work in an operating system. Process management includes creating and deleting processes and providing mechanisms for processes to communicate and synchronize with each other.

    进程是操作系统中的基本工作单元。进程管理包括创建和删除进程，以及为进程之间的通信和同步提供机制。

12. *An operating system manages memory by keeping track of what parts of memory are being used and by whom. It is also responsible for dynamically allocating and freeing memory space.

    操作系统通过记录内存的哪些部分被谁使用来管理内存。它还负责动态分配和释放内存空间。

13. Virtualization involves abstracting a computer’s hardware into several different execution environments.

    虚拟化涉及到把计算机硬件抽象到几个不同的执行环境中。

#### Chapter 2 Operating-System Structures

1. An operating system provides an environment for the execution of programs by providing services to users and programs.

   一个操作系统通过给用户和程序提供服务来为程序执行提供一个环境。

2. The three primary approaches for interacting with an operating system are (1) command interpreters, (2) graphical user interfaces, and (3) touch-screen interfaces.

   与操作系统进行交互的方法主要有三种：命令解释器、图形用户界面、触控屏界面。

3. System calls provide an interface to the services made available by an operating system. Programmers use a system call’s application programming interface (API) for accessing system-call services.

   系统调用为操作系统提供的服务提供接口。程序员使用系统调用的应用程序编程接口(API)来访问系统调用服务。

4. A linker combines several relocatable object modules into a single binary executable file. A loader loads the executable file into memory, where it be comes eligible to run on an available CPU.

   链接器将几个可重定位的对象模块组合到单个二进制可执行文件中。加载器将可执行文件加载到内存中，在那里它可以在可用的cpu上运行。

5. A monolithic operating system has no structure; all functionality is provided in a single, static binary file that runs in a single address space. Although such systems are difficult to modify, their primary benefit is efficiency.

   单片操作系统没有结构，所有的功能都在一个运行在单个地址空间的静态二进制文件中提供。虽然这类系统很难修改，但它们的主要好处是效率。

6. The microkernel approach for designing operating systems uses a minimal kernel; most services run as user-level applications. Communication takes place via message passing.

   用于设计操作系统的微内核方法使用一个最小的内核，大多数服务作为用户级应用程序运行。通信通过消息传递进行。

7. A modular approach for designing operating systems provides operating-system services through modules that can be loaded and removed during run time. Many contemporary operating systems are constructed as hybrid systems using a combination of a monolithic kernel and modules.

   用于设计操作系统的模块化方法通过可在运行时加载和删除的模块来提供操作系统服务。 许多现代操作系统是使用整体内核和模块的组合构建为混合系统的。

8. A boot loader loads an operating system into memory, performs initialization, and begins system execution.

   引导加载程序将操作系统加载到内存中，执行初始化，然后开始系统执行。

#### Chapter 3  Processes

1. A process is a program in execution, and the status of the current activity of a process is represented by the program counter, as well as other registers.

   进程是一个正在执行的程序，进程当前活动的状态由程序计数器和其他寄存器表示。

2. We emphasize that a program by itself is not a process. A program is a passive entity, such as a file containing a list of instructions stored on disk(often called an executable fil).In contrast,a process is an active entity,with a program counter specifying the next instruction to execute and a set of associated resources. A program becomes a process when an executable file is loaded into memory. 

   程序本身不是过程。 程序是静态实体，例如包含磁盘上存储的指令列表的文件（通常称为可执行文件）。相反，进程是动态实体，程序计数器指定要执行的下一条指令和一组相关资源。 当将可执行文件加载到内存中时，程序成为一个进程。 

3. The layout of a process in memory is represented by four different sections:(1) text, (2) data, (3) heap, and (4) stack.

   进程在内存中的布局由四个不同的部分表示:(1)文本，(2)数据，(3)堆，(4)栈。

4. As a process executes, it changes state. There are four general states of a process: (1) ready, (2) running, (3) waiting, and (4) terminated.

   当进程执行时，它会改变状态。进程一般有四种状态:(1)就绪，(2)运行，(3)等待，(4)终止。

5. A process control block (PCB) is the kernel data structure that represents a process in an operating system.

   进程控制块(PCB)是操作系统中表示进程的核心数据结构。

6. The role of the process scheduler is to select an available process to run on a CPU.

   进程调度程序的作用是选择一个可用的进程以在CPU上运行。

7. The fork() and CreateProcess() system calls are used to create pro-cesses on UNIX and Windows systems, respectively.

   fork()和createprocess()系统调用分别用于在unix和Windows系统上创建process。

8. Cooperating processes require an interprocess communication(IPC)mechanism that will allow them to exchange data— that is, send data to and receive data from each other. There are two fundamental models of interprocess communication: shared memory and message passing.

   进程协作需要一个进程间通信(IPC)机制，该机制允许进程间交换数据，即相互发送数据和接收数据。基本的进程间通信模型有两种：共享内存和消息传递。

9. A pipe provides a conduit for two processes to communicate. There are two forms of pipes, ordinary and named. Ordinary pipes are designed for communication between processes that have a parent–child relationship. Named pipes are more general and allow several processes to communicate.

   管道(pipe)为两个进程提供了通信的渠道。管道有两种形式，普通管道和命名管道。普通管道是为具有父-子关系的进程之间的通信而设计的。命名管道更通用，允许多个进程相互通信。

10. UNIX systems provide ordinary pipes through the pipe() system call. Ordinary pipes have a read end and a write end. A parent process can, for example, send data to the pipe using its write end, and the child process can read it from its read end. Named pipes in UNIX are termed FIFOs.

   UNIX systems通过the pipe()系统调用提供普通管道。普通管道有一个读取端和一个写入端。例如，父进程可以使用它的写入端向管道发送数据，子进程可以从它的读取端读取数据。UNIX中的命名管道称为FIFO。

11. Windows systems also provide two forms of pipes—anonymous and named pipes. Anonymous pipes are similar to UNIX ordinary pipes. They are unidirectional and employ parent–child relationships between the communicating processes. Named pipes offer a richer form of interprocess communication than the UNIX counterpart,FIFOs.

    Windows系统也提供了两种形式的管道：匿名管道和命名管道。 匿名管道类似于UNIX的普通管道。 它们是单向的，并且在通信过程之间采用父子关系。 命名管道提供了比UNIX相对应的FIFO更丰富的进程间通信形式。

12. Two common forms of client–server communication are sockets and remote procedure calls (RPCs). Sockets allow two processes on different machines to communicate over a network. RPCs abstract the concept of function (procedure) calls in such a way that a function can be invoked on another process that may reside on a separate computer.

    客户端与服务器通信的两种常见形式是套接字和远程过程调用（RPC）。 套接字允许不同机器上的两个进程通过网络进行通信。RPC抽象化函数（过程）调用的概念，这样可以在驻留在单独计算机上的另一个进程上调用一个函数。

13. The Android operating system uses RPCs as a form of interprocess communication using its binder framework.

    Android操作系统使用其绑定程序框架将RPC用作进程间通信的一种形式。

#### Chapter 4 Threads & Concurrency

1. A thread represents a basic unit of CPU utilization, and threads belonging to the same process share many of the process resources, including code and data.

   线程是CPU利用中的一个基本单位，而属于同一进程的线程共享许多进程资源，包括代码和数据。

2. There are four primary benefits to multithreaded applications: (1) responsiveness, (2) resource sharing, (3) economy, and (4) scalability.

   多线程应用程序有四个主要好处:(1)响应性，(2)资源共享，(3)经济性，(4)可伸缩性。

3. Concurrency exists when multiple threads are making progress, whereas parallelism exists when multiple threads are making progress simultaneously. On a system with a single CPU, only concurrency is possible;parallelism requires a multicore system that provides multiple CPUs.

   当多个线程正在运行时，存在并发性；当多个线程同时进行时，存在并行性。在只有一个cpu的系统上，只有并发性是有可能的，并行性需要一个提供多个cpu的多核系统。

   补充：Different concurrent designs enable different ways to parallelize.

   “并发”指的是程序的结构，“并行”指的是程序运行时的状态。并发设计让并发执行成为可能，而并行是并发执行的一种模式。

4. Data parallelism distributes subsets of the same data across different computing cores and performs the same operation on each core. Task parallelism distributes not data but tasks across multiple cores. Each task is running a unique operation.

   数据并行性将相同数据的子集分布在不同的计算核心上，并在每个核心上执行相同的操作。 任务并行化不在多个核心上分配数据，而是分配任务。 每个任务运行一个独特的操作。
   
5. User applications create user-level threads, which must ultimately be mapped to kernel threads to execute on a CPU. The many-to-one model maps many user-level threads to one kernel thread. Other approaches include the one-to-one and many-to-many models.

   用户应用程序创建用户级线程，这些线程最终必须映射到内核线程才能在CPU上执行。 多对一模型将许多用户级线程映射到一个内核线程。 其他方法包括一对一和多对多模型。

6. A thread library provides an API for creating and managing threads. Three common thread libraries include Windows, Pthreads, and Java threading. Windows is for the Windows system only, while Pthreads is available for POSIX-compatible systems such as UNIX,Linux,and macOS. Java threads will run on any system that supports a Java virtual machine.

   线程库提供用于创建和管理线程的API。 三种常见的线程库包括Windows，Pthreads和Java 线程。Windows仅用于Windows系统，而Pthreads可用于POSIX兼容系统，例如UNIX，Linux和macOS。Java线程将在支持Java虚拟机的任何系统上运行。

7. One way to address these difficulties and better support the design of concurrent and parallel applications is to transfer the creation and management of threading from application developers to compilers and run-time libraries. This strategy, termed implicit threading, is an increasingly popular trend. 

   解决这些困难并更好地支持并发和并行应用程序设计的一种方法是将线程的创建和管理从应用程序开发人员转移到编译器和运行时的库。这种称为隐式线程的策略是一种日益流行的趋势。

8. Implicit threading involves identifying tasks—not threads—and allowing languages or API frameworks to create and manage threads. There are several approaches to implicit threading, including thread pools, fork-join frameworks, and Grand Central Dispatch. Implicit threading is becoming an increasingly common technique for programmers to use in developing concurrent and parallel applications.

   隐式线程涉及识别任务（而不是线程），并允许语言或API框架创建和管理线程。 隐式线程有几种方法，包括线程池，fork-join框架和Grand Central Dispatch。 隐式线程正成为程序员在开发并行和并行应用程序中使用的越来越普遍的技术。

9. Threads may be terminated using either asynchronous or deferred cancellation. Asynchronous cancellation stops a thread immediately, even if it is in the middle of performing an update. Deferred cancellation informs a thread that it should terminate but allows the thread to terminate in an orderly fashion. In most circumstances, deferred cancellation is preferred to asynchronous termination.

   线程可以使用异步或延迟取消来终止。异步取消立即停止线程，即使它正处于执行更新的中间。延期取消通知一个线程它应该终止，但允许线程以一种有序的方式终止。在大多数情况下，延迟取消优先于异步终止。

#### Chapter 5 CPU Scheduling

1. CPU scheduling is the task of selecting a waiting process from the ready queue and allocating the CPU to it. The CPU is allocated to the selected process by the dispatcher.

   CPU调度是从就绪队列中选择一个等待进程并将CPU分配给它的任务。 CPU由调度程序分配给选定的进程。

2. Scheduling algorithms may be either preemptive (where the CPU can be taken away from a process) or nonpreemptive (where a process must voluntarily relinquish control of the CPU). Almost all modern operating systems are preemptive.

   调度算法可以是抢占式（CPU可能会脱离进程），或者是非抢占式（进程必须自愿放弃对CPU的控制）。几乎所有现代操作系统都是抢占式的。

3. Scheduling algorithms can be evaluated according to the following five criteria: (1)CPU utilization, (2) throughput, (3) turnaround time, (4) waiting time, and (5) response time.

   调度算法可以根据以下5个标准来评估:(1)CPU利用率，(2)吞吐量，(3)周转时间，(4)等待时间，(5)响应时间。

4. First-come, first-served (FCFS) scheduling is the simplest scheduling algorithm, but it can cause short processes to wait for very long processes.

   先来先服务（FCFS）调度是最简单的调度算法，但是它可能导致较短的进程等待非常长的进程。

5. Shortest-job-first (SJF) scheduling is provably optimal, providing the shortest average waiting time. Implementing SJF scheduling is difficult, however, because predicting the length of the next CPU burst is difficult.

   最短作业优先(SJF)调度是一种可以证明是最优的调度算法，它提供了最短的平均等待时间。但是，实现SJF调度很困难，因为很难预测下一个CPU突发的长度。

6. Round-robin (RR) scheduling allocates the CPU to each process for a time quantum. If the process does not relinquish the CPU before its time quantum expires, the process is preempted, and another process is scheduled to run for a time quantum.

   轮询（RR）调度将CPU分配给每个进程并给一个时间量。 如果该进程在其时间量到期之前没有放弃CPU，则抢占该进程，并安排另一个进程运行一个时间段。

7. Priority scheduling assigns each process a priority, and the CPU is allocated to the process with the highest priority. Processes with the same priority can be scheduled in FCFS order or using RR scheduling.

   优先级调度为每个进程分配一个优先级，并将CPU分配给具有最高优先级的进程。 具有相同优先级的进程可以按FCFS顺序或者RR调度进行调度。

8. Multilevel queue scheduling partitions processes into several separate queues arranged by priority, and the scheduler executes the processes in the highest-priority queue. Different scheduling algorithms may be used in each queue.

   多级队列调度将进程划分为按优先级排列的几个单独的队列，调度程序在最高优先级的队列中执行进程。 在每个队列中可以使用不同的调度算法。

9. Multilevel feedback queues are similar to multilevel queues, except that a process may migrate between different queues.

   多级反馈队列与多级队列相似，不同之处在于进程可以在不同的队列之间迁移。

10. Multicore processors place one or more CPUs on the same physical chip,and each CPU may have more than one hardware thread. From the perspective of the operating system, each hardware thread appears to be a logical CPU.

    多核处理器将一个或多个CPU放在同一物理芯片上，每个CPU可能具有多个硬件线程。 从操作系统的角度来看，每个硬件线程都好像是逻辑CPU。

11. Load balancing on multicore systems equalizes loads between CPU cores,although migrating threads between cores to balance loads may invalidate cache contents and therefore may increase memory access times.

    多核系统上的负载均衡可以均衡CPU内核之间的负载，尽管在内核之间迁移线程以平衡负载可能会使缓存内容无效，从而可能增加内存访问时间。

12. Soft real-time scheduling gives priority to real-time tasks over non-real-time tasks. Hard real-time scheduling provides timing guarantees for real-time tasks.

    软实时调度将实时任务优先于非实时任务。 硬实时调度可为实时任务提供时间保证。

13. Rate-monotonic real-time scheduling schedules periodic tasks using astatic priority policy with preemption.

    速率单调实时调度使用具有抢占权的静态优先级策略调度周期性任务。

14. Earliest-deadline-first (EDF) scheduling assigns priorities according to deadline. The earlier the deadline, the higher the priority; the later the deadline, the lower the priority.

    最早截止时间优先（EDF）调度根据截止时间分配优先级。 截止日期越早，优先级越高； 截止日期越晚，优先级越低。

15. Proportional share scheduling allocates T shares among all applications. If an application is allocated N shares of time, it is ensured of having N/T of the total processor time.

    比例份额调度在所有应用程序之间分配T个份额。 如果应用程序被分配到N个时间份额，则可以确保它拥有总处理器时间的N ∕ T。

16. Linux uses the completely fair scheduler (CFS), which assigns a proportion of CPU processing time to each task. The proportion is based on the virtual runtime (vruntime) value associated with each task.

    Linux使用完全公平的调度程序（CFS），它为每个任务分配一定比例的CPU处理时间。 该比例基于与每个任务关联的虚拟运行时间（vruntime）的值。

17. Windows scheduling uses a preemptive, 32-level priority scheme to deter-mine the order of thread scheduling.

    Windows调度使用抢占式的32级优先级方案来确定线程调度的顺序。

18. Solaris identifies six unique scheduling classes that are mapped to a global priority. CPU-intensive threads are generally assigned lower priorities(and longer time quantums), and I/O-bound threads are usually assigned higher priorities (with shorter time quantums.)

    Solaris确定了六个映射到全局优先级的唯一调度类。通常将CPU密集型线程分配给较低的优先级（和更长的时间范围），并且将I / O绑定线程分配给更高的优先级（具有更短的时间范围）。

#### Chapter 6 Synchronization Tools

1. A race condition occurs when processes have concurrent access to shared data and the final result depends on the particular order in which con-current accesses occur. Race conditions can result in corrupted values of shared data.

   当进程可以并发访问共享数据并且最终结果取决于并发访问发生的特定顺序时，就会发生竞争状态。 竞争状态可能导致共享数据的值损坏。

2. A critical section is a section of code where shared data may be manipulated and a possible race condition may occur. The critical-section problem is to design a protocol whereby processes can synchronize their activity to cooperatively share data.

   临界区是代码的一部分，在其中共享数据可能被使用，并且可能发生竞争状态。临界区的问题是设计一个协议，使进程能够同步它们的活动，以协同地共享数据。

3. A solution to the critical-section problem must satisfy the following three requirements: (1) mutual exclusion, (2) progress, and (3) bounded waiting. Mutual exclusion ensures that only one process at a time is active in its critical section. Progress ensures that programs will cooperatively determine what process will next enter its critical section. Bounded waiting limit show much time a program will wait before it can enter its critical section.

   临界区问题的解决方案必须满足以下三个要求：（1）相互排斥，（2）进展，（3）有界等待。相互排斥确保在临界区中一次仅激活一个进程 。 进展确保程序将协作确定下一步将进入临界区的进程。 有界的等待限制显示程序在进入临界区之前需要等待的时间。

4. Software solutions to the critical-section problem, such as Peterson’s solution, do not work well on modern computer architectures.

   临界区问题的软件解决方案（例如Peterson的解决方案）在现代计算机体系结构上效果不好。

5. Hardware support for the critical-section problem includes memory barriers; hardware instructions, such as the compare-and-swap instruction; and atomic variables.

   临界区问题的硬件支持包括内存限制、硬件指令（如比较和交换指令）和原子变量。

6. A mutex lock provides mutual exclusion by requiring that a process acquire a lock before entering a critical section and release the lock on exiting the critical section.

   互斥锁通过要求进程在进入临界区之前获取一个锁并释放与该临界区对应的锁来提供互斥。

7. Semaphores, like mutex locks, can be used to provide mutual exclusion. However, whereas a mutex lock has a binary value that indicates if the lock is available or not, a semaphore has an integer value and can therefore be used to solve a variety of synchronization problems.

   信号量，就像互斥锁一样，可以用来提供互斥。然而，互斥锁有一个二进制值来指示锁是否可用，而信号量有一个整数值，因此可以用来解决各种同步问题。

8. A monitor is an abstract data type that provides a high-level form of process synchronization. A monitor uses condition variables that allow processes to wait for certain conditions to become true and to signal one another when conditions have been set to true.

   监视器是一种抽象的数据类型，提供了高级形式的进程同步。 监视器使用条件变量，这些条件变量允许进程等待某些条件变为真，并在条件设置为真时互相发出信号。

9. Solutions to the critical-section problem may suffer from liveness problems, including deadlock.

   临界区问题的解决方案可能会遇到活性问题，包括死锁。

10. The various tools that can be used to solve the critical-section problem as well as to synchronize the activity of processes can be evaluated under varying levels of contention. Some tools work better under certain contention loads than others.

    可以在各种竞争水平下评估可用于解决关键部分问题以及同步流程活动的各种工具。 有些工具在某些工作量负载下比其他工具更好。

#### Chapter 7 Synchronization Examples

1. Classic problems of process synchronization include the bounded-buffer,readers–writers, and dining-philosophers problems. Solutions to these problems can be developed using the tools presented in Chapter 6, including mutex locks, semaphores, monitors, and condition variables.

   流程同步的经典问题包括有限缓冲区，读者-作家和用餐哲学家问题。 可以使用第6章中介绍的工具开发这些问题的解决方案，包括互斥锁，信号量，监视器和条件变量。

2. Windows uses dispatcher objects as well as events to implement process synchronization tools.

   Windows使用调度程序对象和事件来实现进程同步工具。

3. Linux uses a variety of approaches to protect against race conditions,including atomic variables, spinlocks, and mutex locks.

   Linux使用多种方法来防止竞争情况，包括原子变量，自旋锁和互斥锁。

4. The POSIX API provides mutex locks, semaphores, and condition variables. POSIX provides two forms of semaphores: named and unnamed. Several unrelated processes can easily access the same named semaphore by simply referring to its name. Unnamed semaphores cannot be shared as easily,and require placing the semaphore in a region of shared memory.

   POSIX API提供互斥锁，信号量和条件变量。POSIX提供两种形式的信号量：已命名和未命名。 几个不相关的进程可以通过简单地引用其名称来轻松访问相同的已命名的信号量。 未命名的信号量不能轻易共享，需要将信号量放置在共享内存的区域中

5. Java has a rich library and API for synchronization. Available tools include monitors (which are provided at the language level) as well as reentrant locks, semaphores, and condition variables (which are supported by the API).

   Java有一个丰富的库和用于同步的API。 可用的工具包括监视器（在语言级别提供）以及可重入锁，信号量和条件变量（API支持）

6. Alternative approaches to solving the critical-section problem include transactional memory, OpenMP, and functional languages. Functional languages are particularly intriguing, as they offer a different programming paradigm from procedural languages. Unlike procedural languages, functional languages do not maintain state and therefore are generally immune from race conditions and critical sections.

   解决临界区问题的替代方法包括事务存储，OpenMP和功能语言。 功能语言特别吸引人，因为它们提供了与程序语言不同的编程范例。 与程序语言不同，功能语言不会保持状态，因此通常不受竞争状态和临界区的影响。

#### Chapter 8 Deadlock

1. Deadlock occurs in a set of processes when every process in the set is waiting for an event that can only be caused by another process in the set.

   当一组进程中的每个进程都在等待一个只能由该集中的另一个进程引起的事件时，就会发生死锁。

   抽象解释：Perhaps the best illustration of a deadlock can be drawn from a law passed by the Kansas legislature early in the 20th century. It said, in part:“When two trains approach each other at a crossing, both shall come to a full stop and neither shall start up again until the other has gone.”

   当两列火车在交叉口接近时，两列列车应完全停止，在另一列列车离开之前，任何一列列车都不得重新启动。

2. There are four necessary conditions for deadlock: (1) mutual exclusion, (2)hold and wait, (3) no preemption, and (4) circular wait. Deadlock is only possible when all four conditions are present.

   死锁有四个必要条件：（1）互斥，（2）保持等待，（3）无抢占，（4）循环等待。只有当所有四个条件都存在时，才可能出现死锁。

3. Deadlocks can be modelled with resource-allocation graphs, where a cycle indicates deadlock.

   死锁可以用资源分配图建模，其中循环表示死锁。

4. Deadlocks can be prevented by ensuring that one of the four necessary conditions for deadlock cannot occur. Of the four necessary conditions,eliminating the circular wait is the only practical approach.

   可以确保死锁的四个必要条件之一不会发生来防止死锁。 在这四个必要条件中，消除循环等待是唯一可行的方法。

5. Deadlock can be avoided by using the banker’s algorithm, which does not grant resources if doing so would lead the system into an unsafe state where deadlock would be possible.

   死锁可以通过使用银行家算法来避免，如果这样做会导致系统进入可能出现死锁的不安全状态，那么就不会授予资源。

6. A deadlock-detection algorithm can evaluate processes and resources on a running system to determine if a set of processes is in a deadlocked state.

   死锁检测算法可以评估正在运行的系统上的进程和资源，以确定一组进程是否处于死锁状态。

7. If deadlock does occur, a system can attempt to recover from the deadlock by either aborting one of the processes in the circular wait or preempting resources that have been assigned to a deadlocked process.

   如果确实发生死锁，系统可以通过中止循环等待中的某个进程或抢占已分配给死锁进程的资源来尝试从死锁中恢复。

#### Chapter 9 Main Memory

