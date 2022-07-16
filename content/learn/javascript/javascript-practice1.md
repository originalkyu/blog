---
title: "Javascript Practice1"
date: 2022-07-03T11:05:30+09:00
type: 
draft: false
---

참고
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference

## 예제로 연습하기
---
## 문자열 거꾸로 출력하기
```JS
var reverse = function(str) {
    var reverseStr = "";
    for(var i = str.length-1; i >= 0, i--) 
        // length 필드는 문자열의 문자 개수
        // null제외
    {
        reverseStr = reverseStr + str.charAt(i);
    }
    return reverseStr;
}
console.log(reverse("Nice to Meet you"));
```

## \ 출력하기
```javascript
console.log("(\\_/)");
console.log("(. . )");
console.log("|\\ /|");
```
\ 를 출력하려면 \\로 해야한다

## readline 모듈 사용법
```javascript
// 1. realine 모듈 불러오기
const readline = require("readline");

// 2. 인터페이스 생성하기
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
})

// 3. 입출력을 처리하는 코드
// 3.1입력 부분
var input = [];
rl.on("line", (line) => {
    // 입력받은 후 실행할 코드
    input.push(line);
    console.log(line);
    rl.close();
});

// 3.2출력 부분
rl.on('close', () => {
    // 입력이 끝난 후 실행할 코드
});
```
```javascript
const readline = require("readline");

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
});

var input = [];
rl.on("line", (line) => {
    input.push(line);
    //console.log(line);
    rl.close();
});

rl.on('close', () => {
    console.log(input[0]);
});

```
* rl.on()
    * 인터페이스가 가지는 on 메서드를 사용해서 이벤트와 콜백함수를 전달
    * 위에서는 line 이벤트와 close 이벤트를 전달하고 있음
* rl.close(): 인터페이스를 종료해서 무한히 입력받는 것을 방지
    * close 이벤트를 발생시켜서 입력값을 활용하여 출력값을 도출하는 코드 작성
    * close는 더이상 입력되는 값이 없을 때 실행되는 이벤트
* process.exit(): 프로세스를 종료시킨다

## 정수의 배열 오름차순 정렬하기
```javascript
var soldier = [12, 2, 5, 3, 7, 4, 10, 8, 1, 9, 13, 11, 6];

// 정렬된 배열과 길이를 구하세요.

var count = 0;

var compareNumbers = function(a,b) 
{
    if ( a < b )
        return -1;
    else if ( a > b )
        return 1;
    else
        return 0;
}
soldier.sort(compareNumbers);
// array.sort(함수) 를 하면 복사본이 만들어지는 것이 아니라 원래의 배열이 정렬

console.log(soldier);
console.log(count);
```
sort()를 이용하면 복사본이 만들어지는 것이 아니라 원래의 배열이 정렬된다.
compareNumbers 함수의 return이 0보다 작다면 a를 b보다 더 낮은 색인으로 정렬한다  
return이 0이라면 변경하지 않는다

문자열을 비교하기 위해서 아래의 함수를 이용할 수 있다
```javascript
function compareNumbers(a, b) {
  return a - b;
}
```

## splice, join, match
```javascript
var words = ['i', 'have', 'a', 'pen', 'i', 'have', 'pineapple', 'i', 'have', 'an', 'apple', 'pen'];
var count = function(lyrics)
{
    return lyrics.match(/p/g).length;
}

words.splice(4,2);
words.splice(5,3);

lyrics = words.join(' ')

console.log(lyrics);
console.log(count(lyrics));
```
* splice
    * 배열.splice(m, n) : m+1번째 원소부터 n개 제거
* join
    * 배열.join(' ') : ' '로 원소들을 연결하여 문자열로 return
* match
    * 문자열.match(regexp)
        https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/match
## 정규표현식
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/RegExp
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/match
https://curryyou.tistory.com/234
* 정규표현식 소개  
/패턴/플래그
=> 패턴 : {매칭패턴,검색패턴}{수량 패턴}
010-111-2222 는 "숫자3개", "-", "숫자4개", "-", "숫자4개" 로 이루어져있다.  
이것은 const regex = /\d{3}-\d{4}-\d{4}/; 로 표현할 수 있다.  
\d 는 숫자, {}는 개수를 의미한다
다음처럼 특정 문자열이 해당 패턴에 맞는지 체크하거나 문자열에서 추출할 수 있다. 

    ```javascript

    const regex = /\d{3}-\d{4}-\d{4}/;
    regex.test("010-1111-2222"); // true
    regex.test("010-11-22"); // false

    const text = "제 번호는 010-1111-2222 입니다.";
    text.match(regex); // 010-1111-2222

    ```
* 정규표현식 예시  
    /대/ : '대'를 '하나'만 찾는다  
    /대/g : '대'를 '모두' 찾는다  
    /대나무 빨대/ : '대나무 빨대'를 '하나 찾는다  
    /[대a0]/g : '대', 'a', '0'을 모두 찾는다
    * []는 or의 기능
    
    /[0-9]/g : 숫자 0~9를 모두 찾는다  
    /[a-zA-Z]/g : 알파벳 대문자/소문자를 모두 찾는다  
    /[^0-9]/g : 숫자 0~9가 아닌 것을 모두 찾는다

* 정규표현식의 형식, 패턴, 플래그, 메서드
    1. /패턴/플래그  
        플래그는 하나만 찾을지 모두 찾을지 설정
    2. 정규표현식 매칭 패턴(문자, 숫자, 기호 등)  
        a-zA-Z : 영어알파벳  
        ㄱ-ㅎ가-힣 : 한글 문자  
        0-9 : 숫자  
        . : 모든 문자열. 단 줄바꿈은 x  
        \d : 숫자  
        \D : 숫자가 아닌 것  
        \w : 영어, 알파벳, 숫자, 언더스코어  
        \W : \w가 아닌 것  
        \s : space 공백  
        \S : space공백이 아닌 것  
        \특수기호 : 특수기호
    3. 정규표현식 검색 패턴  
        | : OR  
        [] : 괄호안의 문자들 중 하나
        [^문자] : 괄호 안의 문자를 제외한 것  
        ^문자열 : 특정 문자열로 시작  
        문자열$ : 특정 문자열로 끝남  
        () : 그룹 검색 및 분류  
        (?:패턴) : 그룹 검색(분류x)  
        \b : 단어의 처음/끝  
        \B : 단어의 처음/끝이 아님

    4. 정규표현식 개수(수량) 패턴  
        ? : 최대 한번  
        \* : 없거나 있거나  
        \+ : 최소 한 개  
        {n} : n개  
        {Min,} : 최소 Min개  
        {Min, Max} : 최소 Min, 최대 Max

    5. 정규표현식 플래그  
        동시에 여러개 사용할 수 있다  
        g : 모든 문자 검색(안 쓰면 매칭되는 첫 문자만 검색)  
        i : 대소문자 구분 안 함  
        m : 여러 행의 문자열에 대해 검색
    6. 정규표현식 주요 메서드  
        문자열.match(정규표현식/플래그) : 문자열에서 정규표현식에 매칭되는 항목을 배열로 반환  
        문자열.replace(정규표현식, "대체문자열") : 정규표현식에 매칭되는 항목을 대체문자열로 변환  
        문자열.split(정규표현식) : 문자열을 정규표현식에 매칭되는 항목으로 쪼개어 배열로 반환  
        정규표현식.test("문자열") : 문자열이 정규표현식돠 매칭되면 true, 아니면 false 반환  
        정규표현식.exec("문자열") : match와 유사하지만 첫번째 매칭만 반환  
* 정규표현식 샘플 코드 
    ```javascript
    // 1. 웹사이트 주소 정규표현식
        /https?:/\/\[\w\-\.]+/g
        1) http => http 로 시작
        2) s? => 다음으로 s가 있거나 없음
        3) : => 다음으로 :가 옴
        4) \/\/ => 다음으로 // 가 있음
        5) [\w\-\.]+  
            \w(영문자, 언더스코어)
            -
            .
            으로 이루어진 문자열이 
            + => 한개 이상 있다
        6) g => 매칭되는 모든 것을 다 찾는다


    // 2. 전화번호 정규표현식
        /\d{2,3}-\d{3,4}-\d{4}/g
        1) \d{2,3} => 숫자 2~3개
        2) - => 다음에 하이픈이 옴
        3) \d{3,4} => 다음에 숫자 3~4개가 옴
        4) - => 다음에 하이픈이 옴

    // 3. 이메일주소 정규표현식
        /[\w\-\.]+\@[\w\-\.]+/g
    // 4. 특수기호 정규표현식
        // 1) 모든 특수기호를 나열
            /\[\]\{\}\/\(\)\.\?\<\>!@#$%^&*/g

        // 2) 문자와 숫자가 아닌 것을 매칭
            /[^a-zA-Z0-9가-힣ㄱ-ㅎ]/g

    var regExp = /\s/g;
    /*
    숫자만 체크 정규식
    var regExp = /^[0-9]+$/;

    이메일 체크 정규식
    var regExp = /^[0-9a-zA-Z]([-_\.]?[0-9a-zA-Z])*@[0-9a-zA-Z]([-_\.]?[0-9a-zA-Z])*\.[a-zA-Z]{2,3}$/i; 

    핸드폰번호 정규식
    var regExp = /^\d{3}-\d{3,4}-\d{4}$/;

    일반 전화번호 정규식
    var regExp = /^\d{2,3}-\d{3,4}-\d{4}$/;

    아이디나 비밀번호 정규식
    var regExp = /^[a-z0-9_]{4,20}$/; 

    휴대폰번호 체크 정규식
    var regExp = /^01([0|1|6|7|8|9]?)-?([0-9]{3,4})-?([0-9]{4})$/;
    */
    ```

## 숫자+문자열 웹화면에 출력하기
```javascript
var num = 400;
var str1 = "bus";
var str2 = "like";

document.write(num+str1+str2);
```

```javascript
document.write(400);
document.write("<br>");
document.write("bus<br>");

document.write("li<br>ke");
    // <br>을 이용하면 행이 바뀐다
document.write("Its all right.<br>");
document.write('"Its all right."<br>');
document.write("It\'s all right.");
```

## split와 typeof 
```javascript
var str = "Good morning! Have a nice day."

// step1
var arr = str.split(' ');

// step2
document.writeln(typeof arr);
document.writeln(arr[0]);
```
* 문자열.split(' ')
    * 공백을 기준으로 잘라서 배열을 만든다
* typeof 대상


## 입력받아서 조건에 맞게 출력하기
```javascript
const readline = require("readline");

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
})

rl.on("line", (line) => {
    if(line >= 50)
        console.log("우산을 챙긴다.");
    else
        console.log("그냥 간다.");
    rl.close();
});

rl.on("close", () => {

});
```

## 피보나치 수열
```javascript
var fibo = function(n) 
{
    fiboarr = [];
    for(before = 0, now = 0, post = 1; now < n;)
    {
        fiboarr.push(now);
        before = now;
        now = post;
        post = before + now;
    }
    console.log(fiboarr);
}

const readline = require("readline");

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
})

rl.on("line", (line) => {
    fibo(line);
    rl.close();
});

rl.on("close", () => {

})
```

## match(), includes()
```javascript
// "촉촉한 초코칩"이 몇 번 나오는지 확인해봅시다.
const readline = require("readline");

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
})

var regExp = /촉촉한 초코칩/g;

rl.on("line", (line) => {
    if(line.includes("촉촉한 초코칩"))
        // string.includes(문자열)
        console.log(line.match(regExp).length);
            // string.match(정규표현식)
    else
        console.log(0);sliceㅁ
    rl.close();
});

rl.on("close", () => {

});
```

## 두 줄에 걸쳐서 숫자 2개를 입력받기, slice


## match, join 연습
```javascript
// 지시사항을 참고하여 코드를 작성하세요.
const readline = require("readline");

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
})

var regExp = /[0-9]/g;

result = [];
rl.on("line", (line) => {
    result = line.match(regExp);
    console.log(result.join(""));

    rl.close();
})

rl.on("close", () => {

})
```
string.charCodeAt(index)를 이용하면 문자열 안의 index에 해당하는 문자의 유니 코드 값을 얻을 수 있다