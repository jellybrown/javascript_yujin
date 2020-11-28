# 안내

## 이 글은 공부한 내용을 정리하기 위해 적은 글이라, 틀린 내용이 있을 수 있습니다.

<br>

# 목차

[0. 변수](#0.변수)
<br>
[1. 함수](#1.함수)
<br>
[2. 클래스](#2.클래스)
<br>
[3. Promise](#3.promise)
<br>
[4. 자바스크립트의 환경](#4.자바스크립트의-환경)
<br>
[5. 브라우저 렌더링](#5.브라우저의-렌더링)

   <br>

# 0.변수

<br>

```
var a = 1;
let b = 2;
const c = 3;
```

## ❗️ var

- 함수단위의 스코프(유효범위)를 가진다.

<br>

## ❗️ let, const

- 블록단위의 스코프(유효범위)를 가진다.
- let은 변하는 값을 선언, const는 변하지 않는 값을 선언

<br>

## ❗️ var?.... let, const?

- var로 선언한 변수는 의도치않은 결과를 유도할 수 있다.
- let과 const를 이용해야 상식적인 코딩을 할 수 있다.
- let, const를 이용하면 코드의 의도를 조금 더 빨리 파악할 수 있다.
- 차이를 정확히 이해하려면, 함수스코프와 블록스코프에 대해 이해해야 한다.

<br>

# 1.함수

<br>

## ❗️ 함수를 쓰는 이유는?

- 코드를 재사용 할 수 있어 효율적이다.
- 유지보수를 할 때 편하다.

<br>

## ❗️ 함수를 잘 작성하려면?

- 하나의 함수가 한가지 일만 하게 한다.
- 매개변수가 많아지지 않도록 한다.
- 변수명을 누가 봐도 알아볼 수 있게 간결하고 명확하게 짓는다.

<br>

## ❗️ 함수의 종류

- 함수 선언문:

```
function sum(a + b) {
    a + b;
}
```

- 함수 표현식

```
const sum = function (a, b) {
    return a + b;
}
```

- 클래스

```
class Person {
    constroctor(name, age) {
        name: this.name,
        age: this.age
    }
}
```

- 화살표 함수 : non-constroctor

```
const sum = (a, b) => {
    return a + b;
}
```

<br>

## ❗️ 생성자 함수

- new 를 통해서 객체를 생성할 수 있는 함수.
- 화살표 함수를 제외한 나머지는 생성자 함수라서, new를 통해 객체를 생성할 수 있다.

<br>

## ❗️ 호이스팅(hoisting)이란?

- 어디서 선언하는 지에 상관없이, 끌어올려져서 사용되는 것.
- 변수의 유효범위라고도 한다.

<br>

<br>

# 2.클래스

## ❗️ 클래스가 나온 배경

- 원래 자바스크립트는 class가 없었다.
- class는 prototype을 편하게 쓰기위해 새로 추가된 것이라고 보면 된다.

<br>

## ❗️ 클래스를 쓰는 이유는?

- 코드를 쓰는 시간과 비용을 절약할 수 있다.

<br>

## ❗️ 클래스를 이용하는 곳은?

- 내용물이 다른, 형태가 비슷한 것들을 만들어야 할
  때
- API key, 내장함수를 이용해야 할 때
- 서버에 요청해서 무언가 처리해야할 때(?)

<br>
<br>

# 3.Promise

## ❗️ 동기 (Sync)

- 순차적으로 실행되는 것.

<br>

## ❗️ 비동기 (Async)

- 순서없이 실행되는 것.
- setTimeout, SetInterval, HTTP요청, 이벤트 핸들러는 비동기 방식으로 동작한다.
- 비동기 함수의 결과를 외부에 반환하거나, 변수에 할당할 수 없으므로 내부에서 처리해야 한다. (콜백함수로 전달)

<br>

## ❗️ 콜백 헬 (callback hell)

- 비동기 함수를 중첩으로 이용해야 해서 콜백함수를 계속 쓰게될 때 일어나는 일.
- 가독성이 나쁘고, 에러 처리를 할 수 없다.

<br>

## ❗️ Promise란?

- 성공하면 resolve, 실패하면 reject함수를 호출하는 비동기 처리방식

```
const something = (url, id, password) => {
    return new Promise((resolve, reject) => {
        if( id === user.id && pw === user.pw ) {
            resolve(id, password); //성공하면 넘김
        } else {
            reject(new Error('error!!')); //실패하면 에러
        }
    })
}
```

```
something('http://www.fdgdf.com', id, pw)
    .then(res => userLogin(id, pw))
    .then(...)
```

<br>

## ❗️ async / await

- Promise를 기반으로 동작하는 비동기 처리 함수
- await로 정상적인 결과를 기다렸다가 다음을 처리

```
async const
```

<br>
<br>

# 4.자바스크립트의 환경

## ❗️ strict mode 적용 권장

- 기본적으로 let, const등을 이용해 변수를 선언하지 않아도 이용할 수 있다.
- 'use strict'; 를 사용하면, 이런 비상식적인 일이 발생하지 않는다.
- ESLint가 더 좋다.

<br>

## ❗️ 객체지향 프로그래밍 언어(Object Oriented Programing- OOP)

- 객체를 기반으로 하는 프로그래밍 방식

<br>

## ❗️ 싱글 스레드 (single-thread)

- 자바스크립트 엔진은 싱글 스레드이다.
- 싱글스레드는 한번에 하나의 일만 할 수 있는 것을 말한다.

<br>

## ❗️ 이벤트 루프, 콜스택, 테스크 큐

-

<br>
<br>

# 5.브라우저의 렌더링

## ❗️ 렌더링 과정

- html 파싱 -> 렌더 트리 생성 -> 레이아웃(layout) 배치 -> 렌더링(paint)

<br>

## ❗️ DOM, CSSOM

- DOM(Document Object Model): html 파싱의 결과물
- CSSOM(Css Object Model): css 파싱의 결과물

<br>

## ❗️ 렌더 트리 (render tree)

- DOM과 CSSOM의 결합물로, 브라우저를 렌더링하기 위해 생성되는 자료구조

<br>

## ❗️ 주의사항

- 레이아웃부터 재배치되는 코드를 짜는 것은 성능에 좋지않다.

<br>

## ❗️ script의 위치

- 브라우저는 순차적(동기적)으로 코드를 실행한다.
- script의 위치에 따라 오류가 날 수 있다.

```
  <!-- 동기적 -->

 1. <head>태그가 끝나기전 -> script를 만나면 html파싱을 중단 후 실행
 2. <body>태그가 끝나기전 -> 동기적으로 일어나서, 맨마지막에 실행
```

```
  <!-- 비동기적 -->

 3. async 추가 -> html파싱과 동시에 로드, html파싱 중단 후 script 실행
 4. defer 추가 -> html파싱과 동시에 로드, html파싱 완료 후 script 실행
```