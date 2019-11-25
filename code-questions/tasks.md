
### Create a for loop that iterates up to 100 while outputting "fizz" at multiples of 3, "buzz" at multiples of 5 and "fizzbuzz" at multiples of 3 and 5.

``` 
const fizzBuzz = (num) => {
	for (let i = 0; i <= num; i++) {
		if ((i%3 === 0)&&(i%5 !== 0)) {
			console.log("fizz");
		} else if ((i%5 === 0) && (i%3 !== 0)) {
			console.log("buzz");
		} else if ((i%5 === 0) && (i%3 === 0)) {
			console.log("fizzbuzz");
		}
	}
}
``` 


### Given an array of integers, find the largest product yielded from three of the integers
`[1,2,3,4,5]`

const biggestSum = (arr) => {
	let sorted = arr.sort((a, b) => {
  		return b - a;
	})

	return sorted[0] + sorted[1] + sorted[2]

}

###  Find the intersection of two arrays. 

*An intersection would be the common elements that exists within both arrays.*

*In this case, these elements should be unique!*

```
let arr1 = [2,4,5,2];
let arr2 = [3,8,4,1,7]

const intersection = (arr1, arr2) => {
	let intersectionElement;
	arr1.forEach( (element, index) => {
		if (arr2.indexOf(element) > -1 ) {
			intersectionElement = element;
		}
	})
	return intersectionElement;
}
``` 


### Create a function that will evaluate if a given expression has balanced parentheses using stacks
`var expression = "{{}}{}{}"`

`var expressionFalse = "{}{{}";`    

`isBalanced(expression); // true`

`isBalanced(expressionFalse); // false`

`isBalanced(""); // true`

```
const isBalanced(expression) => {
	const one = (expression.match(/}/g)||[]).length
	const two = (expression.match(/{/g)||[]).length

		return one === two
 
}
``` 

### How would you add your own method to the Array object so the following code would work?
`var arr = [1, 2, 3, 4, 5];` 

`var avg = arr.average();`

`console.log(avg);`

``` 
Array.prototype.average = function() {
	let sum = this.reduce((accumulator, currentValue) => accumulator + currentValue);
	return sum / this.length;
}
``` 

### Create object 
```
{
  "animals": {
    "mammals": {
      "cats": {
        "persian": {},
        "siamese": {}
      },
      "dogs": {
        "chihuahua": {},
        "labrador": {}
      }
    }
  }
}
```

```
let categories = [
 { id: 'animals', parent: null },
 { id: 'mammals', parent: 'animals' },
 { id: 'cats', parent: 'mammals' },
 { id: 'dogs', parent: 'mammals' },
 { id: 'chihuahua', parent: 'dogs' },
 { id: 'labrador', parent: 'dogs' },
 { id: 'persian', parent: 'cats' },
 { id: 'siamese', parent: 'cats' }
];


let makeTree = (categories, parent) => {
  let node = {};
  categories
    .filter(c=> c.parent === parent)
    .forEach(c=>  node[c.id] = makeTree(categories, c.id))
    return node
}
```
