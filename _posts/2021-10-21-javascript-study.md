---
layout: post
title: "[javascript] 10-21 자바스크립트 스터디 - Array 관련 methods"
date:   2021-10-21 18:30:00 +0900
tags:
  - javascript
---

# Javascript Array 관련 method

## 추가

array.push()

```jsx
var li = ['a', 'b', 'c', 'd'];
li.push('e');
alert(li); // ['a', 'b', 'c', 'd', 'e'];
```

array.concat()

```jsx
var li = ['a','b','c','d','e'];
li = li.concat(['f','g']);
alert(li); // ['a', 'b', 'c', 'd', 'e', 'f', 'g'];
```

array.unshift() 첫번째원소로 추가하고 index(색인) 1씩 증가

```jsx
var li = ['a','b','c','d','e'];
li.unshift('z');
alert(li); // ['z', 'a', 'b', 'c', 'd', 'e'];
```

array.splice(index, howmany, element1... elementN)

```jsx
var li = ['a','b','c','d','e'];
li.splice(1, 0, 'z'); // 가운데 0 이면 삭제를 안하고 index가 1인 원소 앞에 element를 추가하겠다.
alert(li); // ['a', 'z', 'b', 'c', 'd', 'e'];

var li = ['a', 'b', 'c', 'd', 'e'];
li.splice(1, 1, 'z'); // 가운데 1 이면 1만큼 삭제를 하고 element를 추가하겠다.
alert(li); // ['a', 'z', 'c', 'd', 'e'];
```

## 삭제

array.shift() 첫번째 원소제거

```jsx
var li = ['a','b','c','d','e'];
li.shift();
alert(li); // ['b', 'c', 'd', 'e'];
```

array.pop() 끝점 원소제거

```jsx
var li = ['a','b','c','d','e'];
li.pop();
alert(li); // ['a', 'b', 'c', 'd'];
```

array.sort()

```jsx
var li = ['a','b','c','d','e'];
li.pop();
alert(li); // ['a', 'b', 'c', 'd'];
```