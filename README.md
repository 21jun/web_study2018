# 자바 스크립트


## 특징
1. 웹브라우저에서 인터프레팅으로 실행
2. 객체기반
3. HTML 내에 포함되어 작성됨
4. 변수의 선언필요X 타입검사 느슨함

## 사용
1. 웹문서 내장 방식
    <script type = "text/javascript">
      //자바스크립트 코드
    </script>
2. 외부파일 참조 방식
    <script type="text/javascript" src="myscript.js"></script>
    <script type="text/javascript" src="http://webclass.me/html5/javascript_example.js"></script>


## 변수

### var로 변수선언을 하는 경우

1. 영구적이다. (delete연산자로 변수를 지울 수 없다.)

2. 지역변수이다.

### var를 생략하고 변수를 선언하는 경우

1. delete연산자로 변수를 지울 수 있다.

2. 전역변수이다. (실제로는 아래와 같은 과정을 거친다)

선언하려는 변수가 바로 위의 scope에 존재하는지 확인하고 없으면 그 위, 없으면 그 위, 없으면 그 위, 반복하다가 global영역까지도 없다면 global영역에 변수선언하게 된다.

### 변수에 저장된값에 따라 변수 타입결정
    var a = "3";            //String
    var b = 2;              //Number
    var c = b + 3 + a;      //String  b+3 연산후 +"3" 문자열붙이기 수행됨
    var d = a + b;          //String  a가 먼저들어가서 "3" + 문자열로 변환된 b ="2" / "32"

+ 변수 형 변환
    String -> Number : parseInt(str), parseFloat(str)
    Number -> String : .toString() 메소드
+ 변수 타입은 5개만 존재
    Number(float), String, Boolean, Undefined, Null
+ typeof() 연산자로 변수 타입 확인가능


## 연산자


### 비교 연산자

#### ==, != 연산자

    좌항과 우항의 값만 비교함
    "2"==2          // true
    true == '1'     // true

#### ===, !== 연산자 

    좌항과 우항의 값과 타입을 비교함
    "2"==2          // false
    true === '1'    // false

## 반복문
1. 객체에 포함된 속성의 갯수나 이름을 모르더라도 객체내의 모든 속성을 접근할 수 있는 방법
2. 개선된 for문 안의 조건식은 (변수 in 객체)로 사용 : 객체의 개수만큼 반복
###

    for (var p in book) {
        document.write( "Property name: " + p + " Property value: " + book[p] + "<br/>");
    }

3. 개선된 for문에서는 변수명을 이용한 객체 접근은 (.)으로 불가능
    []을 사용해야함 (속성의 실제이름을 모르니까 .속성이름 불가능)


## 함수

함수(function)란 하나의 로직을 재실행 할 수 있도록 하는 것으로 코드의 재사용성을 높여준다.
매개변수의 자료형을 규정하지 않는다.
매개변수의 인수의 변수형/개수가 같은지 검사하지 않는다
+ 인수 개수보다 매개변수의 개수가 적다면 남은 인수는 Undefined로 설정

### 함수의 형식
#### (1) 
    function functionName (param){
        ...
        return;
    }
#### (2)
    var fucntionName = function(param){
        ...
        return
    }

### 인자 
+ 다중인자 받는방법
###

    function functionName (param1, param2){
        ...
        return;
    }


## 배열

### 배열 생성

1. 배열 리터럴 []
###

    var arr[100];
    var arr = [1,2,3,4,5,6,7];

2. 배열 객체 생성 Array()
###

    var arr = new Array(100);
    var arr = new Array(1,"Hello World", 3, [1,2,3], 5);


### 배열 속성 & 메소드

    arr.length              //배열 크기
    arr.sort()              //배열 내 요소들의 순서를 오름차순으로 정렬한다. 숫자가 문자보다 앞선다.
    arr.concat()            //배열의 뒤에 요소를 붙인다. (concatenation)
    arr.slice()             //배열의 요소들 중 일부만을 배열로 만든다.
    arr.push()              //배열에 가장뒤에 인자를 삽입한다.
    arr.unshift()           //배열에 가장앞에 인자를 삽입한다
    arr.pop()               //배열의 가장뒤의 원소를 삭제(하고 리턴)
    arr.shift()             //배열의 가장앞의 원소를 삭제(하고 리턴)


## 객체
자바스크립트에서 모든것이 객체이다. (클래스가 존재하지 않음)
상속은 클래스->클래스가 아닌 객체->객체로 이뤄진다.

### 1. 객체 리터럴 {}

    var obj = {};
    
    var obj = new Object();
    
    var obj = {'height':100, 'weight':200};

    var obj = {
        type: "fruit",
        color: "red",
        getColor: function(){
            return this.color;
        }
    }

    // 이렇게 생성할경우 인스턴스할 필요없이 obj를 바로 사용하면됨 (이미 변수로 생성됨)

### 2. 함수를 이용한 생성

    function Apple (param){
        this.name = param;                  //this.변수 로 속성생성
        this.color = 'red';
        this.getColor = function(){         //메소드 정의
            return this.color;
        }
    }

    var a = Apple("myApple");
    a.getName = function(){ return this.name }  //메소드 추가
    a.weight = 10                               //속성 추가




### 접근
1. obj['키값'] 으로 접근가능
2. obj.키값 으로 접근가능


## 모듈
자주 사용되는 코드를 별도의 파일로 만들어서 필요할 때마다 재활용할 수 있다.

### 모듈 사용
(자바스크립트 외부파일 참조)
#### module1.js
    function myFunction(){
        ...
        return 
    }

#### index.html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8"/>
        <script src="module.js"></script>       //모듈 불러오기
    </head>
    <body>
        <script>
            myFunction();                       //모듈 호출
        </script>
    </body>
    </html>

#### jQuery 라이브러리 사용
    <!DOCTYPE html>
    <html>
    <head>
        <script src="https://code.jquery.com/jquery-1.11.0.min.js"></script>
        <!-- jQuery 불러오기 -->
    </head>
    <body>
        <ul id="list">
            <li>empty</li>
            <li>empty</li>
            <li>empty</li>
            <li>empty</li>
        </ul>
        <input id="execute_btn" type="button" value="execute" />
        <script type="text/javascript">
        $('#execute_btn').click(function(){
            $('#list li').text('coding everybody');
        })
        </script>
    </body>
    </html>

## 정규표현식 (regular expression)

문자열에서 특정한 문자를 찾아내는 도구
<br>
정규표현식 시각화 : https://regexper.com/
정규표현식 테스트 : https://regexr.com/
### 정큐표현식 사용방법

#### 컴파일
검출하고자 하는 문자열에서 패턴을 만듬
1. 정규표헌식 리터럴 사용 /찾을문자/
<br>    var pattern = /찾을문자/;
2. 정규표헌식 객체 생성자
<br>    var pattern = new RegExp('찾을문자');

#### 정규 표현식 메소드 실행
##### 원하는 패턴을 추출
    RegExp.exec('검색할 문자열')
    -> pattern.exec('...')
##### 원하는 패턴이 있는지 확인
    RegExp.test('검색할 문자열')
    -> pattern.test('...')

#### 문자열 메소드 실행
##### 원하는 패턴을 추출
    String.match(pattern)
    ->'검색할 문자열'.match(pattern)
##### 원하는 패턴을 치환
    String.replace(pattern, newString)
    ->'검색할 문자열'.replace(pattern, newString)

#### 정규표현식 옵션

##### i 를 붙이면 대소문자를 구분하지 않는다
    var pattern = /a/i;
##### g 를 붙이면 검색된 모든 결과를 리턴한다 (없을땐 맨앞한개 리턴)
    var pattern = /a/g;
##### 옵션은 중첩사용 가능하다
    var pattern = /a/ig;


#### 캡쳐
    괄호안의 패턴은 마치 변수처럼 재사용할 수 있다.
    $기호를 사용하여 그룹을 선택
    var pattern = /(\w+)\s(\w+)/;
    var str = "coding everybody";
    var result = str.replace(pattern, "$2, $1");  // 치환함
    console.log(result);
    >>> "everybody, coding"


### 전역변수
#### 자바스크립트는 "함수"에 대한 유효범위만을 제공함
    for(var i = 0; i < 1; i++){
        var name = 'coding everybody';
    }
    alert(name);

반복문 안에서 생성한 name 변수는 for문 밖에서 사용가능

+ for문 안에 var i 도 계속해서 존재하는데, let i 로 선언하게되면 for문이 끝나고 소멸된다

#### 전역변수를 사용해야 하는경우
1. 전역으로 객체를 만들고 해당 객체의 속성으로 변수를 관리한다
##
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
2. 익명함수를 호출하여 사용
    정의와 동시에 바로 호출됨 (맨 밑에 () 으로)
##
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



## 값으로서의 함수 

자바스크립트에선 모든것이 객체이기 떄문에 함수또한 객체이다 (일종의 값)

### 함수는 다른 함수의 인자로 전달 될 수 있다.
    function cal(func, num){
        return func(num)
    }
    function increase(num){
        return num+1
    }
    function decrease(num){
        return num-1
    }
    alert(cal(increase, 1));        //인자로 increase 함수 전달
    alert(cal(decrease, 1));

### 함수는 다른 함수의 리턴 값으로 사용될 수 있다.
    function cal(mode){

        //funcs 객체 (함수)
        var funcs = {
            // 키 : 벨류
            'plus' : function(left, right){return left + right},
            'minus' : function(left, right){return left - right}
        }
        return funcs[mode];         //funcs 객체의 키값으로 mode 전달
    }
    alert(cal('plus')(2,1));        //funcs 객체의 키값으로 mode = 'plus' 전달  => function(2,1) 호출
    alert(cal('minus')(2,1));   

### 콜백
#### 배열의 sort 메소드 콜백
    //숫자를 정렬하는 방법
    function sortfunc(b,a) {
      return b-a;                       //리턴값이 0,양수, 음수 에따라 sort함수의 동작이 바뀜
    }

    var numbers = [20, 10, 9,8,7,6,5,4,3,2,1];

    numbers.sort(sortfunc);             //콜백함수 지정

    >>> 1,2,3,4,5,6,7,8,9,10,20         //숫자순으로 정렬됨

    numbers.sort();                     //콜백함수 없이 호출

    >>> 1,10,2,20,3,4,5,6,7,8,9         //기본은 아스키코드순으로 정렬


## 클로저 (closure)

내부함수가 외부함수의 맥락(context)에 접근할 수 있게 하는 것.

### 내부함수

    function outter(){                  //외부함수
        var title = 'coding everybody';  
        function inner(){               //내부함수
            alert(title);               //내부함수가 외부함수의 title 변수에 접근가능함
        }
        inner();    
    }
    outter();

### 외부함수가 소멸되면 
    function outter(){
        var title = 'coding everybody';  
        return function(){              //내부함수를 반환함
            alert(title);
        }
    }
    inner = outter();                   //내부함수를 inner에 저장 (outer 함수 소멸)
    inner();                            //내부함수를 호출 -> 외부함수의 title 값이 보존되어있음

+ C++상속과 비슷하게 작동

### private 변수 

    function factory_movie(title){      //외부함수의 지역변수인 title은 외부에서 변경불가 (리턴하고 외부함수 소멸)
        return {                        //객체를 리턴함
            get_title : function (){    //키값이 get_title 벨류가 function()...
                return title;           //title 변수가 클로저로 인해 계속 존재함
            },
            set_title : function(_title){
                title = _title          //title 변수가 클로저로 인해 계속 존재함
            }
        }
    }

    ghost = factory_movie('Ghost in the shell');
    matrix = factory_movie('Matrix');

    ghost.title = "공각기동대"           //변경되지 않음(접근불가)
    ghost.set_title('공각기동대');       //private 변수인 title을 변경함


### + 변수 유효범위로 인한 오류

    var arr = []
    for(var i = 0; i < 5; i++){
        arr[i] = function(){
            return i;               //이때 i는 전역변수인 var i 를 가르킨다
        }
    }
    
    for(var index in arr) {
        console.log(arr[index]()); //전역 변수 i의 값이 5이므로 모두 5를 출력
    }

#### 클로저 이용

    var arr = []
    for(var i = 0; i < 5; i++){
        arr[i] = function(id){      //함수 선언
            return function(){
                return id;          //id는 외부함수의 지역변수(인자값)이므로 클로저로 인해 접근할수 있고 
                                    //외부함수가 소멸되어도 존재함
            }
        }(i)                        //여기서 호출시 i넣어줌 외부함수를 만들어 id에 반복당시의 i값 저장
    }
    
    for(var index in arr) {
        console.log(arr[index]());  // 0~4 출력함
    }

#### let 이용 ???

    var arr = []
    for(let i = 0; i < 5; i++){     //이때 i는 지역변수인 let i 를 가르킨다
        arr[i] = function(){
            return i;
        }
    }
    
    for(var index in arr) {
        console.log(arr[index]());  // 0~4 출력함
    }

## arguments

위에서 언급했듯이 자바스크립트는 함수의 인자의 갯수를 검사하지 않음

    function sum(){                                         //매개변수로 아무것도 적지 않음 (파이썬에서 *args **kwargs 와 비슷한 역할)
        var i, _sum = 0;    
        for(i = 0; i < arguments.length; i++){              //arguments 변수는 이미 정의되어있는 변수임
            document.write(i+' : '+arguments[i]+'<br />');  //arguments 는 사용자가 전달한 모든 인자를 저장한 유사배열
            _sum += arguments[i];
        }   
        return _sum;
    }
    document.write('result : ' + sum(1,2,3,4));             //인자로 4개의 숫자 전달함

+ arguments는 사실 배열은 아니다. 실제로는 arguments 객체의 인스턴스다.
+ arguments.length : 전달받은 매개변수의 갯수

### 매개변수와 인자의 수

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

    zero(); // zero.length 0 arguments 0                    //함수이름.length 하면 함수의 매개변수의 갯수,
    one('val1', 'val2');  // one.length 1 arguments 2       //arguments.length 하면 실제로 전달받은 인자의 갯수
    two('val1');  // two.length 2 arguments 1               //함수이름.length != arguments.length 가 다를때 예외처리 가능


## 함수의 호출
자바스크립트의 모든 것은 객체이므로 함수 또한 객체이고 내장메소드로 apply, call 등이 있다
### 기본적인 함수 호출
    function func(){
        ...
    }

    func();

### apply메소드를 사용한 함수 호출
    function func(a,b){
        return a+b
    }

    func.apply(null,[1,2]);

### apply 메소드의 인자

    o1 = {val1:1, val2:2, val3:3}
    o2 = {v1:10, v2:50, v3:100, v4:25}

    function sum(){
        var _sum = 0;
        for(name in this){              //this는 전달받은 인자로 치환됨
            _sum += this[name];
        }
        return _sum;
    }
    alert(sum.apply(o1)) // 6           
    alert(sum.apply(o2)) // 185         

#### 기본 호출로 바꿀려면...
    o1 = {val1:1, val2:2, val3:3}
    o2 = {v1:10, v2:50, v3:100, v4:25}
    function sum(o){
        var _sum = 0;
        for(name in o){
            _sum += o[name];
        }
        return _sum;
    }
    alert(sum(o1)) // 6
    alert(sum(o2)) // 185


## 객체지향 

### 객체 생성방법
#### 1 생성이후 속성을 추가
    var person = {}
    person.name = 'egoing';
    person.introduce = function(){
        return 'My name is '+this.name;
    }
    document.write(person.introduce());

#### 2 속성명:속성 으로 초기화
    var person = {
        'name' : 'egoing',
        'introduce' : function(){
            return 'My name is '+this.name;
        }
    }
    document.write(person.introduce());

### 생성자와 new연산자

    function Person(name){                      //함수의 파라메터가 생성자 역할을 한다
        this.name = name;   
        this.introduce = function(){
            return 'My name is '+this.name; 
        }   
    }
    var p1 = new Person('egoing');              //이미 정의된 객체를 new 연선자로 생성함(instance), 생성자또한 불림
    document.write(p1.introduce()+"<br />");
    
    var p2 = new Person('leezche');
    document.write(p2.introduce());

함수 호출시 new 연산자를 사용하면 생성자로 작동한다 (함수로 만들어진 객체 리턴함)    

### 전역객체 (Global object)
    function func(){
        alert('Hello?');    
    }
    func();
    window.func();

    var o = {'func':function(){
        alert('Hello?');
    }}
    o.func();
    window.o.func();

func();와 window.func();는 모두 실행이 된다. 모든 전역변수와 함수는 사실 window 객체의 프로퍼티(속성)다. 객체를 명시하지 않으면 암시적으로 window의 프로퍼티로 간주된다. -> window 객체의 메소드로 간주

<br>
웹브라우저에서는 window.
<br>
Node.js에서는 global.

### this
this는 함수 내에서 함수 호출 맥락(context)를 의미한다.
###
    function func(){
        if(window === this){
            document.write("window === this");
        }
    }
    func();
    //window === this

window.func() 이기때문에 this===window
###
    var o = {
        func : function(){
            if(o === this){
                document.write("o === this");
            }
        }
    }
    o.func();
    //o === this

o.func() 이기떄문에 this===o


#### 생성자내에서 this
    var funcThis = null; 
    
    function Func(){
        funcThis = this;
    }
    var o1 = Func();                            //new 없으므로 함수그 자체로 작동
    if(funcThis === window){                    //함수에선 this가 window임
        document.write('window <br />');
    }
    
    var o2 = new Func();                        //new로 부르면 생성자로 작동함
    if(funcThis === o2){                        //생성자에선 this가 생성된 객체임
        document.write('o2 <br />');
    }

#### call,apply 에 의한 this값 변화
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
                break;          
        }
    }
    func();
    func.apply(o);
    func.apply(p);
    //window
    //o
    //p


## 상속
    자바스크립트는 객체가 객체를 상속받는다.
##
    function Person(name){
        this.name = name;
    }
    Person.prototype.name=null;                 //prototype으로 정의해야함
    Person.prototype.introduce = function(){    //prototype으로 정의해야함
        return 'My name is '+this.name; 
    }
    
    function Programmer(name){
        this.name = name;
    }
    Programmer.prototype = new Person();        //Person객체를 상속받음
    Programmer.prototype.coding = function(){   //Programmer 객체에 속성 추가함
        return "hello world";
    }
    var p1 = new Programmer('egoing');
    document.write(p1.introduce()+"<br />");
    document.write(p1.coding()+"<br />");

### prototype

    prototype에 저장된 속성들은 생성자를 통해서 객체가 만들어질 때 그 객체에 연결된다.

###
    function Ultra(){}
    Ultra.prototype.ultraProp = true;
    
    function Super(){}
    Super.prototype = new Ultra();
    
    function Sub(){}
    Sub.prototype = new Super();
    
    var o = new Sub();
    console.log(o.ultraProp);

Chain
1. 객체 o에서 ultraProp를 찾는다.
2. 없다면 Sub.prototype.ultraProp를 찾는다.
3. 없다면 Super.prototype.ultraProp를 찾는다.
4. 없다면 Ultra.prototype.ultraProp를 찾는다.


## 표준 내장 객체의 확장
    Array.prototype.rand = function(){                          //표준 내장 객체 Array에 rand라는 메소드를 추가시킴
        var index = Math.floor(this.length*Math.random());
        return this[index];
    }
    var arr = new Array('seoul','new york','ladarkh','pusan', 'Tsukuba');
    console.log(arr.rand());


## 원시 데이터 타입
    숫자
    문자열
    불리언(true/false)
    null
    undefined

### 레퍼 객체 (wrapper)
    숫자                    -> Number
    문자열                  -> String
    불리언(true/false)      -> Boolean

    원시 데이터 타입을 자동으로 객체로 치환해주는것 (사용후 삭제됨)
<pre>
    var str = 'coding';
    console.log(str.length);        // 6
    console.log(str.charAt(0));     // "C"
    //str = new String('coding'); 자동으로 레퍼객체 생성된것처럼 작동함

</pre>
<pre>
    var str = 'coding';
    str.prop = 'everybody';     // 사용후 삭제되어버림...
    console.log(str.prop);      // undefined   (삭제되어 남아있지 않음)
</pre>
