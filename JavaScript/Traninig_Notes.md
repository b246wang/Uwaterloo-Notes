#### Lesson One: Play with JavaScript at the console of the browser. E.g. alert("Hello World");
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
- Variable:
```javascript
var year; //undefined, no-type generic variable
year = "Hello"; //Or 'Hello', true
var x = 200;
var X = 300; //case-sensitive
var yera = 2011, month = 10, day = 31;
```
- Conditional Code
```javascript
if ( condition ) { //e.g. ( a < 50 ), ( c === 99 ) will explain this later.
  //code goes here
  
} else {
  // something
  if ( ) {
    //others
  }
}
```
- Arithmetic operators: same as other languages(===, !==).
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

##### Finish with 2.operators
