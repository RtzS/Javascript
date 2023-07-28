**What are memory leaks?**
In simple words, a memory leak is an allocated piece of memory that the JavaScript engine is unable to reclaim. The JavaScript engine allocates memory when you create objects and variables in your application, and it is smart enough to clear out the memory when you no longer need the objects. Memory leaks are caused due to flaws in your logic, and they make way for poor performance in your application.

**Memory lifecycle**
In any programming language, memory lifecycle consists of three steps:

**Memory allocation:** the operating system allocates memory to the program during execution as needed
**Use memory:** your program uses previously allocated memory. Your program can perform read and write actions on the memory
**Release memory:** once your task is finished, allocated memory is released and becomes free. In high-level languages like JavaScript, memory release is handled by the garbage collector
If you understand how memory allocation and release happens in JavaScript, it’s very easy to solve memory leaks in your application.


**Memory allocation**
JavaScript has two storage options for memory allocation. One is the stack, and the other is the heap. All the primitive types, like number, Boolean, or undefined will be stored on the stack. Heap is the place for reference types like objects, arrays, and functions.

**Stack**
Stack follows the LIFO approach to allocate memory. All the primitive types like number, Boolean, and undefined can be stored under the stack:
![image](https://github.com/RtzS/Javascript/assets/8089250/1d2e7a60-952d-4e69-9e4f-06400c05d518)

Javascript Fifo Stack Diagram

**Heap**
Reference types like objects, arrays, and functions are stored on the heap. The reference types’ size cannot be determined at compile time, so memory is allocated based on the objects’ usage. The reference of object is stored on the stack and the actual object is stored on the heap:
![image](https://github.com/RtzS/Javascript/assets/8089250/85bc243c-b81c-40c1-8a2b-cc8dc55b47c2)

In the image above, the otherStudent variable is created by copying the student variable. In this scenario, otherStudent is created on the stack, but it points to the student reference on the heap.

We’ve seen that the main challenge for memory allocation in the memory cycle is when to release the allocated memory and make it available for other resources. In this scenario, garbage collection comes to the rescue.

**Garbage collector**
The main cause of memory leaks in an application is due to unwanted references. The garbage collector finds the memory that is no longer in use by the program and releases it back to the operating system for further allocation.

To know what is an unwanted reference, first, we need to get an idea of how garbage collection determines that a piece of memory is unreachable. Garbage collection uses two main algorithms to find unwanted references and unreachable code, reference count and mark-and-sweep.

**Reference count** : The reference count algorithm looks for objects that have no references. An object can be released if it has zero references pointing to it.

**Mark-and-sweep algorithm**
The mark-and-sweep algorithm reduces the definition of an unnecessary object to an unreachable object. If the object is not reachable, the algorithm considers this object unnecessary:
![image](https://github.com/RtzS/Javascript/assets/8089250/588679f5-74b0-4a03-8580-b597e99fcbb5)
The mark-and-sweep algorithm follows two steps. First, in JavaScript, the root is the global object. The garbage collector periodically starts from the root and finds all objects that are referenced from the root. It will mark all the reachable objects active. Then, garbage collection frees the memory for all objects that are not marked as active, returning the memory to the operating system.

**Types of memory leaks**
We can prevent memory leaks by understanding how unwanted references are created in JavaScript. The following scenarios cause unwanted references.
**1] Undeclared or accidental global variables**
One of the ways in which JavaScript is permissive is in the way it handles undeclared variables. A reference to an undeclared variable creates a new variable inside the global object. If you create a variable without any reference, its root would be the global object.
As we just saw in the mark-and-sweep algorithm, the references that are directly pointed to the root are always active, and the garbage collector cannot clear them, resulting in a memory leak:

function foo(){
    this.message = 'I am accidental variable';
}
foo();

As a solution, try to nullify these variables after use, or add use strict to enable a stricter mode of JavaScript that prevents accidental global variables.

**2] Closures**
A closure is a combination of a function bundled together or enclosed with references to its surrounding state, the lexical environment. In simple terms, a closure is an inner function that has access to the outer function’s scope.

Function scoped variables get cleaned up after the function has exited the call stack, whereas a closure keeps the outer scope variables referenced after its execution. Outer scope variables reside in the memory even though they are unused, so this is a common cause for memory leaks:

**3] Forgotten timers**
setTimeout and setInterval are the two timing events available in JavaScript. The setTimeout function executes when the given time is elapsed, whereas setInterval executes repeatedly for the given time interval. These timers are the most common cause of memory leaks.

**4] Out of DOM reference**
Out of DOM reference indicates nodes that have been removed from the DOM but are still available in the memory. The garbage collector cannot release these DOM objects since they are being referred to as object graph memory.
