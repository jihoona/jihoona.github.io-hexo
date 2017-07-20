---
title: 자바스크립트 기초
date: 2017-07-17 19:48:58
categories:
- Javascript
tags:
- javascript
- basic
---

# Javascript Basics

## Primitive data types

### Numbers

```javascript
5
-1
12.1

3+10  // 13
1/10  // 0.1
10%3  // 1
```

### Strings

```javascript
"Hello World"
'Hello World'

"abc"+"def"           // abcdef
"This is \"a dog\""   // This is "a dog"
"Hello World".length  // 11
"hello"[0]            // h
"hi\\".length         // 3
```

### Booleans

```javascript
true
false
```

### Null and undefined

**Null**: It can be assigned to a variable as a representation of no value. (Object)

**Undefined**: A variable has been declared but has not yet been assigned a value. (A Type itself)

```javascript
// null
var player = "Jihoon";
player = null;

// undefined
var name;
```
- [What is the difference between null and undefined in JavaScript? (StackOverflow)](https://stackoverflow.com/questions/5076944/what-is-the-difference-between-null-and-undefined-in-javascript)

## Variables

```javascript
var name = "Jihoon";
var number = 111;
var isNumber = true;

var name = "Jihoon";
"Hello " + name       // Hello Jihoon

var num = 100;
num + 11 + 10         // 121

// Dynamically Typed, and Weakly Typed.
var name = "Jihoon";
name = 50;
```

- [Is JavaScript an untyped language? (StackOverflow)](https://stackoverflow.com/questions/964910/is-javascript-an-untyped-language)

## Useful built-in methods

- alert("Message");
- console.log("Message");
- prompt("What is your name?");
	- var userName = prompt("What is your name?");

## Control Flow

### Boolean logic

When x = 5,

Example | Result | Description
--------|--------|------
x > 10  | false |
x >= 5 | true  |
x < -10 | false |
x == "5"  | true  | Equal to
x != "a"  | true  | Not equal to
x === "5" | false | Equal value and type
x !== "5" | true  | Not equal value and equal type

```javascript
var x = 10;
x == "10";  // ture
x === "10"; // false

var y = null;
y == undefined  // true
y === undefined // false

true == "1"       // true
0 === false       // true
null == undefined // true
NaN == NaN        // false (not a number)
```

### Logical operators

Operator | Name
---------|------
&&       | AND
{% raw %}||{% endraw %}     | OR
!        | NOT

```javascript
var x = 10;
var y = "a";

y === "b" || x >= 10  // true

x = 3;
y = 8;

!(x == "3" || x === y) && !(y != 8 && x <= y) // false


!"Hello World"  // false
!!""            // false
!!null          // false
!!0             // false
!!NaN           // false
!!-1            // true


var str = "";
var msg = "hello"
var isFunny = "false"

!((str || msg  && isFunny)) // false
```

- [Truthy (MDN)](https://developer.mozilla.org/ko/docs/Glossary/Truthy)
- [Falsy (MDN)](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)

### Conditionals

```javascript
if (age < 18) {
	console.log("Sorry, you are not old enough.");
} else if (age < 21) {
	console.log("You can enter, but cannot drink.");
} else {
	console.log("Come on in. You can drink.");
}


var guess = prompt("Guess a number");

if (Number(guess) === 10) {
	console.log("Right!");
}
```

- [JavaScript Number() Function](https://www.w3schools.com/jsref/jsref_number.asp)

### Loops

```javascript
var count = 1;

while (count < 4) {
	console.log("count is: " + count);
	count++;
}

// Output
// count is: 1
// count is: 2
// count is: 3
```

```javascript
for (var i = 0; i < 4; i++) {
	console.log("count is: " + i);
}

// Output
// count is: 1
// count is: 2
// count is: 3

var str = "ahceclwlxo";

for (var i = 1; i < str.length; i+=2) {
	console.log(str[i]);
}

// Output
// h
// e
// l
// l
// o
```

## Functions

```javascript
//function declaration
function capitalize(str) {
	return str.charAt(0).toUpperCase() + str.slice(1);
}

capitalize("paris");
// Output
// Paris

// function expression
var capitalize = function(str) {
	return str.charAt(0).toUpperCase() + str.slice(1);
}

capitalize("paris");
// Output
// Paris
```

```javascript
var doStep = function nextStep(step) {
	if (step > 0) {
		console.log("Step! : " + this.name);
		nextStep.call(this, step - 1);
	}
};
var person = {name: "stranger", walk: doStep};
person.walk(5);
```

```javascript
var unikys = {
	 yell: function () {
		 console.log("YELL!");
	 }
 };
 unikys.yell();
```

```javascript
 var callback = function (e) {
	 console.log("Mouse clicked!");
 };
 document.body.addEventListener("click", callback);

 var func = new Function("a", "b", "return a+b;");
 console.log(func(5, 6) === 11);
```

- [[속깊은 자바스크립트 강좌] function declaration vs function expression 차이점](http://unikys.tistory.com/305)

## Scope

```javascript
function doMath() {
	var x = 1;
	console.log(x);
}

doMath();
// Output: 1
console.log(x);
// Error, x is not defined.
```

```javascript
var y = 1;
function doSomething() {
	y = 10;
	console.log(y);
}

doSomething();
// Output: 10
console.log(y);
// Output: 10;
```

```javascript
var phrase = "Hi there!";
function doSomething() {
	var phrase = "Goodbye!";
	console.log(phrase);
}

doSomething();
// Output: GoodBye!
console.log(phrase);
// Output: Hi there!
```

## Higher order functions

A higher-order function is a function that can take another function as an argument, or that returns a function as a result.

- First Class Functions
	- Functions in JavaScript are treated as objects.

```javascript
// Taking Functions as Arguments.
var proveIt = function() {
	alert("you triggered " + this.id);
};
document.getElementById("clicker").addEventListener("click", proveIt);

// Returning Functions as Results.
var snakify = function(text) {
	return text.replace(/millenials/ig, "Snake People");
};
console.log(snakify("The Millenials are always up to something."));
// Output: The Snake People are always up to something.
```

```javascript
var attitude = function(original, replacement, source) {
	return function(source) {
		return source.replace(original, replacement);
	};
};

var snakify = attitude(/millenials/ig, "Snake People");
var hippify = attitude(/baby boomers/ig, "Aging Hippies");

console.log(snakify("The Millenials are always up to something."));
// Output: The Snake People are always up to something.
console.log(hippify("The Baby Boomers just look the other way."));
// Output: The Aging Hippies just look the other way.
```

- [Higher-Order Functions in JavaScript](https://www.sitepoint.com/higher-order-functions-javascript/)

## Arrays

```javascript
var friends = ["Charlie", "Liz", "David", "Mattias"];

console.log(friends[0]);
// Output: Charlie

friends[0] = "Amelie";  // Edit data
friends[4] = "Andrea"   // Add data

// Initialize an empty array
var friends = [];
var friends = new Array();

var random_collection = [4, true, "abc", null];
console.log(random_collection.length);
// Output: 4
```

### Methods

```javascript
var colors = ["red", "orange", "yellow"];

colors.push("green");     // ["red", "orange", "yellow", "green"]
var color = colors.pop(); // ["red", "orange", "yellow"]
console.log(color);
// Output: Green

colors.unshift("blue"); // ["blue", "red", "orange", "yellow"]
colors.shift();         // ["red", "orange", "yellow"]


var index = colors.indexOf("red");
console.log(index);
// Output: 0
console.log(colors.indexOf("black"))
// Output: -1

var carColors = colors.slice(0, 2);
console.log(carColors);
// Output: ["red", "orange"]
console.log(colors);
// Output: ["red", "orange", "yellow"]
```

### Iteration

```javascript
var colors = ["red", "orange", "yellow"];

for (var i=0; i < colors.length; i++) {
	console.log(colors[i]);
}
// Output
// red
// orange
// yellow

colors.forEach(function(color)) {
	console.log(color);
}
// Output
// red
// orange
// yellow

function printColor(color) {
	console.log(color);
}
colors.forEach(printColor);
// Output
// red
// orange
// yellow

var count = 0;
while (count < colors.length) {
	console.log(colors[count]);
	count++;
}
// Output
// red
// orange
// yellow


Array.prototype.myForEach = function(func) {
	for (var i =0; i < this.length; i++) {
		func(this[i]);
	}
}
colors.myForEach(function(name){
	console.log(name);
});
// Output
// red
// orange
// yellow
```

- [Array.prototype.forEach() (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

## Objects

```javascript
// Array
var person = ["Cindy", 32, "Missoula"];

// Object: store data in key-value pairs.
var person = {
	name: "Cindy",
	age: 32,
	city: "Missoula"
}

console.log(persion["name"]); // Output: Cindy
console.log(person.name);     // Output: Cindy

person["age"] += 1;
person.city = "London";
```

```javascript
// Create objects
var person = {};
person.name = "Travis";
person.age = 20;

var person = {
	name: "Travis",
	age: 20
}

var person = new Object();
person.name = "Travis";
person.age = 20;

var junkObject = {
	age: 20,
	color: "blue",
	friends: ["Travis", "Cindy"],
	pet: {
		species: "Dog",
		age: 2
	}
};
```

```javascript
someObject.1blah    // Invalid: can't start with number.
someObject["1blah"] // Valid

var str = "name";
someObject.str  // Invalid
someObject[str] // Valid

someObject.fav color    //Invalid
someObject["fav color"] // Valid
```

```javascript
// Object with method
var obj = {
	name: "Chunk",
	age: 45,
	isCool: false,
	friends: ["bob", "tina"],
	add: function(x, y) {
		return x+y;
	}
}

// Like namespace
var dog = {
	speak: function(){
		return "WOOF!";
	}
}

var cat = {
	speak: function(){
		return "MEOW!";
	}
}

dog.speak();  // Output: WOOF!
cat.speak();  // Output: MEOW!
```

```javascript
// This

var comments = {};

comments.data = ["Good Job!", "Bye", "Hey"];

comments.print = function() {
	this.data.forEach(function(el){
		console.log(el);
	});
}

comments.print();
// Output
// Good Job!
// Bye
// Hey
```

## DOM

- Document Object Model
	- The interface between Javascript and HTML+CSS
	- The browser turns every HTML tags into a Javascript object.

### Selectors

```html
<body>
	<h1>Hello</h1>
	<h1>Goodbye</h1>
	<ul>
		<li id="highlight">List Item 1</li>
		<li class="bolded">List Item 2</li>
		<li class="bolded">List Item 3</li>
	</ul>
</body>
```

```javascript
var tag = document.getElementById("highlight");
console.log(tag); // Output: <li id="highlight">List Item 1</li>

var tags = document.getElementsByClassName("bolded");
console.log(tags[0]);  // Output: <li class="bolded">List Item 2</li>

tags = document.getElementsByTagName("li");
console.log(tags[0]); // Output: <li id="highlight">List Item 1</li>

// Returns the first element that matches a given CSS-style selector.
tag = document.querySelector("#highlight");
tag = document.querySelector(".bolded");
tag = document.querySelector("h1");

tags = document.querySelectorAll("h1");
console.log(tags[0]);  // Output: <h1>Hello</h1>
```

### Manipulating style

Recommended for styles to be defined in a separate file or files.

```css
.some-class {
	color: blue;
	border: 10px solid red;
}
```

```javascript
// This is bad.
var tag = document.getElementById("highlight");
tag.style.color = "blue";
tag.style.border = "10px solid red";

//This is better.
var tag = document.getElementById("highlight");
tag.classList.add("some-class");
```

### Manipulating text and content

```html
<p>
	This is an <string>awesome</string> paragraph
</p>
```

```javascript
var tag = document.querySelector("p");
console.log(tag.textContent)  
// Output: This is an awesome paragraph
console.log(tag.innerHTML)	
// Output: This is an <stong>awesome</string> paragraph

```

### Manipulating attributes

```html
<a href="www.google.com">I am a link</a>
<img src="logo.png">
```

```javascript
var link = document.querySelector("a");
console.log(link.getAttribute("href")); // Output: www.google.com

var img = document.querySelecotr("img");
img.setAttribute("src", "corgi.png");
```

### Events

```javascript
var button = document.querySelector("button");
button.addEventListener("click", function() {
	console.log("Clicked the button!");
});

var lis = document.querySelectorAll("li");
for (var i=0; i < lis.length; i++) {
	lis[i].addEventListener("click", function(){
		this.style.color = "pink";
	});
}
```

- [What is the difference between “change” and “input” event for an INPUT element (StackOverflow)](https://stackoverflow.com/questions/17047497/what-is-the-difference-between-change-and-input-event-for-an-input-element/17047607#17047607)

## Tips

1. `<script type="text/javascript" src="script.js" async></script>`
	- `<head>`안에서 `<script type="text/javascript" src="script.js"></script>`로 스크립트 파일을 불러오면 다 불러오기 전까지 다음 코드로 진행하지 않거나 HTML 엘리먼트를 선택하는 스크립트가 있다면 오류가 발생한다. 이를 보완하기 위해 `async`, `defer` 속성을 지원하게 되었으며 IE10 미만에서는 지원하지 않기 때문에 <body> 태그의 마지막 부분에서 스크립트 파일들을 호출하기도 한다.
	- [Where should I put script tags in HTML markup?  (StackOverflow)](https://stackoverflow.com/questions/436411/where-should-i-put-script-tags-in-html-markup)
	- [Remove Render-Blocking JavaScript (Google Developers)](https://developers.google.com/speed/docs/insights/BlockingJS)
