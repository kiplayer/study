# DeepDive - 04장 변수

----

<blockquote class="well alert-block alert-danger">
<big>
변수는 하나의 값을 저장하기 위해 확보한 메모리 공간 자체 또는 그 메모리 공간을 식별하기 위해 붙인 이름을 말합니다.<br>
다시 말해서 프로그래밍을 하기 위해서 어떤 값을 저장하고 사용하기 위해서 만들어진 식별자, 이름을 말합니다.
</big>
</blockquote>

----
<br>

## 4.1 변수란 무엇인가? 왜 필요한가?

자바스크립트 언어는 자바스크립트 엔진을 통해서 실행할 수 있고, 모든 브라우저는 자바스크립트 엔진을 내장하고 있다. PC에서 사용되는 브라우저 이외에도 모바일 기기내에 존재하는 브라우저, 하이브리드 앱을 만들기 위해 구현되는 webview 등에서도 자바스크립트 엔진을 통해 실행이 가능하며, 상황에 따라서 자바스크립트 엔진을 끄고 킬 수 있습니다.

프로그래밍 언어로 만들어진 소프트웨어는 데이터 처리하는 과정을 포함하고 있으며, 변수는 모든 프로그래밍 언어에서 데이터를 관리하기 위한 핵심 개념입니다.

컴퓨터는 CPU에서 연산을 처리하고 메모리를 사용해서 연산을 위해 사용되는 데이터를 기록합니다. 
메모리는 데이터를 저장할 수 있는 메모리 셀의 집합체이며 메모리 셀의 크기는 1바이트(8비트)입니다.

<strong>* 여러개의 값을 자료 구조(객체, 배열 등)를 이용하여 하나의 값 처럼 사용할 수 있습니다.</strong>

```javascript
var lastName = 'Keun'; //하나의 값
var lastNames = ['Keuns', 'Jungmin', 'Hyuna', 'Kyungsu']; //배열을 사용하여 여러개의 값을 하나의 값 처럼 사용
```
*변수는 메모리를 사용하여 저장되며, 변수의 사용 방법이나, 상황에 따라 브라우저의 메모리에 영향을 주게 됩니다.
<br><br>

## 4.2 식별자
<big>정의 : 어떤 값을 구별해서 식별할  수  있는 고유한 이름</big>

```javascript
var lastName = 'Keun'; 
```
위의 코드에서 'lastName' 은 Keun 값을 식별 할 수 있는 식별자(변수 이름) 입니다.   
변수를 메모리에 특정 메모리 위치에 저장하고, 메모리 위치를 확인 할 수 있는 주소를 기억하고 있는 것이 식별자입니다. 

프로그래밍 언어에서 변수, 함수, 클래스 등 선언을 해서 사용하는 것은 식별자인 변수 이름으로 메모리 존재하는 각각을 식별할 수 있습니다.

변수 뿐만 아니라 모든 식별자는 네이밍 규칙을 준수해야 합니다.

네이밍 규칙에 대해서는 4.7에서 다시 설명드리도록 하겠습니다.
<br><br>   

## 4.3 변수 선언
<big>정의 : 변수를 생성하는 것</big>   
변수를 사용하려면 반드시 선언이 필요하며, 변수 이외에도 메모리에 저장이 필요한 함수, 클래스 등도 사용하기 위해서는 선언이 필요합니다.

키워드 : 자바스크립트 코드를 해석하고 실행하는 자바스크립트 엔진이 수행할 동작을 규정한 일종의 명령어(대소문자 구분함)
var, let, const 키워드 뒤에 오는 문자를 변수명으로 인식합니다. 

변수 선언 벙법에는 총 3가지 키워드가 있으며, ES6이전 var만 사용가능하다가 var의 단점을 보완하여, ES6부터는 let, const가 추가 되었습니다.

변수를 선언 하는 방법은 아래와 같습니다.

* 변수명만 선언하는 경우
```javascript
var lastName;
let tel;
const address; //Uncaught SyntaxError: Missing initializer in const declaration
```
주의! const의 경우 값의 재할당이 금지되어 있기 때문에, 변수명만으로는 선언이 불가능합니다.

* 값을 포함하여 선언하는 경우
```javascript
var lastName = 'Keun';
let tel = '01012345678';
const address = '서울특별시 강남구 역삼동';
```

변수의 값을 할당하지 않고 변수명만 선언하는 경우 자바스크립트 엔진에 의해서 undefined 라는 값으로 할당되어 초기화됩니다.

```javascript
var lastName;
console.log(lastName); //'undefined'
```

자바스크립트 엔진은 변수 선언 과정
1. 선언 단계 : 변수 이름 등록
2. 초기화 단계 : 값을 저장하기 위한 메모리 공간 확보, undefined를 할당해 초기화 

```javascript
var count;
console.log(count); //'undefined'
console.log(typeof count); //'undefined'

var count = 1;
console.log(typeof count); //'number'

var count = '1';
console.log(typeof count); //'string'

var count = {
  start: 1,
  end: 100
};
console.log(typeof count); //'object'

var count = function(){
  return ;
};
console.log(typeof count); //'function'
```

참고! 변수에 값을 할당하고 나면 변수의 타입이 자동으로 지정됩니다.
<br><br>   

## 4.4 변수 선언의 실행 시점과 변수 호이스팅
자바스크립트는 인터프리터 언어로 위에서 부터 한줄씩 순차적으로 실행됩니다.
변수 선언의 경우 소스코드가 순차적으로 실행되는 런타임에 따라 실행되는 것이 아니라 그 이전 단계에서 먼저 실행됩니다.

* 하나의 코드내에 있는 경우
```javascript
console.log(lastName); //'undefined'
var lastName = 'Keun';
```

* 순차적으로 개별 실행하는 경우
```javascript
console.log(lastName); //'lastName is not defined'
```
```javascript
var lastName = 'Keun';
```

* 정상적인 경우
```javascript
var lastName = 'Keun';
console.log(lastName); //'Keun'
```

### 브라우저 예외

브라우저에서는 window 객체에 담겨 있는 것들의 경우, window가 없이 사용할 수 있습니다. window.name, window.open, window.localStorage 등 앞의 window. 를 넣지 않아도 되는 명칭의 경우 이미 정의가 되어 있기 때문에, 오류가 발생하지 않으며, 일부는 값의 재할당을 통해서 변형도 가능합니다.

* 오류가 나지 않는 경우

```javascript
console.log(name); //''
console.log(window.name); //''
console.log(open); //'ƒ open() { [native code] }'
console.log(window.open); //'ƒ open() { [native code] }'
```

* 재할당 주의

```javascript
name = 'Keun'
console.log(name); //'Keun'

open = 'Y'
console.log(open); //'Y'
window.open('www.naver.com'); //'window.open is not a function'
```

* 재할당 불가
* 
```javascript
localStorage = { a: 'b' };
console.log(localStorage); //'Storage {length: 0}'
```

호이스팅 : 변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트 고유의 특징 말합니다.
<br><br>   

## 4.5 값의 할당
변수에 값을 할당(대입, 저장)할때는 할당 연산자(=)를 사용합니다.
할당 연산자는 우변의 값을 좌변의 변수에 할당합니다.
변수의 선언과 할당을 하나의 문으로 단축 표현 할 수 있습니다.

```javascript
var lastName; //변수의 선언
var lastName = 'Keun'; // 변수의 선언과 값의 할당하는 경우
```

변수의 선언과 할당에 대한 동작 예시
```javascript
console.log(lastName); //'undefined'
var lastName;
console.log(lastName); //'undefined'
lastName = 'Keun'; 
console.log(lastName); //'Keun'
```

식별자의 대소문자 구분합니다.
```javascript
var LASTNAME = 'KEUN';
var lastname = 'keun';
console.log(LASTNAME); //'KEUN'
console.log(lastname); //'keun'
```
<br><br>   

## 4.6 값의 재할당
재할당 : 변수에 이미 값이 할당되어 있는 변수에 새로운 값을 다시 할당하는 것

var, let 키워드의 경우 선언과 동시에 값이 undefined로 초기화 되기 때문에, 값을 할당하는 과정을 재할당으로 볼 수 있다.

```javascript
var firstName = 'Kim';
let lastName = 'Keun';
console.log(firstName); //'Kim'
console.log(lastName); //'Keun'
firstName = 'Lee';
lastName = 'Chulsu';
console.log(firstName); //'Lee'
console.log(lastName); //'Chulsu'
```

const 처럼 값을 재할당할 수 없는 경우 상수라고 한다. 

```javascript
const lastName = 'Keun';
console.log(lastName); //'Keun'
lastName = 'Chulsu'; //'Assignment to constant variable.'
```

값의 할당은 메모리의 값을 저장하게 되며, 재할당시 해당 메모리의 값을 변경하지 않고, 메모리의 공간을 새로 만들어서 저장하게되며, 메모리상의 위치가 변경됩니다.
이렇게 재할당으로 인해서 기존의 저장된 값이 있는 공간은 식별자와 연결이 끊어지게 되고, 이러한 불필요한 공간은 메모리에서 가비지 콜렉터에 의해 해제됩니다.

<big>가비지 콜렉터</big> : 애플리케이션에서 할당된 메모리 공간을 주기적으로 검사하여 더 이상 사용되지 않은 메모리를 해제 하는 기능

<big>언매니지드 언어</big> : 언매니지드 언어는 개발자가 명시적으로 메모리를 할당하고 해제하기 위해 제공된 메모리 제어 기능을 사용합니다.

<big>매니지드 언어</big> : 언어 차원에서 메모리 관리 기능을 제공하며, 개발자의 직접적인 메모리 제어가 허용되지 않습니다.

언매니지드 언어와 매니지드 언어의 차이점은 개발자가 메모리의 관리를 직접 할 수 있는지에 있습니다.
<br>

### < 변수와 메모리에 대한 고민 >

* 변수를 많이 사용하면 메모리 사용이 늘어난다. 
* 재할당이 반복적으로 일어나는 형태의 경우, 메모리를 어떻게 관리할 것인가?
  * 스크롤 위치에 따른 액션 사용시
  * 자동 슬라이드 시
  * 드레그앤드롭 시
<br><br>   

## 4.7 식별자 네이밍 규칙
식별자는 다음과 같은 네이밍 규칙을 준수해야 한다.

- 식별자는 특수문자를 제외한 문자, 숫자, 언더스코어(_), 달러 기호($)를 포함할 수 있다.
- 단, 식별자는 특수문자를 제외한 문자, 언더스코어(_), 달러 기호($)로 시작해야 한다. 숫자로 시작하는 것은 허용하지 않는다.
- 예약어는 식별자로 사용할 수 없다.

사용이 불가능한 식별자 예)
```javascript
var 1test; //'Invalid or unexpected token'
var *test; //'Unexpected token '*''
var last-name; //'Unexpected token '-''
var this; //'Unexpected token 'this''
var delete; //'Unexpected token 'delete''
```

권장하지 않는 식별자 예)
```javascript
var a = 1; //변수 목적이 불분명함
var lastname; //문자에 대한 가독성을 높이기 위해서 카멜 케이스를 추천
var LASTNAME; //문자에 대한 가독성을 높이기 위해서 카멜 케이스를 추천
```
<br>

### < 변수명에 대한 개인적인 생각 >

* 진행중인 프로젝트의 경우 사용중인 네이밍 규칙을 최대한 유지하는 것을 권장합니다.
* DB나 BE에서 사용되는 그대로를 사용하는 경우 보안에 문제가 있거나, 더 복잡해질 수 있습니다.
* 변수명이 너무 길지 않으면서 가독성이 좋은 명칭이 좋다고 생각합니다.












