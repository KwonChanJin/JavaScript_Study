# JavaScript_Study
## Chapter01
### 자바스크립트의 역사와 현재 그리고 미래(JavaScript, ECMAScript, Babel, Node.js)
- 1993 Mosaic Web Browser
  - 최초의 웹 브라우저
- 1994 Netscape Navigator(Mar Andreesen) 
  - 정적인 웹사이트
  - 시장의 80% 차지
  - 더 동적인 웹사이트를 만들기 위해 Scripting 언어 추가
- 1994, Sep Netscape Navigator - LiveScript Interpreter
  - 당시 유행하던 Java의 힘을 받기 위해 이름을 JavaScript로 변경
- 1995 Microsoft JavaScript를 그대로 복원하는 Reverse engineering을 이용하여 Jscrip 언어를 시장에 출시
  - Internet Explorer 출시
- 1996, Nov Netscape에서 ECMA International에 JavaScript를 표준안으로 사용할 것을 제안
  - Internet Explorer와 Netscape 두 가지가 혼용되어 혼란스러워졌기 때문
  - ECMAScript 완성
- 2000, Internet Explorer의 점유율이 95%로 증가
- 2004 Firefox 출시
  - ECMA에 표준안 요청
  - 기존 JScript나 JavaScript와 차이가 너무 커서 거절당함
  - 세 회사의 경쟁 심화
  - 다양한 브라우저를 사용해야하기 때문에 개발자 수가 증가
- 2008 Google에서 Chrome 브라우저 출시
  - JavaScript를 빠르게 구현가능한 강력한 엔진 소유
  - Chrome의 등장으로 기존에 경쟁하고 있던 세 회사들이 긴장
- 2008, Jul Chrome, Firefox, Internet Explorer, NetScape 표준안에 대해 논의
- 2009 ECMAScript5
- 2015 ECMAScript6
  - 현재의 형태가 거의 만들어짐
 
 
- JavaScript Engines
  - V8(Chrome)
  - SpiderMonkey(Firefox)
  - JSCore(Safari)
  - Chakra(MS Edge)
  - Carakan(Opera)
  - Tamarin(Adobe Flash)

- 현재 가고 있는 방향
  - SPA(Single Page Appication)
  - React, Javascript 등의 라이브러리를 이용하여 개발 가능
 
- 요즘 뜨고 있는 다른 기술?
  - WA(Web Assembly)


## Chapter02
### 콘솔에 출력, script async와 defer의 차이점 및 앞으로 자바스크립트 공부 방향
#### JavaScript 공부 사이트
- ecma-international.org
  - Javascript 공식 사이트
  - 문법 등 확인가능
  - 개발자가 참고하기에 조금 난해함
- developer.mozilla.org
  - Java Script 공부할 때 추천함
  - 프론트 개발자들이 주로 이용

#### 개발자 모드 사용하기
- Console
  - console.log : JavaScript 파일에서 지정한 내용 출력
  - alert : 팝업창 출력
  - 문자 정의
- Sources & Network
  - Sources : 소스코드를 모두 볼 수 있고, 명령줄에서 브레이크를 걸 수 있으며, 디버깅할 때 유용하다.
  - Network : 네트워크들의 크기와 다양한 데이터가 얼마나 오고가는지 등의 정보를 알 수 있다.

#### HTML에서 JavaScript 실행
- head에서 script 실행
  - Javascript를 실행시키는동안 페이지가 뜨지 않는다.
~~~ html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="main.js"></script>
</head>
<body>
    <div></div>
</body>
</html>
~~~

- body에서 script 실행
  - 웹 사이트가 빠르게 뜨기 때문에 사용자에게 빠르게 화면을 보여줄 수 있다.
  - 웹 사이트가 JavaScript에 의존적인 형식이라면 좋지 않은 방식이다.
~~~ html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div></div>
    <script src="main.js"></script>
</body>
</html>
~~~

- Asyn + head 
  - 병렬로 실행한다.
  - 자바스크립트 파일을 실행시킬 때만 html 실행을 중지한다.
  - 자바스크립트 다운로드를 빠르게 할 수 있다.
  - 사용자가 페이지를 보는데 여전히 시간이 걸린다.
~~~ html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script asyn src="main.js"></script>
</head>
<body>
    <div></div>
</body>
</html>
~~~

- Defer + head 
  - 다운로드를 병렬로 받은 뒤, html 실행이 끝나면 JavaScript를 실행한다.
  - 가장 좋은 옵션
  - 가장 효율적이며, 안전하다.
~~~ html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script defer src="main.js"></script>
</head>
<body>
    <div></div>
</body>
</html>
~~~

#### 1. Use strict 
~~~ javascript
'use strict';
console.log('Hello World!');

a = 6;
~~~
- use strict를 사용하지 않을 때는 콘솔 창에 오류가 뜨지 않는다.
- use strict를 사용할 때 console창에 a가 정의되지 않았다는 오류 문구가 뜬다.

~~~ javascript
// Whole-script strict mode syntax
// JavaScript is very flexible
// flexible == dangerous
// added ECMAScript 5

'use strict';
console.log('Hello World!');

let a;
a = 6;
~~~
- let a;를 통해 a를 선언해주면 오류가 뜨지 않는다.
- a가 정의 되었기 때문이다.

- use strict를 사용해야하는 이유
  - Javascript는 매우 유연한 언어이기 때문에 비상식적인 선에서도 구동이 가능하다.
  - Strict 모드를 사용해야 효율적이게 실행할 수 있고, 성능을 향상시킬 수 있다.
  - 따라서 개발할 때는 strict 모드를 사용하는 것을 추천

## Chapter03
### 데이터타입, data types, let vs var, hosting
#### 2. Variable
~~~ javascript
let name = 'chanjin';
console.log(name);
name = 'hello';
console.log(name);
~~~
name이라는 변수에 chanjin을 할당했다가 출력한 뒤, 다시 hello를 할당한다.

- block scope
~~~ javascript
{
  let name = 'chanjin';
  console.log(name);
  name = 'hello';
  console.log(name);
}
console.log(name);
~~~
block 밖에서는 block 안의 변수를 볼 수 없다.

- GlobalName
~~~ javascript
let globalName = 'global name'
{
    let name = 'chanjin';
    console.log(name);
    name = 'hello';
    console.log(name);
    console.log(globalName);
}
console.log(name);
console.log(globalName);
~~~
golbal 변수는 어디에서든 호출 가능하다.

- var
~~~ javascript
age = 4;
var age;
~~~
  - var은 let 이전에 사용하던 것으로 더이상 사용하지 않도록한다.
  - var hosting : 어디에 선언했는지 상관없이 항상 제일 위로 선언을 올려주는 것
~~~ javascript
{
  age = 4;
  var age;
}
console.log(age);
~~~
  - var은 block scope의 영향을 받지 않는다.

#### 3.Constants
- 한 번 할당하면 절대 바뀌지 않는 값
- favor immutable data type always for a few reasons:
  - security
  - thread safety
  - reduce human mistakes
~~~ javascript
const daysInWeek = 7;
const maxNumber = 5;
~~~

#### 4.Variable types
- primitive, single item: number, string, boolean, null, underfiedn, symbol
- object, box container
- function, first-class function
- Javascript에서는 숫자를 지정할 때 datatype(int, double 등)을 따로 설정하지 않고, number로 할당하면 된다.
~~~ javascript
const count = 17; // integer
const size = 17.1; // decimal number
console.log(`value: ${count}, type: ${typeof count}`);
console.log(`value: ${size}, type: ${typeof size}`);
~~~

- number : Infinity, -Infinity, NaN
- bigInt : 숫자 마지막에 n 붙이면 아주 큰 숫자 호환가능 * over (-2**53) ~ 2 *53
- string
- boolen
- null : 명확하게 비어있는 값으로 지정
- undefined : 선언은 되었지만 아직 값이 정해지지 않은 상태
- symbol, create unique identifiers for objects

#### 5.Dynamic typing : dynamically typed language
~~~ javascript
let text = 'hello';
console.log(`value: ${text}, type: ${typeof text}`); // hello, string
text = 1;
console.log(`value: ${text}, type: ${typeof text}`); // 1, number
text = '7' + 5;
console.log(`value: ${text}, type: ${typeof text}`); // 75, string
text = '8' / '2';
console.log(`value: ${text}, type: ${typeof text}`); // 4, number
~~~
알아서 계산한다. 
심지어 스트링과 스트링의 연산을 해도 type이 number로 지정된다.

~~~ javascript
let text = 'hello';
console.log(text.charAt(0)); // h
console.log(`value: ${text}, type: ${typeof text}`);
text = 1;
console.log(`value: ${text}, type: ${typeof text}`);
text = '7' + 5;
console.log(`value: ${text}, type: ${typeof text}`);
text = '8' / '2';
console.log(`value: ${text}, type: ${typeof text}`);
console.log(text.charAt(0)) // error
~~~
여러 개발자가 동시에 작업할 경우 문자 형태가 바뀌어 혼란을 겪을 수 있다.

## Chapter04
### 코딩의 기본 operator, if, for loop 코드리뷰 팁

## Chapter05
### Arrow Fuction은 무엇인가? 함수의 선언과 표현

## Chapter06
### 클래스와 오브젝트의 차이점(class vs object), 객체지향 언어 클래스 정리

## Chapter07
### 오브젝트 넌 뭐니?

## Chapter08
### 배열 제대로 알고 쓰자. 자바스크립트 배열 개념과 APIs 총정리

## Chapter09
### 유용한 10가지 배열 함수들. Array APIs 총정리

## Chapter10
### JSON 개념 정리와 활용방법 및 유용한 사이트 공유

## Chapter11
### 비동기 처리의 시작 콜백 이해하기

## Chapter12
### 프로미스 개념부터 활용까지 JavaScript Promise

## Chapter13
### 비동기의 꽃 JavaScript async와 await 그리고 유용한 Promise APIs


