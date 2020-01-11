---
layout: post
title: git bash로 github 기초사용법 정리
subtitle: github
date: 2020-01-12T07:30:25.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/IMG_2463.JPG'
tags: github
---

<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/cover/IMG_2463.JPG?raw=true">

<h3>github 기본 사용법</h3>

git으로 형상관리할 폴더에서 git bash를 실행시킨다

해당 폴더에 .git 폴더가 없다면(숨김 폴더니 확인하려면 숨김을 볼 수 있게 설정해야한다) 최초 git init를 실행한다
<br><br>

git config \--local user.name 본인의깃허브닉네임<br>
git config \--local user.email 본인의깃허브이메일<br>

* 해당 폴더에서만 사용될 세팅이다. 해당 컴퓨터 전체에서 세팅하고 싶다면 local이 아니라 global로 세팅한다

git add .       을 입력하면 .git폴더에서 관리하는 형상에서 변경사항이 있는 모든 것을 status에 올린다. 최초에는 폴더의 모든 것이 등록된다
<br>

git commit -m MESSAGE   를 입력해서 깃허브에 커밋할 파일들에 메시지를 달아준다
* 띄어쓰기를 포함시키려면 큰따옴표를 열어서 문자열로 "2020. 1. 12. 깃 최초 커밋"같이 메시지를 입력해줘야한다
<br>
git remote add origin https://github.com/본인의깃허브닉네임/repository명.git 을 입력해서 origin이라는 이름으로 repository 별명을 입력해준다. 최초 1회만 사용한다
* 다른 방법을 사용한다면 git remote는 할 필요가 없다

git push -u origin master 명령어를 사용한다. master branch로 origin이라는 별명을 가진 repository에 업로드(push)하라는 명령어이다
* 다른 방법은 remote를 하지 않고 git push \--set-upstream github/repositoryURL master 명령어를 사용해 upload를 해당 repository로 고정하는 명령어이다
* 다른 방법을 사용하면 remote도 하지 않으며 최초 설정 후에는 add와 commit 후에 git push만 입력하면 된다


git은 형상관리를 하므로 현재 repository에 존재하는 파일과 local에 존재하는 파일이 다르면 push시에 reject 에러를 띄운다. git pull을 수행하여 각각을 동기화하고 업로드하라고 하는데,
pull 하지 않고 강제로 push를 하고 싶다면 git push -f라는 명령어를 사용해 강제로(force) push를 시킬 수 있다. 단, 이 때는 기존 commit 기록이 모두 삭제되므로 사용에 주의

<br>

여러 컴퓨터에서 하나의 repository에 접근하여 local과 repository의 형상이 어긋나게 되면 git pull 명령어를 해도 원하는만큼 파일을 받아오지 못할 때가 있는데, 이럴 때는 그냥 새로운 폴더를 만들고 git init 명령어 수행 후 git pull repositoryURL을 입력해 파일을 받아오고 config와(global이라면 패스) 추가되길 원하는 파일을 올리고 add, commit, push세팅을 순서대로 해주면 된다
<br>

git 명령어에 대해 더 알고 싶다면 아래 링크를 참조
<br><a href="https://terms.naver.com/entry.nhn?docId=4125964&cid=59321&categoryId=59321&expCategoryId=59321">네이버에 있는 깃 소개 및 명령어</a><br>
<a href="https://git-scm.com/docs">영어로 된 github에 있는 모든 명령어와 사용법.</a><br> 모두 숙지하면 좋겠지만, 자주 사용하는 merge나 잘 사용하지 않는 추가 명령어들(push 뒤에 붙는 -f라든가)에 대한 레퍼런스가 필요하다면 여기로
