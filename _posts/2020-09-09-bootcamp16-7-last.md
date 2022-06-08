---
layout: post
title: "[javascript] javascript boot camp 16기 일곱번째 수업 운영체제 등"
date:   2020-09-09 21:45:00 +0900
tags:
  - javascript
---

### 데이터 포맷, JSON

JSON(JavaScript Object Notation)은 속성-값 쌍으로 이루어진 데이터 오브젝트를 전달하기 위해 인간이 읽을 수 있는 텍스트를 사용하는 개방형 표준 포맷이다. 

javascript 객체 일부 유형의 형식을 데이터포맷으로 만든거. <br>
손쉽게 다른쪽에서 읽을 수 있는. 모든 컴퓨터가 읽을 수 있는 plain text 파일로 읽을 수 있는 형식

```javascript
let person = {
  name: '홍길동',
  age: 25,
  familly: ['아빠', '엄마', '형1', '형2']
}; // 이거는 자바스크립트 객체지 JSON이 아니다. 

let json = JSON.stringify(person);
// 다른 컴퓨터각 읽을 수 있는 문자열 즉 JSON으로 바꿔야한다

console.log(person);
console.log(json);
```

```javascript

let json = `{"name":"홍길동","age":25,"familly":["아빠","엄마","형1","형2"]}`;

let person = JSON.parse(json);
// 이건 자바스크립트에서 읽을 수 있는 객체 형태로 바꾸는 메소드다.

console.log(person);

```

JSON 파일은 반드시 key를 더블쿼터("")로 감싸줘야한다.<br>
오른쪽 value값은 number, String, Boolean, Array, Object, null 만 지원<br>

요것이 객체리터럴과 다른 점. 대표적으로 *함수가 없다<br>
밖으로 나갔을때는 데이터로써의 의미가 없고 다른 컴퓨터에서도<br>
실행할 수 없다. 제일 극명하게 다른 점. 제이슨은 함수를 지원하지않습니다. 

제이슨이 만들어진 이유는 <br>
자바스크립트의 객체를 json 포맷으로 손쉽게 내보내서<br>
데이터를 사용할 수 있도록 하기위한것. 자바스크립트 객체를 위한 포맷
<br><br>
## json 중요한 이유

server and client > cs 기법<br>
clinet 로부터 요청받은 데이터를 서빙(응답)하는 소프트웨어: server<br>
server 한테 요구하는 client<br>

client software / server software 

웹서버 <- 웹클라이언트

client 는 종류가 많을 수 있다. web, app, android, iphone...<br>
가장 많은 software client는 web client가 많다.

예전엔 서버가 제공하는 데이터유형이 많았는데<br>
web client가 워낙에 많다보니 그냥 json 포맷을 많이 씀.<br>
서버가 다 json 포맷을 반환하니깐 그냥 기본 통신규격 데이터를 json으로 대동단결...

단점은 텍스트포맷이기에 비대해지고, 자료형도 한계되있어서 그렇게 좋은건 아니지만,,, javascript client를 개발하는 입장에선 json이 대세니께 배우면 됍니다.

앞서 말한것들을 직렬화라고 함. 
JSON.stringfy 같은걸 직렬화 방식이라고 합니다. 통일 시켜주는~? ㅎㅎ

> 직렬화(直列化) 또는 시리얼라이제이션(serialization)은 컴퓨터 과학의 데이터 스토리지 문맥에서 데이터 구조나 오브젝트 상태를 동일하거나 다른 컴퓨터 환경에 저장(이를테면 파일이나 메모리 버퍼에서, 또는 네트워크 연결 링크 간 전송)하고 나중에 재구성할 수 있는 포맷으로 변환하는 과정이다.

cs개념 알고싶으면 한번 자세히 살펴보기~
