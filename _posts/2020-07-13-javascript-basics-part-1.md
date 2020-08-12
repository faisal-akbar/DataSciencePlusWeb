---
title: 'JavaScript Basics Part- 1'
comments: true
excerpt: 'Post displaying the fundamental concepts of JavaScript'
last_modified_at: 2020-07-13T10:27:01-05:00
categories:
  - JavaScript

tags:
  - JavaScript
  - JavaScript Fundamentals
---

{% include toc %}

# 1 GETTING STARTED WITH JAVASCRIPT

## 1.1 WHAT IS VARIABLE, DECLARE A VARIABLE, SEE OUTPUT

```javascript
// declare Variable 5 things (var, varName, =, value, ;)
var bananaPrice = 12;
console.log(bananaPrice);
```

## 1.2 VARIABLE TYPE, NUMERIC, STRING, BOOLEAN

```javascript
// variable type & Keywords
var seenAfter = 21;
console.log(seenAfter);

// number
console.log(typeof seenAfter);

// string
var name = 'Faisal Akbar';
console.log(name);
console.log(typeof name);

// boolean
var isHot = true;
var isRich = false;

console.log(isHot);
console.log(typeof isHot);
```

## 1.3 VARIABLE NAME NAMING CONVENTION AND BEST PRACTICE

```javascript
// var keyword, most of the cases keywords are lower case
// google JS keywords
// variable name case sensitive
// no need to declare same variable more than once
// naming convention- Camel Case
// use Meaningful name e.g. userName
var myName = 'Hero Alom';
myName = 'Hero Abdul';
MyName = 'Hero Mosharof';

console.log(myName);
```

## 1.4 EXPLORE STRING CASE CHANGE INDEX SPLIT

```javascript
// string declaration use- double quote(" "); single quote (' '); punctuation mark(``)
var promise = 'I promise I will word HARD to become a programmer';

// make lowercase
console.log(promise.toLowerCase());

// make uppercase
console.log(promise.toUpperCase());

// find index, start at 0
console.log(promise.indexOf('will'));
console.log(promise.indexOf('promise'));

// -1 index meaning not found
console.log(promise.indexOf('pomise'));
console.log(promise.indexOf('hard'));

// split string
console.log(promise.split('I'));
console.log(promise.split(' '));
```

## 1.5 INTEGER FLOAT PARSE INT PARSE FLOAT TYPE CONVERSION

```javascript
// integer and float
var number1 = 25;
var number2 = 15.5;
console.log(number1 + number2);

var number1 = '25';
var number2 = 15.5;
console.log(number1 + number2);

var number1 = 25;
var number2 = '15.5';
console.log(number1 + number2);

// parsing string to float, use if you are not sure
number2 = parseFloat(number2);
console.log(number1 + number2);

// parsing string to integer, use when whole number is necessary only
number2 = parseInt(number2);
console.log(number1 + number2);

// shortcut to convert string number to float
var number3 = '15.5';
number3 = +number3;
console.log(number1 + number3);

// convert number to string, add an empty string('')
number4 = 12;
number4 = '' + number4;
console.log(typeof number4);

// issue with decimal
var number5 = 0.1;
var number6 = 0.2;
console.log(number5 + number6);

// fixed decimal precision, the toFixed() method formats a number using fixed-point notation
var total = number5 + number6;
total = total.toFixed(1);
console.log(total);
```

## 1.6 MATHEMATICAL OPERATIONS IN JAVASCRIPT

```javascript
// addition
var a = 35;
var b = 20;
var sum = a + b;
console.log(sum);

// subtraction
var sub = a - b;
console.log(sub);

// multiplication
var mul = a * b;
console.log(mul);

// division
var div = a / b;
console.log(div);

// remainder or modulus
var mod = a % b;
console.log(mod);

// plus plus; minus minus Operator
var c = 40;
var d = 45;

c++; /*same as c=c+1*/
console.log(c);

d--; /* same as d=d-1*/
console.log(d);

// string and number
var userName = 'jack';
var age = 30;

// string + number
var result = userName + age;
console.log(result);

// number + string
var result = age + userName;
console.log(result);

var price = '35';
var age = 30;

// string + number
var result = userName + age;
console.log(result);

// number + String
var result = age + userName;
console.log(result);

// add String
var firstName = 'jack';
var lastName = 'Smith';
var fullName = firstName + ' ' + lastName;
console.log(fullName);
```

## 1.7 MATH ABSOLUTE ROUND FLOOR CEIL RANDOM

```javascript
// absolute number
var x = -5;
var absoluteNumber = Math.abs(x);
console.log(absoluteNumber);

// the Math.round() function returns the value of a number rounded to the nearest integer.
var y = 5.4545;
var roundNumber = Math.round(y);
console.log(roundNumber);

// the Math.ceil() function always rounds a number up to the next largest integer
var ceilingNumber = Math.ceil(y);
console.log(ceilingNumber);

// the Math.floor() function returns the largest integer less than or equal to a given number
var floorNumber = Math.floor(y);
console.log(floorNumber);

// the Math.random() function returns a floating-point, pseudo-random number between 0 (inclusive) and 1 (exclusive)
var randomNumber = Math.random();
console.log(randomNumber);

var randomNumber = Math.random() * 100;
var roundRandomNumber = Math.round(randomNumber);
console.log(roundRandomNumber);
```

## 1.8 MAKE CONDITIONAL DECISION, IF-ELSE, COMPARISON

```javascript
// if else
// The if statement executes a statement if a specified condition is truthy. If the condition is falsy, another statement can be executed

/* less than */
var coffeePrice = 12;

if (coffeePrice < 10) {
  console.log('I will drink coffee');
} else {
  console.log('I will not drink coffee');
}

/* greater than */
if (coffeePrice > 10) {
  console.log('I will not drink coffee');
} else {
  console.log('I will drink coffee');
}

/* equal ==, === */
if (coffeePrice == 10) {
  console.log('I will not drink coffee');
} else {
  console.log('I will drink coffee');
}

/* not equal */

if (coffeePrice != 10) {
  console.log('I will not drink coffee');
} else {
  console.log('I will drink coffee');
}

// Multiple Condition
var job = true;
var savingAmount = 5000000;

/* Both condition must be fullfil */
if (job == true && savingAmount > 200000) {
  console.log('Well done');
} else {
  console.log('You need to work hard');
}

var job = true;
var savingAmount = 500;

if (job == true && savingAmount > 200000) {
  console.log('Well done');
} else {
  console.log('You need to work hard');
}

/* any of one condition must be fullfil */
if (job == true || savingAmount > 200000) {
  console.log('Well done');
} else {
  console.log('You need to work hard');
}

// if else if
if (job == true && savingAmount > 200000) {
  console.log('Well done!!');
} else if (job == true) {
  console.log('Save some money!!');
} else {
  console.log('You need to work hard!!');
}

// Date & Time Zone
var newDate = new Date();
console.log(newDate);

var newDate = new Date('1971-12-16');
console.log(newDate);
```

# 2 JAVASCRIPT FUNDAMENTAL CONCEPTS

## 2.1 ARRAY, INDEX, SET BY INDEX, INDEXOF

```javascript
// declare an array, index start at 0
var friendsAge = [15, 17, 14, 16];
console.log(friendsAge);

// finding element or item of an array using index
console.log(friendsAge[0]);
console.log(friendsAge[3]);

// store array element in variable using index
var sonaliAge = friendsAge[2];
console.log(sonaliAge);

// change array element using index
friendsAge[1] = 21;
console.log(friendsAge);

// find element position (index) of certain element
var position = friendsAge.indexOf(14);
console.log(position);

// if index is not available for the specified element, then output will be -1
var position = friendsAge.indexOf(141);
console.log(position);
```

## 2.2 ARRAY ADVANCED, PUSH, POP, ARRAY LENGTH

```javascript
// the push() method adds new items to the end of an array, and returns the new length
friendsAge.push(23);
friendsAge.push(25);
console.log(friendsAge);

// length of an array
console.log(friendsAge.length);
console.log(friendsAge['length']);

// the pop() method removes the last element of an array, and returns that element
friendsAge.pop();
console.log(friendsAge);
```

## 2.3 ARRAY ADD AND REMOVE ELEMENT FROM THE BEGINNING AND SLICE

```javascript
var teaLine = ['Abby', 'Smith', 'Bob'];
console.log(teaLine);

teaLine.push('Alex');
console.log(teaLine);

teaLine.pop();
console.log(teaLine);

// the shift() method removes the first item of an array.
// this method changes the length of the array.
// the return value of the shift method is the removed item.
var teaLine = ['Abby', 'Smith', 'Bob', 'Robert'];
teaLine.shift();
console.log(teaLine.shift());
console.log(teaLine);

// the unshift() method adds new items to the beginning of an array, and returns the new length.
// this method changes the length of an array.
teaLine.unshift('Jane');
console.log(teaLine);

// the slice() method returns the selected elements in an array, as a new array object
// the slice() method doesn't changes the contents of an array
var newTeaLine = ['Abby', 'Smith', 'Bob', 'Robert', 'Jane', 'Anna'];
var part1 = newTeaLine.slice(2); /*start from position 2 to end*/
console.log(part1);

var part2 = newTeaLine.slice(2, 4); /*start from position 2 to 3, excluding 4*/
console.log(part2);

var part3 = newTeaLine.slice(2, 5); /*start from position 2 to 4, excluding 5*/
console.log(part3);

// the splice() method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place using index number
// let arrDeletedItems = array.splice(start[, deleteCount[, item1[, item2[, ...]]]])

var months = ['Jan', 'March', 'April', 'June'];

/*starting index number, ending index number, will remove item(s) based on this numbers*/
months.splice(1, 2);
console.log(months);

months.splice(1);
console.log(months);

/*Insert at index 1 */
var months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
console.log(months);

/*Insert at index 1 */
var months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
console.log(months);

/*Insert at index 4 */
months.splice(4, 0, 'May');
console.log(months);

/*replaces 1 element at index 4 */
var months = ['Jan', 'Feb', 'March', 'April', 'June'];
months.splice(4, 1, 'May');
console.log(months);
```

[Additional Resources](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice){:target="\_blank"}

## 2.4 WHILE LOOP, DEBUG JAVASCRIPT CODE, LESS OR EQUAL

```javascript
// the while loop loops through a block of code as long as a specified condition is true
var num1 = 0;
while (num1 < 15) {
  console.log(num1);
  // num = num + 1;
  num1++;
}

var num2 = 10;
while (num2 < 15) {
  console.log(num2);
  num2++;
}

var num3 = 10;
while (num3 <= 15) {
  console.log(num3);
  num3++;
}
```

## 2.5 FOR LOOP, RUN A LOOP FOR EACH ELEMENT OF AN ARRAY

```javascript
// a for loop repeats until a specified condition evaluates to false
// less than
for (var i = 0; i < 10; i++) {
  console.log(i);
}

// less than and equal
for (var i = 0; i <= 10; i++) {
  console.log(i);
}

// Use for loop for array to find each items
var nums = [55, 66, 77, 88, 99, 11, 44];

for (var i = 0; i < nums.length; i++) {
  var element = nums[i];
  console.log(element);
}
```

## 2.6 JAVASCRIPT SWITCH CASE BREAK AND DEFAULT

```javascript
/* not efficient
var num=5;
if (num>1000) {}
else if (num>100) {}
else if (num>50) {}
else if (num>20) {}
else if (num>10) {}
else if (num>5) {}
else if (num>0) {}
else {}
*/

// A switch statement can replace multiple if checks.
// It gives a more descriptive way to compare a value with multiple variants.
// The switch has one or more case blocks and an optional default.
// Break is important, otherwise will check all conditions

var num = 5;
switch (num) {
  case 1000:
    console.log("I'm 1000");
    break;
  case 100:
    console.log("I'm 100");
    break;
  case 20:
  case 10:
    console.log("I'm either 20 or 10");
    break;
  default:
    console.log("I don't know who you are");
}
```

[Additional Resources- 1](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch){:target="\_blank"}  
[Additional Resources- 2](https://javascript.info/switch){:target="\_blank"}

## 2.7 FUNCTION, CALL FUNCTION

```javascript
// a JavaScript function is defined with the function keyword, followed by a name, followed by parentheses ()
function functionName() {
  console.log("I'm Function");
}

// call a function
functionName();
```

## 2.8 FUNCTION PARAMETER, MULTIPLE PARAMETER, FUNCTION RETURN

```javascript
/* function Parameters are the names that are define in the function definition and 
real values passed to the function in function definition are known as arguments */

function doubleIt(num) {
  var result = num * 2;
  console.log(result);
}

doubleIt(5);
doubleIt(50);

/*When a return statement is used in a function body, the execution of the function is 
stopped. If specified, a given value is returned to the function caller. */

function doubleIt(num) {
  var result = num * 2;
  return result;
}

var first = doubleIt(6);
var second = doubleIt(40);
console.log(first, second);

var total = first + second;
console.log(total);

function add(a, b) {
  var c = a + b;
  return c;
}

var sum = add(15, 17);
console.log(sum);
```

## 2.9 COMMENT, MULTIPLE LINES COMMENT

```javascript
// single line comment, Ctrl + /
/* multiline comment, 
  Shift + Alt + A */
```

## 2.10 OBJECT, KEY VALUE PAIR, GET OBJECT PROPERTY, SET VALUE

```javascript
/* An object is a collection of properties, and a property is an association between a name 
(or key) and a value. A property's value can be a function, in which case the property is 
known as a method. */

// {propertyName: PropertyValue}
var student1 = {
  id: 121,
  phone: 347,
  name: 'Abir',
};

var student2 = {
  id: 131,
  phone: 929,
  name: 'Mahi',
};

console.log(student1);
console.log(student2);

// access object property
var phoneNo1 = student1.phone; /* option-1 */
console.log(phoneNo1);

var phoneNo2 = student1['phone']; /* option-2 */
console.log(phoneNo2);

var phonePropName = 'phone'; /* option-3 */
var phoneNo3 = student1[phonePropName];
console.log(phoneNo3);

// change phone number
student2.phone = 542854;
student2['phone'] = 66688;
student2[phonePropName] = 9999;
console.log(student2);

// add new property
student2.cinema = 'Ogni2';
student2['cinema'] = 'Smart girl';
console.log(student2);
```
