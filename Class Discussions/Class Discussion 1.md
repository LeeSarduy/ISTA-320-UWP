MSSA Cohort 3
Course: ISTA-320
Lesson Plan: 01
Name: Lee Sarduy

List two reasons for multitasking, and explain the rationale for them. 
To improve responsiveness: A long-running operation may involve tasks that do not require processor time. Common examples include I/O bound operations such as reading from or writing to a local disk or sending and receiving data across a network. In both of these cases, it does not make sense to have a program burn CPU cycles waiting for the operation to complete when the program could be doing something more useful instead (such as responding to user input). Most users of mobile devices take this form of responsiveness for granted and don’t expect their tablet to simply halt while it is sending and receiving email, for example. Chapter 24, “Improving response time by performing asynchronous operations,” discusses these features in more detail.
To improve scalability: If an operation is CPU bound, you can improve scalability by making efficient use of the processing resources available and using these resources to reduce the time required to execute the operation. A developer can determine which operations include tasks that can be performed in parallel and arrange for these elements to be run concurrently. As more computing resources are added, more instances of these tasks can be run in parallel. Until relatively recently, this model was suitable only for scientific and engineering systems that either had multiple CPUs or were able to spread the processing across different computers networked together. However, most modern computing devices now contain powerful CPUs that are capable of supporting true multitasking, and many operating systems provide primitives that enable you to parallelize tasks quite easily.

Explain Moore's law. What does Moore's law have to do with multitasking?
Moore’s Law basically states that the number of transistors that can be placed inexpensively on an integrated circuit will increase exponentially, doubling approximately every two years. The ability to pack transistors together led to the ability to pass data between them more quickly. This meant we could expect to see chip manufacturers produce faster and more powerful microprocessors at an almost unrelenting pace, enabling software developers to write ever more complicated software that would run more quickly. The limit to the speed at which processors can transmit data between components has caused chip companies to look at alternative mechanisms for increasing the amount of work a processor can do. The result is that most modern processors now have two or more processor cores.

In UWP, what namespace is used as the container for the multitasking methods?
System.Threading.Tasks.

What is the difference between tasks and threads? Explain.
The Task class is an abstraction of a concurrent operation. You create a Task object to run a block of code. You can instantiate multiple Task objects and start them running in parallel if sufficient processors or processor cores are available. Internally, the Windows Runtime (WinRT) implements tasks and schedules them for execution by using Thread objects and the ThreadPool class. The Task class provides a powerful abstraction for threading with which you can easily distinguish between the degree of parallelization in an application (the tasks) and the units of parallelization (the threads).

What is the ThreadPool?
WinRT optimizes the number of threads required to implement a set of concurrent tasks and schedules them efficiently according to the number of available processors. It implements a queuing mechanism to distribute the workload across a set of threads allocated to a thread pool (implemented by using a ThreadPool object). When a program creates a Task object, the task is added to a global queue. When a thread becomes available, the task is removed from the global queue and is executed by that thread. The ThreadPool class implements a number of optimizations and uses a work-stealing algorithm to ensure that threads are scheduled efficiently.

What parameters does the Task() constructor take?
The Task() constructor is overloaded, but all versions expect you to provide an Action delegate as a parameter. An Action delegate references a method that does not return a value. The default Action type references a method that takes no parameters. Other overloads of the Task constructor take an Action<object> parameter representing a delegate that refers to a method that takes a single object parameter. With these overloads, you can pass data into the method run by the task.

How do you start a thread?
You start a thread by using the Start() method of the task object. So if your task variable was named mytask, you would use mytask.Start();.

What is the difference between the Start() and Run() methods?
The Run() method basically starts a task as soon as it created as opposed to the Start() method that is used with a task object.

What is the difference between creating independent tasks with Tasks and parallelization with Parallel? Explain.
By using the Task class, you have complete control over the number of tasks your application creates. However, you have to modify the design of the application to accommodate the use of Task objects. You also have to add code to synchronize operations. In a complex application, the synchronization of tasks can become a nontrivial process that is easily prone to mistakes. With the Parallel class, you can parallelize some common programming constructs without having to redesign an application. Internally, the Parallel class creates its own set of Task objects, and it synchronizes these tasks automatically when they have completed. The Parallel class is located in the System.Threading.Tasks namespace and provides a small set of static methods that you can use to indicate that code should be run in parallel if possible.

Explain how manual cancellation works using a cancellation token.
A cancellation token is a structure that represents a request to cancel one or more tasks. The method that a task runs should include a System.Threading.CancellationToken parameter. An application that wants to cancel the task sets the Boolean IsCancellationRequested property of this parameter to true. The method running in the task can query this property at various points during its processing. If this property is set to true at any point, it knows that the application has requested that the task be canceled. Also, the method knows what work it has done so far, so it can undo any changes if necessary and then finish. Alternatively, the method can simply ignore the request and continue running.