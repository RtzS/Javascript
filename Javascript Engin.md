What is the JavaScript Engine:

The JavaScript Engine is a program whose responsibility is to execute JavaScript code. All modern browsers come with their own version of the JavaScript Engine but the most popular one is Google’s V8 Engine. Google’s V8 engine powers Google Chrome browsers, as well as, Node.js. Node.js is a JavaScript runtime that is used to build server-side applications outside of the browser.
![image](https://github.com/RtzS/Javascript/assets/8089250/cf26330c-bb7a-4325-ab27-da717104a19d)

A JavaScript engine contains heap memory and a call stack. A call stack is where our code executes. Heap memory is an unstructured memory pool containing the objects that we need in our program.

Here is a list of the different JavaScript Engines for each major Internet browser:
![image](https://github.com/RtzS/Javascript/assets/8089250/fd526173-5eed-4b77-a258-a004895874b1)

Let’s understand each of them.

**1. V8:** V8 is a JavaScript engine developed by the Chromium Project for Google Chrome and Chromium web browsers. It is a JavaScript engine that can run standalone, or be embedded into any C++ application. Using its own parser, it generates an abstract syntax tree. Then, Ignition generates bytecode from this syntax tree using the internal V8 bytecode format. Bytecode is compiled into machine code by TurboFan. It also handles memory allocation for objects, and garbage collects objects it no longer needs. Optimization techniques such as elision of expensive runtime properties, and inline caching. The garbage collector is a generational incremental collector.

V8 provides an edge as it allows JavaScript to run much faster, which improves users’ experience of the web, paves the way for the development of web applications, and spurs rapid growth of server-side JavaScript through projects like Node.js.

**2. Chakra:** Chakra is a JScript engine developed by Microsoft. It is proprietary software. It is used in the Internet Explorer web browser. A distinctive feature of the engine is that it JIT compiles scripts on a separate CPU core, parallel to the web browser.



**3. Spider Monkey:** SpiderMonkey is the first JavaScript engine, written by Brendan Eich at Netscape Communications, later released as open-source and currently maintained by the Mozilla Foundation. It is still used in the Firefox web browser.



**4. Webkit:** WebKit is developed by Apple and used in its Safari web browser, as well as all iOS web browsers. It is used by the BlackBerry Browser, PlayStation consoles beginning from the PS3, the Tizen mobile operating systems, and a browser included with the Amazon Kindle e-book reader. WebKit’s C++ Application Programming Interface (API) provides a set of classes to display Web content in windows and implements browser features such as following links when clicked by the user, managing a back-forward list, and managing a history of pages recently visited.


How Does **Just-in-Time Compilation (JIT)** Work?
So, how does the JavaScript Just-in-Time compiler work? As a new piece of JavaScript code enters the JavaScript Engine, the first step performed is parsing of the code. During this process, the code is parsed into a data structure called the Abstract Syntax Tree (AST).

The Abstract Syntax Tree first splits each line of code into pieces that are meaningful to JavaScript, such as the let, static, or function keywords. It then saves these pieces of code into a tree-like structure. The next step checks whether there are any syntax errors and, if none are found, the resulting tree is used to generate the machine code.
![image](https://github.com/RtzS/Javascript/assets/8089250/248f7bd5-01a5-48fe-99cc-416e5f4cd455)

![image](https://github.com/RtzS/Javascript/assets/8089250/73149595-6a53-4a52-91cb-620a6c92ca48)
