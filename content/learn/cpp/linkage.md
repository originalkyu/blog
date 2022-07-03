---
title: "Linkage"
date: 2022-06-30T11:06:10+09:00
type: 
draft: false
---

## 정리
```plain
Global variable: 전역변수
Static Variable : 정적변수
Internal Linkage : 내부 연결
External Linkage : 외부 연결

linkage가 없다 : 변수의 범위가 블록 안에 갇혀있다.
internal linkage : 변수를 파일 안에서 자유롭게 사용할 수 있다. 파일 안에서만 사용할 수 있는 전역변수
external linkage : 다른 cpp 파일에서도 사용할 수 있다. 다른 파일에서도 사용할 수 있는 전역변수

linking: 각각의 cpp파일에서 만들어진 obj파일 사이에서 연결되는 것끼리 연결함
linkage : 연결의 의미

extern : 다른 곳에 함수의 body가 선언되어 있다는 의미. 생략 가능

---
local variable은 linkage가 없으므로 다른 파일과 linking 할 필요가 없다.
전역변수로 선언한 static 변수는 다른 cpp파일에서 접근할 수 없다. 즉, internal linkage이다.

---

int g_x; // external linkage 
	// 다른 cpp파일에서 g_x를 선언하고 초기화하지 않으면 찾아 쓸 것이다.
	// extern이 생략되어 있다.
	// 어느 한쪽에서는 초기화가 되어있어야한다.
static int g_x; // internal linkage

---
const int g_x(1); // external linkage
	// 선언과 동시에 초기화하지 않으면 오류가 난다.
	// extern 이 생략되어 있다.
int g_y(1); // external linkage
static int g_y(1); // internal linkage
```

## 전역변수
```cpp
#include <iostream>

using namespace std;

int value = 9;

int main()
{
	int value = 1;

	cout << ::value << endl;
	cout << value << endl;
	// 9 1 이 출력된다.
	return 0;
}
```

## static variable
```cpp
#include <iostream>

using namespace std;

void doSomething()
{
	static int a = 1;
	++a;
	cout << a << endl;
}

int main() 
{
	doSomething();
	doSomething();
}
```
* os로부터 할당받은 메모리 영역이 static
* 디버깅할 때 유용하다
```cpp
#include <iostream>

using namespace std;


static int s_a = 1;

int main() 
{

}
```
* 전역변수로 선언한 static 변수는 다른 cpp파일에서 접근할 수 없다

## extern
```cpp
// functions4_02.cpp
#include <iostream>

extern int a = 1;
// 초기화를 해주어야 다른 곳에서 이용할 때 오류가 나지 않는다.

void doSomething()
{
	using namespace std;

	cout << "Hello " << endl;
}
```
```cpp
#include <iostream>

using namespace std;


void doSomething();
// extern이라는 키워드가 숨어있다.
extern int a;
int main() 
{
	int a = 10;
	doSomething();
	return 0;
}
```
* forward declaration을 이용하면 linking과정에서 body를 찾아 쓴다
* 위 코드에서 extern이라는 문구가 생략되어있다
* 변수에도 extern 선언이 가능하다. 오직 한 곳에서만 초기화를 해주어야 한다. 두 곳에서 초기화를 하면 오류가 난다.

## extern const
[Chapter4_02.cpp]
```cpp
#include <iostream>

using namespace std;


void doSomething();
// extern이라는 키워드가 숨어있다.
extern int a;
int main() 
{
	int a = 10;
	doSomething();
	return 0;
}
```
[functions4_02.cpp]
```cpp
#include <iostream>
#include "my_constants4_02.h"

void doSomething()
{
	using namespace std;

	cout << "In functions.cpp " << constants4_02::pi << " " << & constants4_02::pi << endl;
}
```
[my_constants4_02.h]
```cpp
#pragma once

namespace constants4_02
{
	const double pi(3.141592);
	const double gravity(9.8);
}
```
* 서로 다른 cpp파일에서 같은 헤더파일의 같은 상수를 이용했지만 출력되는 주소가 다르다. 즉 1000개의 파일에서 이용하면 메모리를 1000배 이용하는 것이다
* 아래의 방식으로 해결할 수 있다
[my_constants4_02.h]
```cpp
#pragma once

namespace constants4_02
{
	extern const double pi;
	extern const double gravity;
}
```
[my_constants4_02.cpp]
```cpp
namespace constants4_02
{
	extern const double pi(3.141592);
	extern const double gravity(9.8);
}
```