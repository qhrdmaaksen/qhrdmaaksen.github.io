---
layout: post
title: "에러 발생 및 해결, 예외 처리의 개념!"
---

### 예외 : 프로그램을 실행했을 때 발생하는 에러  
  
정의 : 수치를 0 으로 나누거나, 배열의 범위 밖을 이요하려 할 때 예외가 발생
  
1/ 에러, 예외에 대응하는것을 **예외 처리**라고 함
  
2/ 자바는 예외가 발생하면 자동적으로 전용클래스(예외 클래스)의 오브젝트가 생성됨
  
예외 클래스에는 exception 클래스와 그 서브 클래스가 있다.
  
**예외 처리**  
예외가 발생할 것 같은 처리를 수행할 경우에 try 문 , catch 문, finally문 사용

```js
try {
    //예외가 일어날 것 같은 처리를 기술함
  }
  catch(//예외 클래스명 변수명 ex: Exception e) {
    //예외 발생 시 수행할 처리
  }
  //예외가 생기든 안생기든 실행됨 finally 문은 생략 할 수 있다.
  finally {
    //처리
  }
```  
예외 발생 예상 메소드는 **throw**를 사용, 메소드에서 생길수 있는 예외 클래스를 지정해 둠  
but 메소드를 호출한 곳에 예외를 받아 줄 catch 문이 없으면 , 컴파일 에러 발생

```js
class Args {
    public static void main(String[] args){
      try {
        //같은 클래스내의 static 멤버이므로 오브젝트 생성없이 back() 직접 호출가능
        back(args[0]); //인수가 없으면 예외 발생
      } catch (Exception e) {
        System.out.println("커맨드라인 인수가 없음");
      } finally {
        System.out.println("종료");
      }
    }
      static void back(String a) throws Exception {
        System.out.println("커맨드라인 인수는 " +  a + "입니다.");
      }        
}
```

3/**사용자 정의 예외 만들기**  
1)기존 정의된 예외 클래스외에 필요에 따라 새로운 예외 클래스를 정의하여 사용할 수 있음  
2)보통 exception 클래스로부터 상속받는 클래스를 만들지만,예외 클래스를 선택할수있음

```js
class MyException1 extends Exception{
  //noting
}
class MyException2 extends Exception{
  //noting
}
class MyException {
  public static void main(String[] args) {
    try {
      //같은 클래스내의 static 멤버이므로 오브젝트 생성없이 MyMethod메소드 직접 호출가능
      MyMethod(args[0]); //인수가 없으면 예외 발생
    } catch (MyException1 e1) {
      System.out.println("예외 1");
    } catch (MyException2 e2){
      System.out.println("예외 2");
    } finally{
      System.out.println("종료");
    }
  }
  static void MyMethod(String str) throws MyException1,MyException2 {
    System.out.println("입력값은 " + str + "입니다.");
    int x = Integer.parseInt(str); // 문자열을 정수로 변환
    switch ( x ){
      case 1:
        throw new MyException1();//예외 발생 시킴
      case 2:
        throw new MyException2();//예외 발생 시킴
      default:
        System.out.println("예외 없음");
    }
  }
}
==============================================
Prop `className` did not match.
  1/ npm i babel-plugin-styled-components
    npm i babel-preset-next
  2/ 프로젝트 루트 경로에 .babelrc 파일 생성 후 내용 작성하기
  {
   "presets": ["next/babel"],
   "plugins": ["babel-plugin-styled-components"]
}

Server Error
TypeError: Cannot read properties of undefined (reading 'user')
  (user 에서 switch 문 default state return 을 안해줘서 발생)

리덕스 데브툴이 안뜰때
  (configureStore 에서 연결을 안해서 발생)

TypeError: middleware is not a function
  (미들웨어를 배열로 두면 찾지못한다. compose 에 ...middlewares)

internal server error
  (store.dispatch 로 해결, store 쪽 오타)

가상머신 vmware 인터넷 연결 안될시
  1 서비스에서 vmware nat, dhcp 활성화 되었는지 체크
  2 (vmware edit -> vircual network editor 에서 게이트웨이 체크)
      활성화되어있다면 가상머신 내부에서 시작-> ncpa.cpl 검색 후 
        인터넷 프로토콜 버전 4 에서 ip 주소 수동 할당

yum install error 발생 시
 vi or gedit 으로 /etc/yum.repos.d/fedora.repo 파일을 열어 모든 내용 삭제 후 
 아래 내용 추가 
[fedora]
name=Fedora
baseurl=http://archives.fedoraproject.org/pub/archive/fedora/linux/releases/19/Everything/x86_64/os/
enabled=1
gpgcheck=0
--------------------------------------------------------------------------------
[object Object]
  글자를 쳤는데 위와같이떳다면 문자열이 객체로 변환되고있다는것

Failed prop type: Invalid prop `postData` of type `function` supplied to `PostCardContent`, expected `string`.
  :string 이 아닌 문장이 들어왔는데 split() 를 적용하면 발생하는 에러
    {postData.split(/(#[^\s#]+)/g).map((v, i) => { 를
    {postData.toString().split(/(#[^\s#]+)/g).map((v, i) => { 로 해결

로그인하지않았는데 프로필로 가게됐을 경우 에러 발생 
: 
if (!me) {
		Router.push('/');
		return null;
	}

TypeError: Failed to execute 'fetch' on 'Window'
  :fetch 사용법이 잘못되었을 때 발생하는 에러입니다. 코드 상의 문제

 throw new AssociationError(`${source.name}.belongsToMany(
   ${target.name}) requires through option, pass either a 
    string or a model`);
: through 를 넣어줘야한다, belongsToMany 에는

ConnectionRefusedError [SequelizeConnectionRefusedError]:connect ECONNREFUSED 127.0.0.1:3306
: 서비스에서 mysql 시작

can't set headers already sent 
  : 요청과 응답은 한번씩만 교환이되는데 응답이 두번 들어가면 발생

ERR_CONNECTION_REFUSED
: SERVER 가 방화벽에 막히거나, 서버 접속이안됨, 서버가 꺼져있음 등

'Property 'data' does not exist on type 'CallEffect<{data: string}>' 에러
: email: string, password: string 으로 변경

undefined saveUninitialized
undefined resave
undefined secret
:app.use(session({
			saveUninitialized: false,
			resave: false,
			secret: process.env.COOKIE_SECRET, // .env 에 password setting
		}
))

<pre>cannot post /user/logout</pre>
: back end 쪽 router.post 에 /logout 으로 해결
prefix 로 /user 가 붙었기에 /user/user/logout 으로 적용되었던것같다

status code 401 unauthorized ( 로그아웃에서 발생한 에러)
: 쿠키 셋팅 해줘야함 

origin: true, // * 대신 보낸 곳의 주소가 자동으로 들어가 편리하다, access allow control origin, 쿠기가 전달되면서 보안강화해줘야하기에 * 를 사용하면 에러발생

TypeError: Cannot read properties of undefined (reading '0')
: back 에 이미지 설정이 안들어가있어서 발생 아래 코드로 해결
const fullPost = await Post.findOne({ // 게시글의 모든 정보
			where: {id:post.id},
			include:[{
				model: Image, // 게시글에 달린 이미지
			}, {
				model: Comment, // 게시글에 달린 댓글
			}, {
				model: User, // 게시글 작성자
			}]
		})

Cannot read properties of undefined (reading 'data')
: sagas 의 posts 에 인수를 action 으로 잘못넣었음 data 로 넣어주니 해결

Cannot read properties of undefined (reading 'nickname')
: 댓글의 작성자가 누군지 모름 

Failed prop type: Invalid prop `post.Comments[0]` of type `string` 
supplied to `PostCard`, expected `object`.
: propTypes 에 string 으로 들어오는걸 내가 object 로 설정해놔서 생김

Error: Rendered fewer hooks than expected. This may be caused by an 
accidental early return statement.
:훅스 보단 아래에 코드 추가하지 않아서 발생된 문제,(useEffect 등 보단 아래)

Encountered two children with the same key, `3`. Keys should be unique 
so that components maintain their identity across updates.
: loading 문제 해결하면 없어질 문제 당장 급한건아니고 후 처리 

<pre>Cannot DELETE /user/1/unfollow</pre>
: return axios.delete(`/user/${data}/unfollow`)  를
 return axios.delete(`/user/${data}/follow`) 로

Error where params server error 500 
: back , params value typing error 

favicon.ico
: 가장 좋은방법은 파비콘 아이콘을 넣어주는게 좋고, 아니라면 
https://jm0121.tistory.com/4 이런식으로 처리
html 문서의 head 안에 추가
<link rel="icon" href="data:;base64,iVBORw0KGgo="> 

rerendering 이 계속해서 발생된다면, 훅스들을 의심해보자

TypeError: nextCallback is not a function (next-redux-wrapper 7.0)
:해결 방법(변경사항)
version 6.0.2 >
const getServerSideProps = wrapper.getServerSideProps(async (context) => {
  context.store.dispatch(~~~);
  context.store.dispatch(END);
  await store.sagaTask.toPromise();
});
version 7.0.0 >
const getServerSideProps = wrapper.getServerSideProps(
  (store) =>
    async ({ req, res, ...etc }) => {
      store.dispatch(~~~);
      store.dispatch(END);
      await store.sagaTask.toPromise();
    }
);
추가적으로 동적라우팅 (강의 : 다이나믹 라우팅) 할 때도 (req, res, ...etc) > (req, res, params, ...etc) 로 수정하시면 됩니다.
next-redux-wrapper 참고 자료(getServerSideProps)
(https://github.com/kirill-konshin/next-redux-wrapper#getserversideprops)
변경사항
(https://github.com/kirill-konshin/next-redux-wrapper#upgrade-from-6x-to-7x)

Prop 'clssName' did not match
: .babelrc 설정, npm i babel-styled-component 
{
	"presets": [
		"next/babel"
	],
	"plugins": [
		[
			"babel-plugin-styled-components",
			{
				"ssr": true,
				"displayName": true, // 개발모드에서 component 의 이름으로 나와서 보기 편해짐
			}
		]
	]
}

TypeError: Router.use() requires a middleware function but got a Object
: module.exports = router files 중 안붙인게있을것..찾아보자

[ERR_UNESDCAPED_CHARACTERS]: Request path contains unescaped characters
: uri 주소창에 한글or 특수문자 들어가서 발생한 에러,
// 한글or특수문자 들어가면 error, encode 로 감싸주자
	return axios.get(`/hashtag/${encodeURIComponent(data)}?lastId=${lastId || 0}`)
//front 에서 encode 로 요청이왔고 응답은 decode 로 설정
where: {name: decodeURIComponent(req.params.hashtag)}, 

404 error
: 존재하지 않을때 발생하는 에러 

ERR_NAME_NOT_RESOLVED DNS 오류
:DNS 오류를 확인한다
DNS가 진짜 문제일 수 있다.
1. 윈도우 PC에서 커멘트 창을 연다.
2. "nslookup 도메인명"을 하여 정상 IP를 표시하는지 확인한다.
혹은 아래 웹사이트를 참고해 DNS를 점검하여 해당 도메인이 정상 DNS를 
설정하였는지 확인한다.
한국인터넷정보센터 DNS점검 사이트: https://krnic.or.kr

return process.dlopen(module, path.toNamespacedPath(filename));
:$ rm -rf node_modules/
$ npm update

Error: listen EACCES: permission denied 0.0.0.0:80
: sudo npm start

ERROR 1064 (42000): You have an error in your SQL syntax; check the
 manual that corresponds to your MySQL server version for the right 
 syntax to use near 'mysql> UPDATE user set password=password("1234") 
 where user = 'root'' at line 1
:UPDATE mysql.user SET authentication_string=null WHERE User='root';
 FLUSH PRIVILEGES;
exit
 mysql -u root
ALTER USER 'nodeBird'@'localhost' IDENTIFIED WITH aching_sha2_password BY 'voTmdnjem1!';
 flush privileges;
exit

이미지 업로드 시 발생한 에러
CredentialsError: Missing credentials in config, if using 
:깃에 .env 가 올라가지않기때문에 server back 에서 .env 접근하여
s3 엑세스 키를 넣어주자, 이렇게해도 에러 발생한다면 AWS.upload 쪽 코드 보자

uid error
: pm2 start 를 제대로 했는지 체크

getFullYear error
: Form 에서 가져온 date 가 포함된 data 를 따로 저장해주지않았다
  (비용 추적기 프로젝트에서 onSaveExpenseData 에 인수로 저장해주지않았었음)

styled Components 에서 & 기호
  생성한 styled 컴포넌트에 대해 이 경우에 특별한 가상선택자를 사용하겠다고 
    패키지에게 선언하는 것입니다 그래서 이 경우에는 “이 버튼에 focus가 
      있으면 스타일을 적용해 줘”라고 선언하는것
  ex)
  styledComponents 활용 내부 css 
    import styled from 'styled-components';

    const Button = styled.button`
        font: inherit;
        padding: 0.5rem 1.5rem;
        border: 1px solid #8b005d;
        color: white;
        background: #8b005d;
        box-shadow: 0 0 4px rgba(0, 0, 0, 0.26);
        cursor: pointer;

      &:focus {
        outline: none;
      }
  기존 css file
.button {
  font: inherit;
  padding: 0.5rem 1.5rem;
  border: 1px solid #8b005d;
  color: white;
  background: #8b005d;
  box-shadow: 0 0 4px rgba(0, 0, 0, 0.26);
  cursor: pointer;
}

.button:focus {
  outline: none;
}

.button:hover,
.button:active {
  background: #ac0e77;
  border-color: #ac0e77;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.26);
}

npm install error (errno -4058)
-cd 디렉토리로 이동해서 package.json 으로 지정하고 다시 npm start 

this.state is not a function
-1)상태 정의를 this.setState({}) 를 입력해야하지만 this.state 로 명시하여 발생하였음
-2)this.state=({}) 를 this.state({}) 로 문법 오류 


Failed context type: UserFinder: context type `$$typeof` is invalid; it must be a function, 
usually from the `prop-types` package, but received `symbol`.
This often happens because of typos such as `PropTypes.function` instead of `PropTypes.func
-contextType 을 contextTypes 로 잘못 명시하여 발생한 오류 contextType 으로 코드 변경후 기능 작동 정상 확인 완료

ReferenceError: process is not defined
-this.setState({filteredUsers: DUMMY_USERS.filter((user) => user.name.includes(this.state.searchTerm))}) 로 지정해놨고
this.setState({filteredUsers: this.context.users.filter((user) => user.name.includes(this.state.searchTerm))}) 로 
변경하여 에러 해결, filteredUsers 를 contextType 으로 따로 users-context 로 연결 해놨었지만 이전 더미 데이터로 설정해놓고 사용하지 않아 발생한 에러

Cannot read properties of null (reading 'message')
-const [error, setError] = useState(null)
{!isLoading && !error && <p>{error.message}</p>} 를 
{!isLoading && error && <p>{error.message}</p>} 로 변경 후 해결


Uncaught ReferenceError: Cannot access 'fetchMoviesHandler' before initialization
-const fetchMoviesHandler = useCallback(async() =>{ 상수가 전체 코드를 파싱하기 전에 
함수를 호출하기때문에 발생한 문제
--useEffect(() => {
  fetchMoviesHandler()
}, [fetchMoviesHandler])
를 const fetchMoviesHandler 뒤에 위치하여 파싱 후 함수 호출로 문제 해결


Failed to load plugin 'jsx-a11y' declared in 'package.json >> eslint-config-react-app': cannot find module
-"eslint.workingDirectories": [
    { "mode": "auto" }
],
구글 검색하여 위와같이 package.json 에 넣어주니 해결됨
또는 eslint 를 찾을 수 없어서 발생한 에러니 다시 npm 설치해보자


import' and 'export' may only appear at the top level. 
-함수 또는 클래스를 선언할 때 닫는 중괄호를 잊어버리거나 기본 및 명명된 
내보내기 및 가져오기를 혼합할 때 발생하며 함수에서 빠진 중괄호 추가하여 해결


Error: Cannot find module 'D:\intellijProjects\react-etcStudyPJ\react-scripts\bin\react-scripts.js'
-폴더명에 & 가 들어가있어서 발생한 에러였으며 폴더이름 수정후 해결함


Error: could not find react-redux context value; please ensure the component is wrapped in a <Provider>
-index.js 에 root.render(<Provider store={store}><App /></Provider>);
수정 후 해결됨


Error: Actions must be plain objects. Use custom middleware for async actions.
-dispatch(showCartActions.toggleCartButton)
dispatch(showCartActions.toggleCartButton()) 수정 후 해결


price.toFixed is not a function
-price 를 숫자형으로 설정해야했지만 문자열로 설정해서 발생한 에러,
숫자로 바꾼뒤 해결함


Parsing error: 'import' and 'export' may only appear at the top level.
-eslint error 로 package.json eslint 에 아래 코드 추가 하여 재실행 해결
"rules": {
      "global-require": 0
    }

cannot find symbol
-import 가 제대로 안돼서 발생한 에러, import 넣어주니 해결됨


not recognized as an internal or external command
-firebase 인스톨할때 발생한 에러, npm config get prefix 로 현재 기본 경로
확인하고 npm config set prefix "노드 모듈있는 npm 폴더 경로설정" 후 
npm install -g firebase-tools 파이어베이스 설치 성공


INVALID_REQ_TYPE : Unsupported request parameters.
-로그인이 되지 않은 상태에서 패스 워드를 변경하려고 할때 발생하였음
습관적으로 새로고침을 누른 상태에서 패스워드 변경 페이지에서 변경하려고했을때
발생했으며 로그인 후 비밀번호 변경 잘 되었음


Package subpath './lib/parser' is not defined by "exports"
-호환성 문제로 node 를 다운 그레이드하여 문제 해결 


node_module 을 설치했는데도 불구하고 node -v 로 버전이 나오지만 npm -v 로
npm 을 찾을 수 없는 경우
-인텔리제이 종료 후 재시작으로 버전 확인 및 실행 가능하도록함


the fallback key must be returned from getStaticPaths in
-fallback:false 와 같이 폴백 키 설정 해줘서 해결


MongoServerError: user is not allowed to do action [insert]
-mongodb database access 에서 역할 설정 admin 으로 바꿔주니 해결됨


Route did not complete loading
-next version downgrade 10.0.0 으로 한 후 해결 10.0.2 부터 발생하는듯함


Error serializing `.meetups[0]._id` returned from `getStaticProps` in "/".
Reason: `object` ("[object Object]") cannot be serialized as JSON. Please only return JSON serializable data types.
-meetups 를 map 으로 뿌려주며 해결


Failed prop type: Invalid prop `children` supplied to `Transition`, expected one of type [function].
-'react-transition-group/Transition'; 으로 해결 뒤에 Transition 빼먹음


Uncaught Error: React.Children.only expected to receive a single React element child.
-jsx 에 {' '} 빈 중괄호를 삭제해서 해결


Warning: Unknown event handler property `onExited`. It will be ignored.
Warning: Received `true` for a non-boolean attribute `in`.
-알 수 없는 이벤트 핸들러 ‘onExited’ 경고와 불리언 속성이 아닌 ‘in’에 대해 
’true’ 값을 입력받았다는 경고임 이런 경고가 뜨는 이유는 지금 상태의 
TransitionGroup 으로는 여전히 ListItem 의 리스트를 감싸고 있기 때문임, 
TransitionGroup 은 리스트에 애니메이션을 적용할 때 사용할 수 있지만, 반드시
Transition 또는 CSSTransition 컴포넌트와 함께 사용해야한다


ReactDOM.render is no longer supported in React 18. Use createRoot instead. Until you switch to the new API, your app will b
ehave as if it's running React 17
-react testing library의 버전 업데이트
-npm install --save-dev @testing-library/react@latest
npm install --save-dev @testing-library/jest-dom@latest
npm install --save-dev @testing-library/user-event@latest
사용중인 리엑트 테스팅 라이브러리 패키지의 버전을 모두 업데이트 해준 후 해결


A component is changing an uncontrolled input to be controlled. This is likely caused by the value changing from undefined to a defined value, which should not happen. Decide between using a controlled or uncontrolled input element for the lifetime of the component
-useState() 초기값 설정안한 상태에서 입력 값을 받으려할때 발생하였음, 초기값 설정 후 에러 해결


Cannot assign to read only property object
-개체의 읽기 전용 속성 할당 할 수 없음
--props.onAddIngredient=({
      title: enteredTitle,
      amount: enteredAmount,
    });
로 문법 실수로 발생된 에러, 아래 코드로 수정 후 에러 해결
props.onAddIngredient({
      title: enteredTitle,
      amount: enteredAmount,
    });


React.createElement: type is invalid -- expected a string (for built-in components) or a class/function (for composite components) but got: <App />. Did you accidentally export a JSX literal instead of a component?
(React.createElement: type이 잘못되었습니다. 문자열(기본 제공 구성 요소의 경우) 또는 클래스/함수(복합 구성 요소의 경우)가 필요하지만 다음을 얻었습니다. <App /> 컴포넌트 대신 JSX 리터럴을 실수로 내보냈습니까?)
-import 경로 설정 잘못하거나 jsx 에서 문법 에러 발생해서 나옴
--나는 jsx 에서 props.children 을 중괄호가 아닌 <props.children/>
으로 정신없이 코딩하다 발생된 에러 중괄호로 변경 후 에러 해결







```
