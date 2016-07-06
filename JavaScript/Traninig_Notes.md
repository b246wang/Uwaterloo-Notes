## Lesson One: Play with JavaScript at the console of the browser. E.g. alert("Hello World");
- Play with Javascript (inline code): `<script>alert("Hello World");</script>`
- JavaScript is **CASE-Sensitive**! But not whitespaces.
- Good practice: always have semicolon at the end of a line.
- //this is a comment
- /* 
  this is a block of comment 
  */
- **The JS codes are executed as soon as the Browser sees it, position of scripts does matter!!**
- Put JS codes in a seperate .js file
  - Reusable: don't need to copy the script to all HTML files.
  - Clean HTML file
  - Usage: `<script src="root/yourfile.js"></script>`
  - Rule of Thumb: Style sheet at the top, JS code at the bottom of HTML file.

#### Variable:
```javascript
var year; //undefined, no-type generic variable
year = "Hello"; //Or 'Hello', true
var x = 200;
var X = 300; //case-sensitive
var yera = 2011, month = 10, day = 31;
```
#### Conditional Code
```javascript
if ( condition ) { //e.g. ( a < 50 ), ( c === 99 ) will explain this later.
  //code goes here
  // curly braces are not necessary for one line code.
} else {
  // something
  if ( ) {
    //others
  }
}
```
#### Arithmetic operators: same as other languages(===, !==).
- Equality: **===** means **strict equality**, same value and same type, example:
```javascript
var a = 5;
var b = "5";

if ( a === b ) { //what will happen if using "==" instead?
  alert("number a equals string b");
} else {
  alert("number a not equals string b");
} //if using "==", no type check and it finds both are 5 and return true.
```

- Reminder: Difference between ++a and a++: `var a = 5; alert(++a); alert(a++);`
- Ternary: `condition?true:false`

## Lesson Two: More Syntax
- log & debug: `console.log("See this on Console");`, `console.debug("Debug Info");`
- info & warn & error: `console.info("More Info");`, `console.warn("Warning");`, `console.error("Error Msg");`

#### Loop: while, do-while, for, break, continue
```javascript
var a = 1;
while ( a < 10 ) { //also try do-while loop
  console.log(a);
  a++; //without this line, this is an infinite loop
}

for ( var i = 1; i < 10; i++ ) {
  // do something
  if (i == 10) {
    break;
  }
}
```

#### function: not necessary but good: define the function before use it.
- If pass in extra parameters to the function, it will **ignore** them.
- If pass in less parameters, missing parameters are regarded as **undefined**
```javascript
function exampleFunction( x, y ) {
  var newVar = x * y; //newVar only lives in this function. It is undefined outside.
  console.log(newVar);
  return newVar; //**optional return statement!**
}
```

#### Arrays: array has methods reverse(), join(), sort()...
```javascript
var myArray = [];
myArray[0] = 100;
myArray[1] = true;
myArray[2] = "Cat"
var myArray2 = [100, true, "Cat"];

var multiValues = new Array(); // or var a = Array(); All arrays have dynamic length
var myArrayOfLinks = document.getElementsByTagName("a"); //grab all <a ref="xxx"> tags
```

#### Numbers: 
- **All JavaScript numbers are 64-bit floating point numbers.**
```javascript
var foo = 5;
var bar = 5;
console.log(foo + bar); // 10
bar = "5";
console.log(foo + bar); // 55 (concatenation, if found one string, treat all as strings)
bar = "b"; console.log(foo * bar); // NaN: Not a Number
var myNumber = Number(bar); //it tries to convert it to a number, if can't, return NaN
if ( !isNaN(myNumber) ) { //if it is a number
  console.log("It's a number.");
}
```
- Use Math object: `Math.round()`, `.max()`, `.min()`, `.PI`, `.random()`, `.sqrt()`, `.log()`

#### Strings: Works with double quotes", single quotes'
- Need to escape quotes inside quotes: `var phrase = "He said \"I'm a hero!\"";`
- Strings are objects: 
  - `phrase.length`, `phrase.toUpperCase()`, `var words = phrase.split(" ");`
  - `if ( phrase.indexOf("hero") == -1 ) console.log("This string doesn't exist.")`
  - Smilimar but not same functions: `phrase.slice(4, 8)`, `.substring(0, 100)`, `.substr(start, length)`
  - Different Case not Equal: `if (str1.toLowerCase() == str2.toLowerCase())`

#### Dates:
- All numbers are normal except Month... Month: between 0 to 11. 0 is January...
- today.getMonth() => 0-11, getFullYear() => YYYY, getDate() => 1-31, getDay() => 0-6
- .getHours() => 0-23, .getTime() => milliseconds since 1/1/1970
- .setMonth(5), .setFullYear(2012), .setDay(0)
```javascript
var today = new Date(); //current date
// year, month, day
var ymd = new Date(2000, 1, 1);
// year, month, day, hours, minutes, seconds
var ymd = new Date(2015, 1, 3, 1, 15, 25);

// Comparing Dates:
var date1 = new Date(2000, 0, 1);
var date2 = new Date(2000, 0, 1);
if (date1 == date2) {...} // FALSE! different objects
if (date1.getTime() == date2.getTime() ) {...} // True! Equal milliseconds since 1970.1.1
```

#### Objects:
```javascript
// regular declaration
var player = new Object();
player.name = "Brody";
player.score = "99999999";
player.rank = 1;

// shorthand
var player1 = { name: "Jimmy", score: 0, rank: 9999999 };
function showPlayerDetails() {
  console.log(this.name + " has score " + this.score + " and rank " + this.rank);
}
player1.showDetails = showPlayerDetails;
player.showDetails = showPlayerDetails; // Little object-oriented concept... function pointer? XD
```

## Lesson Three: DOM, Document Object Model
- Document: The page
- Object: Any individual "thing". e.g. page title, HTML tags
- Model: Set of terms (Imagine tree-structure of HTML): HTML -> body -> ul -> li, we call them nodes.
- You can access anywhere in the HTML structure with DOM!
- E.g.
  - Get the title text
  - Get the third paragraph
  - Get the third link in the menu and set its CSS
  - Get all `<li>` elements in the last unordered list
  - Find the image with an id of "logo" and move it 40 pixels to the right...

- Each tag is a node, and all attributes and texts inside are nodes.
- when you get an node, you can access its parents/children nodes.
```javascript
//there are 12 types of nodes of DOM, but we are interested in 3 nodes now:
Node.ELEMENT_NODE == 1
Node.ATTRIBUTE_NODE == 2
Node.TEXT_NODE == 3

// Retrieving an element by ID
var myElement = document.getElementById("myId");
var myListItems = document.getElementsByTagName("li"); //an array of all <li> elements, empty if no li exists.
console.log("This is an element of type: ", myElement.nodeType ); //see types of node above
console.log("the Inner HTML is ", myElement.innerHTML ); //inner HTML is the text enclosed
console.log("Child nodes: ", myElement.childNodes.length);

//example:
<ul id="abc">
  <li> aaa </li>
  <li> bbb </li>
  <li> bbb </li>
</ul>
var myList = document.getElementById("abc");
var listsInMyList = myList.getElementByTagName("li"); //get all li nodes in current ul nodes!
```

#### Working with DOM:
- Modify attribute
```javascript
<div id="mainContent">.........</div>
var mainContent = document.getElementById("mainContent");
mainContent.setAttribute("align", "right"); // add/change the align attribute of current node
```

- Create DOM content and add it to the document & Create Text Nodes
```javascript
<ul id="abc">........</ul>
var myElement = document.getElementById("abc");
var myNewElement = document.createElement("li");
myElement.appendChild(myNewElement);

var myText = document.createTextNode("New list item");
myNewElement.appendChild(myText);//or do this: myNewElement.innerHTML = "New list item";
// Don't want to append as the last child?
var secondItem = myElement.getElementByTagName("li")[1];
myElement.insertBefore(myNewElement, secondItem); //add the newElement as second child
```

## Lesson Four: Event, events happen all the time!

- Handling Events
  - method 1: `<button onclick="alert('Hello, world!');">Button</button>`
  - method 2: `element.event = function() { something; };`
    - e.g. `myElement.onclick = function() { something; };`
    - why semicolon at the end? This is an entire statement! Not a function declaration.
  - method 3: `document.addEventListener('click', myFunction, false);`
    - Advantage: You can add eventListener multiple times to one element.
    - Trouble: IE8 or previous doesn't support `addEvetListener` but `attachEvent` instead. Need to detect browser...
      - You can use jQuery library functions to do cross-browser actions.

#### onclick & onload:
  - If you put file.js at the bottom of HTML, everything will likely work fine
  - If you put file.js at the top of HTML, `myElement.onclick = function()` might not work since the page is not loaded and you cannot even get myElement here
    - solution: put all the EventHandler functions in `window.onload = function() {put here};`, so all the functions will run after the page is loaded

#### onblur & onfocus:
- onfocus: when you click into the place
- onblur: when you leave the place
```javascript
// imagine you got this form element in HTML
<input type="text" value="enter your email" name="email" id="email" tabindex="20" />

var emailField = document.getElementById("email");
emailField.onfocus = function() {
  if ( emailField.value == "enter your email") {
    emailField.value = "";
  }
};

emailField.onblur = function() {
  if ( emailField.value == "") {
    emailField.value = "enter your email";
  }
};
```

#### Timers: time is in milliseconds (set and clear)
- setTimeout:
```javascript
function alertMessage() {
  alert("5 seconds earlier you opened this page");
}

setTimeout(alertMessage, 5000);
```
- setInterval:
```javascript
var myImage = document.getElementById("image");
var imageFiles = ["_images/image1.jpg", "_images/image2.jpg", "_images/image3.jpg", "_images/image4.jpg"]
var imageIndex = 0;
function changeImage() {
  myImage.setAttribute("src", imageFiles[imageIndex]);
  imageIndex++;
  if (imageIndex >= imageFiles.length) {
    imageIndex = 0;
  }
}

var intervalHandle = setInterval(changeImage, 2000); //change the image file every 2 seconds

myImage.onclick = function() {
  clearInterval(intervalHandle); //this can stop the image from changing
};
```

- Debug javascript:
  - Use browser console (source in Chrome, for example) to set breakpoints
  - Use step in, step out and step over to debug as other IDEs

#### Smarter Forms with JavaScript:
- We can use events to listen the entire form
- Small tip: 
```javascript
<form id="frmContact" name="frmContact" method="post" action="thanks.htm">
//You can use the name attribute of the form to access the form element
document.forms.frmContact
```

- Textfields:
  - main property: `myTextField.value`
  - useful events: `onfocus`, `onblur`, `onchange`, `onkeypress`, `onkeyup`, `onkeydown`

- Checkboxes & Radio Buttons:
  - main property: `myCheckBox.checked`(boolean)
  - useful events: `onclick`, `onchange`

- Lists:
  - main properties: `mySelect.type` (select-one or select-multiple)
    - for select-one: `mySelect.selectedIndex`
    - for select-multiple: `mySelect.options[x].selected`(boolean)
  - useful events: `onchange`

- Form:
  - useful event: `onsubmit` (`return false` to stop submitting, e.g. validation, or return true to sumbit the form)

## Lesson Five: UI enhancement & Best Practices
#### CSS and JavaScript

- Use JavaScript to modify the CSS of contents
  - `myElement.style.width = "230px";`
  - Remember to use camelCase for CSS with hyphens(-)
```javascript
#example {
  width: 230px;
  color: #fff;
  font-weight: bold;
  background-color: #193742;
}
// equivalent Javascript:
myElement.style.width = "230px";
myElement.style.color = "#fff";
myElement.style.fontWeight = "bold";
myElement.style.backgroundColor = "#193742";
```

#### Class:
- If you defined the CSS for a class in CSS file, you can use JavaScript to set the element to that class!
- Set the class: `myElement.className = "someClassDefinedInCSS";`
- Clear the class: `myElement.className = "";`

#### Javascript Style Guidelines:
- Use camelCase for variables and functions, e.g. DOM functions
- Use uppercase for first letter of Objects, e.g. Date, Math
- General practices: curly braces at the same line of keyword, define functions before use them...

#### Minifying Javascript:
- Often you can see javascript files with all words on a single line, and all variables are simplified to a,b,c...
- That's because the codes are minified to reduce file size and increase downloading speed
- Minifying tools: JSMin, YUI Compressor, Google Closure Compiler
- JavaScript quality checker: "jslint.com"
- Linking to Multiple JavaScript files:
  - Each time you have a line `script src="myscript.js"></script>`, the browser will send a request to download this file
  - So combining javascript files to have as few script files as possible

#### Introduction to jQuery: prefer jQuery $
- jQuery("whatToFind").someAction; OR alias form: $("whatToFind").someAction;
```javascript
document.getElementById("myDiv").className = "highlight";
// with jQuery:
jQuery("#myDiv").addClass("highlight");
jQuery(".someClass") //select the class
jQuery("p") //select all elements with <p> tag
jQuery("li") //select all elements with <li> tag

//find the last li
jQuery("li:last").addClass("highlight");
// find all paragraphs that contain "packages"
$("p:contains('packages')").addClass("highlight");


// EFFECTS

// hide all paragraphs
$("p").hide(4000);
$("p").fadeOut(4000);


// EVENTS

// simple click
$("#pageID").click(function() {
  $("#pageID").text("You clicked me!");
}); //set text instead of going to text node in JavaScript

// add $(this) to refer to current element
$("h2").click(function() {
  $(this).text("You clicked me!");
}); //just change the current clicked <h2>'s text

// Page load events - instead of window.onload()
// window.onload() cannot be called multiple times since it will replace the previous one
$(document).ready(function () {
  $("#pageID").text("The DOM is fully loaded.");
});
$(document).ready(function () {
  $("h1").css("color", "red");
}); // you can call .ready() multiple times!
```

#### Content Distribution Network(CDN)
- A better & faster way to download jQuery: Several companies allow you to link to libraries from their servers
  - e.g. google: `<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.0.0/jquery.min.js"></script>`
  - Why? 
    - improved speed/redundancy
    - improved bandwith
    - improved parallel downloads(from other servers and your server at the same time)
    - caching benefits: others also downloaded jQuery from google, so the don't need to download it again.

## Lesson Six: HTML5 and JavaScript

#### HTML5 new features
- HTML5 supports video/audio and offline storage, so JavaScript has more methods to manage these things
- JavaScript Additions: `var c = document.getElementsByClassName("myClass");`
- Web Workers:
```javascript
var worker = new Worker("anotherjavascriptfile.js");

// get ready to receive messages from the worker
worker.onmessage = function(e) {
  console.log("The worker called me!");
};

// send messages to the worker
worker.postMessage("firstFunction");
```
- Feature Detection
```javascript
if ( document.getElementByClassName ) {
  // it exists, we can use it
  // ...
} else {
  // it doesn't exist on this browser
}
```

#### Using Strict Mode: a higher standard of JavaScript codes
- Add `"use strict";` at the first line of JavaScript file
- In regular mode, many JavaScript errors/warnings are tolerated, but strict mode will report them

#### JavaScript to avoid
- avoid document.write: `document.write("Here is some <em>important</em> content");`, if it is called after the page was fully loaded, it will destroy the previous page and show it's content only
- avoid browser sniffing: `if (navigator.appName == "Microsoft Internet Explorer')`
  - it is very old code to detect the type of browser
- avoid EVAL function: it will execute the code in variables...
  - `var a = "alert('Hello');"`
  - `eval( a );`
- avoid Pseudo-protocols
  - `<a href="javascript:someFunction()">this</a>`
  - Normally, we use http://, but not javascript:
  - it mixes HTML with JavaScript code

#### Regular Expressions are built in the language: validation
- `^` at the start of the string
- `$` at the end of the string
- `+` once or more
- `*` zero or more
- `?` zero or one
- `|` either,or
- `.` any character
- `\w` alphanumeric or underscore(_)
- `\b` word boundary
- `[abc]`, `[0-9]` range of characters to choose

#### AJAX: Asynchronous JavaScript and XML
- Make more responsive site: retreive the data and update the page without reloading it
  1. Create the request
  2. Deal with any response
```javascript
var myRequest = new XMLHttpRequest();

// be prepared to receive response
myRequest.onreadystatechange = function() { 
  if (myRequest.readyState === 4) { // why 4?
    var p = document.createElement("p");
    var t = document.createTextNode(myRequest.responseText);
    p.appendChild(t);
    document.getElementById("mainContent").appendChild(p); //append the content to the page
  }
};

// Then configure and send
myRequest.open("GET", "http://mysite.com/somedata.php", true);
myRequest.send(null);
```

#### Objects and Prototypes
```javascript
// create Objects:
var playerBrody = { name: "Brody", score: 9999, rank: 1 };
playerBrody.gameType = "MMORPG";
playerBrody.logScore = function() {
  console.log(this.score);
};
playerBrody.logScore();
playerJimmy = { name: "Bob", highscore: 50, level: "d" };


// formalizing objects with constructors
function Player(n) {
  this.name = n;
  this.score = s;
  this.rank = r;
}

// prototype: attach the function to the object constructor
Player.prototype.logInfo = function() {
  console.log(this.name + ":" this.score);
}

// now you can crete objects and call same methods of the prototype!
var Brody = new Player("Brody", 9999, 1);
var Jimmy = new Player("Jimmy", 1, 100);
Brody.logInfo();
Jimmy.logInfo();
```

That's it. Go exploring.
