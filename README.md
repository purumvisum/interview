# Interview
Interview questions and solutions

----

## Titles
* [Theoretical Basis](https://github.com/purumvisum/interview/blob/master/theoretical-basis/README.md)


----

### Other Sources
https://github.com/MaximAbramchuck/awesome-interview-questions

## Most common questions (*for me*)

### Remove duplicates of an array and return an array of only unique elements  

```
const noDupsInArray = (arrayWithDup) => {
  return Array.from(new Set(arrayWithDup))
}
noDupsInArray([1,1,2,2,3,4,1])
```

### Given a string, reverse each word in the sentence  

```
const reverseAllWords = (stringWithWords) => {
	return stringWithWords.split("").reverse().join("");
}
reverseAllWords('this string with words');
```

### mul(2)(3)

```
const mul = (a) => {
	return (b) => {
		return a*b;
	}
}
```

### sum(1)(2)(3)(4)(5)

```
const sum = (a) => {

  let currentSum = a;

  const f = (b) => {
    currentSum += b;
    return f;
  }

  f.toString = function() {
    return currentSum;
  };

  return f;
}
```

### How to check if an object is an array or not? Provide some code.\

```
Object.prototype.toString.call({}) //"[object Object]"
Object.prototype.toString.call('asdas') //"[object String]"
Object.prototype.toString.call([1,2,3]) // "[object Array]"

Array.isArray([1,2,3]); // true

```

### How would you check if a number is an integer

```
const isInt = (num) => {
	if (num%1 === 0) return true;
	return false

}
```


### How would you use a closure to create a private counter?

```
const makeCounter = () => {
  let count = 0;

  return function() {
    return count++;
  };
}

```

```
let counter = makeCounter();
counter(); //1
counter(); //2
``` 

### var addSix = createBase(6); addSix(10); // returns 16 addSix(21); // returns 27
```
const createBase = (base) => {
	return (add) => {
		return add + base
	}
}
```

### duplicate([1, 2, 3, 4, 5]); // [1,2,3,4,5,1,2,3,4,5]

```
arr.concat(arr);
```
```
const duplicate = (arr) => {
	return [...arr, ...arr]
} 
```

### Given two strings, return true if they are anagrams of one another 
*Mary is an anagram of Army*

```
const anagram = (str1, str2) => {
	let str1sorted = str1.toLowerCase().split("").sort()
	let str2sorted = str2.toLowerCase().split("").sort()

	return str1sorted.join("") === str2sorted.join("")

}
```

### Check if a given string is a palindrome. 
##### Case sensitivity should be taken into account.
*A palindrome is a word, phrase, number, or other sequence of characters which reads the same backward or forward.*

``` isPalindrome("racecar"); // true ```

``` isPalindrome("race Car"); // true ```
```
const isPalindrome = (str1) => {
	//word.toLowerCase().replace(/\s/g, "");
	
	let withoutSpaces = str1.toLowerCase().split(" ").join('').split("");
	let reverseStr1 = withoutSpaces.reverse().join("");
	if (withoutSpaces.join("") === reverseStr1) {
		return true
	} else {
		return false
	}
}
```
