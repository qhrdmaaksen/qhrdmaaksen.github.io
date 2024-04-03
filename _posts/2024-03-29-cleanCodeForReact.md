---
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
  if(fetchState.isLoading) return <LoadingComponent />
  if(fetchState.isFinish) return <FinishComponent />
  if(fetchState.isError) return <ErrorComponent />
}


```
