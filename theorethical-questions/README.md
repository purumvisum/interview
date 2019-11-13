# What is the drawback of creating true private methods in JavaScript?
One of the drawbacks of creating true private methods in JavaScript is that they are very memory-inefficient, 
as a new copy of the method would be created for each instance.
``` 
const Man = function (name, title) {
    this.name = name || "";       //Public attribute default value is null
    this.title = title || "";  
    
    // Private method
    var hasTitle = (title) => {
        this.name = `${title} ${this.name}`;
    };

    // Public method
    this.showNameAndTitle = () => {
        hasTitle(this.title);
        console.log(this.name);
    };
};

// Create Employee class object
var emp1 = new Man("John");
// Create Employee class object
var emp2 = new Man("Merry","Ms.");
```

Here each instance variable emp1, emp2 has its own copy of the increaseSalary private method.


# What will be the output of the code below?

```
var trees = ["xyz","xxxx","test","ryan","apple"];
delete trees[3];
  
console.log(trees.length);
```

Result: `["xyz", "xxxx", "test", undefined, "apple"]` , so `length = 5`

# What will be the output of the code below?
``` 
var bar = true;
console.log(bar + 0);   
console.log(bar + "xyz");  
console.log(bar + true);  
console.log(bar + false); 
```

Answer: `1, "truexyz", 2, 1`

Rules: 
* Number + Number -> **Addition**
* Number + Boolean -> **Addition**
* Number + String -> **Concatenation**
* String + Boolean -> **Concatenation**
* String + String -> **Concatenation**


# What will be the output of the code below?
```
var z = 1, y = z = typeof y;
console.log(y);  
console.log(z);  
```

In other words: 

```
z = 1; 
var z; 
typeof y; // undefined
z = typeof y // z = undefined
y = z // y = undefined
```

This executes in the following order:

* Assign 1 to z. The value of z is 1.
* Evaluate typeof y. This evaluates to "undefined" because the value of y is undefined.
* Evaluate z = "undefined". The value of z is "undefined".
* Evaluate y = "undefined". The value of y is "undefined".
* Log the value of y. This logs undefined.
* Log the value of z. This logs undefined.

Running it a second time, you get:

* Assign 1 to z. The value of z is 1.
* Evaluate typeof y. This evaluates to "string" because the value of y is "undefined".
* Evaluate z = "string". The value of z is "string".
* Evaluate y = "string". The value of y is "string".
* Log the value of y. This logs string.
* Log the value of z. This logs string.


# How does Array() differ from [] while creating a JavaScript array?

Almost the same:

`Array()` the same as `[]`

`Array('9')` the same as `['9']`

**But:**

`Array(9)` the same as `[9]` // The first will create an uninitialized array of size n `[empty × 9]`  and the second `[9]`


# call(), apply() and bind() Methods in JavaScript.

```
var car = { 
    registrationNumber: "GA12345",
    brand: "Toyota",

    displayDetails: function(ownerName){
        console.log(ownerName + ", this is your car: " + this.registrationNumber + " " + this.brand);
    }
}
```
**IS WORKING**

`car.displayDetails(); // GA12345 Toyota`

**WON'T WORK**
```
var myCarDetails =  car.displayDetails; 
myCarDetails();
```


#### Bind()
```
var myCarDetails = car.displayDetails.bind(car, "Daria");
myCarDetails(); // Daria, this is your car: GA12345 Toyota
``` 

#### call() and apply() 

```
var car = { 
    registrationNumber: "GA12345",
    brand: "Toyota"
}

function displayDetails(ownerName) {
    console.log(ownerName + ", this is your car: " + this.registrationNumber + " " + this.brand);
}
```

```
displayDetails.apply(car, ["Daria"]); // Daria, this is your car: GA12345 Toyota

displayDetails.call(car, "Daria"); // Daria, this is your car: GA12345 Toyota
```

# JS Primitives
* string
* number 
* boolean 
* null 
* undefined
* symbol (ECMAScript 2015).
