---
layout: post
title: 싱글톤 패턴(Single tone Pattern)
subtitle: Design Pattern
date: 2020-01-06T17:20:33.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/[010751].jpg'
tags: DesignPattern
---

<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/cover/[010751].jpg?raw=true">

싱글톤 패턴(Single Tone)

어떤 클래스에 대해 한 번만 메모리를 할당하고 그 메모리에 인스턴스를 만들어 사용하는 디자인 패턴. 객체의 생성과 관련된 생성 디자인 패턴이다

여러번 생성자를 호출해도, 실제 내부에서 생성되는 객체는 하나고 최초 생성 이후에 호출된 생성자는 최초에 생성했었던 객체를 반환할 뿐이다. 즉, 하나만의 인스턴스를 만들어 사용하는 것이다. 여러 곳에서 하나를 공유하여 사용할 때 사용하는 것이 일반적이다


전역 인스턴스를 쓰므로 데이터 공유가 편하고, 공통된 객체를 참조해야할 때 사용하면 좋은 패턴이다

최초 할당 이후 두 번째 이용시부터는 객체 로딩시간이 현저하게 줄어들기 때문에, 성능이 좋아진다



다만, 너무 많은 일을 싱글톤이 처리하게 하면 데이터 결합도가 높아져 좋지 못한 설계의 원인이 될 수 있으며, 그렇게 된다면 수정, 삭제가 대단히 어려워질 수 있다. 또한 멀티쓰레드 환경에서는 동기화 문제가 존재하며 이를 해결하기 위한 몇몇 기법이 존재한다