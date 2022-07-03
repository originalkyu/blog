---
title: "Passing Arguments"
date: 2022-06-30T13:59:56+09:00
type: 
draft: false
---

## 값에 의한 인수 전달
```cpp
// call by value
int x = 6;
doSomething(x);
doSomething(5);

void doSomething(vector<int> arr) {...}
    // vector가 복사되어 이용되고, 함수 밖에 영향을 주지 않는다
```

## 참조에 의한 인수 전달
* reference 페이지 참고

## 주소에 의한 인수 전달
```cpp
void func1(int *ptr) { ... }
...
int value = 5;
func1(&value);
```
* 위의 코드는 포인터 변수 입장에서 보면 값의 의한 전달로 볼 수도 있다
* 아래 코드처럼 생각하면 이해하기 쉽다
```cpp
typedef int* pint;
void foo(pint ptr) {...}
```
* 아래 코드는 const int *ptr로 전달한다. 함수 안 에서 값을 변경할 수 없다
```cpp
void func1(const int *ptr)
{
	*ptr = 10; // error
}

void func2(const int *arr)
{
	arr[0] = 1; // error;
}
```
* 아래 코드는 int const *ptr로 전달한다.
```cpp
void func3(int * const ptr) 
{
	int x =3;
	ptr =&x; // error;
}

void func4(const int * const ptr)
{
...
}
```