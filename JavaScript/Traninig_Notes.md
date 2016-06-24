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

### DOM: Document Object Model
