---
title: "Array"
date: 2022-06-30T11:20:14+09:00
type: 
draft: false
---

## 정적배열
```cpp
#include <iostream>

#define NUM_STUDENTS 10000

using namespace std;

void doSomething(int scores[20])
{
	cout << scores[0] << endl;
}

int main()
{
	// 정적 배열 이용. runtime에 크기가 결정될 수 없다.
	int students_scores1[NUM_STUDENTS];
	// c스타일 방식이다. 권장하지 않는 코딩 방식
	// 차라리 다음처럼 상수를 이용한다.
	const int num_students = 20;
	int students_scores2[num_students];
	doSomething(students_scores2);
	// 배열을 인자로 넘겨줄 수 있다.

}
```

## 동적인 배열
```cpp
#include <iostream>

using namespace std;

int main()
{
	// int array[1000000];
		// error가 난다.
		// 정적으로 배열을 할당하면 stack 영역에 저장되는데 stack영역은 크기가 작다.

	int* ptr1 = new int;
	int* ptr2 = new int{ 7 };
		// new를 이용해서 os로부터 메모리를 할당받을 수 있다.

	int* ptr3 = new (std::nothrow)int{ 7 };
		// 가끔 메모리를 할당받지 못해서 에러가 날 때가 있다.
		// 예외 처리에서 자세히 배운다.
		// 혹은 다음처럼 이용할 수도 있다.
	if (ptr1 != nullptr)
	{
		*ptr1 = 8;
	}

	delete ptr1;
	delete ptr2;
	delete ptr3;
		// 직접 할당받은 메모리는 반환해야한다.
}
```
* delete를 한 이후에 다시 사용하고자 한다면 포인터를 nullptr로 초기화 한 이후에 사용해야한다
```cpp
#include <iostream>

using namespace std;

int main()
{
	int length;
	cin >> length;

	int* array = new int[3]{ 1, 2, 3 };
	delete[] array;
		// 정적 배열은 크기가 컴파일 타임에서 결정되기 때문
		// 배열의 크기를 바꾸려면 두 가지 방법이 있다.
		// 1. 새로운 배열을 만들고 element를 복사해서 붙여넣는다.
		// 2. 기존 배열의 뒷 부분에 추가해서 붙일 수 있는지 OS에 물어보고 요청함 
}
```