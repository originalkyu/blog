---
title: "For each"
date: 2022-06-30T11:01:20+09:00
type: 
draft: false
---

## for each문
```cpp
#include <iostream>
#include <limits>

using namespace std;

int main()
{
	const int c_fibonacci[] = { 0, 1, 10, 45, 91 };
	int fibonacci[] = { 0, 1, 10, 45, 91 };
	
	// for each문 사용법
	for (int number : c_fibonacci)
		cout << number << " ";
	cout << endl;

	// fibonacci의 내용을 바꾸기, 하지만 바뀌지 않는다.
	for (int number : fibonacci)
		number = 10;

	// reference를 이용해서 fibonacci의 내용을 바꿀 수 있다.
	for (int& number : fibonacci)
		number = 10;

	// 다음의 방식이 더 자주 사용된다.
	for (auto& number : fibonacci)
		number = 10;

	// 내용을 바꾸고 싶지 않다면 다음의 방식을 이용한다.
	for (const auto& number : fibonacci)
		cout << number;
		// 상수 배열보다는 이 방식을 자주 이용한다.

	// 동적 할당 배열에는 for each를 사용할 수 없다.
	// vector에는 사용할 수 있다.
}
```