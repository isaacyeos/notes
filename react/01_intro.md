# Setup
## Installation 
- VS Code
- Prettier - Code Formatter VS Code Extension (Go to Settings and set Default Formatter to Prettier)

## JavaScript Refresher
You may try all the code examples on https://jsbin.com

Use let and const instead of var:
- let for variable values
- const for constant values (if you plan on never reassigning the variable)
- Read more about let : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let
- Read more about const : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const

Normal function:
```js
function printMyName(name) {
    console.log(name);
}
```
Arrow function (0 and >=2 arguments need parentheses, 1 argument no need):
- Arrow functions are a different way of creating functions in JavaScript. Besides a shorter syntax, they offer advantages when it comes to keeping the scope of the this  keyword
- Read more: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions
```js
const printMyName = (name) => {
    console.log(name);
}

const printMyName = () => {
    console.log("Max");
}

const printMyName = name => {
    console.log(name);
}

```
Arrow function (1 argument, 1 return statement in body)
```js
const multiply = number => number * 2;

// same as the above
const multiply = number => {
    return number * 2;
}
```

Imports and exports:
- A file can only contain one default and an unlimited amount of named exports. You can also mix the one default with any amount of named exports in one and the same file.
- person.js
```js
const person = {
    name: 'Max'
}
export default person
```
- utility.js
```js
export const clean = () => {}
export const baseData = 10;
```
- app.js
```js
// default export (unnamed) - you can choose any name
import person from './person.js'
import prs from './person.js'

// named export - Named exports have to be imported by their name
import {baseData} from './utility.js'
import {clean} from './utility.js'
import {baseData as bD} from './utility.js'
import * as bundled from './utility.js'
```

Classes:
```js
// "old" syntax
class Human
{
    constructor()
    {
        this.gender = 'Male';
    }
    printGender()
    {
        console.log(this.gender);
    }
}

class Person extends Human
{
    constructor()
    {
        super();
        this.name = 'Max';
    }
    printMyName()
    {
        console.log(this.name);
    }
}

// ES6 - modern JavaScript
class Human
{
    gender = 'Male';

    printGender = () =>
    {
        console.log(this.gender);
    }
}

class Person extends Human
{
    name = 'Max';

    printMyName = () =>
    {
        console.log(this.name);
    }
}

const person = new Person();
person.printMyName();
person.printGender();
```

Spread operator (used to split up array elements OR object properties):
```js
// Arrays
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4]; // with spread operator
const newNumbers2 = [numbers, 4]; // without spread operator will just add the array object
console.log(newNumbers);

// Objects
const person = {
    name: 'Max'
};

const newPerson = {
    ...person,
    age: 28
}
console.log(newPerson);
``` 

Rest operator (used to merge a list of function arguments into an array):
```js
// rest operator merges the arguments into an array
const filter = (...args) => {
    return args.filter(el => el === 1); // checks for type and value equality
}
console.log(filter(1,2,3));
```

Destructuring
```js
// array destructuring
const numbers = [1,2,3];
[num1, num2] = numbers; // extracts 1 and 2 (extracts in sequential order for arrays)
console.log(num1, num2);
[num1, , num3] = numbers; // extracts 1 and 3
console.log(num1, num3);

// object destructuring - does not work on jsbin
{name} = {name: 'Max', age: 28}; // extract based on property name for objects
console.log(name); // Max
console.log(age); // undefined

// destructuring in function arguments
// original
const printName = (personObj) => {
    console.log(personObj.name);
}
printName({name: 'Max', age: 28}); // prints 'Max'

//condensed - using destructuring
const printName = ({name}) => {
    console.log(name);
}
printName({name: 'Max', age: 28}); // prints 'Max'
```

Reference vs Primitives (objects and arrays are reference types, while numbesr, strings, booleans are primitive types)
```js
// copying the pointer which points to the same object in memory
const person = {
    name: 'Max'
};
const secondPerson = person;
person.name = 'Manu';
console.log(secondPerson);

// coyping the values and properties of the object to a new object, using the spread operator
const person = {
    name: 'Max'
};
const secondPerson = {
    ...person
};
person.name = 'Manu';
console.log(secondPerson);
```

Map function
```js
const numbers = [1,2,3];
const doubleArray = numbes.map((num) => {
    return num * 2;
});
console.log(numbers);
console.log(doubleNumArray);
```

Important JS Array Functions:
- map()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map
- find()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find
- findIndex()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex
- filter()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
- reduce()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce?v=b
- concat()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat?v=b
- slice()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
- splice()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice