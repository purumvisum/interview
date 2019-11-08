# Design Patterns

Resources: 
* [JavaScript Patterns](http://index-of.es/JS/Stoyan%20Stefanov%20-%20JavaScript%20Patterns%202010.pdf)
* [Factory Pattern (medium)](https://medium.com/front-end-weekly/understand-the-factory-design-pattern-in-plain-javascript-20b348c832bd)
* [Iterators and Generators (mdn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)

Сontents:
* [Singleton](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#singleton)
* [Factory](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#factory)
* [Mixins](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#mixins)
* [Decorator](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#decorator)
* [Façade](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#façade)
* [Mediator](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#mediator)
* [Proxy](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#proxy)
* [Observer](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#observer)
* [Strategy](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md#strategy)
----

### Singleton

Creating only one object of a “class.” We looked at several approaches if you want
to substitute the idea of a class with a constructor function and preserve the Javalike syntax. Otherwise, technically all objects in JavaScript are singletons. And also
sometimes developers would say “singleton,” meaning objects created with the
module pattern.

Usage: 
* Database connections
* Config files

[__jsfiddle singleton playground__](https://jsfiddle.net/PurumVisum/evgr41qw/)
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

----

### Factory

A method that creates objects of type specified as a string at runtime.
We call the function Animal and both times it gives us a new animal instance.

*es6*

A factory function is any function which is not a class or constructor that returns a (presumably new) object. 
In JavaScript, any function can return an object.
 When it does so without the new keyword, it’s a factory function.

[__jsfiddle factory playground__](https://jsfiddle.net/PurumVisum/pz4jru9q/)

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

#### Mixins

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

----

### Iterator

[__jsfiddle iterator playground__](https://jsfiddle.net/PurumVisum/xf6r0qug/)
Providing an API to loop over and navigate around a complex custom data
structure.

As an example of a language feature in ES6, that uses the iterator standard in the language is that you can have a language construct such as:

```for (x of someObj) { ... }```
And the for/of logic only uses the iterator interface on someObj. It doesn't have to know anything specific about all the types of objects it can iterate. 
So, because of that, you can use for/of with ANY kind of object that supports a standard iterator. For example, you can use it with an array, a map, a set, or any custom object you create that supports the iterator interface.

Built-in iterables
```String```,``` Array ``` , ```TypedArray```, ```Map``` and ```Set``` are all built-in iterables, 
because their prototype objects all have a Symbol.iterator method.

__*Iterator*__
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
__*Simple Object*__
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

----

### Decorator

Tweaking objects at runtime by adding functionality from predefined decorator
objects.

----

### Strategy

Keeping the same interface while selecting the best strategy to handle the specific
task (context).

----

### Façade

Providing a more convenient API by wrapping common (or poorly designed)
methods into a new one.

----

### Proxy

Wrapping an object to control the access to it, with the goal of avoiding expensive
operations by either grouping them together or performing them only when really
necessary.

----

### Mediator

Promoting loose coupling by having your objects not “talk” to each other directly
but only though a mediator object.

----

### Observer

Loose coupling by creating “observable” objects that notify all their observers when
an interesting event occurs (also called subscriber/publisher or “custom events”).
