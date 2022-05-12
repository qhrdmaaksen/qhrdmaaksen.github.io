---
layout: post
title: "nodeBird AWS 배포"
---

## 배포 정리 글

```js

------------------------------------------------
라이브러리
npm i pm2 (backGroundProcess (터미널 종료되어도 서버 종료 X ))
npm i multer-s3 aws-sdk 
  (multer-s3(멀터를 통해 s3 로 올릴때)aws-sdk (s3 접근권한 얻을때 사용))
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
sudo npm start 로 실행 후 ip 주소로 연결안된다면 pm2 monit 입력
pm2 monit 이 안되면 npx pm2 monit 
npx pm2 kill 은 켰던거 끄는거
sudo npm start 를 사용했다면 pm2 도 sudo npx pm2 monit 
처럼 sudo 를 붙여줘야한다

pm2 는 log 기록을 볼 수 있으며, 서버가 죽었을 시 서버를 자동으로 되살려줌
npx pm2 logs 하면 로그들을 볼 수 있으며,
npx pm2 logs --error 은 에러 로그를 볼 수 있다
sudo npx pm2 list 는 현재 사용중인 port check 
sudo npx pm2 start app.js (app.js 실행)
sudo npx pm2 reload all  (서버들을 한번 씩 재시작하면서 반영됨)

우분투에서 80 port (aws 인스턴스 port number) 를 접근하려면 
sudo 를 붙여줘야한다

aws 에서 ip 고정하게되면 요금이 청구된다

배포를 하기위해 백엔드 설정
(노드에서 프로덕션 실행할땐 helmet hpp 는 필수)
(app.js 에서 설정)
npm i pm2 cross-env 설치
npm i helmet
npm i hpp
을 추가해줬기때문에 aws 운영체제에선 npm i 한번해주자

"start": "cross-env NODE_ENV=production pm2 start app.js"

항상 back 변경 후 커밋 푸쉬하면 aws 운영체제 환경에선  git pull 을 해주자
만약 Aborting 이 뜬다면 git reset --hard 후 다시 git pull 해주고
port 번호 app.js 에서 확인해주자 

front 에서도 terminal 을 끄는 순간 foreground node process 는 꺼진다
(next 도 마찬가지다)

실제 배포할때는 front 와 back 이 local 이 아닌 서로 다른 컴퓨터의 ip 
때문에 front 에서 고정된 변수로 back, aws ip 를 설정해서 주소들어가는곳들을
모두 변경해주자
front package.json 에서 port num 80 으로 변경 후 커밋&푸쉬 
front ubuntu 에서도 git pull 해주고 
npx pm2 start npm -- start ( pm2 를 사용해서 npm start 를)

항상...... front 를 실행할땐 back 서버가 정상 작동되는지 check 하자

front 에서는 git pull 하고 npm run build 하고 sudo npx pm2 reload all

db query 날릴땐 사용자로 로그인해서 해당 db 로 use db명 입력 후 쿼리문작성

만약 table 조회 시 대문자로되어있다면 drop table 해주고 우분투에서 
reload 해서 다시 반영하자

aws의 DB에는 로컬 DB의 데이터가 연동되지 않는 건가요??
aws에서 show tables; 시 기존 테이블들은 보이는 데 입력했던 데이터들은 
확인되지 않습니다.
따로 또 추가를 해야되는 건가요 ??
:네 연동은 직접 명령어를 쳐서 연동해야 연동되는 것이고요. mysqldump 관련 
명령어로 찾아보셔야 하는데, 어차피 테스트데이터이므로 연동하실 필요는 없다고 
봅니다.
테이블은 노드 서버가 실행될 때 자동으로 생성됩니다(sequelize.sync). 아마 
데이터베이스는 npx sequelize db:create로 직접 생성하셨을 겁니다.

원래 시퀄라이즈는 model명을 기반으로 테이블을 생성합니다. 이 이름을 
바꿔주고싶으면 tableName 속성을 설정하면 tableName에 적힌 그대로 
생성됩니다.

Cannot find module error
:pm2 랑 노드 버전 충돌 문제인듯 한데요.
sudo npm i -g pm2로 글로벌 설치 후
npx 빼고 sudo pm2  이런 식으로 해보세요.

nginx관련해서 보고 있는데 nginx가 정적파일도 제공해준다라고 알고 있는데 
제로초님 동영상으로 봐서는 따로 nginx로 정적파일을 제공을 안해주는거 
같습니다. 강의 코드에서 혹시 어떻게 빌드된 정적파일들이 제공되어지는지 
궁금합니다.🔥
:강의에서는 nginx는 정적파일을 제공하지 않습니다. 정적파일은 next 프론트 
서버가 제공합니다.
프론트 서버가 없는 경우 보통은 백엔드서버가 빌드된 파일을 제공합니다. 
react는 서버가 아니므로 정적파일을 제공할 수 없습니다.

ER_ACCESS_DENIED_ERROR
:node app.js할 때는 config/config.json의 development 부분이 실행되고 
npm start를 하면 production 부분이 실행됩니다.

start를 하면 next start를 하게 되고 build를 하면 next build를 하게 되는데
노드가 next start 명령어를 실행하면서 next의 서버가 실행됩니다. nginx나 
apache는 웹서버이고 next는 웹애플리케이션서버(WAS)라고 생각하시면 됩니다. 
nginx나 apache는 리액트 앱을 빌드하거나 SSR할 능력이 없습니다. 다만 이미 
빌드된 js파일을 프런트로 제공할 수는 있습니다.

아 그리고 혹시 인스턴스 상태를 중지로 하면 돈이 안나가나요?
:중지하면 안 나가긴 하는데 elastic ip(고정 ip)나 route53이나 ebs 스토리지
(영구스토리지)를 사용한다면 나갈 수 있습니다.

인스턴스의 임시 스토리지에 있는 데이터는 모두 손실됩니다.
라고 경고 메세지가 뜨는데 괜찮은 건가요? 사용을 안할 땐 꺼놓고 싶은데 
데이터가 무사한지..궁금합니다
중지말고 종료를 하면 아예 없어지는지도 궁금합니다.
:종료하면 아예 없어집니다. 중지할 때는 데이터는 사라지지 않습니다. 임시 
스토리지는 저희가 데이터를 넣는 /home 디렉토리와는 별도입니다.
https://stackoverflow.com/questions/11566223/what-data-is-stored-in-ephemeral-storage-of-amazon-ec2-instance
여기에서 atilacamurca 의 답변

cors 랑 cookie 는 다른문제, 새로고침 시 로그인이 해제되는 문제
브라우저의 network 에 setCookie 가 브라우저에 cookie 를 넣는 header 임

도메인이 없으면, 살생각이없다면 두 서버를 하나의 컴퓨터에 올려서 사용해야
쿠키 공유가 된다

 두개의 컴퓨터를 사용하는 경우 가비아에서 사면되며 aws 에 route53 가서
 dns 관리에서 호스팅 영역 생성에 도메인 이름 적고 생성누르면 생성됨
 ns 와 soa 가 있을건데 네임서버 설정에 내가 산 도메인을 aws 로 바꿔주자
 그리고 아이피를 고정시켜줄땐 탄력적 ip 주소에서 프론트와 백용 두개를
 할당하며 인스턴스 하나만 등록?해주면 무료임
나중에 인스턴스 지울때 실수로 탄력적ip 지우는거 까먹으면 돈나가니까 기억하자
인스턴스가서 고정 ip 복사 해놓고 route53 에서 a 타입으로 front,back ip 
설정해주고 www 로 시작하고싶은 유형만들고싶다면 CNAME 으로만들어서 
내 도메인을 값에 넣어주면됨 
server 는 ip 가 달라졌기때문에 front , back server 모두 끊겼으니 재연결

session({
cookie: {
httpOnly: true (javascript에서 접근하지 못하게)
secure: false(현재는 http니까)
domain: process.env.NODE_ENV === 'production' && '.원하는사이트';
}
})
.을 붙여야 api.xxx.xx 과 xxx.xx 사이에서 cookie 공유가 가능함.

한번 https 로 접속하게되면 http 로 접속하려할때 일정 시간이 지나야 
접속 가능한 문제 해결하기
hsts 해제 검색 후 적용

고정 아이피가 생겼기에 
front config 에서
export const backUrl = 'http://api.vitamin777.shop' 로 변경
back 에 app.js 에서
origin: ['http://localhost:3060','http://vitamin777.shop'], //front local, siteName, aws ip (넣지않으면 cors error 발생)
로 변경
쿠키 공유 설정
app.use(session({
			saveUninitialized: false,
			resave: false,
			secret: process.env.COOKIE_SECRET, // .env 에 password setting
			cookie: {
				httpOnly: true, // cookie 는 js 로 접근 못하게
				secure: false, //나중에 https 적용할땐 true 로 변경
				domain: process.env.NODE_ENV === 'production' && '.vitamin777.shop'
			}
		}
))
.vitamin777.shop 에서 . 을 붙여야 api.vitamin777.shop 과 그냥
vitamin777.shop 사이에서 쿠키 공유가 가능하다
최신 브라우저들은 . 을 안붙여도 된다하지만 예전 브라우저를 위해 . 붙이자

다시한번... 항상 front 에서는 git pull 해주면 sudo npm run build 잊지말자

has been blocked by CORS policy: Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource.
:cors error
if (process.env.NODE_ENV === 'production') { // 배포모드
	/*배포모드일때 combined 를 사용하면 좀더 로그가 자세히나옴 (접속자의 ip 등 확인가능)*/
	app.use(morgan('combined')) // morgan 라이브러리
	/*개발 모드일땐 hpp, helmet 을 꼭넣어주자 (보안관련)*/
	app.use(hpp())
	app.use(helmet())
	app.use(cors({ // 보안정책
		/*
		* 대신 보낸 곳의 주소가 자동으로 들어가 편리하다,또는 직접 주소를적어주자,
		 access allow control origin, 쿠기가 전달되면서 보안강화해줘야하기에 * 를 사용하면 에러발생	*/
		origin: ['http://vitamin777.shop'], //front local, siteName, aws ip (넣지않으면 cors error 발생)
		credentials: true, // true 로 해주면 쿠키전달됨
	}))
} else {
	app.use(morgan('dev')) // morgan 라이브러리
	app.use(cors({ // 보안정책
		/*
		* 대신 보낸 곳의 주소가 자동으로 들어가 편리하다,또는 직접 주소를적어주자,
		 access allow control origin, 쿠기가 전달되면서 보안강화해줘야하기에 * 를 사용하면 에러발생	*/
		origin: ['http://localhost:3060'], //front local, siteName, aws ip (넣지않으면 cors error 발생)
		credentials: true, // true 로 해주면 쿠키전달됨
	}))
}
개발용과 배포용으로 아예 origin 을 나눠줌
만약 cors 에러 또 발생시 브라우저 캐시 삭제 후 재실행하면 됨

로그인되고 쿠키도 있는데 로그인하라고 에러발생할떄
프론트, 백엔드 서버 홈페이지 둘다 들어가셔서
개발자 도구 -> application -> cookie 삭제하고 다시 로그인해보세요

S3
--
s3 가 백업도 처리를 해준다
이미지들은 s3 에 다 올릴것임
백엔드 서버에 저장하는게 아니라 프론트에서 올릴때 s3 로 보낼것임

s3 는 aws 에서 스토리지에 있으며, 버킷을 생성할때 엑세스 차단 설정에서
모든 퍼블릭 엑세스 차단을 체크 해제해줘야한다
(차단을 해줘야 브라우저에서 s3 에 저장된 곳에 접근 가능)
버킷 생성 후 vitamin777-s3 의 버킷 정책 설정
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AddPerm",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": "arn:aws:s3:::vitamin777-s3/*"
        }
    ]
}
위 코드는 퍼블릭 정책 설정 코드?
저장해주고 내 보안 자격 증명에서 엑세스 키를 만들어준다, 
(엑세스 키가있어야 node 에서 s3 로의 접근 권한이 나온다 )
엑세스 키는 남들에게 노출되면 안된다 .env 같은곳에 넣어두면된다
local back 으로 가서 npm i multer-s3 aws-sdk 설치
(multer-s3(멀터를 통해 s3 로 올릴때)aws-sdk (s3 접근권한 얻을때 사용))

실무에서는 엑세스 키 방식보다는 IM 방식으로 더 많이함,엑세스 키는 권한이넘쎔

멀터라는게 업로드를 알아서해주니까 스토리지를 디스크에서 멀터s3 로 바꾸기만해주면 알아서 나머지 과정은 비슷한채 바뀐코드부분만 바뀜
const upload = multer({ // aws cloud save images
	storage: multerS3({
		s3: new AWS.S3(), //S3 권한
		bucket: 'vitamin777-s3',
		key(req, file, cb) {
			cb(null, `original/${Date.now()}_${path.basename(file.originalname)}`) // folder, 확장자, 파일이름
		}
	}),
	limits: {fileSize: 20 * 1024 * 1024}, // 파일 용량 설정 20mb 동영상이라면 좀더 올려줘야한다 100,200mb 정도
})
router.post images
res.json(req.files.map((v) => v.location)) // s3 에 올릴땐 location 을 프론트로

이미지를 s3 에 올리면 api 노드버드 닷컴에 이미지 폴더가 뜨는게아니라
s3 용 이미지 주소가 따로 생긴다 

로컬 back 에서 뭔가 설치했다면 server back 에서도 npm i 를 해줘야한다

백엔드 서버가 재시작하면 로그인은 풀린다















```
