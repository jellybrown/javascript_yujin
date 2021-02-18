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
[3. This](#3.this)
<br>
[4. Promise](#4.promise)
<br>
[5. 자바스크립트의 환경](#5.자바스크립트의-환경)
<br>
[6. 브라우저 렌더링](#6.브라우저의-렌더링)
<br>
[7. Event](#7.Event)

<br>
<br>

# 0.변수

<br>

```js
var a = 1;
let b = 2;
const c = 3;
```

## ❗️ var

- **함수단위의 스코프**(유효범위)를 가진다.
- **렉시컬 스코프**를 가지는 것과 같다. 렉시컬 스코프란, **함수가 실행 될 때** 변수가 가리키는 것이 **결정**되며, 그것을 **기억**하는 것을 말한다.
- **같은 이름의 변수**를 다시 **선언할 수 있다**. (비상식적)

<br>

## ❗️ let, const

- **블록단위의 스코프**(유효범위)를 가진다.
- **let**은 변하는 값을 선언, **const**는 변하지 않는 값을 선언
- **같은 이름의 변수**를 다시 **선언할 수 없다**. (상식적)

<br>

## ❗️ var?.... let, const?

- **var**로 선언한 변수는 의도치 않은 결과를 유도할 수 있다.
- **let과 const**를 이용해야 **상식적인** 코딩을 할 수 있다.
- **let, const**를 이용하면 **코드의 의도**를 조금 더 빨리 **파악**할 수 있다.
- 차이를 정확히 이해하려면, **함수스코프**와 **블록스코프**에 대해 이해해야 한다.

<br>

# 1.함수

<br>

## ❗️ 함수를 쓰는 이유는?

- 코드를 재사용 할 수 있어 효율적이다.
- 유지보수를 할 때 편하다.

<br>

## ❗️ 함수를 잘 작성하려면?

- **하나의 함수**가 **한가지 일**만 하게 한다.
- **매개변수가 많아지지 않도록** 한다.
- **변수명**을 누가 봐도 알아볼 수 있게 **간결하고 명확하게** 짓는다.

<br>

## ❗️ 함수의 종류

- 함수 선언문:

```js
function sum(a + b) {
    a + b;
}
```

- 함수 표현식

```js
const sum = function (a, b) {
  return a + b;
};
```

- 클래스

```js
class Person {
    constroctor(name, age) {
        name: this.name,
        age: this.age
    }
}
```

- 화살표 함수 : non-constroctor

```js
const sum = (a, b) => {
  return a + b;
};
```

<br>

## ❗️ 생성자 함수

- new 를 통해서 **객체를 생성**할 수 있는 함수.
- 화살표 함수를 제외한 나머지는 생성자 함수라서, new를 통해 객체를 생성할 수 있다.

<br>

## ❗️ 호이스팅(hoisting)이란?

- **어디서 선언**하는 지에 상관없이, **끌어올려져서** 사용되는 것.
- **변수의 유효범위**라고도 한다.
- **함수 선언문**에서는 **함수 호이스팅**이 일어난다.
- **함수 표현식**에서는 **변수 호이스팅**이 일어난다.
- **화살표 함수**는 **호이스팅**이 일어나지 않는다.

<br>

<br>

# 2.클래스

## ❗️ 클래스가 나온 배경

- 원래 자바스크립트는 class가 없었다.
- class는 **prototype을 편하게 쓰기위해** 새로 추가된 것이라고 보면 된다.

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

# 3. this

- 생성자 함수에서의 this

```js
Class Animal {
    constructor(color, size) {
        color: this.color,
        size: this.size
    }
}

const dog = new Animal(white, small);

// Animal클래스가 가지고있는 color와 size는,
// 새로 생성이 될때 입력받는 color와 size이다.
```

<br>

- 객체의 메서드에서의 this

```js
const myCat = {
  weight: "5kg",
  goToHospital() {
    return `${this.weight}라니.. 너무 무겁다`;
  },
};

myCat.goToHospital(); //5kg라니.. 너무 무겁다

//this는 goToHospital을 호출한 myCat이다.
```

<br>

- 일반 함수에서의 this

```
단순해서 쓸일이 없다. 굳이 한다면 this는 window이다.
```

<br>

- 중첩 함수에서의 this

```js
window.flavor = 'strawberry';
const flavor = 'chocolate';

function cake() {
    const flavor = 'greentea';

    function coffee() {
        const withCoffee = this.flavor;
        console.log(withCoffee);
    }
    coffee(); // coffee선언후 실행
};

cake(); //cake함수 실행
strawberry 출력 !

// withCoffee는 strawberry다.
// 중첩함수에서의 this는 window이다.


```

<br>
<br>

# 4.Promise

## ❗️ 동기 (Sync)

- **순차적으로** 실행되는 것.
- 현재 하고있는 일을 계속 **기다린다**. (다른 일들은 **blocking**한다.)

<br>

## ❗️ 비동기 (Async)

- **순서없이** 실행되는 것.
- 현재 하고있는 일이 **끝나지 않아도**, **다른 일을 하고 다시 돌아와** 이어서 하는 방식(다른 일들을 **blocking하지 않는다**.)
- setTimeout, SetInterval, HTTP요청, 이벤트 핸들러는 비동기 방식으로 동작한다.
- 비동기 함수의 결과를 외부에 반환하거나, 변수에 할당할 수 없으므로 내부에서 처리해야 한다. (콜백함수로 전달)

<br>

## ❗️ 콜백 헬 (callback hell)

- 비동기 함수를 중첩으로 이용해야 해서 **콜백함수를 계속 쓰게될 때** 일어나는 일.
- **가독성**이 나쁘고, **에러 처리**를 할 수 없다.

<br>

## ❗️ Promise란?

- 성공하면 resolve, 실패하면 reject함수를 호출하는 비동기 처리방식

```js
const something = (url, id, password) => {
  return new Promise((resolve, reject) => {
    if (id === user.id && pw === user.pw) {
      resolve(id, password); //성공하면 넘김
    } else {
      reject(new Error("error!!")); //실패하면 에러
    }
  });
};
```

```js
something('http://www.fdgdf.com', id, pw)
    .then(res => userLogin(id, pw))
    .then(...)
```

<br>

## ❗️ fetch, axios

- **Promise를 기반**으로 동작하는 비동기 처리 방식
- fetch는 내장 라이브러리라서 import를 하지 않아도 된다.
- axios는 구버전 브라우저도 지원한다.

<br>

## ❗️ async / await

- ES7에 나와서 이제는 async, await를 많이 씀
- **Promise를 기반**으로 동작하는 비동기 처리 함수
- Promise를 **간결**하게 이용할 수 있음
- await로 정상적인 결과를 기다렸다가 다음을 처리
- 여러개의 비동기결과를 동시에 가져와서, 넘겨줄 수 있음

```
async const
```

<br>

<br>
<br>

# 5.자바스크립트의 환경

## ❗️ strict mode 적용 권장

- 'use strict'; 를 사용하면, 이런 비상식적인 일이 발생하지 않는다.
- ESLint가 더 좋다.

<br>

## ❗️ 객체지향 프로그래밍 언어(Object Oriented Programing- OOP)

- 객체를 기반으로 하는 프로그래밍 방식

<br>

## ❗️ 싱글 스레드 (single-thread)

- **자바스크립트 엔진**은 **싱글 스레드**이다.
- **싱글스레드**는 **한번에 하나의 일만** 할 수 있는 것을 말한다.

<br>

## ❗️ 멀티 스레딩 (multi-threading)

- **멀티스레딩**은 **하나의 프로세스**에 **여러가지의 스레드**가 일어나는 것을 말한다.

<br>

## ❗️ 이벤트 루프 (Event loop)

- **자바스크립트 런타임 환경 안**에서 **동작**하는 아이
- **이벤트 루프**로 인해, 자바스크립트 런타임 환경은 **멀티스레딩처럼 동작**한다.
- **콜스택과 Microtask Queue, Task Queue**를 **순회**한다.

<br>
<br>

# 6.브라우저의 렌더링

## ❗️ 렌더링 과정

- html 파싱 -> 렌더 트리 생성 -> 레이아웃(layout) 배치 -> 렌더링(paint)

<br>

## ❗️ DOM, CSSOM

- DOM(Document Object Model): html 파싱의 결과물
- CSSOM(Css Object Model): css 파싱의 결과물

<br>

## ❗️ 렌더 트리 (render tree)

- **DOM과 CSSOM의 결합물**로, **브라우저를 렌더링하기 위해** 생성되는 자료구조

<br>

## ❗️ 주의사항

- 레이아웃부터 재배치되는 코드를 짜는 것은 성능에 좋지않다.

<br>

## ❗️ script의 위치

- 브라우저는 순차적(동기적)으로 코드를 실행한다.
- script의 위치에 따라 오류가 날 수 있다.

<br>

## ❗️ 기본 script 태그 (동기적)

```html
<!-- 1.head 태그 안에 작성 -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src=""></script>
    <!--script를 만나면 html파싱을 중단 후 실행 -->
  </head>
  <body></body>
</html>
```

```html
<!-- 2.body 태그 끝에 작성 -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <!-- ...여기는 html 내용물들 -->

    <script src=""></script>
    <!-- 동기적으로 일어나서 맨 마지막에 실행 -->
  </body>
</html>
```

<br>

## ❗️ 옵션을 추가한 script 태그 (비동기적)

```html
<!-- 3.head 태그에 async와 함께 작성 -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script async src=""></script>
    <!-- html파싱과 동시에 로드하다가 로드가 완료되면, html파싱 중단 후 script 실행 -->
  </head>
  <body></body>
</html>
```

```html
<!-- 4.head 태그에 defer와 함께 작성 -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script defer src=""></script>
    <!-- html파싱과 동시에 로드하고, html파싱이 완료되면 script 실행 -->
  </head>
  <body></body>
</html>
```

<br>
<br>

# 7.Event

## ❗️ 이벤트 캡쳐링(Capturing)과 버블링(Bubbling)

- **캡쳐링**: **하위 요소**로 **전달**되는 이벤트방식
- **버블링**: **상위 요소**로 **전달**되는 이벤트 방식

<br>

## ❗️ 이벤트 위임

- **버블링 방식**을 이용해서 하는 방식
- 큰 요소에 이벤트를 걸고, target을 확인

```js
const $ul = document.querySelector('ul');
$ul.addEventListener('click', function() {
        ...
    }
);
```

큰 요소인 ul에 이벤트를 걸어주고, 이벤트가 걸릴때 target을 먼저 확인한다.

```js
if (e.target.className("list")) {
  //할일 작성
}
```

또는

```js
if (!e.target.className("list")) return;
//할일 작성
```

이렇게 할 수 있다.

<br>

## ❗️ 이벤트 위임을 하는 이유

- 각각 요소에 걸지 않으므로, 메모리 사용이 적음
- 새로운 요소가 동적으로 생성되어도 이벤트가 걸림

<br>
<br>

# 8.Prototype

## ❗️ 프로토타입

- javascript는 prototype 기반 언어이다.
- c++, java는 class 기반 언어이다.
- 객체가 가지고 있는 기본 프로퍼티(key + value 형태)이다.

<br>

## ❗️ 프로토타입의 이점

1. 기본적으로 class를 정의하고 객체를 생성하면, 그 안에 있는 메서드는 객체를 생성할 때마다 생성이 된다.

```js
function Book(name) {
  this.name = name;
  this.open = () => {
    console.log("책을 펼칩니다");
  };
}

const uxBook = new Book(ux); //open 메서드 생성
const jsBook = new Book(js); //open 메서드 생성
```

2. 함수의 내부 로직이 바뀌지 않는다면 굳이 계속 생성할 필요가 없다.
3. 이때 prototype을 이용해서 만들 수 있다.

```js
function Book(name) {
  this.name = name;
}
Book.prototype.open = () => {
  console.log("책을 펼칩니다");
};
const uxBook = new Book(ux);
const jsBook = new Book(js);

// 이렇게 하면, open함수가 생성되는 객체의 __proto__안에 내장되어 있다.
```

<br>

<br>
<br>
