# DeepDive - 06장 데이터 타입

----

<blockquote class="well alert-block alert-danger">
<big>
정의 : 값의 종류를 말한다.
</big>
</blockquote>

----

스크립트의 모든 값은 전부 데이터 타입을 갖는다.

데이터 타입은 총 7가지로 원시타입 구분으로 숫자, 문자열, 블리언, undefined, null, 심벌 타입이 있으며 그 외에 객체 타입이 있다.

### < 개인적인 생각 - 타입의 필요성 >
* 메모리 사용의 최적화
* 프로그램의 올바른 동작을 지원하기 위함
* 런타임 오류를 예방하기 위함
* 개발 도구에게 자동 완성 및 사진 오류 체크 등을 위함

변수의 타입을 확인하기 위해서는 typeof를 사용한다.

<br>

## 6.1 숫자 타입

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

## 6.2 문자열 타입

문자열 타입은 텍스트 데이터를 나타내는데 사용합니다.
문자열은 0개 이상의 16비트 유니코드 문자(UTF-16)의 집합으로 전 세계 대부분의 문자를 표현할 수 있다.

문자열 표기 방법
```javascript
var a = 'Keun'; // 작은 따옴표
var b = "Keun"; // 큰 따옴표
var c = 'Keun'; // 백틱(ES6)
```

## 6.3 템플릿 리터럴

ES6부터는 템플릿 리터널 이라고 하는 새로운 문자열이 도입되었습니다.
멀티라인, 표현식, 태그드 템플릿 등 처리가 가능해졌습니다.

* 멀티라인 예)
```javascript
var fullName = 'Kim
Keun'; // 작은 따옴표
var b = "Keun"; // 큰 따옴표
var c = 'Keun'; // 백틱(ES6)
```







