---
title: 'Browser and JavaScript Debug'
comments: true
excerpt: 'Post displaying how browser work, dom tree, render tree, alert, confirmation, prompt, url components, document location, history api, dev tools, cookies, local storage, session storage, javascript debug, basic cmd command'
last_modified_at: 2020-08-12T10:27:01-05:00
categories:
  - JavaScript
tags:
  - JavaScript
  - Browser
  - Dev Tools
---

{% include toc %}

# 1 HOW BROWSER WORKS, BROWSER API AND METHODS

## 1.1 CONTENTEDITABLE, LIVE EDIT

```javascript
// browser console
document.body.contentEditable = true; // website content will be editable
```

## 1.2 HOW BROWSER WORKS, DOM TREE, RENDER TREE

[Resources - 1](https://javascript.info/dom-nodes){:target="\_blank"}  
[Resources - 2](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction){:target="\_blank"}  
[Resources - 3](https://medium.com/jspoint/how-the-browser-renders-a-web-page-dom-cssom-and-rendering-df10531c9969){:target="\_blank"}  
[Resources - 4](https://medium.com/@gneutzling/the-rendering-process-of-a-web-page-78e05a6749dc){:target="\_blank"}

## 1.3 WEBSITE ALERT, CONFIRMATION, PROMPT TO COLLECT DATA

```javascript
// browser console
// alert
alert('This is an alert'); // use case: warning, notification

// confirm
confirm('Are you coming in the picnic'); // take confirmation from user

// prompt
prompt('Tell me your name'); // take input from user
```

[Additional Resources](https://javascript.info/alert-prompt-confirm){:target="\_blank"}

## 1.4 URL, URL PARTS, QUERY STRING, HASH, SUBDOMAIN

**URL: Uniform Resources Locator**  
example: https://reactjs.org/

**URL Part:**  
example: https://reactjs.org/tutorial/tutorial.html

**Query String:**  
example: https://www.youtube.com/watch?v=pQeFxdT3FGY&t=120s

**Hash:**  
example: https://reactjs.org/tutorial/tutorial.html#what-is-react

**SUbdomain:**  
example: support.wordpress.com

[Additional Resources](https://www.tutorialrepublic.com/html-tutorial/html-url.php){:target="\_blank"}

## 1.5 DOCUMENT LOCATION, ACCESS HREF, HASH, ASSIGN

```javascript
// browser console
window.location;
// origin, protocol, host, hostname, hash, href, assign etc
location.reload(); // reload the location

location.assign('dsfaisal.com'); // assign url
location.href('dsfaisal.com'); // link to url
```

[Additional Resources](https://developer.mozilla.org/en-US/docs/Web/API/Window/location){:target="\_blank"}

## 1.6 HISTORY API, BACK, FORWARD, GO, HISTORY LENGTH

```javascript
// browser console
// history
// history.back()
// history.forward()
// history.go(3)
```

[Additional Resources](https://developer.mozilla.org/en-US/docs/Web/API/History_API){:target="\_blank"}

## 1.7 COOKIES, DEV TOOL APPLICATION TAB, COOKIES AT SERVER

```javascript
// browser > inspect > Application > cookies
```

[Additional Resources](https://developer.mozilla.org/en-US/docs/Web/API/Document/cookie){:target="\_blank"}

## 1.8 LOCAL STORAGE, SESSION STORAGE, EDIT STORAGE INFORMATION

```javascript
// browser > inspect > Application > Local Storage
// local storage or persistent storage, save in browser

// browser > inspect > Application > Session Storage
// stay until browser tab is closed

// browser console
// localStorage
// localStorage.setItem("isSubscribed", true);

// sessionStorage.setItem("isPlaying", true);
```

[Additional Resources](https://javascript.info/localstorage){:target="\_blank"}

## 1.9 BROWSER CLEAR CACHE, CHROME EXTENSION, WEB STORE, RESTART BROWSER

```javascript
// browser > inspect
// Click and hold mouse right button on browser reload button icon and
// select "Empty and cache and hard reload"
```

# 2 JAVASCRIPT DEBUG, WEB DEBUG, DEV TOOL MASTERING

## 2.1 COMMAND LINE TOOLS

<img src="../../images/post-img/2020-08-12-browser-and-javascript-debug-1.PNG" class="align-left" alt="cmd command"/>

<img src="../../images/post-img/2020-08-12-browser-and-javascript-debug-2.PNG" class="align-left" alt="cmd command"/>

## 2.2 MODULE OVERVIEW, SALARY APP OVERVIEW, GIT CLONE ISSUES

Browser inspect > Click on **Selector** button

- Change/ add/ delete element text
- Add new class
- Copy > Copy Styles
- Break on
- ctrl + F to find element with class/ id

Click on **Device toolbar** button

- Set breakpoint
- Set device
- Online/ offline
- Show rulers
- Capture Screenshot

## 2.3 EDIT CSS STYLE LIVE, HOVER CLASS, CSS BOX MODEL, EVENT HANDLER

Browser > select element, Click on Styles

- Can find the source css file location with line number
- Own style + Parent Style
- Test style, use up/ down arrow to change px value:
  element.style {margin-left: 20px; color: orange;}
- Uncheck style
- .cls to check classes/ add classes
- :hov to check hover effect
- Filter- margin, color

Click on Computed

- Check final property
- Box model- change margin/ padding/ border/ width value to check

Click on Event Listener

- Check different JS handler
- Uncheck Framework listener to exclude library related handler

Click DOM Breakpoints

Click accessibility

- to help people with disability/ color blind

## 2.4 SOURCES TAB, BREAK POINT, CALL STACK, CONSOLE TABLE

Browser inspect > console

- check is there any error or not

Lets say if you don't have source code  
Browser inspect > Sources

- ctrl + F, use search to search specific element
- ctrl+shift+o
- Set Breakpoint, reload browser and check, call stack
  press Esc to open console
  example: data
  example: console.table(data[0].values)
- Set breakpoint for local variable, add Watch, then check
  example: data[4]

- ctrl+shift+F for search in all files

## 2.5 CONSOLE TAB, PRESERVE LOG, ERROR LOG, CONSOLE API

browser console,check errors, check all All Levels

[Dev Tools Console](https://developers.google.com/web/tools/chrome-devtools/console){:target="\_blank"}

## 2.6 NETWORK TAB, REQUEST METHOD, HEADER, RESPONSE TYPE

[Dev Tools Network](https://developers.google.com/web/tools/chrome-devtools/network){:target="\_blank"}

## 2.7 PERFORMANCE TAB, MEMORY TAB, AUDIT, APPLICATION TAB

[Dev Tools Evaluate Performance](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance){:target="\_blank"}  
[Dev Tools Memory](https://developers.google.com/web/tools/chrome-devtools/memory-problems){:target="\_blank"}  
[Audit - chrome lighthouse tool](https://developers.google.com/web/tools/lighthouse){:target="\_blank"}  
[Chrome Dev Tools](https://developers.google.com/web/tools/chrome-devtools){:target="\_blank"}  
[Dev Tools Tips](https://umaar.com/dev-tips/){:target="\_blank"}  
[50 Dev tool tips and tricks](https://www.youtube.com/watch?v=oYvtsHu6GmY){:target="\_blank"}

<!-- ```javascript
``` -->

<!-- [Additional Resources - 1](){:target="\_blank"} -->

<!-- ```html
<body>
  <script src="script.js"></script>
</body>
``` -->
