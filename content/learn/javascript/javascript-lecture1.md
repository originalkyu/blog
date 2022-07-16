---
title: "JavaScript Lecture1"
date: 2022-07-03T09:30:39+09:00
type: 
draft: false
---

## 자바스크립트
* 동적인 웹사이트 제작 시 화면의 변화를 표현하기 위해 사용되는 프로그래밍 언어
    * 이미지 슬라이드 효과, 파업효과 등
    * 하이브리드 앱, 서버 개발 등에 사용된다
    * 다음처럼 script 태그 안에 src 속성값으로 js 파일을 입력하고 html파일과 연동한다
        ```HTML
            <body>
                <script src="index.js"></script>
            </body>
        ```

## 기초 문법
```JS
// 1. 변수 선언과 초기화
var fruit;
fruit = "apple";
//var 1fruit;
    // 변수 이름은 숫자로 시작할 수 없다

// 2. 출력하는 함수
console.log(fruit);
document.write(fruit);
document.writeln(fruit);

// 3. 8가지 데이터 타입
/*
    1. String
    2. Number
    3. Function
    4. Array
    5. Object
    6. Boolean
    7. undefined
    8. null
*/
// 1. String
var str1 = "Hello World";
var str2 = "20";

// 2. Number
var num1 = 10;
var num2 = 3.14;

// 3. Function 선언 방법
    // return문이 없다면 undefined를 반환한다
// 방법 1 함수 표현식 : var xxx 는 ~인 함수다
    // 호이스팅에 영향을 받지 않는다
    // 클로져로 사용한다
    // 콜백으로 사용한다
var func1 = function(width, height) {
    console.log("Func1");
    var area = width * height;
    return 'A function expression';
}

// 방법 2 함수 선언식 : 함수 xxx가 있다
    // 호이스팅의 영향을 받는다
function func1() {
    console.log("Func1");
    return 'A function declaration';
}

// 4. Array
var fruits = ["사과", "배", "수박"];
console.log(fruits);
/* 출력 결과
(3) ['사과', '배', '수박']
0: "사과"
1: "배"
2: "수박"
length: 3
[[Prototype]]: Array(0)
*/
console.log(fruit[0]); // 0번째 인덱스의 데이터 추출
fruit[0] = "포도";

// 5. Object
var student = {
    // property
    name : "Chankyu",
    age : 20,
    skills : ["자바스크립트", "HTML", "CSS"],
    // method
    sum : function (num1, num2) 
    { 
        return num1 + num2;
    }
}

// 객체의 데이터 추출과 변경
console.log(studet.name);
console.log(student['name']);
student.age = 30;


// 6. undefined 와 null
var unde; // undefined : 변수 안에 데이터를 입력하지 않은 상태
var empty = null; // null : 빈 데이터를 지정


// 7. Boolean
var t = true;
var f = false;

```

## 프로퍼티와 메서드
* 프로퍼티: 고유한 성질
* 메서드: 편의 기능

### 문자열 프로퍼티와 메서드
```javascript
var str1 = "Hello World";
str1.length; // 문자열 길이 11
str1.charAt(0); // 문자 H 추출
str1.split(" "); // 공백 기준으로 문자를 나눈 후 배열 [Hello, World]로 출력
```

### 배열 프로퍼티와 메서드
```javascript
var fruits = ["사과", "배", "포도"];

fruits.length;

fruits.push("딸기"); // 배열 뒤에 데이터 삽입
fruit.pop(); // 배열 뒤의 데이터 제거

fruits.unshift("레몬"); // 배열 앞에 데이터 삽입
fruit.shift(); // 배열 앞의 데이터 제거
```
### Math의 수학 연산 메서드
```javascript
Math.abs(-3);
Math.ceil(0.3);
floor(10.9);
Math.random();
```
### 문자열을 숫자로 변환하는 메서드
```javascript
parseInt("20.6");
parseFloat("20.6");
```

## 연산자

### 산술 연산자
* 숫자 뿐 아니라 문자열도 산술 연산자가 가능하다
* 하지만 문자열을 + 할 때는 주의핳ㄴ다
```javascript
document.write(20 + 10);
document.write(20 - 10);
document.write(20 * 10);
document.write(20 / 10);
document.write(20 % 10);

document.write("20" + "10"); // 2010 출력되는 것 주의
document.write("20" - "10");
document.write("20" * "10");
document.write("20" / "10");
document.write("20" % "10");
```

### 증감 연산자
```javascript
++num;
--num;

num++;
num--;
```

### 비교 연산자
* Boolean 데이터 타입인 true 혹은 false를 반환한다
```javascript
document.writeln(10 == 10);
document.writeln(10 === 10);
document.writeln(10 !== 20);

document.write(10 > 20);
document.write(10 >= 20);
document.write(10 < 20);
document.write(10 <= 20);
```
* == 와 ===의 차이에 주의한다
```javascript
console.log(10 == "10"); // true
console.log(10 === "10"); // false
```

### 논리 연산자
* &&와 ||가 있다

## 조건문
```javascript
if ( 조건 )
{
    code
}
else if ( 조건 )
{
    code
}
else
{
    code
}
```

## 반복문
```javascript
for (var i = 0; i < 10; i++ )
{
    console.log(i);
}

var num = 0;
while (num < 10)
{
    console.log(num);
    num++;
}

do {
    console.log(i)
    num--;
} while(num > 0);
```
