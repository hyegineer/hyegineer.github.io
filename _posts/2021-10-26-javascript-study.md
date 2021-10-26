---
layout: post
title: "[javascript] 10-26 객체지향 프로그래밍 js 코드"
date:   2021-10-26 23:35:00 +0900
tags:
  - javascript
---

# 객체지향프로그래밍

```jsx
var grades = {
	'list': {'egoing': 10, 'k8805': 8}, // 객체 안의 객체 가능.
	'show': function(){
		alert('hello world');
		alert(this); // this는 약속되어있는 , 정해져있는 변수.
								// 함수가 속해있는 객체를 가르키는 변수임
		console.log(this.list);
	}	// 함수도 일종의 값이고. 값도 객체 안에 저장될 수 있기때문에 객체에 함수가 저장될 수 있음.
}

var grades = { 
    'list': {'egoing': 10, 'k8805': 8, 'sorialgi': 80},
    'show': function(){
        for(var name in this.list){
            console.log(name);
        }
    }
} // grades라는 객체는 list라는 데이터와 show라는 함수를 그룹핑(categorizing) 해서 가지고 있다. 
// 이런것들을 객체지향 프로그래밍이라고 함. 연관되어있는 값(데이터), 연관되어있는 처리를 묶은 프로그래밍기법이 객체지향프로그래밍. 

console.log(grades.list) // {egoing: 10, k8805: 8};
grades.show(); // grades객체 안의 show 함수호출
grades['show']();
```