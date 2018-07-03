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

반복문 안에서 생성한 name 변수는 로컬이지만 for문 밖에서 사용가능

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
