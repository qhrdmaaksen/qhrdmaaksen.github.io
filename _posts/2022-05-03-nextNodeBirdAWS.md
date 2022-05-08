---
layout: post
title: "nodeBird AWS 배포"
---

## 배포 정리 글

```js

------------------------------------------------
라이브러리
npm i pm2 (backGroundProcess (터미널 종료되어도 서버 종료 X ))
------------------------------------------------
EC2 생성 파트
패키지마다 최적화가 되있는게 있고 자동으로 되있는게있고 수동으로 줘야하는게 
있다

"start": "cross-env NODE_ENV=production next start -p 3060"
코드 추가, cross-env 는 환경변수 설정하는 패키지 윈도우에서도 맥과 리눅스와 
같이 환경변수 세팅 할 수 있게 해줬다

빌드한 결과물은 JS 파일로 .next 폴더에 들어간다 실행하려면 npm start 로 
실행하면 된다
--------------------------------------------------------
aws 배포
서버라는것은 컴퓨터며 자기컴퓨터여도되고, 남의 컴퓨터여도됨, 실제 서비스들은 
항상 24 시간 켜놈 내 컴퓨터로는 관리가 힘들며 aws 는 99.99% 의 가동률 보장

aws 는 메모리를 늘리고 줄이고를 어느정도 더 쉽게 할 수 있다

회원가입할때 신용카드 결제 1 달러가되는데 다시 돌려주니까 걱정말자

우분투 무료 및 보안 추가로 http, https 추가해주고 ssh 는 내 ip 
키는 react-nodebird 폴더에 넣어놨음
.gitignore file 에 
react-nodebird.pem
node_modules
.env
.next
적어주자 여기서 react-nodebird.pem 은 아까 aws 에서 생성한 key
.env 는 db id&password 

aws 와 연결하려면 aws 에 인스턴스에서 연결 누르고 ssh 클라이언트에서
//예: <내용> 을 복사해주자
그리고 key 가 있는 프로젝트 폴더 경로에서 git bash 통해 해당 프로젝트의 
바로 윗 줄 내용 복사한거 붙여주고 yes 입력 후 git clone 으로 github
프로젝트 주소를 입력 

ubuntu node 설치
sudo apt-get update
sudo apt-get install -y build-essential (bcrypt, image resizing 할때 error 안남)
sudo apt-get install curl
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash --
sudo apt-get install -y nodejs

위의 5개 설치 후 
node -v
npm -v 
로 버전 뜨면 정상
npm -v 에서 안뜨면 
sudo apt install npm 설치
그 후 npm i 설치

back end 쪽도 똑같이 터미널 하나 더 켜서 진행해주자
mySQL 은 따로 서버를 둬야하지만, aws 에 front back mysql 까지하면 요금이
많이 나올 수 있기에 back 에서 같이 설치 

back 에 mySQL 설치
(5버전 설치) sudo apt-get install -y mysql-server 
8 버전 설치는 
wget -c https://repo.mysql.com//mysql-apt-config_0.8.13-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.13-1_all.deb
sudo apt update
sudo apt-get install mysql-server
sudo su
sudo mysql_secure_installation (비번 강도는 normal 로 하자;)


sudo systemctl status mysql
sudo systemctl enable mysql
sudo apt-get update
sudo apt-get install mysql-workbench-community libmysqlclient18
sudo mysql -u root -p


.next 폴더까지 git에 올린 후 서버에서 받으면 서버에서는 빌드하지 않아도 
됩니다.


정리
코딩하고 깃 푸쉬 오리진 마스터해서 커밋 후에 깃 푸시 마스터해서 깃허브로
보내고 원격 접속해서 설치를 받아 깃 풀 해서 원격 프론트 받고 npm i 도 한번
돌려주고 (디펜던시들 패키지 설치했을수있으니) npm run build 하고 
npm start 이렇게 매번 치기 귀찮기때문에 cicd tool 이라고 명령어 대신해주는
툴이있다, 그리고 위에 sudo 라던지 계속 설치하기 귀찮으면
docker  라고있는데 서버 하나띄우면 docker 에 명령어 넣어두고 실행하면
명령어가 실행되면서 기존서버와 똑같은 서버를 만들어 낸다,
--------------------------------------------------------
back 에서 package json 의 nodemon app 은 개발할때만 사용하며, 배포할땐
node app 을 사용한다 
npm start 해주면 
.env file 을 .gitignore 에 설정했기때문에 db 연결이 불가, 
vim .env 해서 생성 후 .env 파일의 내용 추가
(앞에 . 이 붙으면 숨긴파일이다, 숨길파일 보려면 ls -a 로 확인가능)

npx sequelize db:create (해주면 react-nodebird 생김)

aws 인스턴스 생성 시 port 번호를 80 으로 설정했기에
vim app.js 에서 port 번호를 80 으로 바꿔주자 

npm start or sudo npm start 

foreground process
  터미널 끄면 같이 꺼짐 (node app)
background process (npm i pm2)
  터미널 꺼도 안꺼짐
pm2 사용 시 - pm2 start app.js 로 js 를 꼭 붙여야함










```
