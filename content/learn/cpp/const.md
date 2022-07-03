---
title: "Const"
date: 2022-06-30T10:59:09+09:00
type: 
draft: false
---

## pointer와 const
```cpp
#include <iostream>

using namespace std;

int main()
{
	// case 1 const int* : const int 주소를 담을 수 있는 포인터 변수
	const int c_value1_1 = 5;
	int value1_2 = 6;
	//int* ptr1 = &c_value1_1;
		// error
		// int* ptr1은 심볼릭 상수를 가리킬 수 없다
	const int* ptr1 = &c_value1_1;
		// ok
	//*ptr1 = 6;
		// error
		// const int*로 dereferencing해서 수정할 수 없다.
	//c_value1_1 = 6;
		// error
		// 상수이므로 수정할 수 없다
	ptr1 = &value1_2;
		// ok
		// const int*는 int의 주소도 담을 수 있다.
		// 이럴 때는 ptr로 dereferencing해서 값을 수정할 수 없다.
		// 하지만 value1_2를 직접 수정할 수는 있다.
	

	// case 2 int* const : int 주소를 담을 수 있는 포인터 상수. 선언과 초기화가 같이 일어나야한다.
	int value2_1 = 5;
	int value2_2 = 6;
	int* const ptr = &value2_1;
	*ptr = 10;
		// ok
	//ptr = &value2_2;
		// int* pointer가 다른 것을 가리키도록 바꿀 수 없다

	// case 3 const int* const : 가리키는 변수와 포인터 변수 모두 상수인 경우
		
}
```

### reference와 const
```cpp
int x = 5;
const int y = 6;

int &ref1 = x; // ok
const int &ref2 = x; // ok
int &ref3 = y; // error
const int &ref4 = y; // ok
const int &ref5 = ref1; // ok
const int &ref6 = ref2; // ok
const int &ref7 = ref4; // ok


const int &ref = 3 + 4; // ok
cout << ref;
cout << &ref; // 주소가 출력됨
```
* const reference는 literal로 초기화할 수 있다. 이 때 const reference는 주소도 출력할 수 있다
* 이러한 특징으로 인해 아래의 코드처럼 별도의 변수 선언 없이 literal 등을 바로 인자로 줄 수 있는 장점이 있다
```cpp
void func1(const int &x) {...}

int a = 1;
func1(a); // ok
func1(2); // ok
func1(a+4); // ok
```