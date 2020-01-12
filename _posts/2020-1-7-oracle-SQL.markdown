---
layout: post
title: SQL CRUD 기본정리
subtitle: SQL
date: 2020-01-07T12:36:26.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/IMG_1427.JPG'
tags: DB
---

<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/cover/IMG_1427.JPG?raw=true">

```SQL
SELECT * FROM [table];

실 사용예 ) SELECT * FROM tbl_iolist;
```

테이블에 있는 모든 것들을 보여주는 명령어. 조회의 가장 기초가 되는 개념이다

```SQL
SELECT [COLUMN projection] FROM [table] WHERE [조건];
실 사용예 ) SELECT u_id, u_password FROM tbl_user WHERE u_name LIKE '%민%' AND u_nick = '김';
```
위의 예시는 u_name의 가운데에 민이라는 글자가 들어가며(민이 첫글자거나 끝글자여도 조회된다) u_nick이 김인 u_id, u_password 자료값을 조회한다


원하는 COLUMN만을 조회할 수도 있으며, oracle의 경우 as를 붙여서 임시로 다른 이름으로 보이게 조회할 수도 있다
또, WHERE로 조건을 붙여 해당 조건만을 가진 데이터를 조회할 수 있다


```SQL
INSERT INTO [table](column1, column2, column3 ....) VALUES(column1에 들어갈 값, column2에 들어갈 값, column3에 들어갈 값 ...)
```
테이블에 새로운 자료값을 집어넣는 SQL문
spring framework에서 사용하려면 not null과 unique를 java에서 한번 체크하고, jdbc를 사용한다면 jdbcType을 추가해서 사전에 호환성을 맞춰주는 것이 좋다

```SQL
UPDATE [table] SET(column = 값) WHERE [조건];
실 사용예 ) UPDATE tbl_book SET(b_name = 'JUSTICE') WHERE b_author = '마이클 센델';
```
이미 insert 되어있는 값에 특정 column들을 지정하여 해당하는 값들을 바꿔준다. 수정의 개념으로 사용된다<br><h3>조건을 반드시 붙일 것!!</h3><br>
조건을 붙이지 않으면 해당 table에 들어가있는 모든 자료값들이 일괄적으로 변경된다
백업본이 없는데 커밋을 해버리게 된다면 말 그대로 재앙이 되어버릴 수 있다. 은행에서 근무하는데 조건을 넣지 않는다면 특정 사람의 잔고를 1000원으로 만들려다가 모든 고객들의 잔고를 1000원으로 만들어버리게 된다면 뒷수습은...

```SQL
DELETE FROM [table] WHERE [조건];
실 사용예 ) DELETE FROM tbl_book WHERE b_name = '82년생 김지영';
```
이 역시 조건을 걸어주지 않으면 재앙이 될 수 있다. 해당 테이블의 모든 자료값이 DELETE 되어버린다
DB에 해당하는 자료값을 아예 삭제해버리는 명령어이며, 삭제되더라도 log를 남겨야한다면 테이블의 설계에서 삭제여부를 확인하는 column을 추가하고 삭제시 update하여 해당 column에 스위치를 주어 보관하는 방법도 존재한다. 스위치를 준다면 기본조회시 WHERE b_delete != 'Y' 같은 조건을 붙여주어야 삭제된 내용들이 보이지 않을 것이다
