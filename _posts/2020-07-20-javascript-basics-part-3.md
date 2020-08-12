---
title: 'JavaScript Basics Part- 3'
comments: true
excerpt: 'Post displaying the JavaScript DOM, capturing elements, node, node list, node type, html collections, set attributes, function, callback function, arguments, event, event handler, add event listener, event bubble, propagating event bubble,event delegate'
last_modified_at: 2020-07-20T10:27:01-05:00
categories:
  - JavaScript

tags:
  - JavaScript
  - JavaScript Fundamentals
---

{% include toc %}

# 1 HOW JAVASCRIPT WORKS & DOM

## 1.1 CREATE SCRIPT TAG AND CONNECT EXTERNAL SCRIPT FILE

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <style>
      body {
        background-color: aquamarine;
      }
    </style>
  </head>
  <body>
    <h1>Hello Javascript</h1>
    <h1>Hello Javascript</h1>
    <h1>Hello Javascript</h1>
    <h1>Hello Javascript</h1>
    <h1>Hello Javascript</h1>

    <!-- Internal JS -->
    <script>
      console.log(45);
      // alert("Hello JavaScript");
    </script>

    <!-- External JS -->
    <script src="scripts/second.js"></script>
    <script src="scripts/first.js"></script>
  </body>
</html>
```

## 1.2 HOW JAVASCRIPT RUN AND WHY SCRIPT ORDER IS IMPORTANT

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Learning Javascript</title>
    <style>
      body {
        background-color: aquamarine;
      }
    </style>
  </head>
  <body>
    <h1>Hello Javascript: 1</h1>
    <script src="scripts/first.js"></script>
    <h1>Hello Javascript: 2</h1>
    <script src="scripts/second.js"></script>
    <h1>Hello Javascript: 3</h1>
    <h1>Hello Javascript: 4</h1>

    <!-- Internal JS -->
    <script>
      console.log(45);
      debugger;
      console.log(145);
    </script>
    <h1>Hello Javascript: 5</h1>

    <!-- Output will be based on place of JS orders -->

    <!-- HOW JAVASCRIPT RUN AND WHY SCRIPT ORDER IS IMPORTANT -->
    <!-- JS is High level interpreted language, single threaded, non-blocking -->
  </body>
</html>
```

```javascript
// first.js
console.log(81);
debugger;

// second.js
console.log(120);
debugger;
```

[Additional Resources](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_is_JavaScript){:target="\_blank"}

## 1.3 WHAT IS DOM (DOCUMENT OBJECT MODEL)

```html
<body>
  <main>
    <section>
      <h3>Exploring DOM</h3>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Magni voluptate
        vitae animi corrupti ipsa dolorem eum deserunt, in voluptates explicabo
        quaerat amet, tenetur unde. Beatae deleniti eveniet rerum eligendi
        laboriosam?
      </p>

      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia, fuga?
      </p>
    </section>
    <!-- Chrome browser ->Console -> type document -->
  </main>

  <script>
    var user = {
      name: 'Jalali Set',
      song: 'Kakatua',
      members: 6,
    };
    // DOM = Document Object Model;
    // console.log(document);
    console.log(document.body);
  </script>
</body>
```

[Additional Resources- 1](https://javascript.info/dom-navigation){:target="\_blank"}  
[Additional Resources- 2](https://javascript.info/dom-nodes) {:target="\_blank"}

## 1.4 CAPTURE ELEMENTS FROM HTML FILE USING GETELEMENTBYID

```html
<body>
  <main>
    <section>
      <h3>Exploring DOM</h3>
      <p id="first">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Magni voluptate
        vitae animi corrupti ipsa dolorem eum deserunt, in voluptates explicabo
        quaerat amet, tenetur unde. Beatae deleniti eveniet rerum eligendi
        laboriosam?
      </p>

      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia, fuga?
      </p>
    </section>
    <!-- Chrome browser ->Console -> type document -->
  </main>

  <script>
    // document.getElementsByTagName;
    // document.getElementById("first");
    var first = document.getElementById('first');
    first.style.color = 'darkblue';
    first.style.fontSize = '30px';
    first.style.backgroundColor = 'grey';
  </script>
</body>
```

## 1.5 HOW TO USE GETELEMENTSBYCLASSNAME AND CHANGE INNERHTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Explore DOM</title>
    <style>
        article {
            border: 2px solid tomato;
            border-radius: 20px;
            margin: 5px;
            padding: 5px;
        }
    </style>
</head>
<body>
  <main>
        <section>
            <h3>Exploring DOM</h3>
            <!-- article*3>h3{article-$}+p.author{author-$}+p.description>lorem30 -->
            <article>
                <h3>article-1</h3>
                <p class="author">author-1</p>
                <p class="description">Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda fuga suscipit
                    nulla. Dicta delectus aut minus. Veritatis cumque consectetur perferendis voluptatum ratione dicta
                    nam, perspiciatis distinctio nisi nobis esse doloremque.</p>
            </article>
            <article>
                <h3>article-2</h3>
                <p class="author">author-2</p>
                <p class="description">Architecto illum earum, reprehenderit assumenda minima aliquid dolores, delectus
                    quidem corporis reiciendis quas incidunt nihil possimus unde voluptates laborum tempora. Autem
                    tempora error laborum consequatur atque similique sapiente excepturi voluptates!</p>
            </article>
            <article>
                <h3>article-3</h3>
                <p class="author">author-3</p>
                <p class="description">Quos dolorum, laborum voluptate culpa, natus sequi nesciunt officiis vero tempore
                    magni, exercitationem voluptates consectetur quibusdam doloremque. Laudantium odit at magni vel. Ut
                    nulla reiciendis officia, placeat delectus aut corrupti?</p>
            </article>

    </main>

   <script>
        // document.getElementsByClassName('author');
        var authors = document.getElementsByClassName('author');
        for(var i=0; i<authors.length; i++){
            var element = authors[i];
            // console.log(element);
            console.log(element.innerHTML);
            // element.innerHTML ="Lekhok- " + i;
            element.innerHTML ="Lekhok- " + (i+1);
            element.style.backgroundColor = 'lightblue';
            element.style.margin ='10px';
        }
    </script>
</body>
</html>
```

## 1.6 HOW TO USE QUERYSELECTOR AND QUERYSELECTORALL & NODE, NODE TYPE, NODELIST, HTMLCOLLECTION, SETATTRIBUTE

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Explore DOM</title>
    <style>
        article {
            border: 2px solid tomato;
            border-radius: 20px;
            margin: 5px;
            padding: 5px;
        }
        .special h3 {}
    </style>
</head>

<body>
  <main>
        <section>
            <h3>Exploring DOM</h3>
            <!-- article*3>h3{article-$}+p.author{author-$}+p.description>lorem30 -->
            <article>
                <h3>article-1</h3>
                <p title="best seller author" id="best-seller" class="author">author-1</p>
                <p class="description">Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda fuga suscipit
                    nulla. Dicta delectus aut minus. Veritatis cumque consectetur perferendis voluptatum ratione dicta
                    nam, perspiciatis distinctio nisi nobis esse doloremque.</p>
            </article>
            <article class="special">
                <h3>article-2</h3>
                <p class="author">author-2</p>
                <p class="description">Architecto illum earum, reprehenderit assumenda minima aliquid dolores, delectus
                    quidem corporis reiciendis quas incidunt nihil possimus unde voluptates laborum tempora. Autem
                    tempora error laborum consequatur atque similique sapiente excepturi voluptates!</p>
            </article>
            <article class="special">
                <h3>article-3</h3>
                <p class="author">author-3</p>
                <p class="description">Quos dolorum, laborum voluptate culpa, natus sequi nesciunt officiis vero tempore
                    magni, exercitationem voluptates consectetur quibusdam doloremque. Laudantium odit at magni vel. Ut
                    nulla reiciendis officia, placeat delectus aut corrupti?</p>
            </article>

    </main>

    <script>
        // HOW TO USE QUERYSELECTOR AND QUERYSELECTORALL
        // document.querySelector('.special h3'); will give only the first matching
        // document.querySelectorAll('.special h3'); will give all matching

        document.body.style.backgroundColor = 'tomato';
        var authors = document.querySelectorAll('.special h3');

        for (var i = 0; i < authors.length; i++) {
            var element = authors[i];
            // console.log(element);
            // console.log(element.innerHTML);
            // element.innerHTML ="Lekhok- " + i;
            element.innerHTML = "Lekhok- " + (i + 1);
            element.style.backgroundColor = 'lightblue';
            element.style.margin = '10px';
            element.setAttribute('title', 'all author are same');
        }

        // document.querySelector('.special h3').style.backgroundColor = 'Tomato';

        // NODE, NODE TYPE, NODELIST, HTMLCOLLECTION, SETATTRIBUTE
        // Node
        // Node List

        document.querySelector('h3').setAttribute('title', "You are the title");
        document.getElementById('best-seller').setAttribute('title', "give me your autograph");
    </script>
</body>
</html>
```

[Additional Resources- 1](https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType){:target="\_blank"}

## 1.7 HOW TO ADD ELEMENTS TO HTML USING JAVASCRIPT

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Explore DOM</title>
    <style>
        article {
            border: 2px solid tomato;
            border-radius: 20px;
            margin: 5px;
            padding: 5px;
        }
        .special h3 {}
    </style>
</head>
<body>
  <main>
        <section>
            <h3>Exploring DOM</h3>
            <!-- article*3>h3{article-$}+p.author{author-$}+p.description>lorem30 -->
            <article id="first-article">
                <h3>article-1</h3>
                <p title="best seller author" id="best-seller" class="author">author-1</p>
                <p class="description">Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda fuga suscipit
                    nulla. Dicta delectus aut minus. Veritatis cumque consectetur perferendis voluptatum ratione dicta
                    nam, perspiciatis distinctio nisi nobis esse doloremque.</p>
            </article>
            <article class="special">
                <h3>article-2</h3>
                <p class="author">author-2</p>
                <p class="description">Architecto illum earum, reprehenderit assumenda minima aliquid dolores, delectus
                    quidem corporis reiciendis quas incidunt nihil possimus unde voluptates laborum tempora. Autem
                    tempora error laborum consequatur atque similique sapiente excepturi voluptates!</p>
            </article>
            <article class="special">
                <h3>article-3</h3>
                <p class="author">author-3</p>
                <p class="description">Quos dolorum, laborum voluptate culpa, natus sequi nesciunt officiis vero tempore
                    magni, exercitationem voluptates consectetur quibusdam doloremque. Laudantium odit at magni vel. Ut
                    nulla reiciendis officia, placeat delectus aut corrupti?</p>
            </article>

            <article>
                <h3>Grocery List</h3>
                <ul id="gift-list">
                    <li>gift item- 1</li>
                    <li>gift item- 2</li>
                    <li>gift item- 3</li>
                    <li>gift item- 4</li>
                    <li>gift item- 5</li>
                </ul>
            </article>

    </main>

    <script>
        const article = document.getElementById('first-article');
        const newParagraph = document.createElement('p');
        newParagraph.innerHTML = 'This is added by JavaScript';
        article.appendChild(newParagraph);

        // add one more gift

        const ul = document.getElementById('gift-list');
        const li = document.createElement('li');
        li.innerHTML = "Brand New Gift";
        ul.appendChild(li);

        // document.getElementById('gift-list').childNodes
        // document.getElementById('gift-list').parentNode
        // document.getElementById('first-article').childNodes
    </script>
</body>
</html>
```

# 2 FUNCTION, ADD EVENT LISTENER, EVENT BUBBLE

## 2.1 WHEN TO USE A FUNCTION, FUNCTION INSIDE AN ARRAY

```javascript
let nums = [5, 12, 89, 45, 18, 8];

for (let i = 0; i < nums.length; i++) {
  const num = nums[i];
  // console.log(num * 2);
  // odd and even
  if (num % 2 == 0) {
    console.log(num, ': is even number');
  } else {
    // console.log(num, ':is odd number');
    console.log(num * 2, ':is odd number');
  }
}

// New array
let frndAge = [13, 17, 19, 20, 18];

for (let i = 0; i < frndAge.length; i++) {
  const age = frndAge[i];
  // console.log(age);
  if (age % 2 == 0) {
    console.log(age, ': is even number');
  } else {
    console.log(age * 2, ':is odd number');
  }
}

// repeated or duplicated same thing in both calculation

// create function to avoid duplicate code, call function inside
function evenify(num) {
  if (num % 2 == 0) {
    console.log(num, ': is even number');
  } else {
    console.log(num, ':is odd number');
  }
}

// call function inside another function
function evenifyAll(nums) {
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i];
    evenify(num);
  }
}

// without writing multiple functions
function evenifyAll(nums) {
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i];
    if (num % 2 == 0) {
      console.log(num, ': is even number');
    } else {
      console.log(num, ':is odd number');
    }
  }
}

// call function inside loop

let nums = [7, 13, 89, 45, 18, 8];

for (let i = 0; i < nums.length; i++) {
  const num = nums[i];
  evenify(num);
}

// call function inside loop
let frndAge = [13, 17, 19, 20, 18];
for (let i = 0; i < frndAge.length; i++) {
  const age = frndAge[i];
  // console.log(age);
  evenify(age);
}

// call the function which created with loop
evenifyAll(frndAge);
```

## 2.2 WHEN TO RETURN FROM A FUNCTION AND FROM WHERE

```javascript
// return in all statement
function evenify(num) {
  if (num % 2 == 0) {
    // console.log(num, ':is even number');
    return num;
  } else {
    // console.log(num, ':is odd number');
    return num * 2;
  }
}

let result = evenify(13);
console.log('result', result);

// return after all statement
function evenify(num) {
  let result;
  if (num % 2 == 0) {
    result = num;
  } else {
    result = num * 2;
  }
  return result;
}

let result2 = evenify(15);
console.log('result', result2);

let square = result2 * result2;
console.log('squre', square);

// array with even number
function evenifyAll(nums) {
  let evenArray = [];
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i];

    let result = evenify(num);
    evenArray.push(result);
  }
  return evenArray;
}

let nums = [3, 6, 18, 19, 20, 21];
let numsEven = evenifyAll(nums);
console.log(numsEven);
```

## 2.3 CALLBACK FUNCTION AND PASS DIFFERENT FUNCTION

```javascript
function explnCallback(name, age, task) {
  console.log('Hello', name);
  console.log('Your age', age);
  // washHand();
  // takeShower();
  // console.log(task);
  task();
}

function washHand() {
  console.log('Wash hand with soap');
}

function takeShower() {
  console.log('Take Shower');
}

function scrollFB() {
  console.log('Scrolling FB');
}
// explnCallback('Robert', 17);
// explnCallback('smith', 13);

explnCallback('Robert', 17, washHand);
explnCallback('smith', 13, takeShower);
explnCallback('Jane', 21, scrollFB);
```

## 2.4 ARGUMENTS AND DEAL WITH UNKNOWN NUMBER OF ARGUMENTS

```javascript
function addNumber(num1, num2) {
  return num1 + num2;
}

let result = addNumber(3, 5);
console.log(result);

// add more parameter value than specified in function
let result2 = addNumber(3, 5, 8, 15);
console.log(result2);

// read parameter value using arguments, arguments work inside function
function addNumber2(num1, num2) {
  // console.log(arguments);
  console.log(arguments[3]);
  return num1 + num2;
}
let result2 = addNumber2(3, 5, 8, 15);
console.log(result2);

// arguments
function addNumber3(num1, num2) {
  // console.log(arguments[3]);
  let sum = 0;
  for (let i = 0; i < arguments.length; i++) {
    const num = arguments[i];
    console.log(num);
    sum = sum + num;
  }
  // return num1 + num2;
  return sum;
}

let result3 = addNumber3(3, 5, 8, 15, 29);
console.log(result3);
```

## 2.5 HOW TO ORGANIZE CODE INSIDE A FUNCTION

```javascript
function addNumber4(num1, num2) {
  let sum = 0;
  for (let i = 0; i < arguments.length; i++) {
    const num = arguments[i];
    console.log(num);
    sum = sum + num;
  }
  logInfo('Good Morning'); /* readability issue */

  // declare function before calling
  function logInfo(msg) {
    console.log(msg);
  }

  // logInfo("Good Morning");

  let double = sum * 2; /* assign variable before using */
  /* if variable use in multiple places declare on top */
  return sum;
}

let result4 = addNumber4(3, 5, 8, 15, 29);
console.log(result4);
```

## 2.6 WHAT IS EVENT, DIFFERENT TYPES OF EVENT IN WEB

[Resources- 1](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events){:target="\_blank"}  
[Resources- 2](https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent){:target="\_blank"}  
[Resources- 3](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent){:target="\_blank"}

## 2.7 ADD EVENT HANDLER DIRECTLY ON AN ELEMENT

```html
<body>
  <h1 onclick="console.log('Hello')">Exploring Event</h1>
  <!-- <button onclick="alert(47)">Click Me</button> -->
  <button onclick="handleClick()">Button-1</button>
  <button onmousemove="mouseMove()">Button-2</button>
  <button onmouseout="mouseOut()">Button-3</button>

  <script src="script.js"></script>
</body>
```

```javascript
//script.js
function handleClick() {
  console.log('someone clicked me');
}

function mouseMove() {
  console.log('someone moved over me');
}

function mouseOut() {
  console.log('someone moved out');
}
```

## 2.8 ADD EVENT LISTENER USING JAVASCRIPT

```html
<body>
  <button id="primary-btn">Primary Button</button>
  <button id="secondary-btn">Secondary Button</button>
  <button id="third-btn">Third Button</button>
  <button id="fourth-btn">Fourth Button</button>
  <script src="script.js"></script>
</body>
```

```javascript
// script.js
// applied function method-1, direct function
let secondaryBtn = document.getElementById('secondary-btn');
secondaryBtn.onclick = function () {
  console.log('You just clicked me');
};

// applied function method-2, create function first
function handleClick2() {
  document.body.style.backgroundColor = 'cyan';
}

let primaryBtn = document.getElementById('primary-btn');
primaryBtn.onclick = handleClick2;

// applied function method-3, event listener
function handleClick3() {
  document.body.style.backgroundColor = 'tomato';
}

let thirdBtn = document.getElementById('third-btn');

thirdBtn.addEventListener('click', handleClick3);

// applied function method-4, event listener
function handleClick4() {
  document.body.style.backgroundColor = 'orange';
}
// const fourthBtn = document.getElementById('fourth-btn').addEventListener('click', handleClick4);
const fourthBtn = document
  .getElementById('fourth-btn')
  .addEventListener('click', function () {
    document.body.style.color = 'tomato';
  });

// function() is called anonymous function
```

## 2.9 EVENT BUBBLE WITH EXAMPLE AND STOP PROPAGATING EVENT BUBBLE

```html
<body>
  <!-- EVENT BUBBLE WITH EXAMPLE -->
  <!-- div#container>ul#myList>li.item*5>lorem3 -->
  <div id="container">
    <h1>My List</h1>
    <ul id="myList">
      <li id="first" class="item">Lorem, ipsum dolor.</li>
      <li class="item">Obcaecati, minima mollitia.</li>
      <li class="item">Distinctio, quasi autem?</li>
      <li class="item">Sint, placeat labore.</li>
      <li class="item">Quibusdam, ipsam deserunt!</li>
    </ul>
  </div>
  <script src="script.js"></script>
</body>
```

```javascript
// script.js
document.getElementById('first').addEventListener('click', function (event) {
  console.log('First Item Clicked');
  // STOP PROPAGATING EVENT BUBBLE
  // event.stopPropagation();
});
document.getElementById('myList').addEventListener('click', function (event) {
  console.log('ul Clicked');
  event.stopPropagation();
});

document
  .getElementById('container')
  .addEventListener('click', function (event) {
    console.log('Container Clicked');
  });

// stopPropagation
// stopImmediatePropagation
```

[Additional Resources](https://javascript.info/bubbling-and-capturing){:target="\_blank"}

## 2.10 EVENT DELEGATE AND PURPOSE OF EVENT BUBBLE

```html
<body>
  <div id="container">
    <h1>My List</h1>
    <ul id="myList">
      <li id="first" class="item">Lorem, ipsum dolor.</li>
      <li class="item">Obcaecati, minima mollitia.</li>
      <li class="item">Distinctio, quasi autem?</li>
      <li class="item">Sint, placeat labore.</li>
      <li class="item">Quibusdam, ipsam deserunt!</li>
    </ul>

    <button id="addNew">Add New</button>
  </div>
  <script src="script.js"></script>
</body>
```

```javascript
// script.js
// EVENT DELEGATE AND PURPOSE OF EVENT BUBBLE
// in chrome:
// document.getElementsByClassName('item');

/*
        let items = document.getElementsByClassName('item');
        for (let i = 0; i < items.length; i++) {
            let item = items[i];
            // console.log("item");

            item.addEventListener('click', function (event) {
                // console.log(this);
                // console.log(this, event.target); 
                //access event.target- target the event where clicked
        // console.log(event.target.innerText);
        // console.log(event.target.parentNode); 
        //will give parent 
        event.target.parentNode.removeChild(event.target);
        })
        }
        */

document.getElementById('addNew').addEventListener('click', function (event) {
  let itemsParent = document.getElementById('myList');
  let newItem = document.createElement('li');
  newItem.innerText = 'Brand New Item';
  itemsParent.appendChild(newItem);
});

document.getElementById('myList').addEventListener('click', function (event) {
  // console.log(this, event.target);

  event.target.parentNode.removeChild(event.target);
});
```

# INTEGRATE JAVASCRIPT BONUS CONTENT

## 3.1 GLOBAL VS LOCAL VARIABLE IIFE FUNCTION EXPRESSION VS DECLARATION

```javascript
function addToDo() {
  // Local variable, inside function
  const newTaskElement = document.createElement('li');
}

// Global Variable
var name = 'Rashed';

function addUser() {
  var localUser = 'Andy';
  //localUser = "Andy"; global leaking, wrong
  console.log(name);
}

addUser();

console.log(localUser); // will give an error: localUser is not defined

//  IIFE (Immediately Invoked Function Expression)
(function () {
  var localUser = 'Andy';
  console.log(localUser);
})();

// Function Declaration vs Statement
// Example: Function Expression
alert(foo()); // ERROR! foo wasn't loaded yet
var foo = function () {
  return 5;
};

// Example: Function Declaration
alert(foo()); // Alerts 5. Declarations are loaded before any code can run.
function foo() {
  return 5;
}
```

[Additional Resources - 1](<https://developer.mozilla.org/en-US/docs/Glossary/IIFE#:~:text=An%20IIFE%20(Immediately%20Invoked%20Function,soon%20as%20it%20is%20defined.)>){:target="\_blank"}  
[Additional Resources - 2](https://medium.com/@mandeep1012/function-declarations-vs-function-expressions-b43646042052#:~:text=Function%20declarations%20load%20before%20any,reaches%20that%20line%20of%20code.&text=Function%20expressions%20aren){:target="\_blank"}

## 3.2 FOUR SITUATION WHEN YOU SHOULD CREATE A FUNCTION

1. Handle Specific task or situation
2. Reduce Code Repetition (DRY- Do Not Repeat Yourself)
3. Specific unit or atomic task
4. Organize larger code

## 3.3 WHEN AND HOW TO USE ARGUMENTS IN A FUNCTION

```javascript
//argument is array like object
function getFullName(firstName, lastName) {
  // console.log(arguments);
  // let fullName = firstName + ' ' + lastName;
  let fullName = '';
  for (let i = 0; i < arguments.length; i++) {
    const namePart = arguments[i];
    fullName = fullName + ' ' + namePart;
  }
  return fullName;
}

let name = getFullName('Hanif', 'Songkhet', 'Poribohon', 'Hasib');
console.log(name);

// convert arguments to a real Array:

let args = Array.from(arguments);
// or
let args = [...arguments];
```

[Additional Resources](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments#:~:text=The%20arguments%20object%20is%20a,first%20entry's%20index%20at%200%20.){:target="\_blank"}

## 3.4 WHEN AND HOW TO USE JAVASCRIPT CALLBACK FUNCTION

```javascript
function welcomeGuest(name, greetHandler) {
  // console.log(name);
  greetHandler(name);
}

function greetUserMorning(name) {
  console.log('Good Morning', name);
}

function greetUserEvening(name) {
  console.log('Good Evening', name);
}

function greetUserAfternoon(name) {
  console.log('Good Afternoon', name);
}

const actorName = 'Tom Hanks';
welcomeGuest(actorName, greetUserMorning);
welcomeGuest(actorName, greetUserEvening);
welcomeGuest(actorName, greetUserAfternoon);

welcomeGuest('Kate Winslet', greetUserMorning);

welcomeGuest('Shaib Khan', function (name) {
  console.log('Special Welcome to', name);
});

function handleClick() {
  console.log('Someone Clicked Me');
}
document.getElementById('demo').addEventListener('click', handleClick);
```

<!-- ```html
<body>
  <script src="script.js"></script>
</body>
``` -->

<!-- ```javascript
``` -->
