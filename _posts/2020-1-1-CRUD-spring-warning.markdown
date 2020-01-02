---
layout: post
title: CRUD와 Spring MVC PATTERN
date: 2020-1-1T22:00:04.000Z
categories: update
---

<img src="https://github.com/arhrina/arhrina.github.io/blob/master/images/fulls/[000759].jpg?raw=true" class="fit image">

# CRUD는 Create, Read, Update, Delete를 의미한다

이것들은 각각 DB와 연동하여 동작하며,

Create는 insert SQL을 사용해서 자료를 만들고,
Read는 select SQL을 사용하여 단순 조회한 정보를,
Update는 특정값, 이를테면 어떠한 이름이나 값으로 조회한 값에 대한 자료를 불러들여와서 필요한 부분만을 수정하고
update SQL문을 사용하여 수정한 정보를 바꿔넣어준다. update SQL문은 일괄되게 작동하므로 반드시 where로 조건을 건 SQL문을 사용해야한다
Delete는 사이트 운영에 있어서 로그를 남기기 위해 테이블에 조회만을 위한 컬럼을 하나 만들어 delete 여부를 update SQL 사용하거나, delete SQL문으로 DB에서 지우는 방식으로 사용한다


이를 바탕으로 스프링의 MVC를 사용한다

# MVC에 대하여

M은 어떠한 자료도 담을 수 있는 Model 클래스를 의미한다. Model로 attribute를 보내서 View에서 사용하게 하기 위한 자료형으로 이해하면 되겠다

V는 스프링 형식의 views 폴더에 들어있는 xml, html 등의 페이지이다. 컨트롤러에서 method의 return값으로 가지는 정보는 servlet에서 자동으로 mapping되어 views폴더의 xml 파일을 열게 된다. 여기에는 front-end쪽에서 사용되는 html, css, js, jquery, ajax등을 통한 기법으로 레이아웃과 내부동작을 만들어줘야한다

C는 Controller를 의미한다. Autowired annotation을 통해 single tone으로 동작하는 인스턴스들을 만들고, requestMapping annotation으로 URI(URL)을 만들어 GET, POST 등의 method 동작들의 내부를 만든다

* 여기서 GET과 POST 동작들은 같은 URL에 대해서만 동작한다. 리퀘스트매핑으로 value지정하여 만들어준 URL이 같은 GET의 return인 views폴더의 xml파일에서 method동작을 POST로 지정해주면 해당 페이지에서 사용된 변수명 등을 담아 동일한 value를 가진 POST로 전달되어 POST가 동작한다




# 스프링으로 프로그래밍을 하기 위해서는 기본적인 환경설정이 절반정도를 차지한다

* pom.xml 파일을 통한 라이브러리들의 세팅(maven repository를 참조하거나 local에 지정해둔 maven을 사용)
* DB와 연결하기 위한, jdbc를 사용한다고 가정했을 때 bean에 올릴 4개의 설정값을 올릴 파일, mapper에 대한 설정을 올릴 파일, 실제 SQL문으로 동작하는 mapper, mapper를 동작시키기 위한 interface class(보통 dao) 등의 경로와 존재를 정확하게 설정해주어야한다
* 동작은 V와 C에서 세세하게 만들어주며 필요하다면 컨트롤러에 올릴 서비스파일 등을 만들 수 있다
<br><br><br>

<h1>스프링은 친절하지 않다. 정확하게 어디서 오류가 발생하였는지를 짚어주지 않으며, 프로그래머가 이것에 대한 기본 이해를 바탕으로 흐름을 더듬거나 자주 발생하는, 혹은 설정에서 발생하는 오류에 대해서 정확하게 인지하고 있어야 수월하게 수정을 할 수 있다</h1>