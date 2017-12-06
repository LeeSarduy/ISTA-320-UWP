MSSA Cohort 3
Course: ISTA-320
Lesson Plan: 03
Name: Lee Sarduy

What are the two scenarios in which you can use PLINQ to speed up operations? Why does using PLINQ in these scenarios speed up processing?
PLINQ can speed up operations when searching through lengthy enumerable data structures. PLINQ is ideal for scenarios that involve data sets with large numbers of elements, or if the criteria specified for matching data involve complex, computationally expensive operations. PLINQ provides a set of extensions to LINQ that is based on Tasks and that can help you boost performance and parallelize some query operations.

How does AsParallel qualify as an extension method? First, explain what an extension method is and how you de fine extension methods, and them explain why AsParallel qualifies as an extension method.
Using an extension method, you can extend an existing type (a class or a structure) with additional static methods without affecting the existing code. These static methods become immediately available to your code in any statements that reference data of the type being extended. The AsParallel method extends the ParallelQuery class that acts in a similar manner to the original, except that it provides parallel implementations of many of the LINQ operators, such as join and where.

How do you cancel a PLINQ query before it finishes? Be specfic with respect to the variables and methods used for the cancellation operation, and how the variables and methods are used.
To cancel a PLINQ query before it finishes, you specify a CancellationToken object from a CancellationTokenSource and use the WithCancellation extension method of the ParallelQuery. For example: 
CancellationToken tok = ...;
...
var orderInfoQuery =
    from c in CustomersInMemory.Customers.AsParallel().WithCancellation(tok)
    join o in OrdersInMemory.Orders.AsParallel()
    on ...

	Why is it important to synchronize concurrent access to a server? Give an example of a specific condition that will cause an error in your application if concurrent access is not synchronized.
It is important to synchronize concurrent access because if a task stores a value in a variable, it needs to ensure that another task doesn't modify that variable before it has a chance to read it. For example, if an online shopping app stored the price of a users shopping cart as $50, but between the time the total was displayed and the payment was processed, another task changed that variable to 200 so the customer was charged $200.

What does the lock statement do?
The lock statement attempts to obtain a mutual-exclusion lock over the specified object (you can actually use any reference type, not just object), and it blocks if this same object is currently locked by another thread. When the thread obtains the lock, the code in the block following the lock statement runs. At the end of this block, the lock is released. If another thread is blocked waiting for the lock, it can then grab the lock and continue its processing.

This is not in the book. Define mutex, define semaphore, and explain the difference between them. A mutex is analogous to a single key to a room. A person holding the key, which is analogous to a thread, is the only one who can have access to the room. The person with the access will then have to give up the key to the next person in line. Therefore, a mutex can only be released by the thread that acquires it. Using the same analogy in mutex, semaphores are the number of similar keys that can access the same number of rooms with similar locks. A semaphore or the value of a semaphore count will depend on the number of people (threads) who enter or exit from the room. If there are 5 rooms and they are all occupied, then the semaphore count is zero. If two leave the room, then the count is two and the two keys are given to next two in the queue.
Read more: Difference Between Mutex and Semaphore | Difference Between http://www.differencebetween.net/language/difference-between-mutex-and-semaphore/.

What does it mean to say that some collection classes are not thread safe? Explain how not being thread safe may lead one of these collection classes to produce a malfunction in the program.
The List<T> class is not thread safe. If running in parallel, multiple calls the Add method to append a value to the collection make it highly probable that some of the calls to Add will interfere with one another and cause some corruption. A solution is to use one of the collections from the System.Collections.Concurrent namespace because these collections are thread safe. The generic ConcurrentBag<T> class in this namespace is probably the most suitable collection to use for this example.

Explain how thread safe collection classes are made thread safe.
The methods in thread safe collection classes like ConcurrentBag<T> have to lock and unlock data to guarantee thread safety.

Why are thread safe classes slower than non-thread safe classes? Be specific.
Locking and unlocking data to guarantee thread safety adds to the overhead of the calling methods.