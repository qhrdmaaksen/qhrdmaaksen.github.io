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


클라이언트 오류 응답
400 Bad Request
서버는 클라이언트 오류로 인식되는 것으로 인해 요청을 처리할 수 없거나 처리하지 않을 것입니다(예: 잘못된 요청 구문, 잘못된 요청 메시지 프레이밍 또는 사기성 요청 라우팅).

401 Unauthorized
HTTP 표준은 "인증되지 않음"을 지정하지만 의미상 이 응답은 "인증되지 않음"을 의미합니다. 즉, 클라이언트는 요청된 응답을 얻기 위해 자신을 인증해야 합니다.

402 Payment Required 실험적
이 응답 코드는 향후 사용을 위해 예약되어 있습니다. 이 코드를 만드는 초기 목표는 디지털 결제 시스템에 사용하는 것이었지만 이 상태 코드는 거의 사용되지 않으며 표준 규칙이 없습니다.

403 Forbidden
클라이언트는 콘텐츠에 대한 액세스 권한이 없습니다. 즉, 권한이 없기 때문에 서버가 요청된 리소스 제공을 거부하고 있습니다. 와 달리 401 Unauthorized클라이언트의 ID는 서버에 알려져 있습니다.

404 Not Found
서버가 요청한 리소스를 찾을 수 없습니다. 브라우저에서 이는 URL이 인식되지 않음을 의미합니다. API에서 이는 엔드포인트가 유효하지만 리소스 자체가 존재하지 않음을 의미할 수도 있습니다. 403 Forbidden서버는 권한이 없는 클라이언트로부터 리소스의 존재를 숨기는 대신 이 응답을 보낼 수도 있습니다 . 이 응답 코드는 웹에서 자주 발생하기 때문에 아마도 가장 잘 알려져 있을 것입니다.

405 Method Not Allowed
요청 방법이 서버에 알려져 있지만 대상 리소스에서 지원되지 않습니다. 예를 들어 API는 DELETE리소스를 제거하기 위한 호출을 허용하지 않을 수 있습니다.

406 Not Acceptable
이 응답은 웹 서버가 서버 기반 콘텐츠 협상을 수행한 후 사용자 에이전트가 지정한 기준을 준수하는 콘텐츠를 찾지 못할 때 전송됩니다.

407 Proxy Authentication Required
이는 401 Unauthorized프록시와 유사하지만 인증이 필요합니다.

408 Request Timeout
이 응답은 클라이언트의 이전 요청 없이도 일부 서버에서 유휴 연결로 전송됩니다. 이는 서버가 이 사용하지 않는 연결을 종료하려고 함을 의미합니다. 이 응답은 Chrome, Firefox 27+ 또는 IE9와 같은 일부 브라우저가 서핑 속도를 높이기 위해 HTTP 사전 연결 메커니즘을 사용하기 때문에 훨씬 더 많이 사용됩니다. 또한 일부 서버는 이 메시지를 보내지 않고 단순히 연결을 종료합니다.

409 Conflict
이 응답은 요청이 서버의 현재 상태와 충돌할 때 전송됩니다.

410 Gone
이 응답은 요청한 콘텐츠가 전달 주소 없이 서버에서 영구적으로 삭제되었을 때 전송됩니다. 클라이언트는 리소스에 대한 캐시와 링크를 제거해야 합니다. HTTP 사양은 이 상태 코드를 "기간 한정 프로모션 서비스"에 사용하도록 합니다. API는 이 상태 코드로 삭제된 리소스를 표시해야 한다고 느껴서는 안 됩니다.

411 Length Required
Content-Length헤더 필드가 정의되지 않았고 서버에서 요구하기 때문에 서버가 요청을 거부했습니다 .

412 Precondition Failed
클라이언트는 서버가 충족하지 않는 전제 조건을 헤더에 표시했습니다.

413 Payload Too Large
요청 엔터티가 서버에서 정의한 제한보다 큽니다. 서버는 연결을 닫거나 Retry-After헤더 필드를 반환할 수 있습니다.

414 URI Too Long
클라이언트가 요청한 URI가 서버가 해석하려는 것보다 깁니다.

415 Unsupported Media Type
요청한 데이터의 미디어 형식이 서버에서 지원되지 않으므로 서버에서 요청을 거부합니다.

416 Range Not Satisfiable
Range요청의 헤더 필드 에 지정된 범위를 충족할 수 없습니다. 범위가 대상 URI의 데이터 크기를 벗어날 수 있습니다.

417 Expectation Failed
이 응답 코드는 요청 헤더 필드에 표시된 기대치를 Expect서버에서 충족할 수 없음을 의미합니다.

418 I'm a teapot
서버는 찻주전자로 커피를 추출하려는 시도를 거부합니다.

421 Misdirected Request
요청이 응답을 생성할 수 없는 서버로 지정되었습니다. 이것은 요청 URI에 포함된 체계와 권한의 조합에 대한 응답을 생성하도록 구성되지 않은 서버에서 보낼 수 있습니다.

422 Unprocessable Content( WebDAV )
요청이 잘 구성되었지만 의미론적 오류로 인해 따를 수 없었습니다.

423 Locked( WebDAV )
액세스 중인 리소스가 잠겨 있습니다.

424 Failed Dependency( WebDAV )
이전 요청의 실패로 인해 요청이 실패했습니다.

425 Too Early 실험적
서버가 재생될 수 있는 요청을 처리하는 위험을 감수하지 않음을 나타냅니다.

426 Upgrade Required
서버는 현재 프로토콜을 사용하여 요청을 수행하는 것을 거부하지만 클라이언트가 다른 프로토콜로 업그레이드한 후에 기꺼이 수행할 수 있습니다. 서버는 Upgrade필요한 프로토콜을 나타내기 위해 426 응답으로 헤더를 보냅니다.

428 Precondition Required
원본 서버는 요청이 조건적이어야 합니다. 이 응답은 '업데이트 손실' 문제를 방지하기 위한 것입니다. 클라이언트가 GET리소스의 상태를 수정하고 PUT서버로 다시 보내는 동안 제3자가 서버의 상태를 수정하여 충돌을 일으키는 경우입니다.

429 Too Many Requests
사용자가 주어진 시간 동안 너무 많은 요청을 보냈습니다("속도 제한").

431 Request Header Fields Too Large
헤더 필드가 너무 커서 서버가 요청을 처리하지 않습니다. 요청 헤더 필드의 크기를 줄인 후 요청을 다시 제출할 수 있습니다.

451 Unavailable For Legal Reasons
사용자 에이전트가 정부에서 검열한 웹 페이지와 같이 법적으로 제공할 수 없는 리소스를 요청했습니다.

서버 오류 응답
500 Internal Server Error
서버에서 처리 방법을 알 수 없는 상황이 발생했습니다.

501 Not Implemented
요청 방법은 서버에서 지원되지 않으며 처리할 수 없습니다. 서버가 지원해야 하는(따라서 이 코드를 반환하지 않아야 하는) 유일한 메서드는 GET및 입니다 HEAD.

502 Bad Gateway
이 오류 응답은 서버가 요청을 처리하는 데 필요한 응답을 얻기 위해 게이트웨이 역할을 하는 동안 잘못된 응답을 받았음을 의미합니다.

503 Service Unavailable
서버가 요청을 처리할 준비가 되지 않았습니다. 일반적인 원인은 유지 관리를 위해 다운되었거나 과부하된 서버입니다. 이 응답과 함께 문제를 설명하는 사용자 친화적인 페이지를 보내야 합니다. 이 응답은 임시 조건에 사용해야 하며 Retry-AfterHTTP 헤더에는 가능하면 서비스 복구 전 예상 시간이 포함되어야 합니다. 이러한 임시 조건 응답은 일반적으로 캐시되지 않아야 하므로 웹마스터는 이 응답과 함께 전송되는 캐싱 관련 헤더에 대해서도 주의를 기울여야 합니다.

504 Gateway Timeout
이 오류 응답은 서버가 게이트웨이 역할을 하고 제 시간에 응답을 받을 수 없을 때 제공됩니다.

505 HTTP Version Not Supported
요청에 사용된 HTTP 버전이 서버에서 지원되지 않습니다.

506 Variant Also Negotiates
서버에 내부 구성 오류가 있습니다. 선택한 변형 리소스가 투명한 콘텐츠 협상 자체에 참여하도록 구성되었으므로 협상 프로세스에서 적절한 끝점이 아닙니다.

507 Insufficient Storage( WebDAV )
서버가 요청을 성공적으로 완료하는 데 필요한 표현을 저장할 수 없기 때문에 리소스에서 메서드를 수행할 수 없습니다.

508 Loop Detected( WebDAV )
요청을 처리하는 동안 서버에서 무한 루프를 감지했습니다.

510 Not Extended
서버가 이를 이행하려면 요청에 대한 추가 확장이 필요합니다.

511 Network Authentication Required
클라이언트가 네트워크 액세스 권한을 얻기 위해 인증해야 함을 나타냅니다.


Cannot read properties of null (reading 'edgesOut')
해결: 
1. node_modules 폴더 삭제
2. npm cache clean --force
3. npm install
4. npm 으로 하려고 했던 작업하면됨





```