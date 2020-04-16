---
layout: post
title: Eclipse, Could not create the Java Virtual Machine
subtitle: Error:A fatal exception has occurred
date: 2020-04-16T19:09:25.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/buildpath_JavaVersion.png'
tags: java
---

## Java Virtual Machine Launcher Error

Eclipse에서 server run을 하였는데 Could not create the Java Virtual Machine 에러가 발생하였다

두번째 줄에 존재하는 에러마다 해결 방법이 다른데, A fatal exception has occurred. Program will exit에 대한 포스팅이다

한 워크스페이스에서 다른 jdk version을 적용하여 프로젝트가 돌아가고 있는 상황이다. jdk 7과 9로 라이브러리가 설정되어 되어있는 상황인데,

9로 설정된 상태에서 7을 run server 시키니까 에러가 발생하였다

이클립스의 run setting이 프로젝트마다 관리되는 것이 아닌, 워크스페이스마다 관리되다보니, jdk 7로 설정된 프로젝트를 9로 돌리려다보니 발생하였다

해결방법은 간단하다. prj 우클릭해서 build path-configure buildpath하여 JRE System library를 Edit,

Alternate JRE를 들어가서 9에 체크되어있는 것을 7로 바꿔주면 된다. 이러면 워크스페이스가 7로 설정되어, 9를 run시키려하면 다른 에러가 발생한다. 동일하게 9로 바꿔주면 해결된다

혹시나하니, java compiler도 버전을 확인해주고 prj facets도 확인해주자