---
layout: post
title: "[javascript] 10-18 자바스크립트 스터디 - 표준내장객체"
date:   2021-10-18 23:30:00 +0900
tags:
  - javascript
---

# 10-18 [객체지향-표준내장객체의 확장]

# 표준내장객체 (standard built-in object)

- 자바스크립트가 우리에게 제공하는 객체
    - Object
    - Function
    - Array
    - String
    - Boolean
    - Number
    - Math
    - Date
    - RegExp
    
    → 자바스크립트가 동작하는 **호스트 환경**에서 제공하는 api는 이것보다 더 많을 수 있음.
    
    → 자바스크립트를 통해서 소프트웨어를 제어한다는건 
    자바스크립트 코어 엔진이 제공하는 api와 호스트환경이 제공하는 api를 통해서 소프트웨어를 만든다.
    
- 사용자 정의 객체는 표준내장객체와 대비되는 개념

# 내장객체에 우리가 어떤 기능을 추가하는 방법,
세련된 방법으로 추가하는 방법

[배열의 확장 (Array)]

- prototype을 이용해서 내장객체에 우리가 원하는 메소드를 추가할 수도 있고 가공할 수 있다.