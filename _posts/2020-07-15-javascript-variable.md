---
layout: post
title: "[javascript] 변수와 유효범위 scope"
date:   2020-07-15 15:00:00 +0900
tags:
  - javascript
---

#### 전역변수와 지역변수

함수에 포함되지 않은 스크립트 제일 바깥영역에서 선언한 변수를 전역변수라고 하는데,
전역변수 (global variable)를 만드는건 최대한 지양해야함
→ 규모가 커질 수록 변수의 혼용 충돌이 일어날 가능성이 높아진다. 
협업을 할 때, 다른 라이브러리를 쓸 때 같은 변수이름으로 오버라이트되는 불상사가 생길 수 있음
이런 불상사를 예방하기 위해 전역변수 쓰는 일은 최대한 없어야함

지역변수 (local variable)는 함수 내에 선언이 되는 변수이며, 
이 지역변수는 해당 함수 안에서만 사용할 수 있음

```javascript
  var x = 'global'; // global variable

  function alertFn(){
    var x = 'local';
  }

  alertFn();
  console.log(x); // global
```

```javascript
  var x = 'global'; // global variable

  function alertFn(){
    var x = 'local';
    x = 'change';
  }

  alertFn();
  console.log(x); // global
```
→ 함수 안에서 선언된 x 변수는 지역변수로서 함수 내부에서 재할당이 이루어진다.

#### 스코프체인

```javascript
  var x = 'global';

  function alertFn(){
    x = 'change';
  }

  alertFn();
  console.log(x); // change
```
→ 함수 안에서 변수는 전역변수를 참조해 재할당이 이루어지기 때문에 change로 바뀜
`x = 'change'`를 했을 때 전역변수가 바뀌는데, 자바스크립트는 변수의 범위를 호출한 함수의 지역스코프부터
전역변수들이 있는 전역스코프까지 넓혀가며 찾음
이렇게 꼬리를 물고 계속 범위를 넓혀나가면서 찾는 관계를 `스코프체인` 이라고 함

#### 정적 유효범위 (lexical scoping)

스코프는 함수를 호출할 때가 아니라 선언할 때 생김.

```javascript
  var i = 5;

  function a(){
    var i = 10; // 지역변수
    b();
    // 2. b 함수 내부의 i가 a 내부의 지역변수 10에 접근하는건 아니다. (선언할 때 유효범위가 생기기 때문에) 
    // 4. 함수 b가 호출(사용)될 때가 아니고 정의될 때 i에는 전역변수가 사용됌. => 요런걸 정적유효범위라고 함
  }

  function b(){
    document.write(i);
  }
  // 1. b 함수 내부에 i라고 하는 지역변수가 존재하는지 확인 후, 바깥범위의 전역변수를 찾음
  // 3. 함수 b가 선언된 시점에서 i는 전역변수가 사용된다.

  a(); // 출력은 5
```

함수가 정의되는 시점에서 변수를 바라보게 된다면, 누가 사용하건 상관없이 똑같은 결과를 갖고오기 때문에
lexical scoping

##### 출처
[생활코딩 유튜브: JavaScript - 유효범위](https://www.youtube.com/watch?time_continue=315&v=kfIlysJAkBA&feature=emb_title)

[제로초님 블로그: 함수의 범위(scope)](https://www.zerocho.com/category/JavaScript/post/5740531574288ebc5f2ba97e)