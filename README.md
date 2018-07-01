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

