---
title: "Reference"
date: 2022-06-30T09:55:04+09:00
type: 
draft: false
---

## reference 기본 설명
```cpp
#include <iostream>

using namespace std;

void func(int& value)
{
    cout << &value << endl;
    value = 1000;
}

int main()
{
    int value = 1;
    const int c_value = 9;
    int* ptr = &value;
    int& ref = value;
        // reference 변수 선언 방법

    // int &c_ref = c_value;
        // error가 난다.
    const int& c_ref = c_value;
        // ok

    ref = 10;
        // *ptr = 10;

    cout << ref << endl;
        // 1 출력

    cout << &value << endl;
    cout << &ref << endl;
    cout << ptr << endl;
        // 모두 같은 주소를 출력한다.
    func(value);
        // 마찬가지로 같은 주소를 출력한다.
}
```


## 참조에 의한 인수 전달
```cpp
#include <iostream>
#include <cmath> // sin(), cos()

using namespace std;

void getSinCos(const double &degrees, double& sin_out, double& cos_out)
// 입력을 앞에 두고, 출력을 뒤에 둔다.
// 입력만을 위한 인자는 const를 붙인다.
{
	static const double pi = 3.141592 / 180.0;
	// 180으로 나누는 것은 static const 에서 하면 호출할 때마다 반복되지 않는다.
	double radians = degrees * pi;
	sin_out = std::sin(radians);
	cos_out = std::cos(radians);
}

int main()
{
	double sin(0.0);
	double cos(0.0);

	getSinCos(30.0, sin, cos);

	cout << sin << " " << cos << endl;

	return 0;
}
```

## 리터럴 상수를 인자로 줄 수 있다
```cpp
#include <iostream>

using namespace std;

void foo(const int &x)
{
	cout << x << endl;
}

int main()
{
	foo(6);

	return 0;
}
```

## 포인터를 reference로 전달할 수 있다
```cpp
#include <iostream>

using namespace std;

typedef int* pint;
void foo(int *&ptr)
// 이렇게 해석하면 편하다. ((int*) &ptr)
// pint &ptr 과 같다.
{
	cout << ptr << " " << &ptr << endl;
}

int main()
{
	int x = 5;
	int* ptr = &x;

	cout << ptr << " " << &ptr << endl;
	foo(ptr);

	return 0;
}
```
* 

## array를 reference로 전달할 수 있다
```cpp
#include <iostream>

using namespace std;

void printElements(int (&arr)[4])
{

}

int main()
{
	int arr[]{ 1, 2, 3, 4 };
	printElements(arr);
}
```
* 이 방식은 이용하지 않는다. 배열은 정적으로 이용하기보다는 동적으로 이용하기 때문

## vertor를 reference로 전달할 수 있다
```cpp
#include <iostream>
#include <vector>
using namespace std;

void printElements(const vector<int>& arr)
{

}

int main()
{
	vector<int> arr{ 1, 2, 3, 4 };
	printElements(arr);
}
```
