---
layout: post
title: "[javascript] javascript 집공부"
date:   2020-08-26 23:10:00 +0900
tags:
  - javascript
---

### arguments

arguments는 자바스크립트에서 약속된 용어
함수에 전달된 인자를 유사배열로 처리해준다. (진짜 배열은 아니고, 배열이랑 비슷한 역할을 하기에 유사배열이라 말함)

그래서 함수에 전달됀 인자를 체크하기 위해 arguments.length로 체크한다.

```javascript

function ex(){
    console.log('함수의 length'+ex.length);
    console.log('전달 인자의 length'+arguments.length);
}
ex(); // 0, 0

function ex1(arg1){
    console.log('함수의 length'+ex1.length);
    console.log('전달 인자의 length'+arguments.length);
}
ex1('num01', 'num02'); // 1, 2

function ex2(arg1, arg2){
    console.log('함수의 length'+ex2.length);
    console.log('전달 인자의 length'+arguments.length);
}
ex2('num01', 'num02'); // 2, 2
```

이 arguments의 효용은 어디서 나오냐면,
함수의 length와 arguments의 length를 비교해 일치할 때만 실행되는 식으로 하거나
함수의 인자가 의도된 갯수만큼 전달되지않을 경우 경고를 띄우는 식으로 해서
의도를 벗어나지않게 함수를 사용할 수 있게끔 유도할 수 있다.
