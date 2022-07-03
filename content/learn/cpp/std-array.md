---
title: "Std Array"
date: 2022-06-30T11:24:22+09:00
type: 
draft: false
---

## std::array
```cpp
#include <iostream>
#include <array>
using namespace std;

int main() 
{
	// std::array는 정적 배열을 대체할 수 있다.
	// std::array 선언과 초기화
	std::array<int, 5> my_arr = { 1, 2, 3, 4, 5 };
	my_arr = { 0, 1, 2, 3, 4 };
	my_arr = { 0, 1, 2, }; // 나머지 두 개는 0으로 채워준다.
		// 이 때, my_arr 은 {0, 1, 2, 0, 0}으로 초기화되어 있다.
	for (auto element : my_arr)
		cout << element << " ";
	cout << endl;

	// std::array 접근 방법과 기능
	cout << my_arr[0] << endl; // ok
	cout << my_arr.at(0) << endl; // ok

	cout << my_arr[10];   // 문제가 있는지 확인하지 않고 바로 액세스
	cout << my_arr.at(10);// 문제가 있는지 확인하고 액세스

	// element가 몇 개인지 보여준다.
	my_arr.size();
	// 파라미터로는 다음처럼 넘겨준다.
	void printLength(array<int, 5> my_arr) { .., };
	// 위 방식은 array가 복사되는 형태이므로 array가 크다면 곤란하다.
	void printLength(array<int, 5>& my_arr); // 
	void printLength(const array<int, 5>& my_arr); // 전달한 array가 변하지 않길 바랄 때
}
```

