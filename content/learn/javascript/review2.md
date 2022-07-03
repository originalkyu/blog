---
title: "Review2"
date: 2022-07-03T10:18:46+09:00
type: 
draft: false
---

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
## 연습