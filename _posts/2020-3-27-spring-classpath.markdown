---
layout: post
title: Spring-ClassPath?
subtitle: classpath
date: 2020-03-27T16:28:25.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/IMG_1076.JPG'
tags: spring
---

<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/cover/IMG_1076.JPG?raw=true">

web.xml을 열어보면 ContextLoaderListener의 환경설정 파일인 applicationContext.xml의 위치를 지정하는 것으로, param-name으로 contextConfigLocation을 가지고 value로 classpath*:로 JVM이 인식하도록 되어있는 일종의 프로젝트 내에서 쓰는 환경변수라고 볼 수 있다

eclipse prj의 build path에서 configure build path(java build path)의 source 탭을 보면 classpath: 의 위치가 나타난다

와일드카드 문자열 /*과 /**을 활용해서 디렉토리를 지정해줄 수 있다

/*의 경우는 바로 하위 디렉토리까지만 접근하는 것이며, /**은 그 이하 디렉토리까지도 접근할 수 있게 해준다

<!-- classpath의 빌드는 gradle을 활용하는지, maven을 활용하는지에 따라 다르다. -->

스프링의 빌드 도구로는 Ant, Maven, Gradle이 있는데 이는 다른 포스트에서 다루겠다