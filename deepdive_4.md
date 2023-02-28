# DeepDive - 04장 변수

----

<blockquote class="well alert-block alert-danger">
<big>
As of 2017, DeepDive project is in maintenance mode and no longer under active development.
The user community remains active, but the original project members can no longer promise exciting new features/improvements or responding to requests.
For the more up-to-date research, please see the <a href="https://hazyresearch.github.io/snorkel/">Snorkel Project</a> or <a href="https://ds3lab.org/~czhang/">Ce Zhang's Projects</a>.
</big>
</blockquote>

----

<strong><big>변수는 하나의 값을 저장하기 위해 확보한 메모리 공간 자체 또는 그 메모리 공간을 식별하기 위해 붙인 이름을 말한다.</big></strong><br>

<strong>* 프로그래밍을 하기 위해서 어떤 값을 저장하고 사용하기 위해서 만들어진 식별자, 이름을 말한다.</strong><br>
<strong>* 여러개의 값을 자료 구조(객체, 배열 등)를 이용하여 하나의 값 처럼 사용할 수 있다.</strong>
```bash
var name = 'Keun'; //하나의 값
var names = ['Keuns', 'Jungmin', 'Hyuna', 'Kyungsu']; //배열을 사용하여 여러개의 값을 하나의 값 처럼 사용
```
*변수는 메모리를 사용하여 저장되며, 변수의 사용 방법이나, 상황에 따라 브라우저의 메모리에 영향을 주게 됩니다.

<strong><big>let, const </big></strong>

변수를 사용하기 위해서는 반드시 선언이 필요합니다.<br>
선언하는 벙법은 ES6이전 var만 사용가능하다가 ES6부터는 let, const가 추가 되었습니다.<br>
var은 블록 레벨 스코프를 지원하지 않고, 함수 레벨 스코프만 지원합니다.

