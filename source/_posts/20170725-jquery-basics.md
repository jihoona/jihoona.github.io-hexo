---
title: jQuery 기초
categories:
  - Javascript
date: 2017-07-25 16:52:56
tags:
  - javascript
  - basic
  - jquery
---

# jQuery Basics

> jQuery is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript. - [jQuery.com](http://jquery.com)

- **Why use jQuery?**
  - Fixes "broken" DOM API
  - Brevity and clarity
  - Ease of use
  - Cross-browser support
  - Ajax
  - Lot's of people use jQuery.
- **Why not use jQuery?**
  - The DOM API is no longer "broken".
  - It doesn't do anything you can't do on your own.
  - It's an unnecessary dependency.
  - Performance
  - Lot's of people are moving away from jQuery.

## Add jQuery

```html
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
</head>
```

## Selectors

Select elements with $("selector")

```javascript
// all img tags
$("img")

// all element with class "sale"
$(".sale")

// element with id "bonus"
$("#bonus")

// all a tags inside of li's
$("li a")
```

## Manipulating style

$("selector").css(property, value)

```javascript
$("#special").css("border", "2px solid red");


var styles = {
  border: "2px solid red",
  fontWeight: "bold"
}
$("#special").css(styles);

$("div:first-of-type").css("color", "pink");
```

## Common methods

### Text and html

```html
<div class="demo-container">
  <div class="content">Demo content</div>
  <ul>
    <li>first</li>
    <li>second</li>
  </ul>
</div>
```

**Get and set combined text contents**

```javascript
$("content").text();
// Output: Demo content first second

$("li").text("Changed");
// Output
// <div class="demo-container">
//   <div class="content">Demo content</div>
//   <ul>
//     <li>Changed</li>
//     <li>Changed</li>
//   </ul>
// </div>
```

**Get and set HTML contents**

```javascript
$("ul").html();
// Output: <li>first</li>  <li>second</li>

$("ul").html("<li>a new item</li>");
// Output
// <div class="demo-container">
//   <div class="content">Demo content</div>
//   <ul>
//     <li>a new item</li>
//   </ul>
// </div>
```

### Attr and val

```html
<img src="http://www.gstatic.com/webp/gallery/1.jpg">
```

**Get and Set the value of an attribute for the first element.**

```javascript
$("img").attr("src");
// Output: http://www.gstatic.com/webp/gallery/1.jpg

$("img").attr("title", "This is sample");
// Output
// <img src="http://www.gstatic.com/webp/gallery/1.jpg" title="This is sample">
```

- [attr() vs prop() (jQuery APi)](http://api.jquery.com/attr/)
  - To retrieve and change DOM properties such as the checked, selected, or disabled state of form elements, use the .prop() method. (related to boolean attributes)

**Get and set the values of the first form elements.**

```javascript
$("input").val();
$("input").val("put something");
```

### Manipulating class

**Add and remove classes**

```javascript
$("p").addClass("correct");
$("p").removeClass("correct");
$("p").toggleClass("correct");
```

## Events

### Click

```javascript
$("#submit").click(function() {
  console.log("Complete submit");
});

$("#submit").click(function() {
  $(this).css("background", "blue");
});
```

- [jQuery: What's the difference between '$(this)' and 'this'? (StackOverflow)](https://stackoverflow.com/questions/1051782/jquery-whats-the-difference-between-this-and-this)
  - Basically every time you get a set of elements back jQuery turns it into a jQuery object.

### Keypress

```javascript
$("input").keypress(function(event){
  if(event.which === 13) {
    alert("You hit enter");
  }
});
```

- [jQuery – Difference between Keypress and Keydown Events (HowToDoInJava)](http://howtodoinjava.com/scripting/jquery/jquery-difference-between-keypress-and-keydown-events/)

### On

```javascript
$("submit").on("click", function(){
  console.log("Clicked");
});

$("submit").on("dblclick", function(){
  console.log("Clicked");
}); 
```

- click() only adds listeners for existing element.
- on() will add listeners for all potential future elements.
- [Difference between .on('click') vs .click() (StackOverflow)](https://stackoverflow.com/questions/9122078/difference-between-onclick-vs-click)

## Effects
 
```javascript
$("button").on("click", function() {
  $("div").fadeOut(1000, function() {
    console.log("Fade Completed!"); // Callback function
    $(this).remove();
  });
});

$("button").on("click", function() {
  $("div").slideUp();
});
```
