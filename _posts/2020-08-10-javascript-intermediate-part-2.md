---
title: 'JavaScript Intermediate Part- 2'
comments: true
excerpt: 'Post displaying api, json, json parse, json stringify, load data, get data, display data on UI, http request status code, network tab, send data to server, object method, bind, call, apply, window, global scope, new keyword, class, this keyword, async, await, setTimeout, setInterval, event loop and datetime'
last_modified_at: 2020-08-10T10:27:01-05:00
categories:
  - JavaScript

tags:
  - JavaScript
  - JavaScript Fundamentals
---

{% include toc %}

# 1 API JSON, SERVER, DATA LOAD, DYNAMIC WEBSITE, HTTP

## 1.1 WHAT IS AN API, THE PURPOSE OF API, GET, POST

[Resources - 1](https://www.youtube.com/watch?v=OVvTv9Hy91Q){:target="\_blank"}  
[Resources - 2](https://medium.com/@9cv9official/what-are-get-post-put-patch-delete-a-walkthrough-with-javascripts-fetch-api-17be31755d28){:target="\_blank"}

## 1.2 JSON, JSON STRUCTURE, PARSE, STRINGIFY, JSON PROPERTIES

```html
<body>
  <h1>JSON</h1>
  <h2>JavaScript Object Notation</h2>
  <script>
    const user = {
      // JS object
      id: 245,
      name: 'Masud',
      age: 26,
      sibling: {
        name: 'Riya',
        favoriteFood: 'pizza',
        age: 22,
      },
      friendAge: [25, 23, 26],
      friends: ['Kamal', 'Jamal', 'Riaj'],
    };

    // when sending
    const userJSON = JSON.stringify(user); // convert JS object to JSON
    console.log(userJSON); // {"id":245,"name":"Masud"} // JSON

    // when receiving
    const userFromJSON = JSON.parse(userJSON); // JSON to JS Object
    console.log(userFromJSON); // {id: 245, name: "Masud"}
  </script>
</body>
```

## 1.3 LOAD DATA, JSON PLACEHOLDER, GET DATA, DISPLAY DATA ON UI

```html
<body>
  <h1>JSON</h1>
  <h2>JavaScript Object Notation</h2>
  <ul id="user-container"></ul>
  <script>
    // https://jsonplaceholder.typicode.com/
    // fetch('https://jsonplaceholder.typicode.com/todos/1')
    //     .then(response => response.json())
    //     .then(json => console.log(json))
    fetch('https://jsonplaceholder.typicode.com/users')
      .then((response) => response.json())
      .then((json) => displayUser(json));

    function displayUser(users) {
      // console.log("users", users);
      const userNames = users.map((user) => user.username);
      // console.log(userNames);

      const ul = document.getElementById('user-container');
      for (let i = 0; i < userNames.length; i++) {
        const user = userNames[i];
        const li = document.createElement('li');
        li.innerText = user;
        ul.appendChild(li);
      }
    }
  </script>
</body>
```

## 1.4 HTTP REQUEST, STATUS CODE, NETWORK TAB, BAD API

```html
<body>
  <h1>JSON</h1>
  <h2>JavaScript Object Notation</h2>
  <ul id="user-container"></ul>
  <script>
    // https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

    fetch('https://jsonplaceholder.typicode.com/people')
      .then((response) => response.json())
      .then((json) => displayUser(json))
      .catch((error) => console.log(error));

    function displayUser(users) {
      // console.log("users", users);
      const userNames = users.map((user) => user.username);
      // console.log(userNames);

      const ul = document.getElementById('user-container');
      for (let i = 0; i < userNames.length; i++) {
        const user = userNames[i];
        const li = document.createElement('li');
        li.innerText = user;
        ul.appendChild(li);
      }
    }
  </script>
</body>
```

## 1.5 SEND DATA TO THE SERVER, HTTP POST METHOD, GET VS POST AND SEND DATA TO SERVER, HTTP POST, JSON STRINGIFY

```html
<body>
  <h1>JSON</h1>
  <h2>JavaScript Object Notation</h2>
  <ul id="user-container"></ul>
  <input type="text" name="" id="title" placeholder="title" />
  <br />
  <input
    type="text"
    name=""
    id="body-content"
    placeholder="post main section"
  />
  <br />
  <button id="submit">Submit</button>
  <script>
    //    const postInfo = {
    //         title: 'fooooooo',
    //         body: 'barrrrrrr',
    //         userId: 1
    //     }

    document.getElementById('submit').addEventListener('click', function () {
      const title = document.getElementById('title').value;
      const bodyContent = document.getElementById('body-content').value;
      // console.log(title, bodyContent)
      const post = {
        title: title,
        body: bodyContent,
      };
      nowPostToServer(post);
    });

    function nowPostToServer(postInfo) {
      fetch('https://jsonplaceholder.typicode.com/posts', {
        method: 'POST',
        body: JSON.stringify(postInfo),
        headers: {
          'Content-type': 'application/json; charset=UTF-8',
        },
      })
        .then((response) => response.json())
        .then((data) => console.log(data))
        .catch((error) => alert('Please try again later'));
    }

    function displayUser(users) {
      // console.log("users", users);
      const userNames = users.map((user) => user.username);
      // console.log(userNames);

      const ul = document.getElementById('user-container');
      for (let i = 0; i < userNames.length; i++) {
        const user = userNames[i];
        const li = document.createElement('li');
        li.innerText = user;
        ul.appendChild(li);
      }
    }
  </script>
</body>
```

[Additional Resources - 1](https://www.w3schools.com/tags/ref_httpmethods.asp){:target="\_blank"}  
[Additional Resources - 2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#:~:text=It%20allows%20you%20to%20associate,some%20point%20in%20the%20future.){:target="\_blank"}

## 1.6 JQUERY AJAX, JQUERY GET, JQUERY POST REACT INSTALL ISSUE

[Resources](https://www.w3schools.com/jquery/jquery_ajax_get_post.asp){:target="\_blank"}

# 2 OBJECT MASTERING, INTERVIEW QUESTION

## 2.1 OBJECT METHOD PROPERTY REVIEW

```javascript
const person = {
  firstName: 'Rahim',
  lastName: 'Udding',
  salary: 15000,
  getFullName: function () {
    // this can be used to access any property of an object
    console.log(this.firstName, this.lastName);
  },
  chargeBill: function (amount) {
    this.salary = this.salary - amount;
    return this.salary;
  },
};

console.log(person);
// if access from outside object, if access inside object use this
console.log(person.firstName); // Rahim // access object property

// call function inside a object
person.chargeBill(150);
console.log(person.salary);
```

## 2.2 OBJECT USE BIND TO BORROW METHOD FROM ANOTHER OBJECT

```javascript
// BINDING

// object - 1
const normalPerson = {
  firstName: 'Albert',
  lastName: 'Einstein',
  salary: 15000,
  getFullName: function () {
    // this can be used to access any property of an object
    console.log(this.firstName, this.lastName);
  },
  chargeBill: function (amount) {
    console.log(this);
    this.salary = this.salary - amount;
    return this.salary;
  },
};

// object - 2
const heroPerson = {
  firstName: 'Blaise',
  lastName: 'Pascal',
  salary: 25000,
};

// object - 3
const friendlyPerson = {
  firstName: 'Enrico',
  lastName: 'Fermi',
  salary: 35000,
};

// normalPerson.chargeBill();

// bind normalPerson with heroPerson
const heroBillCharge = normalPerson.chargeBill.bind(heroPerson);

heroBillCharge(2000);
heroBillCharge(3000);
console.log(heroPerson.salary); // 20000

console.log(normalPerson.salary); // 15000

// bind normalPerson with friendlyPerson
const friendlyChargeBill = normalPerson.chargeBill.bind(friendlyPerson);
friendlyChargeBill(1500);
console.log(friendlyPerson.salary);
```

[Additional Resources - 1](https://www.geeksforgeeks.org/javascript-function-binding/){:target="\_blank"}  
[Additional Resources - 2](https://www.digitalocean.com/community/conceptual_articles/understanding-this-bind-call-and-apply-in-javascript){:target="\_blank"}

## 2.3 DIFFERENCE BETWEEN BIND, CALL AND APPLY

```javascript
// CALL

// object - 1
const manager = {
  firstName: 'Albert',
  lastName: 'Einstein',
  salary: 80000,
  getFullName: function () {
    // this can be used to access any property of an object
    console.log(this.firstName, this.lastName);
  },
  chargeBill: function (amount, tips, tax) {
    console.log(this);
    this.salary = this.salary - amount - tips - tax;
    return this.salary;
  },
};

// object - 2
const assistantManager = {
  firstName: 'Blaise',
  lastName: 'Pascal',
  salary: 70000,
};

// object - 3
const employee = {
  firstName: 'Enrico',
  lastName: 'Fermi',
  salary: 35000,
};

manager.chargeBill.call(assistantManager, 900, 100, 10);
manager.chargeBill.call(assistantManager, 3000, 300, 30);
console.log(assistantManager.salary); // 65660

manager.chargeBill.call(employee, 5000, 500, 50);
console.log(employee.salary); // 29450

// APPLY - in apply array needs to be pass as function arguments
manager.chargeBill.apply(assistantManager, [900, 100, 10]);
manager.chargeBill.apply(assistantManager, [3000, 300, 30]);
console.log(assistantManager.salary); // 65660

manager.chargeBill.apply(employee, [5000, 500, 50]);
console.log(employee.salary); // 29450
```

[Additional Resources - 1](https://medium.com/@omergoldberg/javascript-call-apply-and-bind-e5c27301f7bb){:target="\_blank"}  
[Additional Resources - 2](https://medium.com/@owenyangg/javascript-call-apply-and-bind-explained-to-a-total-noob-63f146684564){:target="\_blank"}  
[Additional Resources - 3](https://www.w3schools.com/js/js_function_call.asphttps://www.w3schools.com/js/js_function_call.asp){:target="\_blank"}  
[Additional Resources - 4](https://www.w3schools.com/js/js_function_apply.asp){:target="\_blank"}

## 2.4 WINDOW, GLOBAL VARIABLE, GLOBAL SCOPE

```html
<body>
  <script>
    // Browser ->devloper tool -> console -> type window
    // document === window.document // true
    // console === window.console // true
    // document.getElementById

    var name = 'Alex';

    function add(num1, num2) {
      var result = num1 + num2;
      // result = num1 + num2; // without var the variable will be implicitly global
      // result = num1 + num2;
      // console.log('result inside', result); // local variable
      console.log('name inside', name);

      function double(num) {
        return num * 2;
      }
      var total = double(result);
      return total;
    }

    // console.log('result outside', result); // throw error because result is not global variable
    console.log('name outside', name);
    // console.log(result); // if result set as implicitly global then it can't be access before calling the function
    var sum = add(13, 21);
    console.log(sum);
    console.log(result);
    // console.log(result);

    // browser console -> name -> will display because it's global
    // browser console -> double -> throw error because it's local
    // browser console -> add -> will display because it's global
  </script>
</body>
```

## 2.5 NEW KEYWORD, CLASS AND OBJECT DIFFERENCE

```javascript
class Person {
  constructor(firstName, lastName, salary) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.salary = salary;
  }
}

// new keyword is used to create object from class
const heroPerson = new Person('Blaise', 'Pascal', 25000);
console.log(heroPerson);
// Person { firstName: 'Blaise', lastName: 'Pascal', salary: 25000 }

const friendlyPerson = new Person('Enrico', 'Fermi', 35000);
console.log(friendlyPerson);
// Person { firstName: 'Enrico', lastName: 'Fermi', salary: 35000 }

// before ES6 function is used to create class, function name start with capital letter indicating it used for class
function Person2(firstName, lastName, salary) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.salary = salary;
}

const oldPerson = new Person2('Grand', 'Papa', 12000);
console.log(oldPerson);
// Person2 { firstName: 'Grand', lastName: 'Papa', salary: 12000 }
```

[Additional Resources](https://www.freecodecamp.org/news/demystifying-javascripts-new-keyword-874df126184c/){:target="\_blank"}

## 2.6 HOW TO UNDERSTAND THE THIS KEYWORD

```html
<body>
  <h1>This is not confused anymore</h1>
  <p onclick="this.innerText = 'Thank you for clicking me'">
    Click for surprise
  </p>

  <script>
    const myObj = {
      name: 'Niels Bohr',
      getFullName: function () {
        console.log(this);
        return 'Mr. ' + this.name;
      },
    };

    // myObj.getFullName();

    const anotherObj = {
      name: 'Sarah Boysen',
    };

    anotherObj.getFullName = myObj.getFullName;
    console.log(anotherObj.getFullName);
    myObj.getFullName(); // left of .function() is the object this will refer
    anotherObj.getFullName(); // left of .function() is the object this will refer

    function add(a, b) {
      console.log(this); // this will return window object
      return a + b;
    }

    add(12, 13); // nothing before function(), means this will refer window

    anotherObj.sum = add;
    anotherObj.sum();

    setTimeout(function () {
      console.log(this);
    }, 1000);
  </script>
</body>
```

[Additional Resources](https://medium.com/better-programming/understanding-the-this-keyword-in-javascript-cb76d4c7c5e8){:target="\_blank"}

## 2.7 ASYNC AWAIT HOW TO USE IT FOR ASYNC CALL

```html
<body>
  <ul id="myList"></ul>

  <script>
    // 26.8 ASYNC AWAIT HOW TO USE IT FOR ASYNC CALL
    /*  async function greet(name) {
            return "Hello " + name;
        }

        const greeting = greet("Mofiz");
        console.log(greeting); // will return promise
        // access using then
        greeting.then(res => console.log(res));

        // arrow function with async
        // const abc = async () =>
        */

    async function loadData() {
      const response = await fetch(
        'https://jsonplaceholder.typicode.com/users'
      );
      const data = await response.json();
      // console.log(data);
      displayData(data);
      return data;
    }

    loadData();

    // function loadData() {
    //     fetch('https://jsonplaceholder.typicode.com/users')
    //         .then(response => response.json())
    //         .then(data => {
    //             displayData(data);
    //         })
    // }
    // loadData();

    function displayData(data) {
      // console.log(data);
      const parentNode = document.getElementById('myList');
      for (let i = 0; i < data.length; i++) {
        const user = data[i];
        const item = document.createElement('li');

        item.innerText = user.name;
        parentNode.append(item);
      }
    }
  </script>
</body>
```

[Additional Resources - 1](https://javascript.info/async-await){:target="\_blank"}  
[Additional Resources - 2](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await){:target="\_blank"}  
[Additional Resources - 3](https://medium.com/javascript-in-plain-english/async-await-javascript-5038668ec6eb){:target="\_blank"}  
[Additional Resources - 4](https://medium.com/javascript-in-plain-english/truly-understanding-promises-in-javascript-cb31ee487860){:target="\_blank"}

## 2.8 ASYNCHRONOUS JAVASCRIPT SETTIMEOUT, SETINTERVAL

```javascript
function doSomething() {
  console.log(3333);
}

console.log(2222);
// doSomething();
// SetTimeOut run only once
setTimeout(doSomething, 3000);

setTimeout(function () {
  console.log('Lazy and waiting');
}, 5000);

// arrow function
setTimeout(() => {
  console.log('Lazy and waiting....');
}, 5000);

console.log(4444);

// setInterval run repeatedly
setInterval(() => {
  console.log('Set interval');
}, 1000);
```

## 2.9 HOW JAVASCRIPT WORKS EVENT LOOP STACK AND QUEUE

[Resources -1](https://www.youtube.com/watch?v=8aGhZQkoFbQ&vl=en){:target="\_blank"}  
[Resources -2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop){:target="\_blank"}

## 2.10 JAVASCRIPT DATETIME TIMEZONE AND OTHERS

```javascript
// browser console
let start = new Date();
let sum = 0;
for (let i = 0; i < 100000000; i++) {
  sum++;
}
let end = new Date();
console.log('Time elapsed', end - start, sum);
```

[Additional Resources -1](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date){:target="\_blank"}  
[Additional Resources -2](https://momentjs.com/){:target="\_blank"}

<!-- ```javascript
``` -->

<!-- ```html
<body>
  <script src="script.js"></script>
</body>
``` -->
