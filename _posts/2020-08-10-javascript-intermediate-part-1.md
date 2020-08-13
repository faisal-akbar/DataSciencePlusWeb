---
title: 'JavaScript Intermediate Part- 1'
comments: true
excerpt: 'Post displaying the modern JavaScript, ES6, let, const, function default parameter, template string, arrow function, spread operator, concatenate multiple arrays, class, constructor, object from class, inheritance, extended class, super,destructing object, truthy vs falsy, null vs undefined, double vs triple equal, map, filter, find, scope, block scope, closure, encapsulation, array slice, splice, join'
last_modified_at: 2020-08-10T10:27:01-05:00
categories:
  - JavaScript

tags:
  - JavaScript
  - JavaScript Fundamentals
---

{% include toc %}

# 1 MODERN JAVASCRIPT, ES6, ES2015, ECMA SCRIPT 2015

## 1.1 LET, CONST, ARRAY DECLARED WITH CONST, OBJECT DECLARED WITH CONST

```javascript
const name = 'Jane Smith'; // if value will not change;

const numbers = [12, 45];
numbers[1] = 88; // can change value
numbers.push(15); // can add new value
console.log(numbers); // [ 12, 88, 15 ]

//const numbers = [50, 60, 34]; // can't change the variable with new array

const person = {
  name: 'Will Smith',
  phone: 000 - 000 - 0000,
}; // can add, change property value but can't change the variable with new object

// if value may change use let, let is scope variable
let userName = 'Ed Sheeran';
userName = 'Adam Levine';

let sum = 0;
for (var i = 0; i < 10; i++) {
  // var will be accessible outside the loop
  sum = sum + i;
}
console.log(i); // 10

// use let instead
let sum = 0;
for (let i = 0; i < 10; i++) {
  sum = sum + i;
}
```

## 1.2 FUNCTION DEFAULT PARAMETER FOR NOT PROVIDED VALUES

```javascript
function add(num1, num2) {
  // if num2 is not provided
  // way 1:
  // if (num2 == undefined) {
  //     num2 = 0;
  // }
  // way 2:
  num2 = num2 || 20;
  return num1 + num2;
}

// way 3: ES6 convention
function add(num1, num2 = 0) {
  // = 0 is default parameter value
  return num1 + num2;
}

const total = add(15, 17);
console.log(total); //32
const total2 = add(15);
console.log(total2); // 15
const total3 = add(15, 1);
console.log(total3); // 16
```

## 1.3 TEMPLATE STRING, MULTIPLE LINE STRING

```javascript
const firstName = 'Justin';
const lastName = 'TimerLake';
const fullName = firstName + ' ' + lastName + ' is a good boy';
console.log(fullName);
// Justin TimerLake is a good boy

// Create ES6 template instead:
const fullName2 = `${firstName} ${lastName} is a nice person.`;
console.log(fullName2);
// Justin TimerLake is a nice person.

const fullName3 = `${firstName} ${20 + 50 + 30} is a nice person.`;
console.log(fullName3);

// Before
const multiLine = 'I love you\n' + 'I miss you\n' + 'I need you';
console.log(multiLine);

// ES6:
const multiLine2 = `I love you
I miss you
I need you`;
console.log(multiLine2);

/* I love you
I miss you
I need you */
```

## 1.4 ARROW FUNCTION, MULTIPLE PARAMETER, FUNCTION BODY

```javascript
function doubleIt(num) {
  return num * 2;
}
console.log(doubleIt(2)); // 4

const doubleIt2 = function myFun(num) {
  return num * 3;
};
console.log(doubleIt2(2)); // 4

// Arrow Function:
// if one parameter
const doubleIt3 = (num) => num * 2;
console.log(doubleIt3(5)); //25

// if more than one parameter
const add = (x, y) => x + y;
console.log(add(4, 3)); // 7

// if no parameter
const noParameter = () => 5;
console.log(noParameter()); // 5

const doMath = (x, y) => {
  const sum = x + y;
  const diff = x - y;
  const result = sum * diff;
  return result;
};

console.log(doMath(7, 5)); // 24
```

## 1.5 SPREAD OPERATOR, CONCATENATE MULTIPLE ARRAYS, ARRAY MAX

```javascript
const ages = [12, 14, 16, 13, 17];
const ages2 = [15, 16, 12];
const ages3 = [25, 36, 22, 29];

// const allAges = ages.concat(ages2).concat(ages3);
const allAges = ages.concat(ages2).concat([5]).concat(ages3);
console.log(allAges);
// [ 12, 14, 16, 13, 17, 15, 16, 12,  5, 25, 36, 22, 29 ]

const allAges2 = [ages, ages2, 5, ages3]; // array inside array
console.log(allAges2);
// [ [ 12, 14, 16, 13, 17 ], [ 15, 16, 12 ], 5, [ 25, 36, 22, 29 ] ]

// spread operator
const allAges3 = [...ages, ...ages2, 5, ...ages3]; // new array
console.log(allAges3);
// [ 12, 14, 16, 13, 17, 15, 16, 12,  5, 25, 36, 22, 29 ]

const business = 650;
const minister = 450;
const sochib = 250;

const maximum = Math.max(business, minister, sochib);
console.log(maximum); // 650

// if array
const amount = [650, 450, 250];
const maxAmount = Math.max(...amount);
console.log(maxAmount); // 650
```

## 1.6 CLASS, CONSTRUCTOR, CREATE OBJECT FROM CLASS

```javascript
class Student {
  constructor(sId, sName) {
    this.id = sId; //property that can change, pass as parameter
    this.name = sName; //property that can change, pass as parameter
    this.school = 'E-School'; //shared property
  }
}

const student1 = new Student(12, 'shuvo');
const student2 = new Student(22, 'Mahiya');
console.log(student1, student2);
// Student { id: 12, name: 'shuvo', school: 'E-School' } Student { id: 22, name: 'Mahiya', school: 'E-School' }

// access attribute:
console.log(student1.name, student2.name); // shuvo Mahiya

// new
const student3 = new Student(22, 'Bappi');
console.log(student3);
// Student { id: 22, name: 'Bappi', school: 'E-School' }
```

[Additional Resources - 1](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes){:target="\_blank"}  
[Additional Resources - 2](https://javascript.info/class){:target="\_blank"}  
[Additional Resources - 3](https://javascript.info/constructor-new){:target="\_blank"}

## 1.7 INHERITANCE, EXTENDS CLASS, SUPER, CLASS METHOD

```javascript
class Parent {
  constructor() {
    this.fatherName = 'Schwarzenegger';
  }
}

class Child extends Parent {
  constructor(name) {
    // call Parent class constructor
    super();
    this.name = name;
  }

  // create function, not required to specify function keyword
  getFullName() {
    return this.name + ' ' + this.fatherName;
  }
}

const baby = new Child('Arnold');
const baby2 = new Child('Tom');
console.log(baby); // Child { fatherName: 'Schwarzenegger', name: 'Arnold' }
console.log(baby2); // Child { fatherName: 'Schwarzenegger', name: 'Tom' }

console.log(baby.getFullName()); // Arnold Schwarzenegger
console.log(baby2.getFullName()); // Tom Schwarzenegger

// inheritance, encapsulation, polymorphism
```

[Additional Resources - 1](https://javascript.info/class-inheritance){:target="\_blank"}  
[Additional Resources - 2](https://medium.com/@viktor.kukurba/object-oriented-programming-in-javascript-4-encapsulation-4f9165cd26f9){:target="\_blank"}  
[Additional Resources - 3](https://www.javatpoint.com/javascript-oops-polymorphism#:~:text=The%20polymorphism%20is%20a%20core,data%20members%20with%20the%20methods.){:target="\_blank"}  
[Additional Resources - 4](https://medium.com/@viktor.kukurba/object-oriented-programming-in-javascript-3-polymorphism-fb564c9f1ce8){:target="\_blank"}

## 1.8 DESTRUCTURING, OBJECT, ARRAY, DESTRUCTURING COMPLEX OBJECT

```javascript
const person = {
  name: 'Jack William',
  age: 17,
  address: 'Brooklyn',
  sibling: 'Ema Watson',
  phone: '000 - 000 - 0000',
  job: 'Facebook Analyst',
  friends: ['Tom Hancks', 'Tom Cruise', 'Will Smith'],
};

// way 1:
console.log(person.sibling); // Ema Watson
console.log(person.sibling); // Ema Watson
console.log(person.sibling); // Ema Watson
console.log(person.sibling); // Ema Watson

// way 2:
const sibling1 = person.sibling;
const phoneNumber = person.phone;
console.log(sibling1, phoneNumber); // Ema Watson 000 - 000 - 0000
console.log(sibling1, phoneNumber); // Ema Watson 000 - 000 - 0000
console.log(sibling1, phoneNumber); // Ema Watson 000 - 000 - 0000
console.log(sibling1, phoneNumber); // Ema Watson 000 - 000 - 0000

// way 3: efficient and convenient
// one variable
const { phone } = person;

// same as above
// const {
//     phone
// } = {
//     name: 'Jack William',
//     age: 17,
//     address: 'Brooklyn',
//     sibling: "Ema Watson",
//     phone: "000 - 000 - 0000",
//     job: "Facebook Analyst",
//     friends: ['Tom Hancks', 'Tom Cruise', "Will Smith"]
// };

console.log(phone); // 000 - 000 - 0000

// more than one variable
const { name, sibling, job } = person;

console.log(name, sibling, job); // Jack William Ema Watson Facebook Analyst

// if any property is not in object
const {
  address,
  salary, // is not in person object, will give undefined
} = person;

console.log(address, salary); // Brooklyn undefined

// array destructuring
const friends2 = [
  'Sakib Khan',
  'Arman Khan',
  'Aamir Khan',
  'Salman Khan',
  'Sharukh Khan',
];
const [first, nextFriend, ...restFriends] = friends2;
console.log(first); // Sakib Kha
console.log(restFriends); // [ 'Aamir Khan', 'Salman Khan', 'Sharukh Khan' ]

// accessing another object property from an object using deconstructing
const complexObject = {
  name: 'abc',
  info: {
    city: 'New Rochelle',
    state: 'NY',
  },
};

const { state } = complexObject.info;
console.log(state); // NY
```

[Additional Resources - 1](https://www.javascripttutorial.net/es6/javascript-object-destructuring/){:target="\_blank"}  
[Additional Resources - 2](https://www.freecodecamp.org/news/array-destructuring-in-es6-30e398f21d10/){:target="\_blank"}

# 2 INTERMEDIATE JAVASCRIPT, INTERVIEW QUESTIONS

## 2.1 TRUTHY AND FALSY VALUES

```javascript
// Falsy: 0, "", undefined, null, NaN, let name=false
// Truthy: '0', " ", [], let name='false'

// 0 will return false, for other value true
const age = 0;
// const age = 4;
// const age = 6;

if (age) {
  console.log('condition is true');
} else {
  console.log('condition is false');
}

// empty string will return false, other string will be true
let name = '';
// const name = "Solaiman";

if (name) {
  console.log('condition is true');
} else {
  console.log('condition is false');
}

// if variable value is not defined, false will return
let name;
console.log(name); // undefined
if (name) {
  console.log('condition is true');
} else {
  console.log('condition is false');
}

// if variable value is null, false will return
let name = null;

if (name) {
  console.log('condition is true');
} else {
  console.log('condition is false');
}

// if variable value is NaN, false will return
let name = NaN;

if (name) {
  console.log('condition is true');
} else {
  console.log('condition is false');
}
```

## 2.2 NULL VS UNDEFINED, DIFFERENT WAYS YOU WILL GET UNDEFINED

```javascript
// Common cases that return undefined
// 1.
let name;
console.log(name); //undefined

// 2.
function add(num1, num2) {
  console.log(num1 + num2); // if you're not returning anything
}
console.log(add(13, 82)); // undefined

// 3.
function add(num1, num2) {
  console.log(num1 + num2);
  return; // if typed return, bot not specify what to return
}
console.log(add(13, 82)); // undefined

// 4.
function add(num1, num2) {
  console.log(num1, num2);
}
console.log(add(13)); // undefined - if less parameter value is passed than required
// set default value can resolve the issue

// 5.
const car = {
  make: 'Tesla',
  currentSpeed: '30 mph',
  color: 'blue',
  fuelType: 'Electric',
};
console.log(car.mpg); // undefined - if tried to access object property which is not exist

// 6.
let fun = undefined; // if assigned undefined as variable value
console.log(fun);

// 7.
let ageArray = [23, 25, 18];
console.log(ageArray[10]); // if tried to access the element which is not exist

// The value null represents the intentional absence of any object value.
// It is one of JavaScript's primitive values and is treated as falsy for boolean operations.

// Exercise
function doSomething(x, y) {
  console.log(y);
}
console.log(doSomething(32)); // undefined
```

## 2.3 DOUBLE EQUAL (==) VS TRIPLE EQUAL (===), IMPLICIT CONVERSION

```javascript
// == will check value only but not the type, so this will return true
let first = 2;
let second = '2';
// let first = 1;
// let second = true;
// let first = 0;
// let second = false;

if (first == second) {
  console.log('Condition is true');
} else {
  console.log('Condition is false');
}

// === will check the both value and type also, so this will return false
let first = 2;
let second = '2';
// let first = 1;
// let second = true;
// let first = 0;
// let second = false;

if (first === second) {
  console.log('Condition is true');
} else {
  console.log('Condition is false');
}
```

## 2.4 MAP, FILTER, FIND, SMART WAY TO RUN FOR LOOP

```javascript
const numbers = [3, 4, 5, 6, 7, 9];
const output = [];

for (let i = 0; i < numbers.length; i++) {
  const element = numbers[i];
  const result = element * element;
  output.push(result);
}
console.log(output); // [ 9, 16, 25, 36, 49, 81 ]

// using map
function square(element) {
  return element * element;
}

// arrow function, above function can be written as
const square2 = (element) => element * element;
const square3 = (x) => x * x;

//numbers.map(square);
numbers.map(function (element, index, array) {
  // map can take three parameter
  console.log(element, index, array);
  /*  3 0 [ 3, 4, 5, 6, 7, 9 ]
    4 1 [ 3, 4, 5, 6, 7, 9 ]
    5 2 [ 3, 4, 5, 6, 7, 9 ]
    6 3 [ 3, 4, 5, 6, 7, 9 ]
    7 4 [ 3, 4, 5, 6, 7, 9 ]
    9 5 [ 3, 4, 5, 6, 7, 9 ] */
});

const result = numbers.map(function (element) {
  return element * element;
});
console.log(result); // [ 9, 16, 25, 36, 49, 81 ]

// map and arrow function
const result2 = numbers.map((x) => x * x);
console.log(result2); // [ 9, 16, 25, 36, 49, 81 ]

// filter
const numbers2 = [3, 4, 5, 6, 7, 9];
const bigger = numbers2.filter((x) => x > 5); // will return matching element based on condition
console.log(bigger); // [ 6, 7, 9 ]

// find
const numbers3 = [3, 4, 5, 6, 7, 9];
const isThere = numbers3.find((x) => x > 5); // will return first matching element
console.log(isThere); // 6

// forEach, reduce
```

[Additional Resource - 1](https://javascript.info/array-methods){:target="\_blank"}  
[Additional Resource - 2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map){:target="\_blank"}  
[Additional Resource - 3](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce){:target="\_blank"}  
[Additional Resource - 4](https://www.freecodecamp.org/news/reduce-f47a7da511a9/){:target="\_blank"}  
[Additional Resource - 5](https://www.freecodecamp.org/news/javascript-foreach-how-to-loop-through-an-array-in-js/){:target="\_blank"}  
[Additional Resources - 6](https://youtu.be/rRgD1yVwIvE){:target="\_blank"}

## 2.5 APPLY MAP, FILTER, FIND ON AN ARRAY OF OBJECTS

```javascript
const students = [
  {
    id: 31,
    name: 'Jeff Bezos',
  },
  {
    id: 31,
    name: 'Elon Musk',
  },
  {
    id: 41,
    name: 'Bill Gates',
  },
  {
    id: 71,
    name: 'Tim Cook',
  },
];

const names = students.map((s) => s.name);
console.log(names); // [ 'Jeff Bezos', 'Elon Musk', 'Bill Gates', 'Tim Cook' ]

const ids = students.map((s) => s.id);
console.log(ids); // [ 31, 31, 41, 71 ]

const bigger = students.filter((s) => s.id > 40);
console.log(bigger); // [ { id: 41, name: 'Bill Gates' }, { id: 71, name: 'Tim Cook' } ]

const biggerOne = students.find((s) => s.id > 40);
console.log(biggerOne); // { id: 41, name: 'Bill Gates' }
```

## 2.6 SCOPE, BLOCK SCOPE, ACCESS OUTER SCOPE VARIABLE

```javascript
let bonus = 20; //global scope, accessible any where

function sum(first, second) {
  let result = first + second + bonus;
  return result; //local scope, not accessible outside function
}

const output = sum(3, 7);
console.log(output); // 30

//console.log(result); // return error
console.log(bonus); // 20

function sum2(first, second) {
  let result = first + second;
  if (result > 9) {
    // block scope and hoisting
    // if let and const is used in block scope then hoisting will not happen
    // but var will hoist, so accessible outside block scope
    let mood = 'Happy';
    // const mood ="Happy"
    mood = 'Fishy';
    mood = 'Funky';
    mood = 'Cranky';
    console.log(mood);
  }
  //console.log(mood); // throw error because it outside the block scope if let or const is used.
  return result;
}
const output2 = sum2(6, 7);
console.log(output2); // Cranky 13

// Difference when var and let used and try to access variable before variable declaration
//console.log(day); //Error: undefined
var day = 'Friday';
console.log(day);

//console.log(dayLet); // Error: Cannot access 'dayLet' before initialization
let dayLet = 'Saturday';
console.log(dayLet);
```

[Additional Resources - 1](https://www.thatjsdude.com/jsConcepts/concepts/scope.html){:target="\_blank"}  
[Additional Resources - 2](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting){:target="\_blank"}  
[Additional Resources - 3](https://javascript.info/var){:target="\_blank"}

## 2.7 CLOSURE, ENCAPSULATION, PRIVATE VARIABLE

```javascript
// Closure:
/* A closure is the combination of a function bundled together (enclosed) with references 
to its surrounding state (the lexical environment). In other words, a closure gives you 
access to an outer function’s scope from an inner function. In JavaScript, closures are 
created every time a function is created, at function creation time. */

function stopWatch() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}

const clock1 = stopWatch();
console.log(clock1()); // 1
console.log(clock1()); // 2
console.log(clock1()); // 3
console.log(clock1()); // 4

const clock2 = stopWatch();
console.log(clock2()); // 1
console.log(clock2()); // 2
console.log(clock1()); // 5
console.log(clock2()); // 3
```

[Additional Resources - 1](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures){:target="\_blank"}  
[Additional Resources - 2](https://javascript.info/closure){:target="\_blank"}

## 2.8 ARRAY SLICE, SPLICE, ARRAY JOIN ELEMENTS

```javascript
const nums = [1, 2, 3, 4, 5, 6, 7, 8];

// slice
const part = nums.slice(2, 5); // start index, excluding end index, select based on index
console.log('slice: ', part); // [3, 4, 5]
console.log('array after slice: ', nums); // original array will remain same

// splice
const removed = nums.splice(2, 3); // here 2 is index start, and 3 is count of element remove
console.log('splice: ', removed); // [3, 4, 5]
console.log(' array after splice: ', nums); // [ 1, 2, 6, 7, 8 ]

const nums2 = [1, 2, 3, 4, 5, 6, 7, 8];
const removedPPlusInject = nums2.splice(2, 3, 77, 88); // here 2 is index start, and 3 is count of element remove, 77, 88 item that want to inject
console.log('splice: ', removedPPlusInject); // [3, 4, 5]
console.log(' array after splice: ', nums2); // [ 1, 2, 77, 88, 6, 7,  8 ]

// join
const nums3 = [1, 2, 3, 4, 5, 6, 7, 8];
// const together = nums3.join(""); // when join array element together
// const together = nums3.join(" ");
// const together = nums3.join("ami");
const together = nums3.join(',');
console.log(together); // 1,2,3,4,5,6,7,8
```

[Additional Resources - 1](https://www.freecodecamp.org/news/lets-clear-up-the-confusion-around-the-slice-splice-split-methods-in-javascript-8ba3266c29ae/){:target="\_blank"}  
[Additional Resources - 2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice){:target="\_blank"}  
[Additional Resources - 3](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice){:target="\_blank"}  
[Additional Resources - 4](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join){:target="\_blank"}  
[Additional Resources - 5](https://javascript.info/array-methods){:target="\_blank"}

## 2.9 SUMMARY AND OVERVIEW

```javascript
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9];

for (let i = 0; i < nums.length; i++) {
  if (nums[i] > 3) {
    // debugger
    break;
  }
  console.log(nums[i]); // 1 2 3
}

const nums2 = [1, -2, 3, 4, -5, 6, 7, -8, 9];

for (let i = 0; i < nums2.length; i++) {
  if (nums2[i] < 0) {
    // debugger
    continue;
  }
  console.log(nums2[i]); // 1 3 4 6 7 9
}
```

[Additional Resources](https://medium.com/javascript-in-plain-english/hot-to-use-break-continue-statements-in-javascript-9b6d30e56deb){:target="\_blank"}

<!-- ```javascript
``` -->
<!-- ```javascript
``` -->

<!-- ```html
<body>
  <script src="script.js"></script>
</body>
``` -->
