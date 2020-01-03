---
layout: post
title: 매개변수와 전달인자
subtitle: parameter, argument?
date: 2020-01-03T13:15:05.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/[001888].jpg'
tags: 매개변수와전달인자
---

<img src="assets/img/cover/[001888].jpg">

매개변수(Parameter)와 전달인자(Argument)



매개변수는 실제 값이 존재하지 않고 형태를 나타내준다
예를 들어,

```c{
#include <stdio.h>

int sum(int a, int b){
return a+b;
}
```
라는 코드가 있을 때, a와 b는 실제 값을 가지진 않는다. 하지만 sum이라는 함수를 호출할 때 2개의 int형 값을 넣어주어야 한다는 '형'을 가지고 있다. Java에서 class와 instance의 관계처럼, 하나의 틀(혹은 templete)을 만들어주는 것이 매개변수이다




전달인자는 실제로 전달되는 값이다

```java{
public void sum(int a, int b){
system.out.printf("%d", a+b);
}
```
이러한 메소드가 있을 때,

```java{
public static void main(String args[]){
sum(10, 25);
}
```

메소드를 사용할 때 전달되는 '실존하는 값'이다. 이는 자료값이 매개변수와 같아야 동작하며, 형변환하여 값을 전달하는 것도 가능하다
