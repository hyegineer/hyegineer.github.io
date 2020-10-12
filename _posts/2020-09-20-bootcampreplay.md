---
layout: post
title: "[javascript] javascript boot camp 16기 8번째 수업 복습하기"
date:   2020-09-20 22:30:00 +0900
tags:
  - javascript
  - 네트워크
  - 비동기통신
---

9월 14일자 8번째 수업은 회사야근때문에 살짝 지각을 해서 앞부분을 놓쳤다.<br>
ㅠㅠ 그래서 주말에 다시 복습을 하기로! 밤이 늦었지만 그래도 하고 자면 맘이 편할테니~ <br>

### 구글 네트워크 탭

서버에게 자원들을 요청한다. <br>
이미지같은걸 클릭해서 우측 탭메뉴에 header 들어가면 여러가지 정보가 나와있다. <br>

1. Request URL
`URL`은 여러가지로 구성되어있는데, <br>
https://는 hypertext transfer protocol secure <br>
각자 컴퓨터가 가지고 있는 IP 주소를 도메인 소프트웨어가 의미가 부여됀 도메인주소로 바꿔줌<br>
그 자원을 request Method GET방식으로 달라고 하는것.

http 프로토콜의 가장 큰 특징은 비동기 통신이다. <br>

### 비동기통신 ? 동기통신 ?

1. 동기통신<br><br>
- 대상에게 전화를 걸고 연결이 된 후 데이터(말)를 주고받음<br>
말을 하지않아도 상대방이 연결되어있는걸 앎. <br>
그렇다고 통신사가 끊진 않음. <br>
모든 데이터(말)가 주고받는게 끝났을 때 연결이 끊기는거<br><br>

장점: 대상이 항상 연결되어있다고 확신할 수 있음. <br>
단점: 한번 연결되면 데이터를 주고받지않음에도 불구하고 연결을 유지해야함<br>
연결을 유지하는 입장에서는 데이터가 낭비고, <br>
최대의 갯수가 20,000개였다 싶으면 20,001개일때 연결이 끊김, 즉 자원과 비용이 많이 듦<br>
<br>
2. 비동기통신<br><br>
데이터를 주고받을때만 연결하고 데이터 주고받았으면 끊어버림<br>
요청한 데이터만 주고받고난다음에 바로 끊음<br>

단점: 요청할 데이터가 여러개 있으면 요청하고 받고 끊기는게 자주 일어남<br>
서버가 받는 입장에선 바로 요청한거만 주고 끊어버림<br>
ex)아이디 패스워드 줄테니깐 로그인시켜줘 - OK<br>
나 마이페이지 들어갈거야 - 회원정보 X<br>
<br>
client를 기억하고있지못해서 기억하기위한 특별한 방법이 필요함<br>
<br>
엄청 큰 장점: 똑같은 컴터를 가지고 20,000개를 처리할 수 있다면<br>
10곱절은 더 처리할 수 있다<br>
웹은 불특정다수가 접속하기때문에 웹의 기본 프로토콜은 비동기로 디자인 되어있다.
<br><br>
그래서 웹의 모든 자원들을 하나하나 다 요청하고 응답받는걸로 되어있음 <br>
`오버헤드 개념` <br>
자원효율성이 좋기때문에 비동기식으로 요청을 하고 응답을 받는다.<br>

### XMLHttpRequest

XMLHttpRequset는 서버에 데이터를 요청하기 위한 네트워크 API임. <br>
이 인스턴스의 메소드로 open이 있는데 이걸로 방식, 경로, 동기or비동기 여부를 세팅한다.
```javascript
let request = new XMLHttpRequest();

request.open('GET', '/api/books'); // 1. 세번째 인자는 기본이 false (비동기), true로 하면 오류남. 하면안되는 방법!

request.addEventListener('load', function() {
  if (request.status >= 200 && request.status < 400) {
    let books = JSON.parse(request.responseText);
    let bookList = document.querySelector('#book-list');

    books.forEach(book => {
      let li = document.createElement('li');

      li.innerText = `${book.title} - ${book.writer}`;

      bookList.appendChild(li);
    });
  } else {
    alert('문제가 발생했습니다');
  }
}); // 3. send로 요청을 받은 데이터를 처리하는건 함수로 처리하기때문에
// 넽웤 API가 제공해주는 이벤트리스너를 이용해 함수를 부른다.

request.addEventListener('error', function() {
  alert('네트워크 연결을 확인해 주세요.');
}); // 4. 실패할 수도 있음. 응답이 정해진 시간을 넘어서면 timeout으로...

request.send(); // 2. 실제로 요청을 보내는건 send 메소드다.
```