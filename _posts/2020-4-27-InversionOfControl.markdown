---
layout: post
title: IoC와 IoC 컨테이너
subtitle: spring
date: 2020-04-27T18:50:25.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/'
tags: spring, design pattern
---

## IoC. Inversion of Control. 제어의 반전(역제어)

정의상으로는 프로그래머가 작성한 코드가 재사용 라이브러리의 <a href="https://ko.wikipedia.org/wiki/%ED%9D%90%EB%A6%84_%EC%A0%9C%EC%96%B4">흐름 제어</a>를 받게 되는 디자인 패턴이다

풀어 얘기하면, 전통적인 흐름은 프로그래머가 작성한 코드가 외부 라이브러리를 호출하는데, 이것을 반대로, 프로그래머의 코드를 외부 라이브러리가 호출하게 되는 것을 얘기한다

이 제어 반전의 목적은,

* 구현과 수행을 분리
* 모듈 제작시 외부 라이브러리(혹은 프로그램)와 결합을 고민할 필요없이 모듈의 목적 그 자체에 집중이 가능
* 다른 시스템은 신경쓰지 않아도 됨
* 모듈이 변경되어도 다른 시스템에 영향을 미치지 않음



## 스프링의 IoC 컨테이너

스프링은 컨테이너(외부)에서 제어를 하게 된다.

스프링의 컨테이너에 대해 알려면 DI(Depedency Injection)도 알아야되는데, 이는 추후 포스팅..

<b>빈(Bean)</b> : 스프링이 제어권을 가지고 직접 생성
<b>빈 팩토리(Bean factory)</b> : 
<a href="https://js2prince.tistory.com/entry/Spring-IOC-%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%84%88-%EB%9E%80"> 스프링 공부</a>

작성중. 시간많을때 확실하게 포스팅해야하는 내용...정말로 확실하게 알아두면 spring framework이든 spring boot든 도움이 될 내용이다