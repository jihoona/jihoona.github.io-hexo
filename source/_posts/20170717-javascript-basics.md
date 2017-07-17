---
title: 자바스크립트 기초
categories:
  - Javascript
date: 2017-07-17 19:48:58
tags:
  - javasciprt
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

## Tips

1. <script type="text/javascript" src="script.js" async></script>
  - `<script type="text/javascript" src="script.js"></script>`로 스크립트 파일을 불러오면 브라우저는 다 불러오기 전까지 다음 단계로 진행하지 않는다. <head> 안에서 스크립트 파일들을 불러오면 곧바로 <body>의 내용이 처리되지 않아 사용자에게 동작하지 않는 페이지인 것처럼 보일 수 있다. 이를 보완하기 위해 `async`, `defer` 속성을 지원하게 되었는데 IE 10 미만에서는 지원하지 않기 때문에 <body> 태그의 마지막 부분에서 스크립트 파일들을 호출하기도 한다.
  - [Where should I put <script> tags in HTML markup?  (StackOverflow)](https://stackoverflow.com/questions/436411/where-should-i-put-script-tags-in-html-markup)
  - [Remove Render-Blocking JavaScript (Google Developers)](https://developers.google.com/speed/docs/insights/BlockingJS)
