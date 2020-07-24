---
title: "Learn to Program in Java (2)"
categories:
  - Java
tags:
  - edx
  - DEV276x
toc: true
toc_label: "Learn to Program in Java (2)"
last_modified_at: 2020-07-22T23:30:00-09:00
---

[지난 포스트][prev-post]에 이은 [Learn to Program in Java][edx-java] 두번째 시간입니다.

## Module 2 | Control Structures

boolean 자료형과 제어문, 반복문에 대해 알아봅니다. 문법적인 부분이 주를 이루다 보니 다른 모듈보다 비교적 빠르게 넘어갔네요. [두 번째 과제][project-2]도 매우 쉬운 편이었습니다.

### Relation Operator

관계 연산자(`==`, `!=`, `<`, `>`, `<=`, `>=`)를 이용하여 두 primitive data type에 대한 관계 연산을 할 수 있습니다. 하지만 String은 primitive data type이 아니기 때문에 객체의 method를 사용해서 비교해야 합니다.

> String 객체를 == 연산자를 통해 비교할 경우, 주소값을 비교한 뒤 true 혹은 false 값을 리턴하게 됩니다. 즉 에러를 발생시키지 않기 때문에 프로그램이 예상치 못한 동작을 할 수 있으므로 주의가 필요합니다.

```java
"string" == "string"        // Please don't do this!
"string".equals("string")   // Great!
```

[prev-post]: https://yyyoungha.github.io/java/learn-to-program-in-java-1/
[edx-java]: https://www.edx.org/course/learn-to-program-in-java-2
[project-2]: https://courses.edx.org/courses/course-v1:Microsoft+DEV276x+1T2020a/discussion/forum/2f82d12a81a1278addb125973090d19e42d17c31/threads/5f185cc1eac4b40841a221b9
