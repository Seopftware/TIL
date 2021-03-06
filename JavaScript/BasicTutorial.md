# JavaScript 기본

- 공부 이유: 회사에서 webSDK 개발도 담당하게 되면서 JS에 대한 기본 지식을 정리하기 위해서

## 숫자

```
Math.pow(3,2); // 9, 3의 2승
Math.round(10.6); // 11, 10.6의 반올림
Math.ceil(10.2); // 11, 10.2를 올림
Math.floor(10.6); // 10, 10.6을 내림
Math.sqrt(9); // 3, 3의 제곱근
Math.random(); // 0부터 1.0 사이의 랜덤한 숫자
```

## 문자

문자는 "(큰 따옴표) 혹은 '(작은 따옴표) 중의 하나로 끝나야 한다. 큰 따옴표로 시작하면 큰 따옴표로, 작은 따옴표로 시작하면 작은 따옴표로 끝나야 한다.

```
alert("coding every");
alert('coding every');
alert(typeof 1); // number
alert('egoing's javascript); // SytaxError: Unexpected identifier
alert('egoing\'s javascript'); // egoing's javascript
```
- 문자열 안에 작은 따옴표나 큰 따옴표를 넣기 위해서는 ₩를 '앞에 위치 시킨다. 그럼 문자열의 시작과 끝을 구분하는 자가 아니라 단순히 문자로 해석하도록 강제할 수 있다. 이러한 기법을 이스케이프(escape)라고 한다

## 문자연산

```
alert("coding" + " everybody"); // coding everybody
alert("coding everybody".length); // 16
```

## 비교 연산자

```
alert(1 == '1'); // true
alert(1 === '1'); // false

alert(null == undefined); // true
alert(null === undefined); // false

alert(true == 1); // true
alert(true === 1); // false
```
- '==='는 서로 같은 수를 표현하고 있더라도 데이터 형이 같은 경우에만 같다고 판단을 한다. 그렇기 때문에 '==' 대신 '==='연산자를 쓰는 것을 강력히 권한다.

## 반복문

break
```
for(var i=0; i<10; i++){
    if(i === 5){
        break;
    }
    document.write('coding' + i + '<br />');
}
```
- coding 0~4까지만 출력이 되고 5일 때는 break문이 실행되면서 반복문이 완전히 종료된다.

continue
```
for(var i=0; i<10; i++){
    if(i === 5){
        continue;
    }
    document.write('coding' + i + '<br />');
}
```
- coding 0~9까지 실행이 되고, 5는 실행 되지 않는다. 하지만 반복문은 중단되지 않고 나머지 결과가 출력된다.

# 함수

- 함수(function)란 하나의 로직을 재실행 할 수 있게 작성하여 코드의 재사용성을 높인다.

함수의 형식
```
function 함수명([인자... [, 인자]] ){
    코드
    return 반환값;
}
```

입력과 출력
- 함수의 핵심은 입력과 출력이다. 입력된 값을 연산해서 출력하는 것이 함수의 기본적인 역할이다.
- return은 함수의 결과를 반환하는 역할을 하는 동시에 함수를 중지시키는 역할도 한다.

인자
- 인자는(argument)는 함수로 유입되는 입력 값을 의미한다.
- 어떤 값을 인자로 전달하느냐에 따라서 함수가 반환하는 값이나 메소드의 동작방법을 다르게 할 수 있다.

함수를 정의 하는 다른 방법

```
var numbering = function (){
    i = 0;
    while(i < 10){
        document.write(i);
        i + = 1;
    }
}
numbering();
```

### 배열
- 배열(array)이란 연관된 데이터를 모아서 통으로 관리하기 위해서 사용하는 데이터 타입이다.
- 변수가 하나의 데이터를 저장하기 위한 것이라면 배열은 여러 개의 데이터를 하나의 변수에 저장하기 위한 것이라고 할 수 있다.
- 따라서 데이터의 추가/수정/삭제와 같은 일을 편리하게 할 수 있도록 돕는 다양한 기능을 가지고 있다.

```
var li = ['a', 'b', 'c', 'd'];

li.push('e'); // a,b,c,d,e 
li.concat(['e', 'f']); // a,b,c,d,e,f
li.unshift(['z']); // z,a,b,c,d
li.splice(2,0, 'B'); // a,b,B,c,d
li.shift(); // b,c,d
li.pop(); // a,b,c
li.sort(); // a,b,c,d
li.reverse(); // d,c,b,a

```
- push는 배열의 끝에 원소를 추가하는 방법
- concat은 복수의 원소를 배열에 추가하는 방법
- unshift는 인자로 전달한 값을 배열의 첫번째 원소로 추가하고 배열의 기존 값들의 색인을 1씩 증가시킴
- splice는 첫번째 인자에 해당하는 원소부터 두번째 인자에 해당하는 원소의 숫자 만큼의 값을 배열로부터 제거한 후에 리턴 
- shift는 배열의 첫번째 원소를 제거
- pop는 배열 끝점의 원소를 제거
- sort는 배열을 정렬
- reverse는 역순으로 정렬

## 객체

- 배열은 아이템에 대한 식별자로 숫자를 사용했다. 데이터가 추가되면 배열 전체에서 중복되지 않는 인덱스가 자동으로 만들어져서 추가된 데이터에 대한 식별자가 된다. 이 인덱스를 이용해서 데이터를 가져오게 되는 것이다.
- 인덱스를 문자로 사용하고 싶다면 객체(dictionary)를 사양해야 한다.

객체의 생성
```
var grades = {'seop': 10, 'jaywon': 20, 'seops': 15};
alert(grades['seops']);
alert(grades.seops);
```
- seop은 key가 되고, 10은 value가 된다. 

```
var grades = {'seop': 10, 'jaywon': 20, 'seops': 15};
for (key in grades){
    document.write("key : " + key + " value: " + grades[key]+"<br />");
}
```
- for 문은 in 뒤에 따라나오는 배열의 key 값을 in 앞의 변수 name에 담아서 반복문을 실행한다. 반복문이 실행될 때 key의 값으로 seop, jaywon, seops가 순차적으로 할당된다.

# 모듈
코드의 재활용성을 높이고, 유지보수를 쉽게 할 수 있는 다양한 기법들이 있다. 그 중 모듈은 코드를 여러개의 파일로 분리하는 것이다.

### 모듈의 사용

greeting.js
```
function welcome(){
    return 'Hello world';
}
```
main.html
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <script src="greeting.js"></script>
<head>
<body>
    <script> alert(welcome()); </script>
</body>
</html>
```
- greeing.js에는 함수 welcome이 정의되어 있기 때문에 main.html 안에 이 함수가 정의 되어 있지 않음에도 실행할 수 있는 것이다.

### 라이브러리
- 라이브러리는 모듈과 비슷한 개념이다
- 모듈이 프로그램을 구성하는 작은 부품으로서의 로직을 의미한다면 라이브러리는 자주 사용되는 로직을 재사용하기 편리하도록 잘 정리한 일련의 코드들의 집합을 의미한다.

jQuery
```
<ul id="list">
    <li>empty</li>
    <li>empty</li>
    <li>empty</li>
    <li>empty</li>
</ul>
<input id="execute_btn" type="button" value="execute" />

$('#execute_btn').click(function(){
    $('#list_li').text('coding everybody');
})
```

만약, jQuery가 없다면
```
function addEvent(target, eventType, eventHandler, useCapture){
    if(target.addEventListener){ // W3C DOM
        target.addEventLIstener(eventType, eventHandler, useCapture?useCapture:false)
    } else if(target.attachEvent){ // IE DOM
        var r = target.attachEvent("on" + eventType, evenyHandler);
    }
}

function clickHandler(event){
    var nav = document.getElementById('list');
    for(var i=0; i < nav.childNodes.length; i++){
        var child = nav.childNodes[i];
        if(child.nodeType==3)
            continue;
        child.innerText = 'Coding evetybody';
    }
}
addEvent(document.getElementById('execute_btn'), 'click', clickHandler);
```

# 함수지향

### 유효범위(scope)
- 유효범위는 변수의 수명을 의미한다.

```
var vscope = 'global';
function fscope(){
    alert(vscope);
}
fscope();
```
- 함수 밖에서 변수를 선언하면 그 변수는 전역변수가 된다.
- 전역변수는 애플리케이션 전역에서 접근이 가능한 변수다. 어떤 함수 안에서도 해당 변수에 접근이 가능하다는 것을 의미

```
var vscope = 'global';
function fscope(){
    var vscope = 'local';
    alert('함수안 '+vscope);
}
fscope(); // 함수안 local
alert('함수밖 '+vscope); // 힘수밖 global
```

```
var vscope = 'global';
function fscope(){
    vscope = 'local';
    alert('함수안'+vscope);
}
fscope(); // 함수안 local
alert('함수밖'+vscope); 함수밖 local
```
- 전역변수를 사용하지 않는 것이 좋다. 여러가지 이유로 그 값이 변경될 수 있기 때문이다. 변수를 선언할 때는 꼭 var을 붙이는 것을 습관화해야 한다.
- 만약, 전역변수를 사용해야 하는 경우라면 그것을 사용하는 이유를 명확히 알고 있을 때 사용하자


### 전역변수의 사용
```
MYAPP = {}
MYAPP.calculator = {
    'left' : null,
    'right' : null
}

MYAPP.coordinate = {
    'left' : null,
    'right' : null
}

MYAPP.calculator.left = 10;
MYAPP.calculator.right = 20;

function sum(){
    return MYAPP.calculator.left + MYAPP.calculator.right;
}
document.write(sum());
```
- 불가피하게 전역변수를 사용해야 하는 경우는 하나의 객체를 전역변수로 만들고 객체의 속성으로 변수를 관리하는 방법을 사용한다.

```
(function(){
    var MYAPP = {}
    MYAPP.calculator = {
        'left' : null,
        'right' : null
    }
    MYAPP.coordinate = {
        'left' : null,
        'right' : null
    }
    MYAPP.calculator.left = 10;
    MYAPP.calculator.right = 20;
    function sum(){
        return MYAPP.calculator.left + MYAPP.calculator.right;
    }
    document.write(sum());
}())
```
전역변수를 사용하고 싶지 않다면 위와 같이 익명함수를 호출함으로서 이러한 목적을 달성할 수 있다.

## 값으로서의 함수와 콜백

### 값으로서의 함수
- JavaScript에서는 함수도 객체다. 다시 말해서 일종의 값이다.
- 거의 모든 언어가 함수를 갖고 있는데, JavaScript의 함수가 다른 언어의 함수와 다른 점은 함수가 값이 될 수 있다는 점이다.
- 객체의 속성 값으로 담겨진 함수를 메소드(method)라고 부른다

```
function cal(func, num){
    return func(num)
}
function increase(num){
    return num+1;
}
function decrease(num){
    return num-1;
}
alert(cal(increase, 1));
alert(cal(decrease, 1));
```
- 함수는 값이기 떄문에 다른 함수의 인자로 전달 될 수도 있다.

````
function cal(mode){
    var funcs = {
        'plus' : function(left, right){return left+right},
        'minus' : function(left, right){return left-right}
    }
    return funcs[mode];
}
alert(cal('plus')(2,1)); //3
alert(cal('minus')(2,1)); // 1
````
- 함수는 함수의 리턴값으로도 사용할 수 있다.

```
var process = [
    functiom(input){return input+10;},
    function(input){return input*input;},
    function(input){return input/2;}
];
var input = 1;
for(var i = 0; i < process.length; i++){
    input = process[i](input);
}
alert(input);
```
- 배열의 값으로도 사용할 수 있다.

## 콜백

### 처리의 위임
- 값으로 사용될 수 있는 특성을 이용하면 함수의 인자로 함수를 전달할 수 있다.

### 비동기 처리
- 콜백은 비동기처리에서도 유용하게 사용된다.
- 시간이 오래걸리는 작업이 있을 때 이 작입이 완료된 후에 처리해야 할 일을 콜백으로 지정하면 해당 작업이 끝났을 때 미리 등록한 작업을 실행하도록 할 수 있다.

## 클로저

### 클로저
- 클로저(closure)는 내부함수가 외부함수의 맥락(context)에 접근할 수 있는 것을 가르킨다.

### 내부함수
- 자바스크립트는 함수 안에서 또 다른 함수를 선언할 수 있다.

```
function outter(){
    var title = "coding every";
    function inner(){
        alert(title);
    }
    inner();
}
outter();
```

- 함수 inner를 내부 함수라고 한다.
- 내부함수는 외부함수의 지역변수에 접근할 수 있다

### 클로저

- 클로저(closure)는 내부함수와 밀접한 관계를 가지고 있는 주제다.
- 내부함수는 외부함수의 지역변수에 접근 할 수 있는데 외부함수의 실행이 끝나서 외부함수가 소멸된 이후에도 내부함수가 외부함수의 변수에 접근 할 수 있다.
- 이러한 메커니즘을 클로저라고 한다.

```
function outter(){
    var title = "coding";
    return function(){
        alert(title);
    }
}
innter = outter();
intner();
```
- 원래라면 외부함수 outter의 실행이 끝나기 때문에 이 함수의 지역변수는 소멸되는 것이 자연스럽다.
- 하지만 클로저를 통해서 내부함수가 외부함수의 지역변수에 접근할 수 있고, 외부함수는 외부함수의 지역변수를 사용하는 내부함수가 소멸될 때까지 소멸되지 않는 특성을 말한다

## Arguments
함수에는 arguments라는 변수에 담긴 유사 배열이 있다. 이 배열에는 함수를 호출할 때 입력한 인자가 담겨 있다.

```
function sum(){
    var i, _sum = 0;
    for(i=0; i < arguments.lentgs; i++){
        document.write(i + " : " + arguments[i] + '<br />');
        _sum + = arguments[i];
    }
    return _sum;
}
document.write("resulte : " + sum(1,2,3,4));
```
- 함수의 정의부분에서 인자에 대한 구현이 없으에도 인자를 전달할 수 있는 것은 왜 그럴까? arguments라는 특수한 배열이 있기 때문이다.
- arguments[0]은 함수로 전달된 첫번째 인자를 알아낼 수 있다.
- arguments는 사실 배열은 아니다. 실제로는 arguments 객체의 인스턴스다.

### 매개변수의 수

```
function zero(){
    console.log(
        'zero.length', zero.length,
        'arguments', arguments.length
    );
}
function one(arg1){
    console.log(
        'one.length', one.length,
        'arguments', arguments.length
    );
}
function two(arg1, arg2){
    console.log(
        'two.length', two.length,
        'arguments', arguments.length
    );
}
zero(); // 0, 0
one('val1', 'val2'); // 1, 2
two('val1'); // 2, 1
```
- 매개변수와 관련된 두 가지 수가 있다. 
- 하나는 함수.length, 다른 하나는 arguments.length이다.
- 함수.length는 함수에 정의된 인자의 수를 미하고, arguments.length는 함수로 전달된 실제 인자의 수를 의미한다.

## 함수의 호출

```
function func(){}
func()
```
- 함수에 대한 기본적인 호출 방법은 위와 같다.
- 함수 func는 Function이라는 객체의 인스턴스다. 따라서 func는 객체 Function이 가지고 있는 메소드들을 상속하고 있다.

```
function sum(arg1, arg2){
    return arg1+arg2;
}
alert(sum.apply(null, [1,2])); // 3
```
- Function.apply와 Function.call 메소드
- 첫 번쨰 인자는 함수(sum)가 실행될 맥락이고, 두 번째 인자는 배열이다. 
- apply는 sum이라는 함수 객체 담겨있는 메소드이다.

```
o1 = {val1 : 1, val2 : 2, val3 : 3}
o2 = {v1 : 10, v2 : 50, v3 : 100, v4 : 25}
function sum(){
    var _sum = 0;
    // var this = o1, o2;
    for(name in this){
        _sum += this[name];
    }
    return _sum;
}
alert(sum.apply(o1)); // 6sum() // o1.sum
alert(sum.apply(o2)); // 185sum() // o2.sum
```
- 함수 sum은 객체의 속성을 열거할 때 사용하는 for in 문을 이용해서 객체 자신(this)의 값을 열거한 후에 각 속성의 값을 지역변수 _sum에 저장한 후에 이를 리턴하고 있다.

```
o1.sum = sum;
alert(o1.sum());
delete o1.sum();
```
- 객체 Function의 메소드 apply의 첫번째 인자는 함수가 실행될 맥락이다. sum.apply(o1)은 함수 sum을 객체 o1의 메소드로 만들고 sum을 호출한 후에 sum을 삭제한다.
- sum의 o1 소속의 메소드가 된다는 것은 이렇게 바꿔 말할 수 있다. 함수 sum에서 this의 값이 전역객체가 아니라 o1이 된다는 의미다. 
- 일반적인 객체지향 언어에서는 하나의 객체에 소속된 함수는 그 객체의 소유물이 된다. 하지만 JavaScript에서 함수는 독립적인 객체로서 존재하고, apply나 call 메소드를 통해서 다른 객체의 소유물인 것처럼 실행할 수 있다.

## 객체지향 프로그래밍

- 객체 지향 프로그래밍(Object-Oriented Programming, OOP)은 로직을 상태(state)와 행위(behave)로 이루어진 객체로 만드는 것
- 이 객체들을 마치 레고 블록처럼 조립해서 하나의 프로그램을 만드는 것
- 객체는 변수와 메소드를 그룹핑한 것이다. (어렵게 생각하지 말자)
- 프로그래밍은 여러개의 목적성을 가지고 있는 로직들의 집합이라고 할 수 있다. ex) 글 목록, 본문, 댓글 등..

### 설계
- 좋은 객체를 만드는 법 (=설계를 잘하는 법)
- 좋은 설계는 현실을 잘 반영해야 한다. 현실은 복잡하다. 하지만 그 복잡함 전체가 필요한 것이 아니다.
- ex)지하철 노선도 (우리가 필요한 정보만을 잘 전달해주고 있음)
- 현실의 복잡성을 제거하고 우리에게 필요한 관점(정보)만을 추출하는 행위를 추상화(abstract)라고 한다

### 부품화
- 초창기의 컴퓨터는 본체, 모니터, 키보드가 하나로 단일화되어 있다. 이는 각 부품 중 하나라도 고장이나면 컴퓨터를 교체해야 함을 뜻한다.
- 최신 컴퓨터는 본체, 모니터, 키보드가 다 분리되어 있다. 즉, 부품화 시킨 것이다.
- 모니터와 키보드 그리고 본체를 분리하는 기준을 세우는 것이 추상화이다.
- 메소드는 부품화의 예라고 할 수 있다. 메소드를 사용하면 코드의 양을 극적으로 줄일 수 있고, 메소드 별로 기능이 분류되어 있기 때문에 필요한 코드를 찾기도 쉽고 문제 진단도 빨라진다.
- 하지만 소프트웨어가 점점 거대해 지면서 메소드와 변수를 관리하는 것이 점점 어려운 일이 되었다.
- 그래서 객체 지향 프로그래밍 개념이 등장했고, 연관된 메소드와 그 메소드가 사용하는 변수들을 분류하고 그룹핑하게 되었다.
- 그룹핑 한 대상을 객체(Object)라고 한다.
- 파일과 디렉토리가 있을 때 메소드나 변수가 파일이라면 이 파일을 그룹핑하는 디렉토리가 객체라고 할 수 있다.

### 은닉화, 캡슐화
- 객체가 어떻게 생겼는지를 모르고도 객체를 사용할 수 있도록 하는 것을 은닉화(Information Hiding) 또는 캡슐화(Encapsulation)라고 한다.
- 내부의 동작 방법을 단단한 케이스 안으로 숨기고 사용자에게는 그 부품의 사용 방법만을 노출시키는 것 (케이스 = 객체, 부품 = 메소드)

### 인터페이스
- 잘 만들어진 부품은 부품과 부품을 교체할 수 있어야 한다
- 모니터를 쓰다가 고장나서 다른 모니터로 교체해서 똑같이 이용할 수 있는 이유는 모니터와 컴퓨터를 연결시켜주는 케이블이 표준화 되어있기 때문이다.
- 이러한 연결점을 인터페이스(interface)라고 한다. 
- 인터페이스는 부품들간의 약속이다.

## 생성자와 new

### 객체
- 객체란 서로 연관된 변수와 함수를 그룹핑한 그릇이라고 할 수 있다.
- 객체 내의 변수를 프로퍼티(property), 함수를 메소드(method)라고 부른다.

```
객체를 만드는 방법 (1)

var person = {}
person.name = 'egoing';
person.introduce = function(){
    return 'My name is '+this.name;
}
document.write(person.introduce());

객체를 만드는 방법 (2)
var person = {
    'name' : 'egoing',
    'introduce' : function(){
        return 'My name is '+this.name;
    }
}
document.write(person.introduce());
```

### 생성자
- 생성자(constructor)는 객체를 만드는 역할을 하는 함수다. 자바스크립트에서 함수는 재사용 가능한 로직의 묶음이 아니라 객체를 만드는 창조자라고 할 수 있다.

```
function Person(){}
var p1 = new Person();
p1.name = 'egoing';
p1.introduce = function(){
    return 'My name is '+this.name; 
}
document.write(p1.introduce()+"<br />");
 
var p2 = new Person();
p2.name = 'leezche';
p2.introduce = function(){
    return 'My name is '+this.name; 
}
document.write(p2.introduce());
```
- 함수를 호출할 때 new를 붙이면 새로운 객체를 만든 후에 이를 리턴한다.

```
function Person(name){
    this.name = name;
    this.introduce = function(){
        return 'My name is '+this.name; 
    }   
}
var p1 = new Person('egoing');
document.write(p1.introduce()+"<br />");
 
var p2 = new Person('leezche');
document.write(p2.introduce());
```
- 생성자 내에서 이 객체의 프로퍼티를 정의하고 이다. 이러한 작업을 초기화라고 한다. 이를 통해 코드의 재사용성을 높였다.
- 생성자 함수는 일반함수와 구분하기 위해서 첫글자를 대문자로 표시한다.

### 자바스크립트 생성자의 특징
- 일반적인 객체지향 언어에서 생성자는 클래스의 소속이다. 하지만 자바스크립트에서 객체를 만드는 주체는 함수다. 함수에 new를 붙이는 것을 통해서 객체를 만들 수 있다는 점은 자바스크립트에서 함수의 위상을 암시하는 단서이면서 또 자바스크립트가 추구하는 자유로움을 보여주는 사례라고 할 수 있다.

## 전역객체

### 전역객체란?
- 전역객체(Global object)는 특수한 객체다. 모든 객체는 이 전역객체의 프로퍼티다.

```
var o = {'func':function(){
	alert('Hello');
    }}
o.func();
window.function();
```
- 모든 전역 변수와 함수는 window 객체의 프로퍼티다.
- 객체를 명시하지 않으면 암시적으로 window의 프로퍼티로 간주된다.
- 자바스크립트에서 모든 객체는 기본적으로 전역객체의 프로퍼티임을 알 수 있다. (객체지향-모든 것이 객체에 소속되어 있기 때문에)

### 전역객체의 API
- ECMAScript에서는 전역객체의 API를 정의해두었다. 그 외의 API는 호스트 환경에서 필요에 따라서 추가로 정의하고 있다. 이를테면 웹브라우저 자바스크립트에서는 alert()이라는 전역객체의 메소드가 존재하지만 node.js에는 존재하지 않는다. 
- 또한 전역객체의 이름도 호스트환경에 따라서 다른데, 웹브라우저에서 전역객체는 window이지만 node.js에서는 global이다. 

## this
- this는 함수 내에서 함수 호출 맥락(context)을 의미한다.
- 맥락이라는 것은 상화에 따라서 달라진다는 의미인데, 즉 함수를 어떻게 호출하느냐에 따라서 this가 가르키는 대상이 달라진다는 뜻이다.
- 함수와 객체의 관계가 느슨한 자바스크립트에서 this는 이 둘을 연결시켜주는 실질적인 연결점의 역할을 한다

### 함수호출

```
function func(){
	if(window === this) {
    	console.log("window === this");
    }
}
func(); // window === this
```
- this는 전역객체인 window와 같다.

### 메소드의 호출

```
var o = {
	func : function(){
    	if( o === this ) {
        	console.log("o === this");
        }
    }
}
o.func(); // o === this
```
- 객체의 소속인 메소드의 this는 그 객체를 가리킨다.
- (=함수 안에서 this라는 키워드는 그 함수가 소속되어 있는 객체를 가리킨다)

### 생성자의 호출
```
var funcThis = null;

function Func(){
	funcThis = this;
}
var o1 = Func(); // 일반 함수
if(funcThis === window){
	document.write('window <br />');
}
var o2 = new Func(); // 생성자 함수
if(funcThis === o2){
	document.write('o2 <br />');
}
```
- 함수를 호출하면, 그 함수는 window라는 객체의 메소드 이기 때문에 this는 window를 가리킨다.
- 생성자는 빈 객체를 만든다. 그리고 이 객체내에서 this는 만들어진 객체를 가르킨다. (new라는 생성자를 붙이면 JS는 내부적으로 비어있는 객체를 만들고, 비어있는 객체가 그 생성자 안에서의 this가 된다.)
```
function func(){
	document.write(o);
}
var o = new Func(); // undefined
```
- 생성자가 실행되기 전까지 객체는 변수에도 할당될 수 없기 때문에 this가 아니면 객체 대한 어떠한 작업을 할 수 없다. (중요!)

### apply, call
```
var o = {}
var p = {}
function func(){
	switch(this){
    	case o:
        	document.write('o<br />');
            break;
        case p:
        	document.write('p<br />');
            break;
        case window:
        	document.write('window<br />');
            break
     }
}
func(); // window
func.apply(o); // o
func.apply(p); // p
```
- 전통적인 객체지향 언어에서 메소드(slave)는 객체(master)에 소속되어 있었다.
- 하지만 JS에서 함수가 객체 이기도하고, 함수를 어떻게 호출하느냐에 따라 객체 window, o, p에 소속되기도 한다.

## 상속

### 상속(inheritance)이란?
- 객체는 연관된 로직들로 이루어진 작은 프로그램이라고 할 수 있다.
- 상속은 객체의 로직을 그대로 물려 받는 또 다른 객체를 만들 수 있는 기능을 의미한다. 단순히 물려받는 것 뿐만 아니라 기존의 로직을 수정하고 변경해서 새로운 객체를 만들 수 있게 해준다.

```
fuction Person(name){
	this.name = name;
}
Person.prototype.name = null;
Person.prototype.introduce = function(){
	return "My name is " + this.name;
}
function Programmer(name){
	this.name = name;
}
Programmer.prototype = new Person();

var p1 = new Person('egoing');
document.write(p1.introduce()+"<br />");
```
- Programmer라는 생성자를 만들었다. 이 생성자의 prototype과 Person의 객체를 연결했더니 Progrmmaer 객체도 메소드 introduce를 사용할 수 있게 되었다.
- Programmer가 Person의 기능을 상속하고 있는 것이다.

```
function Person(name){
	this.name = name;
}

Person.prototype.name = null;
Person.prototype.introduce = function(){
	return "My name is " + this.name;
}

function Programmer(name){
	this.name = name;
}
Programmer.prototype = new Person();
Programmer.prototype.coding = function(){
	return "hello world";
}

function Designer(name){
	this.name = name;
}
Designer.prototype = new Person();
Designer.prototype.design = function(){
	return "beautiful!";
}

var p1 = new Programmer("inseop");
document.write(p1.introduce()+"<br />");
document.write(p1.coding()+"<br />");

var p2 = new Designer("jaywon");
document.write(p2.introduce()+"<br />");
document.write(p2.design()+"<br />");
```
- Programmer는 Person의 기능을 가지고 있으면서 Person이 갖고 있지 않은 기능인 메소드 coding을 갖고 있다.

## prototype

### prototype
- prototype은 일반적인 객체지향 언어와 다른 가장 큰 차이점이다
- prototype은 원형이라는 뜻으로 말 그대로 객체의 원형이라고 할 수 있다.
- 함수는 객체다. 그러므로 생성자로 사용될 함수도 객체다.
- 객체는 프로퍼티를 가질 수 있는데 prototype이라는 프로퍼티는 그 용도가 약속되어 있는 특수한 프로퍼티다.
- prototype에 저장된 속성들은 생성자를 통해서 객체가 만들어질 때 그 객체에 연결된다.
- 생성자 new의 역할은 비어있는 객체를 만드는 역할을 한다.

```
// prototype chain 이라고 한다.
function Ultra(){}
Ultra.prototype.ultraProp = true;

function Super(){}
Super.prototype = new Ultra();

function Sub(){} 
Sub.prototype = new Super();

var o = new Sub();  
console.log(o.ultraProp); // true
```
- 생성자 Sub를 통해서 만들어진 객체 o가 Ultra의 프로퍼티 ultraProp에 접근 가능한 것은 prototype 체인으로 Sub와 Ultra가 연결되어 있기 때문이다.
- 1.객체 o에서 ultraProp를 찾는다
- 2.없다면 Sub.prototype.ultraProp를 찾는다
- 3.없다면 Super.prototype.ultraProp를 찾는다
- 4.없다면 Ultra.prototype.ultraProp를 찾는다
- prototype는 객체와 객체를 연결하는 체인의 역할을 한다. 이러한 관계를 prototype chain이라고 한다.

```
*주의*
Super.prototype = Ultra.prototype으로 하면 안된다. 이렇게하면 Super.prototype의 값을 변경하면 그것이 Ultra.prototype의 값도 변경하기 때문이다. Super.prototype = new Ultra();는 Ultra.prototype의 원형으로 하는 객체가 생성되기 때문에 new Ultra()를 통해서 만들어진 객체에 변화가 생겨도 Ultra.prototype의 객체에는 영향을 주지 않는다.
```

## 표준 내장 객체의 확장
- 표준 내장 객체(Standard Built-in Object)는 자바스크립트가 기본적으로 가지고 있는 객체들을 의미한다.
- 내장 객체가 중요한 이유는 프로그래밍을 하는데 기본적으로 필요한 도구들이기 때문이다.

**자바스크립트는 아래와 같은 내장 객체를 가지고 있다.**
	- Object
	- Function
	- Array
	- String
	- Boolean
	- Number
	- Math
	- Date
	- RegExp

### 배열을 확장
```
var arr = new Array("seoul", "newyork", "pusan", "london", "ladarkh");
function getRandomValueFromArray(arr){
	var index = Math.floor(arr.length*Math.random());
    return arr[index];
}
console.log(getRandomVelueFromArray(arr));
```
- 위 방식을 조금 더 세련되게 개선할 수 있다.
- 이 함수를 배열 객체에 포함시키는 것이다. 그렇게하면 마치 배열에 내장된 메소드인 것처럼 위의 기능을 사용할 수 있다.

```
Array.prototype.rand = function(){
	var index = Math.floor(this.length*Math.random());
    return this[index];
}
var arr = new Array("seoul", "newyork", "pusan", "london", "ladarkh");
console.log(arr.rand());
```

## Object

### Object란?
- Object 객체는 객체의 가장 기본적인 형태를 가지고 있는 객체이다. (데이터를 저장하는 그릇, container)
- 다시 말해서 아무것도 상속받지 않는 순수한 객체다.
- JS에서는 값을 저장하는 기본적인 단위로 Object를 사용한다.

```
var grades = {'inseop':10, 'jaywon':20, 'seope':30}; // 객체를 만들고 변수에 저장
```
- 자바스크립트의 모든 객체는 Object 객체를 상속 받는데, 그런 이유로 모든 객체는 Object 객체의 프로퍼티를 가지고 있다.

### Object API 사용법
```
// Object.keys()
var arr = ["a", "b", "c"];
console.log('Object.keys(arr)', Object.keys(arr));

//Object.prototype.toString()
var o = new Object();
console.log('o.toString()', o.toString());

var a = new Array();
console.log('a.toString()', a.toString());
```
- Object는 모든 객체의 부모이기 때문에, a.toString()처럼 접근이 가능하다.

- [Mozilla JavaScript MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript)에 가면 기술 명세를 볼 수 있다. (사용 가능한 API 버전 등..)

### Object 확장

```
Object.prototype.contain = function(needle){
	for(var name in this){
    	if(this[name] === needle){
        	return true;
        }
    }
    return false;
}
var o = {'name':'seop', 'city':'seoul'};
console.log(o.contain('seop'); // true
var a = ['seop', 'jaywon', 'seope'];
console.log(a.contain('seop'); // true

for (var name in a){
	if(a.hasOwnProperty(name){
    	console.log(name);
    }
}
```
- Object객체는 확장하지 않는 것이 바람직하다. 왜냐하면 모든 객체에 영향을 주기 때문이다. 
- 위에서는 문제가 있다. 확장한 프로퍼티인 contain이 포함되어 있기 때문이다.
- 이 문제를 회피하기 위해서 프로퍼티의 해당 객체의 소속인지를 체크해볼 수 있는 hasOwnProperty를 사용하면 된다.
- 만약 prototype으로 상속 받은 객체라면 false가 된다.

## 데이터 타입

### 원시 데이터 타입
- 데이터 타입이란 데이터의 형태를 의미한다. 데이터 타입은 크게 두가지로 구분할 수 있다. 객체와 객체가 아닌 것, 그럼 객체가 아닌 것은 무엇일까?
	- 숫자
	- 문자열
	- Boolean (true/false)
	- null
	- undefined
- 객체가 아닌 데이터 타입을 원시 데이터 타입(primitive type)이라고 한다. 그 외의 모든 데이터 타입들은 객체다.

### 레퍼 객체(wrapper object)
```
var str = 'coding'; // = new String('coding');
console.log(str.length); // 6
console.log(str.charAt(0)); // "C"
```
- 문자열은 분명히 프로퍼티와 메소드가 있다. 그렇다면 객체다. 그런데 왜 문자열이 객체가 아니라고할까?
- 그것은 내부적으로 문자열이 원시 데이터 타입이고 문자열과 관련된 어떤 작업을 하려고 할 때 자바스크립트는 임시로 문자열 객체를 만들고 사용이 끝나면 제거하기 때문이다. (이러한 처리는 내부적으로 일어난다)

```
var str = 'coding';
str.prop = 'everybody'; // 이 열이 끝나면 객체 제거됨
console.log(str.prop); // undefined
```
- str.prop를 하는 순간 자바스크립트 내부적으로 String 객체가 만들어진다.
- prop 프로퍼티는 이 객체에 저장되고 이 객체는 곧 제거된다. 그렇기 때문에 prop라는 속성이 저장된 객체는 존재하지 않게된다. 이러한 특징은 일반적인 객체의 동작 방법과는 다르다.
- 하지만 문자열과 관련해서 필요한 기능성을 객체지향적으로 제공해야 하는 필요 또한 있기 때문에 원시 데이터 형을 객체처럼 다룰 수 있도록 하기 위한 객체를 자바스크립트는 제공하고 있는데 그것이 레퍼객체(wrapper object)다.
- 레퍼객체로는 String, Number, Boolean이 있다. null과 undefined는 레퍼 객체가 존재하지 않는다.

## 참조

### 복제
- 전자화된 시스템의 가장 중요한 특징은 복제다.
```
var a = 1; // 원시 데이터 타입
var b = a;
b = 2;
console.log(a); // 1
```
- 파일을 복사했다고 했을 때, 복사한 파일을 변경해도의 그 파일의 원본은 바뀌지 않는 것과 같은 개념

### 참조(reference)
```
var a = {'id':1}; // 객체 (참조 자료형)
bar b = a;
b.id = 2;
console.log(a.id); // 2

var a = {'id':1}; // 객체
bar b = a;
b = {'id':2}; // 객체 생성 (새롭게 객체를 생성한 것)
console.log(a.id); // 1
```
- 컴퓨터의 파일로 치면 바로가기 기능을 활용했다라고 생각하면 된다. (참조!)
- 기본 데이터형(원시 데이터형)은 복제되지만, 참조 데이터형(객체)는 참조된다.
- 데이터가 원시형이면 그 안에는 실제 데이터가 들어있고, 객체면 변수 안에는 데이터에 대한 참조 방법이 들어있다고 할 수 있다.

### 함수
- 일종의 변수할당이라고 할 수 있는 메소드의 매개변수는 어떻게 동작하는가를 살펴보자.
```
var a = 1; // a=1
function func(b){
	b = 2;
} // b=2
func(a); // b=a;
console.log(a); // a=1
```
- 원시 데이터 타입을 인자로 넘겼을 떄 동작 모습

```
var a = {'id':1}; // a={'id':1}
function func(b){ 
	b = {'id':2};
} // b={'id':2}
func(a); // a=b;
console.log(a.id); // 1 (a와 b가 모두 새로운 객체를 생성했기 때문에)
```
- 참조 데이터 타입을 인자로 넘겼을 때 동작 모습

```
var a = {'id':1}; // a={'id':1}
function func(b){
	b.id = 2;
} // b.id=2;
func(a); // a=b;
console.log(a.id); // 2
```
- 파라미터 b는 객체 a의 레퍼런스다. 이 값의 속성을 바꾸면 그 속성이 소속된 객체를 대상으로 수정작업을 한 것이 되기 때문에 b의 변경은 a에도 영향을 미치게 된다.

## 패턴
- 패턴은 자주 사용하는 로직들의 구현방법과 그것에 대한 이름을 의미한다.
- 이를 통해서 문제를 해결하는 탁월한 방법들을 빠르게 익힐 수 있다. 또한, 문제를 해결하기 위한 방법을 논의 할 때 패턴의 이름을 사용함으로써 의사소통을 효율적으로 할 수 있다.

### 재귀함수
- 재귀함수는 함수 자신을 호출하는 프로그래밍 기법이다

reference
- [생활코딩 JS 언어 수업](https://opentutorials.org/course/743/4650)