# Theoretical basis

## Patterns

Resources: 
* [Learning JavaScript Design Patterns (Book by Addy Osmani)](https://addyosmani.com/resources/essentialjsdesignpatterns/book/)
* [JavaScript Patterns (Book by Stoyan Stefanov)](http://index-of.es/JS/Stoyan%20Stefanov%20-%20JavaScript%20Patterns%202010.pdf)
* [Factory Pattern (medium)](https://medium.com/front-end-weekly/understand-the-factory-design-pattern-in-plain-javascript-20b348c832bd)
* [Iterators and Generators (mdn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)

__*Singleton*__

Creating only one object of a “class.” We looked at several approaches if you want
to substitute the idea of a class with a constructor function and preserve the Javalike syntax. Otherwise, technically all objects in JavaScript are singletons. And also
sometimes developers would say “singleton,” meaning objects created with the
module pattern.

Usage: 
* Database connections
* Config files

[jsfiddle](https://jsfiddle.net/PurumVisum/evgr41qw/)
```
class SingletonClass {
    constructor() {
        if (!!SingletonClass.instance) {
            return SingletonClass.instance;
        }

        SingletonClass.instance = this;

        return this;
    }
}
```
__*Factory*__

A method that creates objects of type specified as a string at runtime.
We call the function Animal and both times it gives us a new animal instance.

*es6*

A factory function is any function which is not a class or constructor that returns a (presumably new) object. 
In JavaScript, any function can return an object.
 When it does so without the new keyword, it’s a factory function.

[jsfiddle](https://jsfiddle.net/PurumVisum/pz4jru9q/)

```
const Animal = function(name){
    const animal = {};
    animal.name = name;
    animal.walk = function(){
        console.log(this.name + " walks");
    }
    return animal;
};

const rabbit = Animal("rabbit");
const cat = Animal("cat");
rabbit.walk() // rabbit walks
cat.walk() // cat walks
```

*Mixins*

To further add functionality we use __mixins__ which is just a fancy way of describing an 
object which doesn’t have state itself but has some methods attached to it.

```
const canKill = {
  kill() {
    console.log("I can kill")
  }
}

k1 = Object.assign(Animal("k1"), canKill)
```

However if we need multiple killing animals we can create a __factory__ for this also.

```
const KillingAnimal = function(name) {
  const animal = Animal(name)
  const killingAnimal = Object.assign(animal, canKill)
  return killingAnimal;
}
```

__*Iterator*__
[jsfiddle](https://jsfiddle.net/PurumVisum/xf6r0qug/)
Providing an API to loop over and navigate around a complex custom data
structure.

As an example of a language feature in ES6, that uses the iterator standard in the language is that you can have a language construct such as:

```for (x of someObj) { ... }```
And the for/of logic only uses the iterator interface on someObj. It doesn't have to know anything specific about all the types of objects it can iterate. 
So, because of that, you can use for/of with ANY kind of object that supports a standard iterator. For example, you can use it with an array, a map, a set, or any custom object you create that supports the iterator interface.

Built-in iterables
```String```,``` Array ``` , ```TypedArray```, ```Map``` and ```Set``` are all built-in iterables, 
because their prototype objects all have a Symbol.iterator method.

*Iterator*
```
var myIterable = {
  *[Symbol.iterator]() {
    yield 1;
    yield 2;
    yield 3;
  },
  "key1": "key1Value",
  "key2": "key2Value",
  "key3": "key3Value"
}

try {
  for (let value of myIterable) {
    console.log(value);  // 1,2,3
  }
} catch (error) {
  console.log(error);
}
``` 
*Simple Object*
``` 
var myObject = {

  "key1": "key1Value",
  "key2": "key2Value",
  "key3": "key3Value"
}

try {
  for (let value of myObject) {
    console.log(value);
  }
} catch (error) {
  console.log(error);  //TypeError: myObject is not iterable 
}
``` 

__*Decorator*__

[jsfiddle](https://jsfiddle.net/PurumVisum/drz60nhk/)

Tweaking objects at runtime by adding functionality from predefined decorator
objects.

*at the time of writing, the decorators are currently in “Stage 2 Draft” form, meaning that they are mostly finished but still subject to changes*
```
function readonly(target, name, descriptor) {
  descriptor.writable = false;
  return descriptor;
}
class Job {
  @readonly
  title() { return 'CEO' }
}
``` 
*Mobx decorators (works only with babel or TS)*
``` 
import { observable, computed, action } from "mobx"

class Timer {
    @observable start = Date.now()
    @observable current = Date.now()

    @computed
    get elapsedTime() {
        return this.current - this.start + "milliseconds"
    }

    @action
    tick() {
        this.current = Date.now()
    }
}
``` 
*Create decorator (example in the jsFiddle)*
``` 
function doSomething(name) {
  console.log('Hello, ' + name);
}

function loggingDecorator(wrapped) {
  return function() {
    console.log('Starting');
    const result = wrapped.apply(this, arguments);
    console.log('Finished');
    return result;
  }
}

const wrapped = loggingDecorator(doSomething);

doSomething('Daria');
console.log("----------")
wrapped('Graham');
``` 

__*Façade*__

Providing a more convenient API by wrapping common (or poorly designed)
methods into a new one.

__*Proxy*__

Wrapping an object to control the access to it, with the goal of avoiding expensive
operations by either grouping them together or performing them only when really
necessary.

__*Mediator*__

Promoting loose coupling by having your objects not “talk” to each other directly
but only though a mediator object.

__*Observer*__

The Observer is a design pattern where an object (known as a subject) maintains a list of
 objects depending on it (observers),
 automatically notifying them of any changes to state.
 
 An Observable is simply an object where you can observe it's actions. So anything where you can listen to an action and then be told that action occurs is an Observable.
 
 This means an Event Listener is one. Because you can listen to events and the events immediately notify you that they have happened.


__*Strategy*__

Keeping the same interface while selecting the best strategy to handle the specific
task (context).
