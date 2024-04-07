a---
layout: post
title: "클린코드 리액트"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```js

----------------------------------------------------------------------
코드의 목적성(앱의 완성도)을 우선적으로 생각하고 클린코드를 사용지향하자.

eslint or prettier 를 활용해 클린코드화

----------------------------------------------------------------------

초기 값
  - 가장 먼저 렌더링될때 순간적으로 보여질 수 있는 값이기도 함
  - 초기에 렌더링 되는 값
초기 값을 지키지 않을 경우
  - 렌더링 이슈, 무한 루프, 타입 불일치로 의도치 않은 동작으로 런타임 에러 발생 가능성
  - 초기값을 넣지 않으면 undefined 가 발생됨
  - 상태를 CRUD 할때 초기 값을 잘 기억해놔야지 원상태로 돌아감
  - 비어있는 값 또는 NULL 처리 할때 불필요한 방어코드도 줄일 수 있음

----------------------------------------------------------------------

업데이트 되지 않는 일반적인 객체일 경우 리액트 외부에서 관리하도록하자
  - 컴포넌트 내부에 방치하도록하면 해당 객체 또는 상수를 참조 할때마다 불필요한 렌더링이 발생할 수 있음

----------------------------------------------------------------------

플래그 값
 - 프로그래밍에서 조건 또는 제어를 위한 Boolean 으로 나타내는 값

플래그 상태의 경우 useState 를 사용하지 않고 표현식만으로도 활용할 수 있다
ex)
/* before */
  const [isLogin, setIsLogin] = useState(false);
  useEffect(() => {
    if(isLogin) {
      setIsLogin(true);
    }

    if(hasToken) {
      setIsLogin(true);
    }
    등등등
  }, [isLogin, hasToken 등등등]); 을 아래와 같이 상태를 사용하지 않고 표현식으로 사용할 수 있다

  /* after */
  const isLogin =
    hasToken === true &&
    hasCookie === true &&
    isValidCookie === true &&
    isNewUser === false &&
    isValidToken;


-props 를 useState 에 넣지 않고 바로 return 문에 사용하도록해보자
-컴포넌트 내부 변수는 렌더링마다 고유한 값을 가지기 때문에
useState 가 아닌 const 로 상태를 선언하는게 좋은 경우도 있다

----------------------------------------------------------------------

리렌더링 방지가 필요하다면 useState 대신 useRef 를 사용 할 수 있다
useState 대신 useRef 를 사용하면 컴포넌트의 생명주기와 동일한 리렌더링되지 않는 상태를 만들 수 있다.
ex)
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
  }, [])

----------------------------------------------------------------------

/**
 * 연관된 상태 단순화 하기 KISS
 * K : Keep
 * I : It
 * S : Simple
 * S : Stupid
 *
 * 리액트의 상태를 만들때 연관된것들 끼리 묶어서 처리하면 에러 방지 및 코드 간결화
*/
ex)
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
      })
  }

  if(isLoading) {
    return <LoadingComponent/>;
  if(isFinish) {
    return <FinishComponent/>;
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
}
function FlatState() {
  const [promiseState, setPromiseState] = useState(PROMISE_STATE.INIT);

  function fetchData() {
    // fetch data 시도
    setPromiseState(PROMISE_STATE.LOADING);

    fetch(url)
      .then(() => {
        // fetch 성공
        setPromiseState(PROMISE_STATE.LOADING);
        setPromiseState(PROMISE_STATE.FINISH);
      })
      .catch(() => {
        // fetch 실패
        setPromiseState(PROMISE_STATE.LOADING);
        setPromiseState(PROMISE_STATE.ERROR);
      })
  }

  if(promiseState === PROMISE_STATE.LOADING) return <LoadingComponent />
  if(promiseState === PROMISE_STATE.FINISH) return <FinishComponent />
  if(promiseState === PROMISE_STATE.ERROR) return <ErrorComponent />
}



/**
 * 연관된 상태는 객체로 묶어내자
 * 동일한 코드가 반복될 때 그 반복을 멈출 수 있는 지 생각을 한번 해보자
 */

/* Before */
function ObjectState () {
  const [isLoading, setIsLoading] = useState(false)
  const [isFinish, setIsFinish] = useState(false)
  const [isError, setIsError] = useState(false)

  const fetchData = () => {
    setIsLoading(true)

    fetch(url)
      .then(() => {
        setIsLoading(false)
        setIsFinish(true)
      })
      .catch(() => {
        setIsLoading(false)
        setIsError(true)
      })
  }
  if(isLoading === true) return <LoadingComponent />
  if(isFinish === true) return <FinishComponent />
  if(isError === true) return <ErrorComponent />
}

/* After */
function ObjectState () {
  const [fetchState, setFetchState] = useState({
    isLoading: false,
    isFinish: false,
    isError: false,
  })

  const fetchData () => {
    /* fetch 시도 */
    setFetchState((prevState) => {
      ...prevState,
      isLoading: true,
    })
    fetch(url)
      .then(() => {
        setFetchState((prevState) => {
          ...prevState,
          isLoading: false,
          isFinish: true,
        })
      })
      .catch(() => {
        setFetchState((prevState) => {
          ...prevState,
          isError: true,
        })
      })
  }
  if(fetchState.isLoading) {
    return <LoadingComponent />
  }
  if(fetchState.isFinish) return <FinishComponent />
  if(fetchState.isError) return <ErrorComponent />
}


/**
 * useState 를 useReducer 로 리팩터링
 * 구조화된 상태를 원한다면 useReducer 를 사용하자
 * */

const INIT_STATE = {
  isLoading: false,
  isSuccess: false,
  isFail: false,
}

const ACTION_TYPE = {
  FETCH_LOADING: 'FETCH_LOADING',
  FETCH_SUCCESS: 'FETCH_SUCCESS',
  FETCH_FAIL: 'FETCH_FAIL'
}

const reducer = (state, action) => {
  switch (action.type {
    case "FETCH_LOADING":
      return {...state, isLoading: true, isSuccess: false, isFail: false}
    case "FETCH_SUCCESS":
      return {...state, isLoading: false, isSuccess: true, isFail: false}
    case "FETCH_FAIL":
      return {...state, isLoading: false, isSuccess: false, isFail: true}

    default:
      return INIT_STATE;
  }
}

function stateToReducer () {
  const [state, dispatch] = useReducer(reducer, INIT_STATE)

  const fetchData () => {
    dispatch({ type: ACTION_TYPE.FETCH_LOADING})

    fetch(url)
      .then(() => {
        dispatch({ type: ACTION_TYPE.FETCH_SUCCESS})
      })
      .catch(() => {
        dispatch({ type: ACTION_TYPE.FETCH_FAIL})
      })
  }

  if(state.isLoading) return <LoadingComponent />
  if(state.isSuccess) return <SuccessComponent />
  if(state.isFail) return <FailComponent />
}


/**
 * 상태로직 Custom Hooks 로 뽑아내기
 * Custom Hooks 을 사용하면 코드를 확장성 있고 재사용 가능하게 작성할 수 있다.
 */

/* Before */
const INIT_STATE = {
  isLoading: false,
  isSuccess: false,
  isFail: false,
}

const ACTION_TYPE = {
  FETCH_LOADING: 'FETCH_LOADING',
  FETCH_SUCCESS: 'FETCH_SUCCESS',
  FETCH_FAIL: 'FETCH_FAIL'
}

const reducer = (state, action) => {
  switch (action.type {
    case "FETCH_LOADING":
      return {...state, isLoading: true, isSuccess: false, isFail: false}
    case "FETCH_SUCCESS":
      return {...state, isLoading: false, isSuccess: true, isFail: false}
    case "FETCH_FAIL":
      return {...state, isLoading: false, isSuccess: false, isFail: true}

    default:
      return INIT_STATE;
  }
}

function stateToReducer () {
  const [state, dispatch] = useReducer(reducer, INIT_STATE)

  const fetchData () => {
    dispatch({ type: ACTION_TYPE.FETCH_LOADING})

    fetch(url)
      .then(() => {
        dispatch({ type: ACTION_TYPE.FETCH_SUCCESS})
      })
      .catch(() => {
        dispatch({ type: ACTION_TYPE.FETCH_FAIL})
      })
  }

  if(state.isLoading) return <LoadingComponent />
  if(state.isSuccess) return <SuccessComponent />
  if(state.isFail) return <FailComponent />
}


/* After */
const INIT_STATE = {
  isLoading: false,
  isSuccess: false,
  isFail: false,
}

const ACTION_TYPE = {
  FETCH_LOADING: 'FETCH_LOADING',
  FETCH_SUCCESS: 'FETCH_SUCCESS',
  FETCH_FAIL: 'FETCH_FAIL'
}

const reducer = (state, action) => {
  switch (action.type {
    case "FETCH_LOADING":
      return {...state, isLoading: true, isSuccess: false, isFail: false}
    case "FETCH_SUCCESS":
      return {...state, isLoading: false, isSuccess: true, isFail: false}
    case "FETCH_FAIL":
      return {...state, isLoading: false, isSuccess: false, isFail: true}

    default:
      return INIT_STATE;
  }
}

const useFetchData = (url) => {
  const [state, dispatch] = useReducer(reducer, INIT_STATE)

  useEffect (() => {
    const fetchData = async () => {
    dispatch({ type: ACTION_TYPE.FETCH_LOADING})

    await fetch(url)
      .then(() => {
        dispatch({ type: ACTION_TYPE.FETCH_SUCCESS})
      })
      .catch(() => {
        dispatch({ type: ACTION_TYPE.FETCH_FAIL})
      })
  }
    fetchData()
  }, [url])
  return state
}


function CustomHooks () {
  const {isLoading, isFail, isSuccess} = useFetchData('url')
}

if(isLoading) return <LoadingComponent />
if(isFail) return <FailComponent />
if(isSuccess) return <SuccessComponent />


/**
 * 이전 상태 활용하기
 * -update function 을 사용해서 prev state 를 고려한다면 예상치못한 
 * 결과를 예방할 수 있다
 * -이전 state 를 꺼내서 사용하는 방식으로 바꿔줘야 랜더링이나 
 * 특히 인풋을 핸들링하는 경우 불필요한 에러를 내지 않을 수 있다
 * -이전 상태를 완전히 덮어 씌우고 싶은 경우 값을 일방적으로 할당하는 경우를 생각할 수 있다.
 *  */

ex)
/* before */
setAge(age+ 1);
/* after */
setAge((prevAge) => prevAge + 1);
/* before */
function PrevState () {
  const [age, setAge] = useState(42)

  function updateState() {
    setAge(age + 1 );// setAge(42=>43)
    setAge(age + 1 );// setAge(42=>43)
    setAge(age + 1 );// setAge(42=>43)
  }
}
/* after */
function PrevState () {
  const [age, setAge] = useState(42)

  function updateState() {
    setAge((prevAge) => prevAge +1);// setAge(42=>43)
    setAge((prevAge) => prevAge +1);// setAge(43=>44)
    setAge((prevAge) => prevAge +1);// setAge(44=>45)
  }
}


/**
 * 불필요한 props 복사를하지 말자 (데이터의 흐름을 끊는것이기 때문)
 * -컴포넌트에 들어오기전에 값 비싸고 무거운 연산들은 끝내는게 좋다 (연산된 값을 props 로 넘기기)
 * -비싸지 않은 경우 컴포넌트 내부의 변수로도 간단히 사용 가능
 * -props 로 내려오는 값을 조작하는 행위로 조작을 무겁게 하는경우 useMemo 를 사용하자 (연산 최적화)
 * -props 바로 사용하기
 */

/* before */
function CopyProps ({value}) {
  const [copyValue] = useState(value)
  return <div>{copyValue}</div>
}

/* after */
function CopyProps ({value}) {
  return <div>{value}</div>>
}

/* before */
function CopyProps ({value}) {
  const copyValue = 값_비싸고_무거운_연산(value)
  return <div>{copyValue}</div>
}
/* after */
function CopyProps ({value}) {
  const copyValue = useMemo(() => 값_비싸고_무거운_연산(value), [value])
  return <div>{copyValue}</div>
}


/**
 * 중괄호
 * - jsx 에서 중괄호의 필요사항
 * 1.논리적인 변수나 숫자
 * 2.boolean, object 에 해당되는 배열이나 함수, 표현식을 표현할수있는 창구
 * - string 일땐 curly braces 사용하지 말자
 * - 이중 줄괄호 안에는 일반적으로 in-line 객체를 넣었다고 생각하자
 * - 전혀 신경쓰고 싶지 않다면 eslint or prettier 로 설정해놓자
 */
ex code
function CurlyBraces() {
  const style = {
    backgroundColor: 'blue',
    width: 1000,
  }
  return (
    <header
      className='clean-header'
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
  )
}


/**
 * props 축약 (shorthand props)
 */

/* before */
function component (props) {
  <HeaderComponent hasPadding={props.hasPadding}>
    <ChildComponent isDarkMode={props.isDarkMode} isLogin={props.isLogin} />
  </HeaderComponent>
}
/* after */
function component ({hasPadding, ...props}) {
  <HeaderComponent hasPadding={hasPadding}>
    <ChildComponent {...props} />
  </HeaderComponent>
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
  )
}
/* after */
function ShorthandProps ({hasPadding,isAdmin, ...props}) {
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
      <ChildComponent {...props}} />
    </header>
  )
}


/**
 * singleQuote vs doubleQuote
 */
{/* O */}
  <a href="www.google.com">Google</a
{/* X */}
  <input class='classExCode' type="button" value='CleanCodeReact'/>
{/* X */}
  <Clean style={{ backgroundPosition: "left"}} />

```
