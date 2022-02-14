---
layout: single
title: "깃 기초 사용법을 알아두자!!"
---

<h2>자주 쓰고있더라도 혹시 모를 미래의 당황할 나에게 깃에 대해 아예 기록해두자!</h2>

<h3>chapter 1</h2>
<p>로컬 작업</p>

<dl>
  <dt>
    git config --global user.name "vitamin777777"
  </dt>
  <dd>
    깃 구성 내가 쓸 이름 지정해주기
  </dd>
  <dt>
    git config --global user.email "myEmail.com"
  </dt>
  <dd>
    깃 구성 내 이메일 주소 지정해주기
  </dd>
  <dt>
    git config --list
  </dt>
  <dd>
    내 이름과 이메일이 정확히 지정되었는지 확인, 끝에 q 누르면 다시 명령입력상태바뀜
  </dd>
  <dt>
    개발 툴이 따로있다면 내가 사용해본 툴이라면 터미널 옵션에서 열어주기
  </dt>
  <dd>
    
  </dd>
  <dt>
    git init
  </dt>
  <dd>
    git initialize ( 깃 초기화 해주기)  
  </dd>
  <dt>
    git add . 
  </dt>
  <dd>
    git add 추가된 내용 추가해주기!
  </dd>
  <dt>
    git commit -m "history"
  </dt>
  <dd>
    기록 중간중간 저장해주기
  </dd>
  <dt>
    git remote add origin git@github.com:company/projectname.git
  </dt>
  <dd>
    깃 허브에 프로젝트와 내 터미널 연결시켜주기
  </dd>
  <dt>
    git remote -v
  </dt>
  <dd>
    내가 연결한 주소 확인해주기
  </dd>
  <dt>
    git push origin master 
  </dt>
  <dd>
    commit 된 내용을 깃 저장소에 push 하기
  </dd>
  <dt>
    git status
  </dt>
  <dd>
    현재 깃 상태확인
  </dd>
</dl>
<hr>

<h3>chapter 2</h3>
####회사에서 처음에 해야할 것?
<dl>
  <dt>
    명령프롬프트 cmd 켜기
  </dt>
  <dd>
    cd 예: Desktop -> 폴더-> 이동 (회사 프로젝트가 들어갈 상위 폴더)
  </dd>
  <dt>
    github에서 코드에서 링크 복사
  </dt>
  <dd>
    cmd 에서 git clone git@github.com:company/projectname.git newFolder
  </dd>
  <dt>
    newFolder에 깃 복제 
  </dt>
  <dd>
    cmd에서 프로젝트가 들어갈 상위폴더지정해준 상태라면 cd newFolder 까지 이동
  </dd>
  <dt>
    cmd 에서 code .  
  </dt>
  <dd>
    코드가 내 tool 에 이동 확인
  </dd>
</dl>
<hr>

###chapter 3
####회사에서 작업 후 병합 
<p>!!!ps 절대! git push origin master 에 혹시나 습관처럼 절대 push 하지말자!</p>
<dl>
  <dt>
    git checkout -b newEmployee
  </dt>
  <dd>
     아마도 이건 회사에서 내가 push 할수 있는곳을 만들어줄것같다.
  </dd>
  <dt>
    git push origin newEmployee
  </dt>
  <dd>
    gitHub 회사 newEmployee 브랜치에 작업물 push<br>
    compare & pull request 눌러서 간단한 코멘트 남기고 create pull request<br>
    위에 code issues pull request(1) << pull request에 요청떠있나 한번확인 
  </dd>
  <dt>
    git pull origin master
  </dt>
  <dd>
    동기화)내가작업하는게있다면 git add . and commit 해주고 ,master branches 에 바뀐게있다면 master pull해주기
  </dd>
  <dt>
    새 리포지토리 remote 추가 / 기존 리포지토리 remote 제거
  </dt>
  <dd>
    추가 : git remote add origin 주소 / 기존 제거 : git remote remove origin
  </dd>
  <dt>

  </dt>
  <dd>

  </dd>
  <dt>

  </dt>
  <dd>

  </dd>
  <dt>

  </dt>
  <dd>

  </dd>
  <dt>

  </dt>
  <dd>

  </dd>
</dl>