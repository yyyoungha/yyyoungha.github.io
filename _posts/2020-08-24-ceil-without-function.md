---
title: "Ceil of a/b without ceil() function"
last_modified_at: 2020-08-24T20:40:00-09:00
categories:
  - algorithm
tags:
  - C++
toc: true
toc_label: "Ceil of a/b without ceil() function"
---

두 자연수 입력 a, b에 대한 ceil(a / b)를 라이브러리 함수 호출 없이 구현하는 방법을 알아보겠습니다.

## Problem

[Atcoder](https://atcoder.jp/home)에서 [굉장히 쉬운 알고리즘 문제](https://atcoder.jp/contests/abc176/tasks/abc176_a)를 풀다가 문득 정답을 작성할 때 아래와 같은 코드가 자주 등장한다는 사실을 깨달았습니다.

```cpp
int quotient(int a, int b) {
    if(a % b == 0)
        return a / b;
    else
        return a / b + 1;
}
```

두 자연수 a, b가 주어졌을 때, a가 b로 나누어 떨어지면 몫을 그대로 반환하고, 그렇지 않은 경우 그 몫에 1을 더해 반환하는 코드입니다. 이 코드를 cmath 라이브러리의 [ceil()](http://www.cplusplus.com/reference/cmath/ceil/?kw=ceil) 함수를 활용하여 다음과 같이 바꿔 쓸 수도 있습니다.

```cpp
#include <cmath>

int quotient(int a, int b) {
    return ceil((double)a / b);
}
```

하지만 매번 `ceil()` 함수를 쓰기 위해 소스코드의 맨 위로 올라가서 `cmath` 라이브러리를 다시 include하는 것이 너무 번거롭게 느껴졌고, if문을 쓰는 것 또한 답답하게 느껴졌습니다. 그래서 a와 b의 식 하나로 같은 결과를 나타낼 방법을 생각해보게 되었습니다.

## Solution

먼저 간단한 예제부터 생각해보기로 했습니다. b = 3 이라 가정하고, a값의 변화에 따른 a / b 값을 첫번째 행에, 원하는 결과값인 WANT을 두번째 행에 표시하면 다음 표와 같이 나타납니다.

| a     | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| ----- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| a / b | 0   | 0   | 0   | 1   | 1   | 1   | 2   | 2   | 2   | 3   | 3   |
| WANT  | 0   | 1   | 1   | 1   | 2   | 2   | 2   | 3   | 3   | 3   | 4   |

이렇게 적어두고 보니 두 행에서 숫자들이 동일한 패턴으로 나타남을 알 수 있습니다! 주기도 b로 동일하네요. a / b값을 한 주기만큼 앞당기고(+b) 한 칸씩 뒤로 밀어내면(-1) WANT와 동일한 값을 가진다는 사실을 알 수 있습니다.

| a               | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| --------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| (a + b - 1) / b | 0   | 1   | 1   | 1   | 2   | 2   | 2   | 3   | 3   | 3   | 4   |
| WANT            | 0   | 1   | 1   | 1   | 2   | 2   | 2   | 3   | 3   | 3   | 4   |

위에서 정리한 사실을 바탕으로 `quotient` 함수를 아래와 같이 a와 b의 식 하나로 만들 수 있습니다.

```cpp
int quotient(int a, int b) {
    return (a + b - 1) / b;
}
```

## More

흥미가 생겨 관련 내용을 더 찾아보다 [Ceil of a/b without ceil() function](https://www.geeksforgeeks.org/find-ceil-ab-without-using-ceil-function/) 이라는 주제로 쓴 글을 발견했습니다. 이 글에는 ceil()을 구현하는 재미있는 코드가 포함되어 있었는데요, 바로 a를 b로 나눈 몫에다 (a % b) != 0 값을 더하는 것이었습니다. `%` 연산자와 `!=` 연산자가 포함되어 있어 바로 위에 작성한 코드보다는 느리겠지만 굉장히 직관적이라는 장점이 있어 알고리즘 문제풀이에는 유용하게 사용할 수 있을 것 같습니다.

```cpp
int quotient(int a, int b) {
    return (a / b) + ((a % b) != 0);
}
```
