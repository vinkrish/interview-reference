# NodeJS

[Follow here](https://vigowebs.medium.com/frequently-asked-node-js-interview-questions-and-answers-b74fa1f20678)

## What is Node.js?

Node.js is a runtime environment that allows you to run JavaScript code on the server-side, outside of a web browser. It is built on the V8 JavaScript engine, which is the same engine that powers Google Chrome, but it extends the capabilities of JavaScript by providing server-side APIs like file system access, network requests, and more.

Key points about Node.js:

- Asynchronous and Event-driven: Node.js uses an event-driven, non-blocking I/O model, which makes it highly efficient, especially for I/O-intensive operations such as handling HTTP requests or interacting with databases. Instead of waiting for operations to complete, Node.js uses callbacks and events to handle multiple tasks concurrently.
- Single-threaded but Scalable: Despite being single-threaded, Node.js is designed to handle many concurrent requests using its non-blocking I/O model. It achieves scalability by using an event loop that efficiently manages asynchronous operations without the overhead of multiple threads.
- NPM (Node Package Manager): Node.js comes with a robust package ecosystem, NPM, which is the largest repository of open-source libraries and modules, allowing developers to easily integrate third-party code and tools into their projects.
- Use Cases: Node.js is commonly used for building real-time applications (like chat applications), RESTful APIs, streaming services, and microservices. It is particularly effective in handling applications that involve a lot of I/O, such as interacting with databases or external APIs.

## Explain event-driven programming in Node.js?

Event-driven programming is a key concept in Node.js, and it refers to the design paradigm where the flow of a program is determined by events like user actions (clicks, keyboard inputs), messages, or system events (file I/O, HTTP requests). In Node.js, event-driven programming allows asynchronous, non-blocking execution, enabling the server to handle many connections concurrently without being tied up by long-running operations.

Here’s a breakdown of how event-driven programming works in Node.js:

**1. Event Loop**:
At the core of Node.js is the event loop, which continuously monitors for incoming events or tasks. These events can be HTTP requests, file system operations, timers, or custom events. When an event occurs, the event loop triggers corresponding callback functions that were registered to handle those events.

- Blocking (Synchronous): If a function performs a task synchronously, it will block the event loop, meaning no other operations can be processed until the task is complete.
- Non-blocking (Asynchronous): In contrast, asynchronous operations are handled by the event loop without blocking it. Once the asynchronous task is complete, the event loop invokes the associated callback.

**2. Event Emitter**:

Node.js has an EventEmitter class that helps in managing event-driven architecture. Any object that listens for events or triggers events is typically an instance of the EventEmitter class. You can attach listeners to events, and when the event occurs, Node.js invokes the corresponding callback.

**3. Callbacks and Listeners**:
In an event-driven system, callbacks (also known as event handlers or listeners) are functions that are executed when a particular event occurs. When an asynchronous operation finishes, a callback function is executed, which allows Node.js to continue running other operations while waiting for the event to occur.

How it works:

- Registering a listener: You attach a function (callback) to an event. This function will be executed whenever the event is emitted.
- Emitting an event: When the event occurs (e.g., an HTTP request is received), the event emitter "emits" the event, triggering any attached listeners.

**4. Advantages of Event-driven Programming in Node.js**:

- Non-blocking I/O: This is particularly useful in scenarios where you have I/O-heavy operations (like reading files, querying databases) because the event loop doesn't wait for these operations to complete before moving on to handle other tasks.
- Scalability: Since Node.js doesn’t block the execution thread for I/O operations, it can handle a large number of concurrent connections with minimal overhead.
- Efficiency: Event-driven programming helps utilize system resources efficiently, especially in handling real-time applications, chat applications, or APIs that involve many simultaneous users or connections.

## What is the difference between require() and import in Node.js?

**1. Module Systems**:

- `require()`: This is the standard way of importing modules in Node.js using the CommonJS module system. It has been in use since the early days of Node.js. 
 - `require()` is dynamic, meaning it can be called conditionally, at any point in the code. This allows you to load modules at runtime.
- `import`: This is part of the ES6 (ECMAScript 2015) standard, also known as the ESM (ECMAScript Module) system, which was introduced later and is now supported in modern JavaScript environments, including Node.js (since version 12+ with certain configurations). 
 - `import` is static, meaning it must be called at the top level of the module and cannot be conditionally imported. All imports are resolved at the start of the program.
