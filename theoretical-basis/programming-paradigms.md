# Programming paradigms
is a style, or “way,” of programming

JavaScript is a multi-paradigm language, supporting imperative/procedural programming along with OOP 
(Object-Oriented Programming) and functional programming. 

JavaScript supports 
* OOP with __*prototypal inheritance*__.
* functional with __*higher order functions*__, __*functions as arguments/values.*__

### Content 
1. [Programming paradigms](https://github.com/purumvisum/interview/blob/master/theoretical-basis/programming-paradigms.md#programming-paradigms-1)
2. [Object Oriented programming concept](https://github.com/purumvisum/interview/blob/master/theoretical-basis/programming-paradigms.md#Object-Oriented-programming-concept)     
    * [Inheritance](https://github.com/purumvisum/interview/blob/master/theoretical-basis/programming-paradigms.md#Inheritance) (Class Inheritance, Prototypal Inheritance)
    * [Encapsulation](https://github.com/purumvisum/interview/blob/master/theoretical-basis/programming-paradigms.md#Encapsulation) 
    * [Polymorphism](https://github.com/purumvisum/interview/blob/master/theoretical-basis/programming-paradigms.md#Polymorphism)

### Programming paradigms

* __*Imperative*__ in which the programmer instructs the machine how to change its state,
    ```
   const doubleMap = numbers => {
      const doubled = [];
      for (let i = 0; i < numbers.length; i++) {
        doubled.push(numbers[i] * 2);
      }
      return doubled;
    };
    console.log(doubleMap([2, 3, 4])); // [4, 6, 8]
    ```
    * *object-oriented* which groups instructions together with the part of the state they operate on. 
    
* __*Declarative*__ in which the programmer merely declares properties of the desired result, but not how to compute it
    ```
    const doubleMap = numbers => numbers.map(n => n * 2);

    console.log(doubleMap([2, 3, 4])); // [4, 6, 8]
    ```
    * *functional* in which the desired result is declared as the value of a series of function applications
        * Pure functions (Given the same inputs, always returns the same output, and)
        * Function composition (is the process of combining two or more functions in order to produce a new function or perform some computation ```f(g(x))```) 
        * Avoid shared state (An immutable object is an object that can’t be modified after it’s created)
        * Avoid mutating state
        * Avoid side effects
        
        
         ##### Higher order function 
         A higher order function is a function that takes a function as an argument, or returns a function. 

         `.map()` and `.filter()` - take a function as an argument. They're both higher order functions.

         [HOC (React)](https://reactjs.org/docs/higher-order-components.html)
         A higher-order component is a function that takes a component and returns a new component.
         Whereas a component transforms props into UI, a higher-order component transforms a component into another component.

    * *Reactive* 
    
        `a:=b+c` - example
        
         in reactive programming, the value of `a 
         is automatically updated whenever the values of `b or c` change (ex "EXEL")
        
         VS *Imperative*
         
         `a` is being assigned the result of `b+c in the instant the expression is evaluated, 
         and later, the values of `b` and `c` can be changed with no effect on the value of `a`. 


## Object Oriented programming concept 

### Encapsulation 
is an object-oriented programming concept that binds together the data and functions 
that manipulate the data, and that keeps both safe from outside interference and misuse.
Data encapsulation led to the important OOP concept of data hiding.

*In js* 
* Using Closures
    ```
    const createCounter = () => {
        // A variable defined in a factory or constructor function scope
        // is private to that function.
        let count = 0;
        return ({
            // Any other functions defined in the same scope are privileged:
            // These both have access to the private `count` variable
            // defined anywhere in their scope chain (containing function
            // scopes).
            click: () => count += 1,
            getCount: () => count.toLocaleString()
        });
    };
    const counter = createCounter();
    counter.click();
    counter.click();
    counter.click();
    console.log(
      counter.getCount()
    );
    ```
* Using Private Fields
    ```
    class Counter {
        #count = 0
  
        click () {
            this.#count += 1;
        }
        getCount () {
            return this.#count.toLocaleString()
        }
    }
    const myCounter = new Counter();
    myCounter.click();
    myCounter.click();
    myCounter.click();
    console.log(
      myCounter.getCount()
    );
    ```

### Inheritance 
* __*Class Inheritance*__: 
    ```
    class Person {
       fn() {...}
   } // or constructor function say, function Person() {}
    
    // create instance
    let person = new Person();
    ```
    instances inherit from classes (like a blueprint — a description of the class),
    and create sub-class relationships: hierarchical class taxonomies. 
    Instances are typically instantiated via constructor functions with the `new` keyword. 
    Class inheritance may or may not use the `class` keyword from ES6.
* __*Prototypal Inheritance*__: 
    ```
    // base object
    let Person = { fn(){...} }
    
    // instance
    let person = Object.create(Person);
    ```
    instances inherit directly from other objects.
    Instances are typically instantiated via factory functions or `Object.create()`.
    Instances may be composed from many different objects, allowing for easy selective inheritance.
    
    
Classes are something like another syntactic sugar over the prototype-based OO pattern.

**ES6**

```
class Vehicle {
 
  constructor (name, type) {
    this.name = name;
    this.type = type;
  }
 
  getName () {
    return this.name;
  }
 
  getType () {
    return this.type;
  }
 
}
let car = new Vehicle('Tesla', 'car');
console.log(car.getName()); // Tesla
console.log(car.getType()); // car
```


**ES5**

```
function Vehicle (name, type) {
  this.name = name;
  this.type = type;
};
 
Vehicle.prototype.getName = function getName () {
  return this.name;
};
 
Vehicle.prototype.getType = function getType () {
  return this.type;
};
var car = new Vehicle('Tesla', 'car');
console.log(car.getName()); // Tesla
console.log(car.getType()); // car
```

### Polymorphism
In an OOP context, “polymorphism” almost always means just one thing: the overriding of inherited methods to
 facilitate calling the same method on
 different objects
 
 It is the practice of designing objects to share behaviors and to be able to override shared behaviors with specific ones.
 
 ```
function Person(age,weight){
 this.age = age;
 this.weight = weight;
}

Person.prototype.getInfo = function(){
 return "I am " + this.age + " years old " +
    "and weighs " + this.weight +" kilo.";
};
```
Next we wish to have a subclass of Person, Employee
``` 
function Employee(age,weight,salary){
 this.age = age;
 this.weight = weight;
 this.salary = salary;
}
Employee.prototype = new Person();
```

And we will override the behavior of getInfo by defining one which is more fitting to an Employee
(Here we overrided shared behaviors with specific ones - Polymorphism)
``` 
Employee.prototype.getInfo = function(){
 return "I am " + this.age + " years old " +
    "and weighs " + this.weight +" kilo " +
    "and earns " + this.salary + " dollar.";  
};
``` 



