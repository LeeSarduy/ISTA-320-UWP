MSSA Cohort 3
Course: ISTA-320
Lesson Plan: 02
Name: Lee Sarduy

What is an asynchronous method? When the book talks about a contract, what is the contract and who is it with?
An asynchronous method is one that does not block the current thread on which it starts to run. When an application invokes an asynchronous method, an implied contract expects the method to return control to the calling environment quite quickly and to perform its work on a separate thread. The definition of quite is not a mathematically defined quantity, but the expectation is that if an asynchronous method performs an operation that might cause a noticeable delay to the caller, it should do so by using a background thread, enabling the caller to continue running on the current thread.

What can be the problem with decomposing a series of discrete method calls into a set of tasks, such as we saw in chapter 23?
A problem with decomposing a series of discrete method calls into a set of tasks is that some method calls rely on information in the other method calls that haven't completed yet.

What can be the problem with decomposing a series of discrete method calls into a set of continuations? When does the last continuation "complete" as compared to the previous continuations? What problem might this cause?
When decomposing a series of discrete method calls into a set of continuations, one problem can be that the signatures of the methods have to change to accommodate the requirements of continuations (the Task object that instigated the continuation is passed as a parameter to a continuation method). The last continuation completes after the previous continuations. Another problem is that any following methods do not wait for the continuations to complete.

What might be the problem with implementing the previous solution as a continuation passing a delegate? What would be your interpretation with this error message: "The application called an interface that was marshaled for a different thread."?
When decomposing a series of discrete method calls into a set of continuations there is the possibility that the final continuation generates a System.Exception exception with the rather obscure message, “The application called an interface that was marshaled for a different thread.” This can happen if your task is trying to access information in another thread..

The book suggests a solution using a continuation delegate calling another continuation delegate via an anonymous function. What does the book identify as a problem with this suggested solution?
This works, but it is messy and difficult to maintain. You now have a delegate (the continuation) specifying another delegate (the code to be run by RunAsync).

What does the async modifier do? What does the await operator do?
The async modifier indicates that a method contains functionality that can be run asynchronously. The await operator specifies the points at which this asynchronous functionality should be performed.

What is an awaitable object? Be specific.
An awaitable object is a type that provides the GetAwaiter method, which returns an object that in turn provides methods for running code and waiting for it to complete. The C# compiler converts your code into statements that use these methods to create an appropriate continuation.

In a method definition, how do you create and run a Task and return a reference to the Task? What is the type of such a method? What does the method return?
You would set the return type as Task in the method definition. Inside the method, you create and run the task using Task mytask = Task.Run(() => { /* code for the task */ });. You would then return the task like any other variable: return mytask;.

How do you define method calls in the implementation of an async method? Specifically, you must define a task, you must run the task, you must implement the task, and you must await the task. What is the syntax for doing this?
This is similar to the above method but adds the use of await.
Task mytask = Task.Run(() => { /* code for the task */ });
await mytask;
What is the difference between decomposing a series of method calls that do not return values, and a series of method calls that return values? What is the Result property of a method that returns a value? How do you use the await operator in this circumstance?
The answer was in the question; the difference is that the method calls that return values have values to return. To do this, you use the generic Task<TResult> class, where the type parameter, TResult, specifies the type of the result. The await operator extracts the value from the Task returned by the method, and in this case assigns it to the result variable.
What is the difference between the await operator and the Wait method?
The await operator is not the same as using the Wait method of a task. The Wait method always blocks the current thread and does not allow it to be reused until the task completes.