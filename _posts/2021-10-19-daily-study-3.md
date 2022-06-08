---
layout: post
title: "[javascript] 10-19 자바스크립트 스터디 - 객체지향-Object"
date:   2021-10-19 21:30:00 +0900
tags:
  - javascript
---

# 10-18~10-19 [객체지향-Object]

# Object

1. 값을 저장하는 기본적인 단위
    - 자바스크립트에서는 값을 저장하는 기본적인 단위로 Object를 사용한다.
    - 제일 기본적인 형태를 가지고 있는 객체이
2. 객체지향 프로그래밍에 있어서의 의의
3. 상속예제를 통해서 모든 객체는 Object 객체의 property를 가지고 있다는걸 알 수 있다. 
모든 객체들의 원형이 될 수 있다. 
Object 객체의 prototype을 이용해, Object 객체 속성을 갖고 있는 모든 객체가 prototype 기반 메소드 및 프로퍼티들을 사용할 수 있다.

# Object 메뉴얼 읽는 법

## Object 메뉴얼 사이트

- MDN을 통해서 볼 수 있다.
    - specifications, browser compatibility를 체크해서 사용해야함!
- Object.methods와 Object.prototype.methods의 차이는?
    - 쉽게 Object.func()는 Object만 사용할 수있는 함수고 Object.prototype.func() 그 Obejct를 상속받는 객체들이 사용할 수 있는 함수다라고
    - ex) Object.keys(), Object.prototype.toString()
    
    Object.keys(인자) 인자로 바로 줌. Object 라는 키워드는 생성자 함수, 
    
    ```jsx
    // 함수는 자바스크립트에서 객체이기 때문에 
    // Object라는 생성자 함수의 keys로
    Object.keys = function(){} // 이렇게 정의가 되어있을 것임
    ```
    
    prototype이 있는건 어떤 객체를 만들고, 어떤 식별자.toString()...
    
    ```jsx
    // 생성자 함수를 이용해서 new Object라고 실행시키는 순간에
    // Array라는 객체를 생성할 때도 javascript 에서 내부적 & 암시적으로 Object 부모 속성을 다 받아옴.
    // 객체는 prototype이라는 특수 프로퍼티에 저장되있는 메소드/프로퍼티를 원형으로 하는 객체가 생성
    
    Object.prototype.toString = function(){}
    
    // 그래서 var arr = new Object(); arr.toString()해야함
    ```
    

# Object 객체의 확장

### 어느 객체에서나 사용할 수 있는 메소드를 만드는 방법

- 자기가 만들고자하는 대략적인 인상을 가지고 코딩을 하게되면, 나중에 사용하기 불편한 api나 변수 객체를 만들게 될 수 있다
- '어떻게 사용될 것인가'를 먼저 생각하고 만들어서 구현하면 좋을 것이다. 기능의 원리적인 측면보다 어떻게 사용되고 어떤 취지의 기능인가를 먼저 생각하고 구현하는게 좋음...

```jsx
// for 문은 foreach, for문 말고도 for in 문을 이용해 열거할 수 있다.
for(var name in this){
	// this의 타입이 Object이면...

	// this의 타입이 Array이면...
}
```

- 모든 객체에 영향을 주고싶어서 객체의 확장을 하는거지만, 모든 객체에 영향을 주기 때문에 위험성 또한 같이 존재한다. (위험성 강의: [https://www.inflearn.com/course/지바스크립트-언어-기본/lecture/2576?tab=note](https://www.inflearn.com/course/%EC%A7%80%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%96%B8%EC%96%B4-%EA%B8%B0%EB%B3%B8/lecture/2576?tab=note))
- object.prototype에 메소드나 프로퍼티를 추가한다는 행위는 신중하게 해야할 행위. **어떠한 위험이 있는지 분명하게 이해한 상태에서** 그것이 최소의 단위에서.. 광역객체에서 영향을 주지 않게끔 사용해야한다.
- `a.hasOwnProperty()`
    
    오브젝트가 갖고있는 메소드인데 property에 해당이 댐. 자신의 프로퍼티에 '직접적으로' 해당이 되고 있느냐를 판별해줌 
    
    상속받고있는 property와 자기자신이 직접 해당하고있는 property인지 판별해주는 좋은 메소드