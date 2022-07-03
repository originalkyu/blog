---
title: "Returning Values"
date: 2022-06-30T12:00:29+09:00
type: 
draft: false
---

## return by value
```cpp
#include <iostream>

using namespace std;

int getValue(int x)
{
	int value = x * 2;
	return value;
}

int main()
{
	int value = getValue(3);
	return 0;
}
```

## return by address
```cpp
#include <iostream>

using namespace std;

int* allocateMemory(int size)
{
	return new int[size];
}

int main()
{
	int* array = allocateMemory(1024);
	return 0;
}
```

## return by reference
```cpp
using namespace std;

int& getValue(int x)
{
	int value = x * 2;
	return value;
}

int main()
{
	int value = getValue(3);
	return 0;
}
```
* 그런데 아래 코드처럼 받는 쪽에서 reference로 받는다면 문제가 생긴다
```cpp
#include <iostream>
using namespace std;

int& getValue(int x)
{
	int value = x * 2;
	return value;
}

int main()
{
	int &value = getValue(3);

	cout << value << endl;
	cout << value << endl;
	return 0;
}
```
* 함수에서 만들어지는 value는 함수가 return할 때 해제되기 때문이다
* 아래의 코드는 return by reference의 유용한 방식
```cpp
#include <iostream>
#include <array>

using namespace std;

int& get(std::array<int, 100>& my_array, int ix)
{
	return my_array[ix];
}

int main()
{
	std::array<int, 100> my_array;
	my_array[30] = 10;

	get(my_array, 30) = 1024;

	cout << my_array[30] << endl;

	return 0;
}
```
## structure
```cpp
#include <iostream>
#include <array>

using namespace std;

struct S
{
	int a, b, c, d;
};

S getStruct()
{
	S my_s{ 1, 2, 3, 4 };
}

int main()
{
	S my_s = getStruct();
	my_s.b;

	return 0;
}
```

## tuple
```cpp
#include <iostream>
#include <array>

using namespace std;

struct S
{
	int a, b, c, d;
};

S getStruct()
{
	S my_s{ 1, 2, 3, 4 };
}

int main()
{
	S my_s = getStruct();
	my_s.b;

	return 0;
}
```