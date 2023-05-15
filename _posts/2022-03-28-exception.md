---
layout: post
title: "에러 모음집(설명 및 해결)"
---

## 에러를 모아보자, 또 만나지 말자

```js
InterruptedException 예외 중단

NumberFormatException 잘못된 숫자 형식입니다.

NullPointerException 메소드의 리턴값 or 오타 ,띄워쓰기 잘못


IOException 데이터 입출력에 문제가 있습니다.

FileNotFoundException 파일이 없으면 예외 발생

Exception 예외 발생

IndexOutOfBoundsException  입력 범위 벗어남

InputMismatchException 입력이 매치가 안됨 예외 

ExceptionInInitializerError Object객체를 생성할때 발생하는 에러 

ArithmeticException 어떤수를 0으로 나누려할때 

https://www.data.go.kr/data/3072201/fileData.do 
성별 만나이 직업분류 학력 결혼 유무 

SQLIntegrityConstraintViolationException 
//sql 에서 예외 발생 

v2 cannot be resolved to a variable
//v2를 해석 할 수 없다 . 

데이터베이스

오류보고

ORA-01920: user name 'ORAMAN' conflicts with another user or role name
// 다른 유저의 이름으로 충돌

ORA-12899: value too large for column "ORAMAN"."EMPLOYEES"."ID" (actual: 30, maximum: 20)
//아이디가 최대 20자리인데 너는 30자리를 넣으려고하고있다 . 

ORA-01439: column to be modified must be empty to change datatype
//타입을 바꾸려고하는데 안비워져있다. == numberfomatexception 

invaible identified // 오타 발생

ORA-00942: table or view does not exist
//1.해당 테이블을 볼수가 없다 . //2.오타 발생 //3.권한이 불충분하여 발생

ORA-00932: inconsistent datatypes: expected CHAR got NUMBER
//데이터 타입이 맞지 않음 

ORA-00920: invalid relational operator
//잘못된 관계 연산자 

ORA-00907: missing right parenthesis
//오른쪽에 소괄호가 없다 

ORA-00937: not a single-group group function
//하나는 그룹함수 하나는 일반 컬럼인데 같이 적었다 

ORA-00934: group function is not allowed here
//

ORA-08004: sequence SEQTEST02.NEXTVAL exceeds MAXVALUE and cannot be instantiated
//최대 값을 넘겨서 생기는 메세지

ORA-01427: single-row subquery returns more than one row
//단일행 연산자로 다중행 결과물과 비교를 하려고 시도할 때 나오는 오류 메세지

ORA-01427: single-row subquery returns more than one row

ORA-01031: insufficient privileges
//권한이 불충분 합니다 . 

insert into view02 values('sim', '심형래', sysdate, '마포')
오류 보고 -
ORA-01400: cannot insert NULL into ("ORAMAN"."EMPLOYEES"."PASSWORD")
//id,name,password가 not null 로되어있기에 필수적으로 넣어줘야하지만
// insert에 필수사항을 입력하지 않았음

ORA-00001: unique constraint (ORAMAN.SYS_C007186) violated
//제약 조건 문제 

ORA-01922: CASCADE must be specified to drop 'SAMPLE'

JdbcSQLIntegrityConstraintViolationException: Unique index or primary key violation
//unique랑 primary key 가 중복되어 뜨는 에러 

404 에러뜰때
	맵핑잘되어있는지  command 확인 겟맵핑에 잘 들어가있는지 확인
	클래스에 s자로 스캔이 잘적용되어있는지 아이콘확인
	웹 엑스엠엘 실제로 접미사가 등록되어있는지 확인 서블릿네임 동일확인 
	paramvalue 경로안에 addresss-config가 실제고있는지 오타없는지
	해당 config 파일로 이동해서 component scan이 해당 컨트롤러를 매핑하고있는지 확인 
	마지막으로 bean:property name에 value 경로안에 실제 파일이 있는지 확인 
	
.IllegalArgumentException: There is no PasswordEncoder mapped for the id "null"
//스프링 시큐리티에서는 패턴을 요구한다 . 

java.lang.AssertionError: Authentication should not be null
//인증은 null이 아니어야합니다.

badCredentialsException = 비밀번호가 틀렸을경우 
LockedException = 계정이 잠겨있는경우
DisabledException = 계정이 비어있는 경우 


Warning: Can't perform a React state update on an unmounted component.
This is a no-op, but it indicates a memory leak in your application.
To fix, cancel all subscriptions and asynchronous tasks in a useEffect cleanup function.
(경고: 마운트 해제된 구성 요소에서 응답 상태 업데이트를 수행할 수 없습니다.
이는 작동하지 않지만 응용 프로그램에서 메모리 누수가 발생했음을 참조하십시오.
수정하려면 useEffect 정리 기능에서 모든 구독 및 비동기 작업을 취소하십시오.)
해결: route 이동 후 이전 route 에서 값을 변경하는 경우에뜨는 메시지이며 finally 문을 router 이동 전으로 옮겨 해결함


Actions must be plain objects. Use custom middleware for async actions
(작업은 일반 개체여야 합니다. 비동기 작업에 사용자 지정 미들웨어 사용)
해결: dispatch 잘못된 형식으로 실행하였기에 발생한 에러이며 disaptch 내부의 값이 함수인데 객체로 실행한 경우 뜨는 에러임
 dispatch(thisIsFunction) -> dispatch(thisIsFunction()) 로 변경해 해결함


You are using a whole package of antd-mobile, please use https://www.npmjs.com/package/babel-plugin-import to reduce app bundle size.
(당신은 antd-mobile의 전체 패키지를 사용하고 있습니다. 앱 번들 크기를 줄이려면 https://www.npmjs.com/package/babel-plugin-import을 사용하십시오.)
해결: 전체 번들 import 를 하지말고 필요한 컴포넌트만 사용해 해결


Another git process seems to be running in this repository, e.g.
an editor opened by 'git commit'. Please make sure all processes
are terminated then try again. If it still fails, a git process
may have crashed in this repository earlier:
remove the file manually to continue.
(이 저장소에서 다른 Git 프로세스가 실행되고 있는 것 같습니다.
'git commit'로 개설된 편집자. 모든 프로세스를 확인하십시오
종료된 후 다시 시도하십시오. 그래도 실패하면 Git 프로세스
이전에 이 저장소에 충돌했을 수 있습니다:
계속하려면 파일을 수동으로 제거하십시오.)
해결: .git delete 후 다시 git init 으로 해결 


ts 작업중 exports is not defined
해결: tsconfig 에서 module 을 ES2015 로 변경, index.html 에 script 의 type 을 module 로 작성해 해결함


Cannot find module 'axios'. Did you mean to set the 'moduleResolution' option to 'node', or to add aliases to the 'paths' option?
(모듈 'axios'를 찾을 수 없습니다. 'moduleResolution' 옵션을 'node'로 설정하거나 'paths' 옵션에 별칭을 추가할 것을 의미합니까?)
해결: tsconfig 에서 moduleResolution 을 node 로 변경해 해결함


Cannot user import statement outside a module
(모듈 외부에서 import 문을 사용할 수 없습니다.)
해결: index.html 에 script 의 type 을 module 로 작성해 해결함


Conversion of type 'string | undefined' to type 'number' may be a mistake because neither type sufficiently overlaps with the other. If this was intentional, convert the expression to 'unknown' first
(유형의 변환 '문자열 | 정의되지 않음'을 '숫자' 유형으로 지정하는 것은 실수일 수 있습니다. 어느 유형도 다른 유형과 충분히 겹치지 않기 때문입니다. 이것이 의도적이었다면 먼저 표현을 '알 수 없음'으로 변환하십시오.)
원인 코드 : const PORT = (process.env.PORT as number) || 5000;
해결: const PORT = (process.env.PORT as unknown as number) || 5000; 로 변경해 해결함


is not assignable to type 'IntrinsicAttributes'
(타입 'IntrinsicAttributes'에 할당할 수 없습니다.)
해결: 타입스크립트에서는 타입을 명시해야하는데 명시하지 않아 발생한 에러이며 타입을 명시해 해결함


Property 'info' does not exist on type 'IntrinsicAttributes'
(속성 'info'는 'IntrinsicAttributes'에 존재하지 않습니다.)
해결: 타입스크립트에서는 info 에 대한 속성 타입을 명시해야하는데 명시하지 않아 발생한 에러이며 타입을 명시해 해결함






```