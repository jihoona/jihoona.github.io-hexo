---
title: 마크다운 참고자료
date: 2017-07-12 23:43:18
categories:
- Etc
tags:
- markdown
- cheatsheet
- blog
---

> 앞으로 블로그 글 작성을 위해 [GitHub Markdown](https://guides.github.com/features/mastering-markdown)을 참고하여 정리했습니다.

# Markdown Syntax

## Headers

```
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

# H1
## H2
### H3
...

## Emphasis

```
*italics*, _italics_
**bold**, __bold__
**bold and __italics__**
~~strike~~
```
*italics*, _italics_
**bold**, __bold__
**bold and __italics__**
~~strike~~

## Lists

```
1. One
2. Two
  1. One
3. Three
  * content

- title
  - content
```

1. One
2. Two
  1. One
3. Three
  * content

- title
  - content

## Images

```
![Unsplash Source](Unsplash Source.jpg)
```
![Unsplash Source](Unsplash Source.jpg)

## Links

```
[GitHub Markdown](https://guides.github.com/features/mastering-markdown)
```

[GitHub Markdown](https://guides.github.com/features/mastering-markdown)

## Blockquotes

```
> A block quotation (also known as a long quotation or extract) is a quotation in a written document that is set off from the main text as a paragraph, or block of text, and typically distinguished visually using indentation and a different typeface or smaller size font. - In [Wikipedia](https://en.wikipedia.org/wiki/Block_quotation)
```

> A block quotation (also known as a long quotation or extract) is a quotation in a written document that is set off from the main text as a paragraph, or block of text, and typically distinguished visually using indentation and a different typeface or smaller size font. - In [Wikipedia](https://en.wikipedia.org/wiki/Block_quotation)

## Inline code

```
Hello, `This is inline code.`
```

Hello, `This is inline code.`

## Horizontal Rule

```
---
```
---

## Syntax highlighting

```
```java
public void printHelloWorld() {
  System.out.println("Hello, World!");
}
``````

```java
public void printHelloWorld() {
  System.out.println("Hello, World!");
}
```

## Tables

```
항목1 | 가운데 정렬 | 오른쪽 정렬
---- | :----: | ----:
첫번째 | 두번째 | 참고
세번째 | 네번째 | 비고
```

항목1 | 가운데 정렬 | 오른쪽 정렬
---- | :----: | ----:
첫번째 | 두번째 | 참고
세번째 | 네번째 | 비고
