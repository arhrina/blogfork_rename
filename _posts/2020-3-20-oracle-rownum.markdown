---
layout: post
title: ROWNUM, ORDER BY에 사용 유의할 점
subtitle: oracle
date: 2020-03-20T09:28:25.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/[011038].jpg'
tags: db, oracle
---

<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/cover/[011038].jpg?raw=true">

programmers level 3 SQL문을 풀다가, ROWNUM 값이 랜덤하게 변하는 듯한 문제가 있어 읽어보고 정리합니다

<h3>ROWNUM의 ORDER BY 실행 순서를 기억하여 사용해야한다</h3>

<b>ROWNUM</b>은 오라클 내부에서, 자료가 join되는 순서, 혹은 select 되는 순서대로 한 줄(row)에 번호를 매겨주는 기능을 한다
시작값은 0이 아닌 1이며, 1씩 값이 증가한다

우리가 따로 테이블을 생성하지 않아도 존재하는 dual 테이블처럼 select, join을 할 때 자동생성되는 칼럼이며 *에는 나타나지 않고 별도로 projection시에 ROWNUM을 추가하여 확인할 수 있다



mysql의 LIMIT과 같은 용도로 쓰게 되는데, 예를 들어 서울시민 중에 마포구에 사는 주민을 상위 <ins>10명을 보여주는</ins> 식의 query문에서 사용된다

```sql
SELECT * FROM 서울시 등록 시민테이블 WHERE 구='마포' AND ROWNUM <= 10;
```

문제는 ORDER BY와 같이 사용될 필요가 있을 때인데, ORDER BY의 실행우선순위가 ROWNUM 조건을 검사하는 것보다 낮기 때문에 문제가 발생한다

예를 들어 마포구에 사는 시민 중 이름을 오름차순 정렬해 가장 빠른 사람 10명을 뽑는다고 한다면

```sql
SELECT * FROM 서울시 등록 시민테이블 WHERE 구='마포' AND ROWNUM <= 10 ORDER BY 이름 ASC;
```

이와 같은 코드를 생각하게 될 수 있는데, 테이블에 들어있는 자료가 많아질수록 전혀 다른 값을 받는다

```sql
SELECT * FROM 서울시 등록 시민테이블 WHERE 구='마포' AND ROWNUM <= 10 ORDER BY 이름 ASC;
-- 이 SQL문이 잘못된 값을 보여주는 이유는,


SELECT * FROM 서울시 등록 시민테이블 WHERE 구='마포'
-- 여기까지 진행된 SELECT 문에 대한 ROWNUM을 1부터 10까지 뽑아낸 다음, ORDER BY 하여 ROWNUM이 1~10인 자료값의 이름을 정렬해주기 때문이다

-- ORDER BY한 자료값들에서 ROWNUM을 10까지 뽑아주는 것이 아니다
```

ROWNUM을 확인해보기 위해서 쓸 수 있는 코드는, 프로젝션에 칼럼처럼 ROWNUM을 쓰는 것이다

```sql
SELECT *, ROWNUM FROM [TABLE];
-- 이와 같이 사용하면 ROWNUM 값도 결과창에서 확인할 수 있다
```


ORDER BY한 자료값을 ROWNUM으로 원하는 개수만큼을 빼내고 싶다면, 여기서 subquery를 사용해야한다

subquery는 SQL문 안에 SQL문을 사용하는 것인데, SELECT tbl.* FROM [테이블1 LEFT JOIN 테이블2 ON '조인시 참조하려하는 칼럼들의 조건'] AS tbl; 등으로 쿼리문의 안에 요소로 쿼리문을 사용하는 것이 subquery이다

ROWNUM의 정의에서, SELECT나 JOIN한 순서대로 값에 매겨지는 순서값이라고 하였으니, FROM [테이블명]에 서브쿼리가 들어가서 원하는 데이터의 정렬까지 된 값을 SELECT 해오면 ORDER BY 되어 넘어온 자료에 순서번호가 붙게 되고, WHERE 조건으로 ROWNUM을 10개까지 지정해주면 원하는 쿼리문을 완성할 수 있다


```sql
SELECT a.* FROM ( -- 필요하다면 쿼리와 서브쿼리 프로젝션 둘 모두에 ROWNUM을 입력해 쿼리의 ROWNUM과 서브쿼리의 ROWNUM을 비교해볼 수도 있다
    SELECT * FROM 서울시 등록 시민테이블 WHERE 구='마포' ORDER BY 이름 ASC;
) AS a
WHERE ROWNUM <= 10;
```