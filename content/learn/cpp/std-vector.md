---
title: "Std Vector"
date: 2022-06-30T11:58:57+09:00
type: 
draft: false
---

## std::vector
```cpp
#include <iostream>
#include <vector>

using namespace std;

int main()
{
	std::vector<int> array;
		// std::array<int, 5> array; 와 다르게 사이즈를 반드시 적지 않아도 된다
	std::vector<int> array2 = { 1, 2, 3, 4, 5 };
	cout << array2.size() << endl;

	std::vector<int> array3 = { 1, 2, 3, };
	cout << array3.size() << endl;

	std::vector<int> array4 { 1, 2, 3, };
	cout << array4.size() << endl;

	for (auto& itr : array2)
		cout << itr << " ";
	cout << endl;

	cout << array2[1] << endl;
	cout << array2.at(1) << endl;
	array2.resize(10);

	// int *my_arr = new int[5]; 
	// delete[] my_arr;
	// 동적 배열은 delete를 해줘야하지만
	// vector는 delete를 할 필요가 없다
}
```
