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


```