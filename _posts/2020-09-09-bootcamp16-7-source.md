---
layout: post
title: "[javascript] javascript boot camp 16기 일곱번째 수업 배열 메소드 참고자료"
date:   2020-09-09 21:30:00 +0900
tags:
  - javascript
---

### 배열 객체 순회 함수

```javascript

const idol = [
  { age: 10, type: "남성", name: "방탄소년단" },
  { age: 5, type: "남성", name: "샤이니" },
  { age: 14, type: "남성", name: "동방신기" },
  { age: 2, type: "여성", name: "2NE1" }
];

function showIdol(dol, idx) {
  console.log(`${idx + 1} - ${dol.name}`);
}

function forEach(array, fn) {
  for (let index = 0; index < array.length; index++) {
    fn(array[index], index, array);
  }
}

function map(array, fn) {
  // 맵은 차곡차곡 쌓는다..

  const newArray = [];

  for (let index = 0; index < array.length; index++) {
    newArray.push(fn(array[index], index, array));
  }

  return newArray;
  // 받았던 배열을 순회하고, 순회한 갯수만큼 push 하고 있기때문에
  // 처음받았던 배열의 갯수와, 리턴하는 배열의 갯수는 같음.

  // 이걸 뭐에 쓰나?
  // <li>동방신기...</li>
}

forEach(idol, showIdol);

// map은
// [ ... ] => map => [ ... ] 왼쪽이 3개면 나오는 애도 3개
// [ ... ] => map(함수) => [ ... ]
// 입력값을 조작해서 새로운 값으로 변경하는 일들을 함
// ex: {name: '동방신기'} => <li>동방신기</li>

const html = map(idol, function (idol) {
  // 리턴한걸 맵함수가 모아서 돌려준다

  return `<li>${idol.name}</li>`;
});

const html2 = map(idol, (idol) => `<div>${idol.name}</div>`);

console.log(html);
console.log(html2);

// filter 의 차이
// 원래 있는 배열보다 같거나 작을 수 있따.

function filter(array, fn) {
  const newArray = [];

  for (let index = 0; index < array.length; index++) {
    if (fn(array[index], index, array) === true) {
      // 이때 함수가 반환이 되는데 클로저 발생!
      newArray.push(array[index]);
    }
    // 함수한테 넘겨주는 데이터는 map 과 똑같다.
    // 함수가 리턴하는 값을 무조건 참이냐 거짓이냐 두가지로 판별한다
  }

  return newArray;
}

const boy = filter(idol, (idol) => {
  if (idol.type === "남성") {
    return true;
  } else {
    return false;
  }
});

const boy1 = filter(idol, (idol) => idol.type === "남성");
const boy2 = filter(idol, (idol) => idol.type === "여성");

// 들여다보면 데이터와 코드가 결합되어있기대문에 중복이 발생.
// type 이 gender로 바뀐다면 두개를 다 바꿔야하네!
// 어떻게 중복을 제거할 수 있을까?

console.log(boy);
console.log(boy1, boy2);

// type -> gender바꾸는 수고를 덜이기 위해, 중복을 줄이기 위해 간단한 함수를 만들자

function filterOperation(key) {
  return (idol) => idol.type === key;
  // 클로저에 잡혀서 함수가 반환되도 쓸수있는거임 여성 남성 등
}

const filterOp = (key) => (idol) => idol.type === key;

const ex1 = filter(idol, filterOperation("여성"));
const ex2 = filter(idol, filterOperation("남성"));
const ex3 = filter(idol, filterOp("여성"));

console.log(ex1);
console.log(ex2);
console.log(ex3);

// 이렇듯 함수를 반환하는 테크닉은 많이 쓰인다.

// 맵과 필터들은 반환값이 배열이기에 바로 연결 가능.
let LIlist = idol
  .filter((dol) => dol.type === "남성")
  .map((dol) => `<span>${dol.name}</span>`)
  .join("");
// 메소드 체이닝 왜냐면 .filter는 어차피 배열을 반환하니깐.
// 그 배열가지고 다시 map으로 하고, join 으로 마무리 (문자열로 반환을 하고..)
// join의 전달인자는 구분자를 결정짓는다. 안쓰고 join()을 쓰면
// default로 ,(쉼표)를 쓰는데, 그래서 join('') 이렇게 빈값을 넣는다.

console.log(LIlist);

let hyejin = "정혜진";
// 백틱을 활용한 템플릿 리터럴 표기법은 멀티라인도 지원한다.
console.log(`안녕하세요. ${hyejin}씨~`);
console.log(`안녕하세요. 
${hyejin}씨~`); // 요로코롬 멀티라인 가능하단 말씀~

```

```javascript
// 원본배열에 가공을 안하고 복사할 수 있는 메소드들
console.log(idol.slice());
console.log(idol.map((x) => x));
console.log([...idol]); // ES6추가구문: ...을 쓰면 풀어헤쳐준다

// 쓰기 복잡하니깐 그냥 Array.from()으로 포장해서 쓰는가보다.

function foo() {
  console.log(arguments);
  // 유사배열일뿐 배열은 아님.
}

function bar() {
  arguments.forEach((n) => console.log(n));
  // 이렇게 유사배열은 배열에 쓸수있는 메소드가 사용이 안됌
}

function bar2() {
  Array.from(arguments).forEach((n) => console.log(n));
  // 그래서 이렇게 유사배열을 배열로 만들어주는 메소드를 사용해서
  // 순회메소드 사용.
}
foo(1, 2, 3, 4, 5);

bar2(3, 4);

```