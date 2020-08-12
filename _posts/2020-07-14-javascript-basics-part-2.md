---
title: 'JavaScript Basics Part- 2'
comments: true
excerpt: 'Post displaying the use of JavaScript fundamental concepts'
last_modified_at: 2020-07-14T10:27:01-05:00
categories:
  - JavaScript

tags:
  - JavaScript
  - JavaScript Fundamentals
---

{% include toc %}

# 1 APPLY JAVASCRIPT CONCEPTS

## 1.1 UNIT CONVERT INCH TO FEET USE VARIABLE AND FUNCTION

```javascript
// without function, not reusable:
var inch = 156;
var feet = inch / 12;
console.log(inch);
console.log(feet);

// with function:
function inchToFeet(inch) {
  var feet = inch / 12;
  return feet;
}

var newFeet = inchToFeet(300);
console.log(newFeet);

// using index of an array:
var inchArr = [156, 288, 300];

var newFeet = inchToFeet(inchArr[1]);
console.log(newFeet);

// using for loop:
var inchArr = [198, 208, 310];

for (i = 0; i < inchArr.length; i++) {
  var feet = inchArr[i] / 12;
  console.log(feet);
}
```

## 1.2 VARIABLE LET AND CONST AND HOW TO USE THEM

```javascript
// use var or let (mostly) if you want to reassign
let name = 'Javed Akhter';
console.log(name.length); /* including space */

if (name.length > 4) {
  name = 'Juvu';
}
console.log(name);

// if variable will be fixed or no need to change use const
const country = 'Bangladesh';
console.log(country);

const age = 15;
console.log(age);

/* apply const wherever possible */
function inchToFeet(inch) {
  const feet = inch / 12;
  return feet;
}

const newFeet = inchToFeet(300);
console.log(newFeet);

// using index of an array:
const inchArr = [156, 288, 300];

const newFeetArry = inchToFeet(inchArr[1]);
console.log(newFeetArry);
```

## 1.3 CHECK WHETHER A YEAR IS A LEAP YEAR OR NOT

```javascript
/* divisible by 4 for leap is not always true */
console.log(2030 / 4);
console.log(2032 / 4);

const year = 3996;
const remainder = year % 4;
console.log(remainder);
console.log(remainder == 0);

if (remainder == 0) {
  console.log('The year is a Leap Year');
} else {
  console.log('The year is not a Leap Year');
}

// using function:
function isLeapYear(year) {
  const remainder = year % 4;

  if (remainder == 0) {
    return true;
  } else {
    return false;
  }
}

const checkYear1 = isLeapYear(2016);
console.log(checkYear1);

const checkYear2 = isLeapYear(1700);
console.log(checkYear2); /* not true */
```

**Correct way of finding leap year:**  
To determine whether a year is a leap year, follow these steps:

1. If the year is evenly divisible by 4, go to step 2. Otherwise, go to step 5.
2. If the year is evenly divisible by 100, go to step 3. Otherwise, go to step 4.
3. If the year is evenly divisible by 400, go to step 4. Otherwise, go to step 5.
4. The year is a leap year (it has 366 days).
5. The year is not a leap year (it has 365 days).

or

1. If a year is divisible by 400, it's a leap year
2. Otherwise, if a year is divisible by 100, it's not a leap year
3. Otherwise, if a year is divisible by 4, it's a leap year

```javascript
// Method: 1
function isLeapYear(year) {
  if (year % 400 === 0) return true;
  if (year % 100 === 0) return false;
  return year % 4 === 0;
}

console.log(isLeapYear(1700));
console.log(isLeapYear(2016));
console.log(isLeapYear(2000));
console.log(isLeapYear(100));

// Method: 2
// function isLeapYear2(year) {
// return (year % 4 == 0 && year % 100 != 0) || year % 400 == 0;
// }

function isLeapYear2(year) {
  if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0) {
    return 'The year is a leap Year';
  } else {
    return 'The Year is not a leap year';
  }
}

console.log(isLeapYear2(1700));
console.log(isLeapYear2(2016));
console.log(isLeapYear2(2000));
console.log(isLeapYear2(100));

// Method 3:
function isLeapYear3(year) {
  return year % 100 === 0 ? year % 400 === 0 : year % 4 === 0;
}

console.log(isLeapYear3(1700));
console.log(isLeapYear3(2016));
console.log(isLeapYear3(2000));
console.log(isLeapYear3(100));
```

[Additional Resources- 1](https://www.w3resource.com/javascript-exercises/javascript-basic-exercise-6.php){:target="\_blank"}  
[Additional Resources- 2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator){:target="\_blank"}  
[Additional Resources- 3](https://dev.to/nas5w/creating-a-javascript-function-to-calculate-whether-it-s-a-leap-year-2cip) {:target="\_blank"}

## 1.4 CALCULATE FACTORIAL OF A NUMBER USING FOR LOOP

```javascript
/* Factorial e.g. 
4! = 4*3*2*1
10!=1*2*3*4*5*6*7*8*9*10 */

/* assume initial value such that it will not affect the result,
 e.g. for multiply assume initial value 1, for addition 0 */

// iterative method, for loop:
let factorial = 1;
for (let i = 1; i <= 10; i++) {
  factorial = factorial * i;
  console.log(i, factorial);
}

// using function:
function newFactorial(n) {
  let factorial = 1;
  for (let i = 1; i <= n; i++) {
    factorial = factorial * i;
  }
  return factorial;
}

let result = newFactorial(5);
console.log(result);
```

## 1.5 CALCULATE FACTORIAL OF A NUMBER USING A WHILE LOOP

```javascript
// 10!=1*2*3*4*5*6*7*8*9*10
// using while loop:
let i = 1;
let factorial = 1;
while (i <= 10) {
  factorial = factorial * i;
  // console.log(i, factorial);
  i++;
}

console.log(factorial);

// using function and while:
function newFactorial(n) {
  let i = 1;
  let newFactorial = 1;
  while (i <= n) {
    newFactorial = newFactorial * i;
    i++;
  }
  return newFactorial;
}

let result = newFactorial(6);
console.log(result);

// reverse way:
// 10!=1*2*3*4*5*6*7*8*9*10

// Using For loop:
let factorial1 = 1;
for (let i = 5; i > 1; i--) {
  factorial1 = factorial1 * i;
  console.log(i, factorial1);
}

function factorialize(n) {
  let i = n;
  let newNum = 1;
  for (i; i > 1; i--) {
    newNum *= i; /* newNum = newNum * i */
  }
  return newNum;
}

console.log(factorialize(6));

// using while:
let i = 5;
let factorial2 = 1;
while (i >= 1) {
  factorial2 = factorial2 * i;
  i--;
}
console.log(factorial2);

function factorialize2(n) {
  let i = n;
  let factorial2 = 1;
  while (i >= 1) {
    factorial2 = factorial2 * i;
    i--;
  }
  return factorial2;
}

console.log(factorialize2(6));
```

## 1.6 CALCULATE FACTORIAL IN A RECURSIVE FUNCTION

```javascript
// Recursive function:

// 10!=1*2*3*4*5*6*7*8*9*10
// 0! = 1
// 2! = 1*2
// 3! = 1*2*3
// 4! = 1*2*3*4
// 5! = 1*2*3*4*5 = 4!*5 = (5-1)! * 5
// n! = (n-1)! * n

function rFactorial(n) {
  if (n == 0) {
    return 1;
  } else {
    return rFactorial(n - 1) * n;
  }
}

let nResult = rFactorial(10);
console.log(nResult);
```

[Additional Resource](<https:// www.freecodecamp.org/news/how-to-factorialize-a-number-in-javascript-9263c89a4b38/#:~:text=function%20factorialize(num)%20%7B%20%2F%2F%20If%20num%20%3D%200%20OR,num%20*%3D%20i%3B%20%2F*%20num>){:target="\_blank"}

## 1.7 CREATE A FIBONACCI SERIES USING A FOR LOOP

[About Fibonacci Series](https:// www.mathsisfun.com/numbers/fibonacci-sequence.html)

```javascript
/* 
position 2, 3, 4, 5, n ,i respectively: 
fibo[2] = fibo[2 - 1] + fibo[2 - 2];
fibo[3] = fibo[3 - 1] + fibo[3 - 2];
fibo[4] = fibo[4 - 1] + fibo[4 - 2];
fibo[5] = fibo[5 - 1] + fibo[5 - 2];
fibo[n] = fibo[n - 1] + fibo[n - 2];
fibo[i] = fibo[i - 1] + fibo[i - 2]; */

// using For loop:
let fibo = [0, 1];

for (let i = 2; i <= 12; i++) {
  fibo[i] = fibo[i - 1] + fibo[i - 2];
  // console.log(fibo[i], fibo[i - 1], fibo[i - 2])
}

console.log(fibo);

// using function:
function fibonacci(n) {
  let fibo = [0, 1];

  for (let i = 2; i <= n; i++) {
    fibo[i] = fibo[i - 1] + fibo[i - 2];
  }
  return fibo;
}

let fiboResult = fibonacci(12);
console.log(fiboResult);
```

## 1.8 FIBONACCI ELEMENT IN A RECURSIVE WAY

```javascript
function rFibonacci(n) {
  if (n == 0) {
    return 0;
  }
  if (n == 1) {
    return 1;
  } else {
    return rFibonacci(n - 1) + rFibonacci(n - 2);
  }
}

let rResult = rFibonacci(10);
console.log(rResult);
```

[Additional Resources](https://medium.com/developers-writing/fibonacci-sequence-algorithm-in-javascript-b253dc7e320e){:target="\_blank"}

## 1.9 CREATE FIBONACCI SERIES IN A RECURSIVE WAY

```javascript
// [0 , 1, 1, 2, 3, 5, 8,, 13, 21,]

function sFibonacci(n) {
  if (n == 0) {
    return [0];
  } else if (n == 1) {
    return [0, 1];
  } else {
    // find array with nth item
    let fibo = sFibonacci(n - 1);
    let nextItem = fibo[n - 1] + fibo[n - 2];
    fibo.push(nextItem);
    return fibo;
  }
}

let sResult1 = sFibonacci(1);
let sResult2 = sFibonacci(2);
let sResult3 = sFibonacci(3);
let sResult4 = sFibonacci(4);
let sResult8 = sFibonacci(10);
console.log(sResult1);
console.log(sResult2);
console.log(sResult3);
console.log(sResult4);
console.log(sResult8);
```

## 1.10 CHECK WHETHER A NUMBER IS A PRIME NUMBER OR NOT

```javascript
function isPrime(n) {
  for (i = 2; i < n; i++) {
    // console.log(i, n % i);
    if (n % i == 0) {
      return 'Not a Prime Number';
    }
  }
  return 'The number is a Prime number';
}

let pResult1 = isPrime(128);
let pResult2 = isPrime(79);

console.log(pResult1);
console.log(pResult2);
```

# 2 JAVASCRIPT CODING PROBLEMS, SIMPLE INTERVIEW QUESTIONS

## 2.1 SWAP VARIABLE, SWAP WITHOUT TEMP, DESTRUCTING

```javascript
let a = 5;
let b = 7;
console.log('Before swap: a=', a, ', b=', b);

// Swap using a temporary variable:
let temp = a; /* store a value in temp variable */
a = b; /* overwrite a value with a value */
b = temp; /* overwrite b value with temp value */

console.log('After swap: a=', a, ', b=', b);

// Swap using addition and difference:
let x = 5;
let y = 7;
console.log('Before swap: x=', x, ', y=', y);

x = x + y;
/* add current x and current y so that we can get combined 
value of x and y (in this case 12) and store it in new x */
y = x - y; /* now new y equal the new x minus y, which is 12-7= 5 */
x = x - y; /* now to transfer y value, overwrite new x, 12-5= 7  */

console.log('After swap: x=', x, ', y=', y);

// Swap using destructing assignment:
let p = 5;
let q = 7;
console.log('Before swap: p=', p, ', q=', q);

[p, q] = [q, p];
/* a temporary array [q, p] is created, which evaluates to [7,5] */
console.log('After swap: p=', p, ', q=', q);
```

[Additional Resources](https://dmitripavlutin.com/swap-variables-javascript/){:target="\_blank"}

## 2.2 RANDOM NUMBER, RANDOM NUMBER BETWEEN 1 TO 6

```javascript
let num = 2.12458;

// the Math.floor() function returns the largest integer less than or equal to a given number.
let result1 = Math.floor(num);
console.log(result1);

// the Math.ceil() function always rounds a number up to the next largest integer.
let result2 = Math.ceil(num);
console.log(result2);

// the Math.round() function returns the value of a number rounded to the nearest integer.
let result3 = Math.round(num);
console.log(result3);

// random number 0 t0 10:
let dice = Math.random() * 6; /* with decimal */
console.log(dice);

let output = Math.round(dice); /* without decimal */
console.log(output);

for (i = 0; i < 10; i++) {
  let dice = Math.random() * 6;
  let output = Math.round(dice);
  console.log('For Loop: ', output);
}
```

## 2.3 FIND MAX OF TWO VALUES, FIND MAX OF THREE VALUES

```javascript
let business = 450;
let minister = 350;
let sochib = 750;

// if compare business and minister only:
if (business > minister) {
  console.log('Business is bigger');
} else {
  console.log('Minister is bigger');
}

// if compare business, minister sochib:
if (business > minister) {
  if (business > sochib) {
    console.log('Business is bigger');
  } else {
    console.log('Sochib is bigger');
  }
} else {
  if (minister > sochib) {
    console.log('Minister is bigger');
  } else {
    console.log('sochib is bigger');
  }
}

// the Math.max() function returns the largest of the zero or more numbers given as input

let max = Math.max(business, minister, sochib);
console.log(max);

console.log(Math.max(1, 3, 2));
// expected output: 3

console.log(Math.max(-1, -3, -2));
// expected output: -1

const array1 = [1, 3, 2];

console.log(Math.max(...array1));
// expected output: 3
```

[Additional Resources- 1](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max){:target="\_blank"}  
[Additional Resources- 2](https://medium.com/coding-at-dawn/the-fastest-way-to-find-minimum-and-maximum-values-in-an-array-in-javascript-2511115f8621){:target="\_blank"}

## 2.4 FIND THE LARGEST ELEMENT OF AN ARRAY

```javascript
let marks = [45, 81, 63, 98, 56, 35, 23];
let max = marks[0];

for (var i = 0; i < marks.length; i++) {
  // debugger;
  let element = marks[i];
  if (element > max) {
    max = element;
  }
}

console.log('Highest value is: ', max);
```

## 2.5 SUM OF ALL NUMBERS IN AN ARRAY

```javascript
let numbers = [45, 65, 68, 12, 3, 54, 65];

let sum = 0;
for (let i = 0; i < numbers.length; i++) {
  let element = numbers[i];
  sum = sum + element;
}

console.log('Total of the numbers: ', sum);

// using function:
function getArrSum(arrayNumbers) {
  let sum = 0;
  for (let i = 0; i < arrayNumbers.length; i++) {
    let element = arrayNumbers[i];
    sum = sum + element;
  }
  return sum;
}

let num = [45, 65, 68, 12, 3];
let getArrSumResult = getArrSum(num);

console.log('Total: ', getArrSumResult);

console.log('Total: ', getArrSum([50, 100, 20, 10]));
```

[Additional Resources- 1](https://codeburst.io/javascript-arrays-finding-the-minimum-maximum-sum-average-values-f02f1b0ce332){:target="\_blank"}  
[Additional Resources- 2](https://medium.com/@chrisburgin95/rewriting-javascript-sum-an-array-dbf838996ed0){:target="\_blank"}

## 2.6 REMOVE DUPLICATE ITEM FROM AN ARRAY

```javascript
let arrNum = [3, 6, 2, 7, 3, 2, 8, 1, 9, 11, 56];

let uniqueNum = [];

for (let i = 0; i < arrNum.length; i++) {
  let element = arrNum[i]; /* each index element */
  let index = uniqueNum.indexOf(
    element
  ); /* check the element index in uniqueNum */

  if (index == -1) {
    /* when the element is not found in uniqueNum, push will add */
    uniqueNum.push(element);
  }
}
console.log(uniqueNum);

// using function:
function findUnique(arrayX) {
  let uniqueNum = [];
  for (let i = 0; i < arrayX.length; i++) {
    let element = arrayX[i];
    let index = uniqueNum.indexOf(element);

    if (index == -1) {
      uniqueNum.push(element);
    }
  }
  return uniqueNum;
}

console.log(findUnique([5, 5, 7, 9, 0, 5, 9, 0, 3]));
```

## 2.7 COUNT THE NUMBER OF WORDS IN A STRING

```javascript
let speech = "I am a good person. I don't snore at night";
// console.log(speech.length);
// console.log(speech[3]);

// Target spaces between words
let count = 0;
for (let i = 0; i < speech.length; i++) {
  let char = speech[i];
  console.log(char);

  if (char == ' ' && speech[i - 1] != ' ') {
    /* speech[i - 1] is applied to ignor double spaces */
    count++;
    /* 1 less than expected word count cause there is no space after last word */
  }
}
count++; /* add 1 to fix the prior count */

console.log(count);
```

## 2.8 REVERSE A STRING

```javascript
function reverseString(str) {
  let reverse = '';
  for (let i = 0; i < str.length; i++) {
    let char = str[i];
    reverse = char + reverse; /* put char in the beginning to reverse */
  }
  return reverse;
}

let statement = 'Hello Alien, How are you doing?';
let reverseStrOut = reverseString(statement);
console.log(reverseStrOut);
```

# 3 Exercise

## 3.1 FIND THE LARGEST VALUE

```javascript
// Write an function to find largest value.
function largestNumber(numbers) {
  var larger = numbers[0];
  for (var i = 0; i < numbers.length; i++) {
    var element = numbers[i];
    if (element > larger) {
      larger = element;
    }
  }
  return larger;
}

console.log(largestNumber([45, 78, 89, 23]));
```

## 3.2 WRITE TWO FUNCTIONS TO FIND FACTORIAL

```javascript
// Find factorial using iteration
// 5!=5*4*3*2*1
function factorial(num) {
  var fact = 1;
  for (var i = 1; i <= num; i++) {
    fact = fact * i;
  }
  return fact;
}

console.log(factorial(5));

// Write a recursive function to find factorial.
function rFactorial(num) {
  if (num == 1) {
    return 1;
  } else {
    return num * rFactorial(num - 1);
  }
}

console.log(rFactorial(5));
```

## 3.3 FIND THE NUMBER OF ANIMAL

```javascript
/* assume you went to amazon forest, the more deeper you will go inside the forest, 
the chance of seeing more animals is greater. 
Let's assume from the beginning of the forest to first 10 miles, you had saw 50 animals,
then second 10 miles 100 animals, and third 10 miles or greater 300 animals respectively. 
Write a function named animalCalculator to find the totalanimal for a given input of depth. */

var depth = 12;

function animalCalculator(depth) {
  var animal = 0;

  if (depth <= 10) {
    animal = depth * 5;
  } else if (depth <= 20) {
    var firstPart = 10 * 50;
    var remaining = depth - 10;
    var secondPart = remaining * 100;
    animal = firstPart + secondPart;
  } else {
    var firstPart = 10 * 50;
    var secondPart = 10 * 100;
    var remaining = depth - 20;
    var thirdPart = remaining * 300;
    animal = firstPart + secondPart + thirdPart;
  }
  return animal;
}

console.log(animalCalculator(32));
```

<!-- ```javascript
``` -->
