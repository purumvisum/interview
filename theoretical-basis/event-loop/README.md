# Event Loop 

### Resourses:
* [JSConf EU 2014, Event loop(video)](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

## V8
![Event loop](https://github.com/purumvisum/interview/blob/master/theoretical-basis/event-loop/event-loop.png)
* **Heap** - Objects are allocated in a heap which is just a name to denote a large mostly unstructured region of memory
* **Stack** - This represents the single thread provided for JavaScript code execution. 
    Function calls form a stack of frames (more on this below)
* **Browser or Web APIs** are built into your web browser, and are able to expose data from 
the browser and surrounding computer environment and do useful complex things with it. They are not part of the JavaScript language itself, rather they are built on top of the core JavaScript language,
 providing you with extra superpowers to use in your JavaScript code.
