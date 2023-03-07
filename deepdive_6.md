# DeepDive - 06장 데이터 타입

----

<blockquote class="well alert-block alert-danger">
<big>
데이터 타입 : 값의 종류를 말한다.
숫자 타입 : 숫자, 정수와 실수 구분 없이 하나의 숫자 타입만 존재
문자열 타입 : 문자열
불리언 타입 : 논리적 참과 거짓
undefined 타입 : var 키워드로 선언된 변수에 암묵적으로 할당되는 값
null 타입 : 값이 없다는 것을 의도적으로 명시할 때 사용하는 값
심벌 타입 : ES6에서 추가된 7번째 타입, 변경 불가능한 원시 타입의 값, 다른 값과 중복되지 않는 유일무이한 값
객체 타입 : 객체, 함수, 배열 등
</big>
</blockquote>

----

스크립트의 모든 값은 전부 데이터 타입을 갖는다.

데이터 타입은 총 7가지로 원시타입에서 숫자, 문자열, 블리언, undefined, null, 심벌 타입이 있으며 그 외에 객체 타입이 있다.

변수의 타입을 확인하기 위해서는 typeof를 사용한다.
<br><br>

## 숫자 타입

ECMAScript : 
Ecma 인터내셔널(정보와 통신 시스템을 위한 국제적 표준화 기구)에서 정한 기술 규격에 따라 정의하고 있는 표준화된 스크립트 프로그래밍 언어

64비트 부동소수점 : 64비트의 공간 중 52비트는 숫자를 저장하는데 사용되고, 11비트는 소수점 위치를(정수는 0), 1비트는 양수/음수 부호를 저장하는데 사용합니다.

숫자 타입의 값은 배정밀도 64비트 부동소수점 형식을 따르며, 모든 수를 실수로 처리합니다.

```javascript
var numberInt = 11; //
console.log(typeof numberInt); //'number'

var numberFloat = 11.22; //
console.log(typeof numberFloat); //'number'

var numberNegative = -22; //
console.log(typeof numberNegative); //'number'
```

2진수, 8진수, 16진수의 경우 10진수로 해석된다.
```javascript
var numberBinary = 0b010101; // (2*2*2*2) + (2*2) + 1 = 21
console.log(numberBinary); //
var numberOctal = 0o010101; // (8*8*8*8) + (8*8) + 1 = 4161
console.log(numberOctal); // 4161
var numberHex = 0x010101; // (16*16*16*16) + (16*16) + 1 = 69793
console.log(numberHex); // 69793
```

숫자 형식 연산
```javascript
var a = 10;
var b = 0;
console.log(a/b); // Infinity
console.log(a/b*-1); // -Infinity
console.log(a*-1/b); // -Infinity
console.log(a - '문자열'); // NaN
console.log(a + '문자열'); // 10문자열

var c = a + '문자열';
console.log(typeof c); // string
```

* 숫자를 0으로 나누는 것은 연산자체는 불가능하지만, 결과는 Infinity 으로 출력됩니다.
* 숫자 + 문자열의 경우 숫자가 문자열로 변환되어 문자열이 합쳐진 형태로 출력됩니다.
* 연산이 불가능한 경우 NaN으로 출력됩니다.
<br><br>

## 문자열 타입

문자열 타입은 텍스트 데이터를 나타내는데 사용합니다.
문자열은 0개 이상의 16비트 유니코드 문자(UTF-16)의 집합으로 전 세계 대부분의 문자를 표현할 수 있다.

문자열 표기 방법
```javascript
var a = 'Keun'; // 작은 따옴표
var b = "Keun"; // 큰 따옴표
var c = 'Keun'; // 백틱(ES6)
```
<br><br>

## 템플릿 리터럴

ES6부터 도입된 새로운 문자열로 멀티라인, 표현식 삽입, 태그드 템플릿 등 편리한 문자열 처리를 가능하게 해주는 기능이 추가되었습니다.<br>
템플릿 리터럴은 런타임에서는 일반 문자열로 변환되어 처리됩니다.

런타임 : 런타임(영어: runtime→실행시간)은 컴퓨터 과학에서 컴퓨터 프로그램이 실행되고 있는 동안의 동작을 말한다.

### 멀티라인 문자열

자바스크립트는 일반 문자열 내에서는 줄바꿈(개행)이 허용되지 않는다.
개행을 하기 위해서는 개행문자를 사용해야 한다. 이와 같이 줄바꿈, 공백, 따옴표, 백슬래시 등을 사용하려면 백슬래쉬로 시작하는 이스케이브 시퀀스를 사용해야 한다.

* 이스케이프 시퀀스 예시
```javascript
'\0' //'Null'
'\b' //'백스페이스'
'\f' //'폼 피드, 프린터로 출력할 경우 다음페이지의 시작 지점으로 이동한다.(인쇄페이지 구분)'
'\n' //'개행, 다음행으로 이동'
'\r' //'개행, 커서를 처음으로 이동'
'\t' //'탭(수평)'
'\v' //'탭(수직)'
'\u0041' //'유니코드 'A''
'\'' //'작은따옴표'
'\"' //'큰따옴표'
'\\' //'백슬래시'
```

* 개행문자를 사용한 예시
```javascript
var htmlStr = '<ul>\n\t<li>목록아이템1</li>\n\t<li>목록아이템2</li>\n</ul>'; // 
console.log(htmlStr);
```

* 템플릿 리터럴을 사용한 예시
```javascript
var htmlStr = `<ul>
  <li>목록아이템1</li>
  <li>목록아이템2</li>
</ul>`; // 
console.log(htmlStr);
```

### 라인 피드와 캐리지 리턴

<blockquote class="well alert-block alert-danger">
개행 문자는 텍스트의 한 줄이 끝남을 표시하는 문자 또는 문자열이다. 개행 문자에는 라인 피드와 캐리지 리턴이 있다. 이는 과거 타자기에서 커서를 제어하는 방식에서 비롯된 것이다. 라인 피드는 커서를 정지한 상태에서 종이를 한 줄 올리는 것이고, 캐리지 리턴은 종이를 우밎ㄱ이지 않고 커서를 맨 앞줄로 이동하는 것이다. 초창기 컴퓨터는 출력을 프린터로 수행했는데, 이때 개행을 위해 라인 피드와 캐리지 리턴을 모두 사용했다. 즉, CRLF(\r\n)
로 커서를 맨 앞으로 이동시키고 종이를 한 줄 올리는 방식으로 개행했다.

현대의 컴퓨터 운영체제는 서로 다른 체계의 개행 방식을 사용한다. 윈도우는 CR+LF(ASCII 코드 13번과 10번)로 새 줄을 나타내고 유닉스는 LF(ASCII 코드 10번)로 새 줄을 나타낸다, macOS에서는 버전 9까지 CR로 새 줄을 나타냈지만 버전 10부터는 LF를 사용한다. 따라서 다른 운영체제에서 작성한 텍스트 파일은 서로 개행 문자를 인식하지 못한다. 다만 대부분의 텍스트 에디터는 운영체제에 맞게 개행 문자를 자동으로 변환해주므로 큰 문제는 없다. 자바스크립트에서 라인 피드와 캐리지 리턴은 모두 개행을 의미한다. 하지만 캐리지 리턴(\r)으로 개행하는 경우는 거의 없고 일반적으로 라인 피드(\n)를 사용해 개행한다.
</blockquote>
<br><br>

## 불리언 타입

불리언 타입의 값은 논리적 참(true), 거짓(false) 뿐이다.

```javascript
var isPerson = true;
console.log(typeof isPerson); //'boolean'
console.log(isPerson); //true
if(isPerson){
  console.log('사람입니다.');
}
```
위의 예시처럼 불리언 타입은 주로 흐름을 제어하는 조건문에서 자주 사용됩니다.
<br><br>

## undefined 타입

undefined 타입의 값은 undefined 가 유일하다.
앞서 변수 학습에서 변수를 선언하면 변수는 암묵적으로 undefined 로 초기화 된다.

이처럼 undefined 는 개발자가 할당한 것이 아닌 자바스크립트에서 초기화를 위해 사용되는 값으로 개발자가 의도적으로 사용하는 것은 권장하지 않는다.

* 변수 선언, 초기화 이후 조건문
```javascript
var isPerson;
console.log(isPerson); //'undefined'
if(isPerson == undefined){
  console.log('값이 할당되지 않음');
}
```

* 변수 선언, 초기화, undefined 재할당 이후 조건문
```javascript
var isPerson;
isPerson = undefined;
console.log(isPerson); //'undefined'
if(isPerson == undefined){ //'true'
  console.log('값이 할당되지 않음');
}
```

* 변수에 값이 없는 경우 null을 할당하는 것을 권장한다.
```javascript
var isPerson;
isPerson = null;
console.log(isPerson); //'null'
if(isPerson == null){ //'true'
  console.log('값이 없음');
}
```

* null로 할당했지만, 조건문에서는 undefined 비교시 true
```javascript
var isPerson;
isPerson = null;
console.log(isPerson); //'null'
if(isPerson == undefined){ //'true'
  console.log('값이 할당되지 않음');
}

if(typeof isPerson == undefined){ //'false'
  console.log('값이 할당되지 않음');
}
```
<br><br>

## null 타입

null 타입의 값은 null이 유일하다.

* null로 할당했지만, 조건문에서는 undefined 비교시 true

```javascript
var hasValue;
hasValue = null;
console.log(hasValue); //'null'
console.log(isPerson == undefined){ //'true'
  console.log('값이 할당되지 않음');
}
console.log(isPerson === undefined){ //'false'
  console.log('값이 할당되지 않음');
}
```
null와 undefined 를 구분하고 싶을때는 typeof 를 검사하거나, === 일치 연산자를 사용하면 구분이 가능하다.

* null 데이터 타입 버그

```javascript
var hasValue;
hasValue = null;
console.log(typeof hasValue); //'object'
```

null의 타입은 null 기본 타입입니다. typeof 에서 object 라고 나오는 것은 초기 버그로 인하여 기존 코드의 에러 문제를 고려하여 수정되지 않았습니다.

* 유효한 값을 반환할 수 없는 경우 null을 반환하기도 한다.

```javascript
document.querySelector('.className'); //'null'
```
<br><br>

## 심벌 타입

심벌 타입은 ES6에서 추가된 7번째 타입으로, 변경 불가능한 원시 타입의 값이다.
심벌 값은 다른 값과 중복 되지 않는 유일무이한 값이다. 따라서 주로 이름이 충돌할 위험이 없는 객체의 유일한 프로퍼티 키를 만들기 위해 사용한다.

심벌은 Symbol 함수를 호출해서 생성됩니다.

















