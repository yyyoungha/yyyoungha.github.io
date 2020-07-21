---
title: "Learn to Program in Java (1)"
categories:
  - Java
tags:
  - edx
  - DEV276x
toc: true
toc_label: "Learn to Program in Java (1)"
last_modified_at: 2020-07-21T23:30:00-09:00
---

## Motivation

취업 준비를 하면서 유명 IT 기업들의 채용 공고를 둘러보니 Java 개발 경험을 자격 요건으로 내세운 공고가 많이 보였습니다. 요즘은 주로 알고리즘 문제를 플고 있는데 풀이에 C++를 사용하다 보니 감을 잃지 않기 위해 Java를 따로 복습할 때가 되지 않았나 하는 마음이 들었습니다. 그래서 관련 학습 자료를 찾아 헤매다 역시 제게 익숙한 MOOC 사이트들을 먼저 둘러보게 되었고, 그 중 edX의 [Learn to Program in Java][edx-java] 코스를 수강하기로 결정했습니다.

### Why this course?

이 강의로 선택한 이유는 Microsoft 강의라서 학교 강의들 보다 실무와 연관되어 있을 것 같았고(나중에 알고 보니 제 생각과는 달리 해당 과정은 전통적인 대학교 프로그래밍 교육과정에 기초하여 만들어졌다고 합니다.) IDE로 Eclipse가 아닌 IntelliJ를 사용하는 점 또한 제게는 매력적으로 다가왔습니다. 처음 언어를 배울 때 처럼 문법적인 부분이 아닌, 개념적인 부분을 중심으로 복습을 해 보려고 합니다.

## Module 0 | About this course

본격적으로 강의를 시작하기 전 코스에 대한 설명, 사전 설문 등이 포함되어 있습니다. 그 과정에서 연습 문제를 풀기 위해 University of Washington에서 운영하고 있는 "[Practice-It][practice-it]" 이라는 서비스에 별도로 계정을 생성해야 하는 번거로움이 있었습니다.

## Module 1 | Java Basics

Java의 특징과 자료형, 입출력에 대하여 알아봅니다.

### Java의 특징

- Most Popular
- [Object Oriented][wiki-oop]
- Platform Independent
- Automatic Memory Management(AMM)

### [Java의 컴파일과 실행 환경][java-exec]

Java의 가장 강력한 장점 중 하나는 플랫폼 독립적으로 설계되었다는 점입니다. 운영체제가 달라질 때 마다 새로 프로그램을 작성하고 컴파일해야 하는 것과는 달리 Java는 소스코드(.java)를 바이트코드(.class)로 컴파일한 후, 이 바이트코드를 JVM에 의해 실행시키는 방식으로 실행됩니다.

### Java 코드를 작성할 때 주의사항

- 클래스명과 파일명을 일치시켜야 합니다.
- [Camel case][gfg-camel-case] 명명규칙에 따라 클래스명, 함수명, 변수명을 작성합니다.

## 중간 코스 평가

전체 과정은 코스 설명을 제외하고 4개의 모듈으로 나뉘어져 있고, 3개 모듈은 끝날 때 마다 하나의 프로그래밍 과제가 있고 마지막 모듈은 최종 프로젝트로 진행됩니다. 오늘은 Module 0 About this course와 Module 1 Java Basics를 끝마치고 과제를 제출해 보았습니다.

개념을 설명하는 각 영상의 길이가 5분 정도로 길지 않아 빨리 듣기에는 부담이 없지만 자세한 설명을 원하시는 분들께는 다소 짧게 느껴질 수 있을 것 같습니다. 프로그래밍을 처음 접하신다면 이 강의는 권하기 어렵겠지만, 저처럼 빠른 복습을 목적으로 하는 분들에게는 괜찮은 선택이라 생각합니다.

[edx-java]: https://www.edx.org/course/learn-to-program-in-java-2
[practice-it]: https://practiceit.cs.washington.edu/
[wiki-oop]: https://en.wikipedia.org/wiki/Object-oriented_programming
[java-exec]: http://tcpschool.com/java/java_intro_programming
[gfg-camel-case]: https://www.geeksforgeeks.org/java-naming-conventions/
