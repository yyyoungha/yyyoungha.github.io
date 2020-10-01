---
title: "Using tuple as key in unordered_map"
last_modified_at: 2020-10-02T00:36:00-09:00
categories:
  - C++ STL
tags:
  - C++
---

C++ unordered_map의 key로 tuple을 사용하는 방법에 대해서 알아보겠습니다.

## Problem

Key로 tuple을, Value로 string을 갖는 unordered_map m을 생성한 다음, m[tuple] 의 형태로 Value에 접근하려고 시도하였으나, [C2280](<https://docs.microsoft.com/ko-kr/cpp/error-messages/compiler-errors-1/compiler-error-c2280?f1url=%3fappid%3ddev16idef1%26l%3dko-kr%26k%3dk(c2280)%26rd%3dtrue&view=vs-2019>) 에러가 발생했습니다. 다음은 오류가 나는 예제 소스코드입니다.

```cpp
#include <iostream>
#include <unordered_map>
#include <tuple>

int main()
{
	std::tuple<int, int, int> a, b;
	a = { 0, 1, 2 };
	b = { 3, 4, 5 };
	std::unordered_map<std::tuple<int, int, int>, std::string> m;
	m[a] = "First";
	m[b] = "Second";
	std::cout << m[a] << std::endl << m[b] << std::endl;

	return 0;
}
```

## Solution

오류가 나는 이유는 unordered_map은 해시 기반 자료구조인데, tuple에 해당하는 해시 함수는 STL에 정의되어있지 않으므로 아래와같이 사용자가 별도로 정의해주어야 합니다.

```cpp
#include <iostream>
#include <unordered_map>
#include <tuple>

typedef std::tuple<int, int, int> key_t;
struct key_hash : public std::unary_function<key_t, size_t>
{
	size_t operator()(const key_t& k) const
	{
		return std::get<0>(k) ^ std::get<1>(k);
	}
};

int main()
{
	std::tuple<int, int, int> a, b;
	a = { 0, 1, 2 };
	b = { 3, 4, 5 };
	std::unordered_map<std::tuple<int, int, int>, std::string, key_hash> m; // Construct with Hash function
	m[a] = "First";
	m[b] = "Second";
	std::cout << m[a] << std::endl << m[b] << std::endl;

	return 0;
}
```

## More

C++ STL 중 map은 Red-Black Tree로 구현되어 있어 별도의 해시 함수 구현 없이도 tuple을 key로 사용할 수 있습니다.

```cpp
#include <iostream>
#include <map>
#include <tuple>

int main()
{
	std::tuple<int, int, int> a, b;
	a = { 0, 1, 2 };
	b = { 3, 4, 5 };
	std::map<std::tuple<int, int, int>, std::string> m;
	m[a] = "First";
	m[b] = "Second";
	std::cout << m[a] << std::endl << m[b] << std::endl;

	return 0;
}
```
