---
layout: post
title: "클린코드 리액트"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```javascript
// 코드의 목적성(앱의 완성도)을 우선적으로 생각하고 클린코드를 사용지향하자.
// eslint or prettier 를 활용해 클린코드화

// 초기 값
// - 가장 먼저 렌더링될때 순간적으로 보여질 수 있는 값이기도 함
// - 초기에 렌더링 되는 값
// 초기 값을 지키지 않을 경우
// - 렌더링 이슈, 무한 루프, 타입 불일치로 의도치 않은 동작으로 런타임 에러 발생 가능성
// - 초기값을 넣지 않으면 undefined 가 발생됨
// - 상태를 CRUD 할때 초기 값을 잘 기억해놔야지 원상태로 돌아감
// - 비어있는 값 또는 NULL 처리 할때 불필요한 방어코드도 줄일 수 있음

// 업데이트 되지 않는 일반적인 객체일 경우 리액트 외부에서 관리하도록하자
// - 컴포넌트 내부에 방치하도록하면 해당 객체 또는 상수를 참조 할때마다 불필요한 렌더링이 발생할 수 있음

// 플래그 값
// - 프로그래밍에서 조건 또는 제어를 위한 Boolean 으로 나타내는 값

// 플래그 상태의 경우 useState 를 사용하지 않고 표현식만으로도 활용할 수 있다
// ex)
/* before */
const [isLogin, setIsLogin] = useState(false);
useEffect(() => {
  if(isLogin) {
    setIsLogin(true);
  }

  if(hasToken) {
    setIsLogin(true);
  }
  // 등등등
}, [isLogin, hasToken /* 등등등 */]);

/* after */
const isLogin =
  hasToken === true &&
  hasCookie === true &&
  isValidCookie === true &&
  isNewUser === false &&
  isValidToken;

// props 를 useState 에 넣지 않고 바로 return 문에 사용하도록해보자
// 컴포넌트 내부 변수는 렌더링마다 고유한 값을 가지기 때문에
// useState 가 아닌 const 로 상태를 선언하는게 좋은 경우도 있다

// 리렌더링 방지가 필요하다면 useState 대신 useRef 를 사용 할 수 있다
// useState 대신 useRef 를 사용하면 컴포넌트의 생명주기와 동일한 리렌더링되지 않는 상태를 만들 수 있다.

/* before */
const [isMount, setIsMount] = useState(false);

useEffect(() => {
  if(!isMount) {
    setIsMount(true);
  }
}, [isMount]);

/* after */
const isMount = useRef(false);

useEffect(() => {
  isMount.current = true;
  return () => (isMount.current = false);
}, []);


/**
 * 연관된 상태 단순화 하기 KISS
 * K : Keep
 * I : It
 * S : Simple
 * S : Stupid
 *
 * 리액트의 상태를 만들때 연관된것들 끼리 묶어서 처리하면 에러 방지 및 코드 간결화
 */
// ex)
/* before */
function FlatState() {
  const [isLoading, setIsLoading] = useState(false);
  const [isFinish, setIsFinish] = useState(false);
  const [isError, setIsError] = useState(false);

  const fetchData = () => {
    // fetch data 시도
    setIsLoading(true);

    fetch(url)
      .then(() => {
        // fetch 성공
        setIsLoading(false);
        setIsFinish(true);
      })
      .catch(() => {
        // fetch 실패
        setIsError(true);
      });
  };

  if(isLoading) {
    return <LoadingComponent/>;
  }
  if(isFinish) {
    return <FinishComponent/>;
  }
  if(isError) {
    return <ErrorComponent/>;
  }
}

/* after */
const PROMISE_STATE = {
  INIT: 'init',
  LOADING: 'loading',
  FINISH: 'finish',
  ERROR: 'error',
};

function FlatState() {
  const [promiseState, setPromiseState] = useState(PROMISE_STATE.INIT);

  function fetchData() {
    // fetch data 시도
    setPromiseState(PROMISE_STATE.LOADING);

    fetch(url)
      .then(() => {
        // fetch 성공
        setPromiseState(PROMISE_STATE.FINISH);
      })
      .catch(() => {
        // fetch 실패
        setPromiseState(PROMISE_STATE.ERROR);
      });
  }

  if(promiseState === PROMISE_STATE.LOADING) return <LoadingComponent />;
  if(promiseState === PROMISE_STATE.FINISH) return <FinishComponent />;
  if(promiseState === PROMISE_STATE.ERROR) return <ErrorComponent />;
}



/**
 * 연관된 상태는 객체로 묶어내자
 * 동일한 코드가 반복될 때 그 반복을 멈출 수 있는 지 생각을 한번 해보자
 */

/* Before */
function ObjectState () {
  const [isLoading, setIsLoading] = useState(false);
  const [isFinish, setIsFinish] = useState(false);
  const [isError, setIsError] = useState(false);

  const fetchData = () => {
    setIsLoading(true);

    fetch(url)
      .then(() => {
        setIsLoading(false);
        setIsFinish(true);
      })
      .catch(() => {
        setIsLoading(false);
        setIsError(true);
      });
  };

  if(isLoading === true) return <LoadingComponent />;
  if(isFinish === true) return <FinishComponent />;
  if(isError === true) return <ErrorComponent />;
}

/* After */
function ObjectState () {
  const [fetchState, setFetchState] = useState({
    isLoading: false,
    isFinish: false,
    isError: false,
  });

  const fetchData = () => {
    /* fetch 시도 */
    setFetchState((prevState) => ({
      ...prevState,
      isLoading: true,
    }));

    fetch(url)
      .then(() => {
        setFetchState((prevState) => ({
          ...prevState,
          isLoading: false,
          isFinish: true,
        }));
      })
      .catch(() => {
        setFetchState((prevState) => ({
          ...prevState,
          isLoading: false,
          isError: true,
        }));
      });
  };

  if(fetchState.isLoading) return <LoadingComponent />;
  if(fetchState.isFinish) return <FinishComponent />;
  if(fetchState.isError) return <ErrorComponent />;
}

/**
 * useState 를 useReducer 로 리팩터링
 * 구조화된 상태를 원한다면 useReducer 를 사용하자
 */

const INIT_STATE = {
  isLoading: false,
  isSuccess: false,
  isFail: false,
};

const ACTION_TYPE = {
  FETCH_LOADING: 'FETCH_LOADING',
  FETCH_SUCCESS: 'FETCH_SUCCESS',
  FETCH_FAIL: 'FETCH_FAIL'
};

const reducer = (state, action) => {
  switch (action.type) {
    case ACTION_TYPE.FETCH_LOADING:
      return {...state, isLoading: true, isSuccess: false, isFail: false};
    case ACTION_TYPE.FETCH_SUCCESS:
      return {...state, isLoading: false, isSuccess: true, isFail: false};
    case ACTION_TYPE.FETCH_FAIL:
      return {...state, isLoading: false, isSuccess: false, isFail: true};
    default:
      return INIT_STATE;
  }
};

function StateToReducer () {
  const [state, dispatch] = useReducer(reducer, INIT_STATE);

  const fetchData = () => {
    dispatch({ type: ACTION_TYPE.FETCH_LOADING });

    fetch(url)
      .then(() => {
        dispatch({ type: ACTION_TYPE.FETCH_SUCCESS });
      })
      .catch(() => {
        dispatch({ type: ACTION_TYPE.FETCH_FAIL });
      });
  };

  if(state.isLoading) return <LoadingComponent />;
  if(state.isSuccess) return <SuccessComponent />;
  if(state.isFail) return <FailComponent />;
}

/**
 * 상태로직 Custom Hooks 로 뽑아내기
 * Custom Hooks 을 사용하면 코드를 확장성 있고 재사용 가능하게 작성할 수 있다.
 */

/* After */
const INIT_STATE = {
  isLoading: false,
  isSuccess: false,
  isFail: false,
};

const ACTION_TYPE = {
  FETCH_LOADING: 'FETCH_LOADING',
  FETCH_SUCCESS: 'FETCH_SUCCESS',
  FETCH_FAIL: 'FETCH_FAIL'
};

const reducer = (state, action) => {
  switch (action.type) {
    case ACTION_TYPE.FETCH_LOADING:
      return {...state, isLoading: true, isSuccess: false, isFail: false};
    case ACTION_TYPE.FETCH_SUCCESS:
      return {...state, isLoading: false, isSuccess: true, isFail: false};
    case ACTION_TYPE.FETCH_FAIL:
      return {...state, isLoading: false, isSuccess: false, isFail: true};
    default:
      return INIT_STATE;
  }
};

const useFetchData = (url) => {
  const [state, dispatch] = useReducer(reducer, INIT_STATE);

  useEffect(() => {
    const fetchData = async () => {
      dispatch({ type: ACTION_TYPE.FETCH_LOADING });

      try {
        await fetch(url);
        dispatch({ type: ACTION_TYPE.FETCH_SUCCESS });
      } catch {
        dispatch({ type: ACTION_TYPE.FETCH_FAIL });
      }
    };
    fetchData();
  }, [url]);

  return state;
};

function CustomHooks () {
  const {isLoading, isFail, isSuccess} = useFetchData('url');

  if(isLoading) return <LoadingComponent />;
  if(isFail) return <FailComponent />;
  if(isSuccess) return <SuccessComponent />;
}

/**
 * 이전 상태 활용하기
 * - update function 을 사용해서 prev state 를 고려한다면 예상치못한
 * 결과를 예방할 수 있다
 * - 이전 state 를 꺼내서 사용하는 방식으로 바꿔줘야 랜더링이나
 * 특히 인풋을 핸들링하는 경우 불필요한 에러를 내지 않을 수 있다
 * - 이전 상태를 완전히 덮어 씌우고 싶은 경우 값을 일방적으로 할당하는 경우를 생각할 수 있다.
 */

// ex)
/* before */
setAge(age + 1);
/* after */
setAge((prevAge) => prevAge + 1);

/* before */
function PrevState () {
  const [age, setAge] = useState(42);

  function updateState() {
    setAge(age + 1); // setAge(42 => 43)
    setAge(age + 1); // setAge(42 => 43)
    setAge(age + 1); // setAge(42 => 43)
  }
}

/* after */
function PrevState () {
  const [age, setAge] = useState(42);

  function updateState() {
    setAge((prevAge) => prevAge + 1); // setAge(42 => 43)
    setAge((prevAge) => prevAge + 1); // setAge(43 => 44)
    setAge((prevAge) => prevAge + 1); // setAge(44 => 45)
  }
}

/**
 * 불필요한 props 복사를하지 말자 (데이터의 흐름을 끊는것이기 때문)
 * - 컴포넌트에 들어오기전에 값 비싸고 무거운 연산들은 끝내는게 좋다 (연산된 값을 props 로 넘기기)
 * - 비싸지 않은 경우 컴포넌트 내부의 변수로도 간단히 사용 가능
 * - props 로 내려오는 값을 조작하는 행위로 조작을 무겁게 하는경우 useMemo 를 사용하자 (연산 최적화)
 * - props 바로 사용하기
 */

/* before */
function CopyProps ({value}) {
  const [copyValue] = useState(value);
  return <div>{copyValue}</div>;
}

/* after */
function CopyProps ({value}) {
  return <div>{value}</div>;
}

/* before */
function CopyProps ({value}) {
  const copyValue = 값_비싸고_무거운_연산(value);
  return <div>{copyValue}</div>;
}

/* after */
function CopyProps ({value}) {
  const copyValue = useMemo(() => 값_비싸고_무거운_연산(value), [value]);
  return <div>{copyValue}</div>;
}

/**
 * 중괄호
 * - jsx 에서 중괄호의 필요사항
 * 1. 논리적인 변수나 숫자
 * 2. boolean, object 에 해당되는 배열이나 함수, 표현식을 표현할수있는 창구
 * - string 일땐 curly braces 사용하지 말자
 * - 이중 줄괄호 안에는 일반적으로 in-line 객체를 넣었다고 생각하자
 * - 전혀 신경쓰고 싶지 않다면 eslint or prettier 로 설정해놓자
 */

// ex code
function CurlyBraces() {
  const style = {
    backgroundColor: 'blue',
    width: 1000,
  };
  return (
    <header
      className="clean-header"
      id="clean-code"
      style={style}
      style={{
        backgroundColor: 'blue',
        width: 1000,
      }}
      value={1}
      value={true}
      value={[]}
      value={() => {}}
      value={1 + 2}
      value={isLogin && hasCookie}
    >
    </header>
  );
}

/**
 * props 축약 (shorthand props)
 */

/* before */
function component (props) {
  return (
    <HeaderComponent hasPadding={props.hasPadding}>
      <ChildComponent isDarkMode={props.isDarkMode} isLogin={props.isLogin} />
    </HeaderComponent>
  );
}

/* after */
function component ({hasPadding, ...props}) {
  return (
    <HeaderComponent hasPadding={hasPadding}>
      <ChildComponent {...props} />
    </HeaderComponent>
  );
}

/* before */
function ShorthandProps (props) {
  return (
    <header
      className="clean-header"
      title="CleanCodeReact"
      isDarkMode={true}
      isLogin={true}
      hasPadding={true}
      isFixed={true}
      isAdmin={true}
    >
      <ChildComponent name={props.name} />
    </header>
  );
}

/* after */
function ShorthandProps ({hasPadding, isAdmin, ...props}) {
  return (
    <header
      className="clean-header"
      title="CleanCodeReact"
      hasPadding={hasPadding}
      isAdmin={isAdmin}
      isDarkMode
      isLogin
      isFixed
    >
      <ChildComponent {...props} />
    </header>
  );
}

/**
 * singleQuote vs doubleQuote
 * 1. 팀에서 일반적인 규칙 => 일관성을 지키기 위함
 * 2. HTML? JavaScript? 에서 사용
 * 3. prettier Or eslint 로 규칙 정해 사용하면 신경 쓸 필요 없다.
 * 4. 일반 HTML 속성은 일반적으로 작은 따옴표 대신 큰 따옴표를 사용
 * 하기에 따라서 JSX 속성은 이 규칙을 사용
 * 5. JSX 속성에는 항상 큰 따옴표를 사용하고 다른 모든 JS 에는 작은 따옴표를 사용
 */

{/* O - html은 보통 더블 쿼터를 많이사용한다.*/}
<a href="www.google.com">Google</a>

{/* X - 일관성이지 않기에 헷갈릴 수 있다.*/}
<input class='classExCode' type="button" value='CleanCodeReact'/>

{/* X - 자바스크립트 표현식으로는 싱글쿼터 사용*/}
<Clean style={{ backgroundPosition: "left"}} />

/* PROPS 네이밍 */
/**
 * 1. react 에서 컴포넌트는 pascal case 로 시작함(대문자로 시작하며 워딩이 바뀔때마다 대문자)
 * 2. camel case 사용하기
 * 3. 무조건 true 라면 isShow={true}가 아닌 isShow 로 축약
 * 4. 컴포넌트라면 대문자로 시작하기
 */

// ex code)
/* before */
<ChildComponent
  class="mt-0"
  Clean="code"
  clean_code="react"
  otherComponent={OtherComponent}
  isShow={true}
/>

/* after */
<ChildComponent
  className="mt-0"
  clean="code"
  cleanCode="react"
  OtherComponent={OtherComponent}
  isShow
/>

function ChildComponent ({clean, cleanCode, OtherComponent}) {
  // component logic
}

/* 인라인 스타일 주의 */
/* JSX 에서 인라인 스타일을 사용하려면 중괄호 안에 camelCase key 를 가진 객체를 넣어야 한다. */

/* before */
function InlineStyle () {
  return (
    <button style="background-color: 'red'; font-size: '14px';">
      clean code
    </button>
  );
}

/* after01 */
const myStyle = {backgroundColor: 'red', fontSize: '14px'};

function InlineStyle () {
  return (
    <button style={myStyle}>
      clean code
    </button>
  );
}

/* after02 */
const myButtonStyle = {
  redButton: {backgroundColor: 'red', fontSize: '14px'},
  blueButton: {backgroundColor: 'blue', fontSize: '14px'},
};

function InlineStyle () {
  return (
    <>
      <button style={myButtonStyle.redButton}>
        redButton Click
      </button>
      <button style={myButtonStyle.blueButton}>
        blueButton Click
      </button>
    </>
  );
}

/**
 *  CSS in JS 인라인 스타일을 지양하자 
 *  
 * 성능에 민감하다.
 * 장점
 *  1. 외부로 분리했기 때문에 이제 스타일 렌더링 될때마다 직렬화되지 않는다 => 한번만 된다.
 *  2. 동적인 스타일을 실수로 건드는 확률이 적어진다.
 *  3. 스타일 관련 코드를 분리해서 로직에 집중하고 JSX 를 볼 때 조금 더 간결하게 볼 수 있다.
 *  4. 타입 안정성
 */

/* before01 */
export function Card ({ title, children}) {
  return (
    <div
      css={css`
        backgroundColor: 'white',
        border: '1px solid #111',
        borderRadius: '0.5rem',
        padding: '1rem',
      `}
    >
      <h5 
        css={css`
          fontSize: '1.25rem',
        `}
      >
        {title}
      </h5>
      {children}
    </div>
  );
}

/* before02 */
export function Card ({ title, children}) {
  return (
    <div css={css({
      backgroundColor: 'white',
      border: '1px solid #111',
      borderRadius: '0.5rem',
      padding: '1rem',
    })}>
      <h5 css={cardCss.title}>
        {title}
      </h5>
      {children}
    </div>
  );
}

/* after */
import { css } from '@emotion/react';

const cardCss = {
  self: css({
    backgroundColor: 'white',
    border: '1px solid #111',
    borderRadius: '0.5rem',
    padding: '1rem',
  }),
  title: css({
    fontSize: '1.25rem',
  })
};

export function Card ({ title, children}) {
  return (
    <div css={cardCss.self}>
      <h5 css={cardCss.title}>
        {title}
      </h5>
      {children}
    </div>
  );
}

/**
 * 객체 props 지양하기 
 *  - 변하지 않는 값일 경우 컴포넌트 외부로 드러내기
 *  - 필요한 값만 객체를 분해해서 PROPS 로 내려준다.
 *  - 값 비싼 연산 및 잦은 연산이 있을 경우 useMemo() 를 활용해 계산된 값을 메모이제이션한다.
 *  - 컴포넌트를 더 평탄하게 나누면 나눌 프롭스 또한 평탄하게 나눠서 내릴 수 있다.
 */

function SomeComponent ({heavyState}) {
  const [propArr, setPropArr] = useState(["hello", "hello"]);

  const computedState = useMemo(() => ({
    heavyState: heavyState
  }), [heavyState]);

  return (
    <>
      <ChildComponent
        hello="world"
        hello2={propArr[0]}
        computedState={computedState}
      />
      <ChildComponent 
        hello={propArr[1]}
      />
    </>
  );
}

/*
* HTML ATTRIBUTE 주의
* HTML 에서 속성은 Attribute 로 사용하고 React 에서는 Props(properties줄인말) 로 사용한다. javascript 에서는 property 로 사용한다.
* HTML, JS 에서 정의한 예약어와 커스텀 컴포넌트 props 가 혼용되지 않도록 주의하자
*/

function MyButton({children, type}) {
  return <button type={type}>{children}</button>;
}

function MyButton({children, ...rest}) {
  return <button {...rest}>{children}</button>;
}

function HTMLDefaultAttribute () {
  const MyButton = ({children, ...rest}) => (
    <button {...rest}>{children}</button>
  );

  return (
    <>
      <MyButton className="mt-0" type="submit">
        CleanCodeReact
      </MyButton>
      <input type="number" maxLength={99} />
    </>
  );
}

/*
* SPREAD 연산자 사용 시 주의
* props 에서 spread 연산자가 쓰이면 관련있는 props, 없는 props, 나머지 props 로 나눠사용해보자
* 그렇다면 어떤 props 를 내리고있는지 직관적으로 알 수 있다. 
*/

/* before */
const ParentComponent = (props) => {
  return <ChildOrHOCComponent {...props} />;
};

/* after */
const ParentComponent = (props) => {
  const {관련없는props, 관련있는props, ...나머지props} = props;
  return (
    <ChildOrHOCComponent
      관련있는props={관련있는props}
      {...나머지props} 
    />
  );
};

/*
* 많은 PROPS 분리 하기
* 결과보다는 일단 실행 => 분리의 대상
* 1. one depth 분리를 한다
* 2. 확장성을 위한 분리를 위해 도메인 로직을 다른 곳으로 모아넣는다.
* props 가 많다면 컴포넌트 분리를 해보자
*/

/* before */
function MorePropsSeparating () {
  return (
    <JoinForm 
      user={user}
      auth={auth}
      location={location}
      favorite={favorite}
      handleSubmit={handleSubmit}
      handleReset={handleReset}
      handleCancel={handleCancel}
    />
  );
}

/* after */
function MorePropsSeparating () {
  return (
    <JoinForm 
      onSubmit={handleSubmit}
      onReset={handleReset}
      onCancel={handleCancel}
    >
      <CheckBoxForm formData={user}/>
      <CheckBoxForm formData={auth}/>
      <RadioButtonForm formData={location}/>
      <SectionForm formData={favorite}/>
    </JoinForm>
  );
}

/*
* 단순하게 props 내리기
* props 에 객체 전체를 내리지 말고 꼭 필요한 값만 내리도록하자
*/

/* before */
const UserInfo = ({user}) => {
  return (
    <div>
      <h1>이름: {user.name}</h1>
      <p>나이: {user.age}</p>
      <p>이메일: {user.email}</p>
    </div>
  );
};

/* after */
const UserInfo = ({name, age, email}) => {
  return (
    <div>
      <h1>이름: {name}</h1>
      <p>나이: {age}</p>
      <p>이메일: {email}</p>
    </div>
  );
};

/*
* 컴포넌트란?
* react component 는 markup 으로 뿌릴 수 있는 javascript 함수
*/

/*
* SELF-CLOSING TAGS
* <Img></Img> => <Img/>
*/
// 자식 요소를 가질 수 없는 Void Element 에 대해서 알고 닫는 태그가 필요한지 파악

/*
* Fragment 지향하기(React v16.2 출시 )
* Fragment 는 DOM 에 별도의 노드를 추가하지 않고 여러 자식을 그룹화할 수 있는 방법을 제공한다.
* 만약 legacy 브라우저를 지원해야한다면 Fragment 대신 div 를 사용하자
* 만약 단일 형태의 요소를 내보내야한다면 fragment 를 사용하자
* 만약 key 를 사용해야한다면 fragment 를 사용하자(<>와 같이 숏컷을 사용할 수 없다)
*/

/* before */
function FragmentComponent () {
  return (
    <div>
      <h1>Fragment</h1>
      <p>Fragment 는 불필요한 div 를 없애고 싶을때 사용한다.</p>
    </div>
  );
}

/* after01 */
function FragmentComponent02 () {
  return (
    <React.Fragment>
      <h1>Fragment</h1>
      <p>Fragment 는 불필요한 div 를 없애고 싶을때 사용한다.</p>
    </React.Fragment>
  );
}

/* after02 */
function FragmentComponent03 () {
  return (
    <>
      <h1>Fragment</h1>
      <p>Fragment 는 불필요한 div 를 없애고 싶을때 사용한다.</p>
    </>
  );
}

/* after03 index 가 필요한 경우 */
function FragmentComponent04(){
  return (
    items.map(({id, term, description}) => (
      <React.Fragment key={id}>
        <dt>{term}</dt>
        <dd>{description}</dd>
      </React.Fragment>
    ))
  );
}


/* Fragment 지양 하기*/
/*before*/
function NoFragmentComponent(){
  return (
    <>
      <div>
        <h1>Fragment</h1>
        <p>Fragment 는 불필요한 div 를 없애고 싶을때 사용한다.</p>
      </div>
    </>  
  );
}

/*after*/
function NoFragmentComponent02(){
  return (
    <>
      <h1>Fragment</h1>
      <p>Fragment 는 불필요한 div 를 없애고 싶을때 사용한다.</p>
    </>
  );
}


/*before*/
return <>hello world</>
/*after*/
return "hello world"

/*before*/
return <h1>{isLoggedIn ? "사용자" : <></>}</h1>
/*after*/
return isLoggedIn && <h1>사용자</h1>


/* 알아두면 좋은 컴포넌트 네이밍 
* -컴포넌트 네이밍 = PascalCase
* -기본 HTML 요소 = low case
* -route base file name = kebab-case
* -- ex) component-naming.jsx => 파일 내 컴포넌트 = <ComponentNaming/>
* */



/*jsx 컴포넌트 함수로 반환
* -함수로 return 하는 경우 다음과 같은 단점
* 01 scope 를 알아보기 어렵다
* 02 반환 값을 바로 알기 어렵다
* 03 props 전달 등 일반적인 패턴이 아니다.*/


/* 컴포넌트 내부에서 컴포넌트 선언
* 단점
* 01 결합도가 증가한다
*   -- 구조적으로 스코프적으로 종속된 개발이 된다
*   -- 나중에 확장성이 생겨서 분리될때 굉장히 힘들어진다.
* 02 성능 저하
*   -- 상위 컴포넌트 리렌더하게되면 => 하위 컴포넌트 재생성*/

/*excode before*/
function ComponentInComponent(){
  const ChildComponent = () => {
    return <div>ChildComponent</div>
  }

  return (
    <div>
      <ChildComponent/>
    </div>
  )
}
/*after*/
const ChildComponent = () => {
  return <div>ChildComponent</div>
}
function ComponentInComponent(){
  return (
    <div>
      <ChildComponent/>
    </div>
  )
}


/* displayName 속성 사용하기 
* devtools 에서 익명함수를 쉽게 디버깅하려면 displayName 속성을 사용하자*/
/*excode*/
const InputText = forwordRef((props, ref) => {
  return <input type="text" ref={ref} />
}) 
InputText.displayName = 'InputText';


/*컴포넌트 구성하기
* 1. 변하지 않을 상수는 컴포넌트 외부에 드러내자
* 2. typescript 에서 interface 사용시 이름은 컴포넌트명을 기반으로 사용해보자ex) interface ComponentProps*/
/*excode*/
interface SomeComponentProps={
  name: string,
  age: number
}
const handleClose = () => {
  //Date.now() 같은 상수는 컴포넌트 외부로 빼자
  // LocalStorage 같은 외부 라이브러리는 컴포넌트 외부로 빼자
}
const SomeComponent = ({props}) => {
  const {name, age, job} = props;
  //플래그성 변수
  let isHold = false;
  const ref = useRef(null);
  // 서드파티 라이브러리 훅
  const location = useLocation();
  const queryClient = useQueryClient();
  const state = useSelector((state) => state);
  // 커스텀 훅
  const state02 = useCustomHook();
  // 컴포넌트 내부 상태
  const [state03, setState03] = useState("SomeState");
  // 함수
  const onClose = () => handleClose();
  const handleClose02 = () => {
    setState03("SomeState02");
  }
  // Early return jsx
  if (!isHold) {
    return <div>데이터가 존재하지 않음</div>
  }
  // useEffect 는 최대한 적은게 좋다, 최소 한개 또는 없음이 좋다. main jsx 와 가까운곳에 위치
  useEffect(() => {
    //side effect
  }, [state03]);
  
  return (
    <div>
      <h1>{name}</h1>
      <p>{age}</p>
      <button onClick={onClose} /> 
    </div>
  )
}


/*jsx 에서의 공백처리*/
/*excode*/
/*before*/ const welcome = <div>`clean&nbsp;code`</div>
/*after*/ const welcome02 = <div>clean{' '}code</div>



/*0(Zero) 는 jsx 에서 유효한 값이다*/
/*excode*/
return <div>{items.length && items.map((item)=> <Item key={items.id} item={item}/>)}</div>
return <div>{items.length > 0 && items.map((item)=> <Item key={items.id} item={item}/>)}</div>
return <div>{items.length > 0 ? items.map((item)=> <Item key={items.id} item={item}/>) : null}</div>


/*리스트 내부에서의 key
* 순회 시 key 를 넣을 때 단순 idex 를 넣거나 항상 새로운 값을 넣는것을 경계하자
* -server에서 id 를 받아오도록
* -또는 items.id 사용 */
/*excode*/
// key 를 index 로 사용하지 않는다 (단, 토이 프로젝트에서만 사용,또는 추가 수정 삭제가 전혀없을 경우 사용)
/*before*/
<ul>
  {items.map((item, index) => (
    <li key={index}>{item}</li>
  ))}
</ul>
/*after01 보여주기만할때 고려해볼만함*/
<ul>
  {items.map((item, index) => (
    <li key={`card-item-`+index}>{item}</li>
  ))}
</ul>

/*after02*/
const KeyInList = ({list}) => {
  const handleAddItem = (value) => {
    setItems((prev) => [
      ...prev,
      {
        id: cryto.randomUUID(),
        value,
      },
    ]);
  }
  
  useEffect(() => {
    /**
     * list 를 만들때 꼭 id 를 부여하자
     * 혹은 새로운 아이템을 추가하는 함수를 만들때 그때 고유한 값을 넣어주자
     */
  }, [list])
  return (
    <>
      <ul>
        {items.map((item, id) => (
          <li 
            key={item.id}
            onClick={() => handleDelete(item.id)}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  )
}


/*안전하게 Raw HTML 다루기
* DOMPurify = (데이터 소독해줌) 많이 사용하는 라이브러리
* HTML Sanitizer API, DOMPurify, eslint-plugin-risxx 를 사용하면 XSS 공격 위험 줄일 수 있음
*/
/*excode*/
const SERVER_DATA = <p>some server data</p>
function DangerouslySetInnerHTMLExample() {
const post = {
  // 악성 스크립트 공격 (XSS) 
  content: `<img src="https://example.com/image.jpg" alt="example"/>`
}
  const sanitizedContent = {__html: DOMPurify.sanitize(SERVER_DATA)}
  //사용자가 입력한 데이터 또는 서버에서 받은 데이터를 사용할때는 항상 소독을 해주자
  setContentHTML(DOMPurify.sanitize(SERVER_DATA))
/*before*/
const markup = {__html: SERVER_DATA}
return <div>{markup}</div>
/*after*/
return <div>{sanitizedContent}</div>
return <div dangerouslySetInnerHTML={sanitizedContent}></div>
/*after02*/
  return <textarea>{contentHTML}</textarea>
}


/*Hooks API
* HOC(HigherOrderComponent) react 에서 사용되는 고급 기술이며, 컴포넌트 로직을 재사용하기 위한 패턴*/
const EnhancedComponent = higherOrderComponent(WrappedComponent)
//redux 에서 connect() 함수가 HOC 의 예시
export default connect(mapStateToProps, mapDispatchToProps)(MyComponent)


/*useEffect() 기명 함수와 함께 사용하기
* 장점
* 1. 에러 발생시 (console.log, monitoring, report, react devtools) 은 모두 로그를 볼 수있으니 
* useEffect 기명함수 사용시 어떤 함수에서 에러 발생했는지 확인하기 편리하다.
* 2. 겉으로 해당 useEffect 의 기능을 직관적으로 확인 가능*/
/*excode*/
useEffect(() => {
  if(navigationType === 'POP') {
  // some logic
  }
}, [navigationType])
/*after*/
useEffect(function onPopState() {
  if(navigationType === 'POP') {
    // some logic
  }
}, [navigationType])
/*before*/
useEffect(() => {
  document.addEventListener();
  return () => {
    document.removeEventListener()
  }
}, [])
/*after*/
useEffect(function addEvent() {
  document.addEventListener();
  return function removeEvent() {
    document.removeEventListener()
  }
}, [])


/*한가지 역할만 수행하는 useEffect
* 객체 지향 원칙(SOLID) = 단일 책임 원칙
* 하나의 역할만 수행하는 무언가를 만들자, 한가지 역할만 하고있는지?
* 방법은? - 기명 함수를 만들자, - dependency arrays 너무 많은 관찰 대상 들어가있는건아닌지?
* useEffect 분리하기*/
/*excode*/
useEffect( () => {
  redirect(newPath);
  const userInfo = setLogin(token);
  // 로그인 로직
},[token, newPath])
/*after*/
useEffect(() => {
  redirect(newPath)
}, [newPath])
useEffect(() => {
  const userInfo = setLogin(token);
  // 로그인 로직
}, [token])

/*before*/
/*해당 useEffect logic 은 위험할 수있다. 
* 1. token 이 바뀌었을 시 redirect 될 수 있음
* 2. newPath 경로를 수행했을 뿐인데 login 경로를 탈 수 있음*/
function LoginPage({token, newPath}) {
  useEffect(() => {
    redirect(newPath);
    const userInfo = setLogin(token);
    // 로그인 로직
  }, [token, newPath])
}
function LoginPage({token, newPath}) {
  useEffect(() => {
    if(prevPath !== newPath) {
      redirect(newPath);  
    }
    if(prevToken !== token) {
      const userInfo = setLogin(token);
      // 로그인 로직  
    }
  }, [token, newPath])
}
/*after*/
function LoginPage({token, newPath}) {
  useEffect(() => {
    redirect(newPath)
  }, [newPath])
  useEffect(() => {
    const userInfo = setLogin(token);
    // 로그인 로직
    if(options) {
      //부가적인 로직 = 추가 동작해도 이상이 없고 부작용 생길일 없음
    }
  }, [token, options])
}



/*Custom Hooks 반환의 종류
* custom hooks 반환 타입을 변수, 배열, 객체 등으로 상황에 맞게 설정하자*/
/*excode*/
const useSomeHooks = (bool) => {
  return oneValue;
}
function ReturnCustomHooks() {
  const oneValue = useSomeHooks(true)
}
/*excode02*/
const useSomeHooks = (bool) => {
  return {
    first,
    second,
    third,
    rest
  };
}
function ReturnCustomHooks() {
  const {first: firstValue, second: secondValue, third: thirdValue, rest: rest} = useSomeHooks(true)
}
/*excode03*/
const useSomeHooks = (bool) => {
  return [state, setState]
}
function ReturnCustomHooks() {
  const [state, setState] = useSomeHooks(true)
}



/*useEffect 내부의 비동기
* -useEffect 의 콜백 함수로 비동기 함수를 바로 넣을 수 없다. (동작이 불안정해지기 때문에)*/
/*excode*/
useEffect(async () => {
  // 비동기 작업
  const result = await fetchData()
}, [])
/*after useEffect 내부에서 비동기 처리는 최대한 피하는게 좋다.*/
useEffect(() => {
  const fetchData = async () => {
    const result = await someFetch() 
  }
  fetchData()
}, [dependency])


/*import react
* - 과거에는 필수였지만 v17 부터는 불필요하다
* - 단, 17버전인지 확인해야하며, class Welcome extends React.Component 와 같이 참조하고 있는지 확인*/


/*디렉토리 구조
* 디렉토리 구조의 정답은 없지만 내 프로젝트 규모에 따라 바꿔나가거나
* one depth 로 표현하거나 base 규칙을 따르거나 하자*/


/*SPA 에서의 새로 고침*/

```