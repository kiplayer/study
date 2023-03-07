# DeepDive - 05장 표현식과 문

----

<blockquote class="well alert-block alert-danger">
<big>
값 : 식이 평가되어 생셩된 결과를 말한다.<br>
평가 : 식을 해석해서 값을 생성하거나 참조하는 것의 의미한다.<br>
리터럴 : 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용해 값을 생성하는 표기법을 말한다<br>
표현식 : 값으로 평가될 수 있는 문이다.
문 : 프로그램을 구성하는 기본 단위이자 최소 실행 단위이다.
</big>
</blockquote>

----
<br>

## 값의 생성

모든 값은 데이터 타입을 가지고 메모리에 2진수(비트)나열로 저장된다.
메모리에 저장된 값은 데이터 타입에 따라 다르게 해석된다.

```javascript
10 //'10'
10 + 20 //'30'
```

```javascript
var score = 10; //'10'
console.log(typeof score); //'number'
```

위의 예시는 score 변수에 10이라는 값을 할당했다.'score' 식별자의 메모리 위치에 숫자 10을 저장했다.
여기서 데이터 타입은 number 로 지정되었으며, 10은 숫자로 해석된다.
<br><br>

## 리터럴의 구분

자바스크립트 코드를 자바스크립트 엔진이 코드가 실행되는 시점인 런타임에 리터럴을 평가해 값을 생성한다.

```javascript
var valueInt = 10;
var valueString = '10';
var valueBoolean = true;
```

위의 리터널의 예시에서 valueInt 는 숫자만 있기 때문에 숫자(number) 타입으로 평가되었고,
valueString 의 경우 ',",백틱 등으로 감싸여 있기 때문에 문자열(string) 타입으로 평가 되었습니다.<br>
true, false 의 경우 불리언(boolean) 타입으로 평가되기 때문에 valueBoolean 불리언 타입으로 지정 되었습니다.
이와 같이 리터럴을 사용하여 다양한 종류의 값을 생성할 수 있습니다.
<br><br>

## 표현식의 이해

값으로 평가될 수 있는 문은 모두 표현식이다.
앞서 예시에서 리터털처험 평가되는 값 또헌 표현식이다.

* 리터럴 표현식
```javascript
10
'10'
'Keun'
true
var score = 10;
```
* 식별자 표현식
  
  변수, 클래스, 객체 등 선언을 한 식별자의 대한 표현식
```javascript
//선언부
var score = 10;
function doScore(){
  return ; 
}
var mall = {
  products: ['과일','생선','육류'],
  sell: function() {
    return ;
  }
}

//식별자 표현식
score
doScore
mall
mall.products

//연산자 표현식
10 + 20
score = 10
score !== 10

//함수/메서드 호출 표현식
doScore();
mall.products();
```

함수 : 일련의 과정을 문으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정의한 것이다.
메서드 : 객체안에 존재하는 함수, 객체에 묶여있는 함수를 의미한다.

표현식은 값으로 평가되며, 값처럼 사용할 수 있다.
식별자 표현식의 score를 값처럼 사용하는 예시

```javascript
//선언부
var score = 10;

function printScore(score){
  console.log(score);
}

if(score == 10){
  console.log(true);
}
```
<br><br>

## 문과 토큰
문은 프로그램을 구성하는 기본 단위이자 최소 실행 단위라고 한다.
토큰은 문법적인 의미를 가지며, 문법적으로 더 이상 나눌 수 없는 코드의 기본 요소를 의미한다.

아래 변수를 선언하는 예시에서 '=','score' 등을 빼면 의미가 달라지거나, 동작하지 않는다.
이를 하나의 토큰으로 본다.

```javascript
let score = 10; //'10'
```
(var는 생략이 가능하지만, 완전한 문장은 아니다)
<br><br>

## 세미콜론과 '문'의 종료

세미콜론은 문의 종료를 나타낸다.
자바스크립트 엔진은 세미콜론으로 문의 종료한 위치를 하악하고 순차적으로 하나씩 문의 실행한다.
따라서 문의 끝낼 때는 세미콜론을 붙여야 한다.
단, 0개 이상의 문을 중괄호로 묶은 코드 블록({...}) 뒤에는 세미콜론을 붙이지 않는다.

```javascript
let score = 10; //세미콜론을 붙임

if(score == 10){
  console.log(true);
} //세미콜론을 붙이지 않음

for(let i=0; i<10; i++){
  console.log(i);
} //세미콜론을 붙이지 않음
```

코드 블록의 세미콜론을 붙이지 않는 이유는 자체 종결성을 갖기 때문이다.

### 세미콜론의 자동 삽입 기능(ASI)

자바스크립트는 세미콜론 자동 삽입 기능이 암묵적으로 수행된다.
```javascript
let score = 10
let count = 1
const doScore = function(){
  count = count + 1
  console.log(count)
  console.log(score)
}
```
위의 예시를 보면 선언문에도 세메콜론을 붙이지 않았고, 함수 내부에 존재하는 문에도 세미콜론을 붙이지 않았지만 자바스크립트에서 세미콜론이 없이 줄바꿈으로 다음 문이 시작된 경우 종료를 인식하였기 때문에 동작이 됩니다. 

하지만 자동 삽입 기능이 개발자의 의도나 예측과는 다르게 동작하는 경우가 있습니다.

```javascript
let score = 10;

const doScore = function(){
  return
    score
} //'undefined'

const doScore = function(){
  return score
} //'undefined'
```




