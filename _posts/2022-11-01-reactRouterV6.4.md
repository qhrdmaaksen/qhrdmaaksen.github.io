---
layout: post
title: "React Router V6.4 추가 기능"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```js

-React Router 버전 6.4에는 React 앱에서의 데이터 페칭과 데이터 제출을 단순화하는 기능이 있다


-기존 데이터 페칭
useEffect를 사용해 요청을 초기화하고 요청을 보내고 로딩 상태를 관리하거나
오류 상태를 관리하는 것을 의미하며 이를 UI에도 나타내겠죠
우리 앱의 경우와 같은 경우에는 데이터 제출이 있을 수도 있고요
NewPostForm.jsx 컴포넌트에 중첩된 양식이 있고 디폴트를 방지해 직접 
데이터를 추출한 후
제출 상태를 관리해 몇 가지 유틸리티 기능을 통해 요청을 보내게 되며
이 유틸리티 기능은 별개의 파일에 정의되는데 바로 Fetch API를 통해 기본 HTTP 요청을 보내는 파일이죠
오류 상태 역시 관리합니다 요청을 모두 보낸 후 사용자를 다른 페이지로 리디렉션하거나
오류가 있다면 오류를 보여주게 됩니다
,또한 이 방식의 또 다른 단점은 컴포넌트 내비게이션이 시작될 때가 아니라
컴포넌트가 로드된 다음에야 데이터 페칭이 시작된다는 겁니다
즉 로딩 상태와 오류 상태를 직접 관리해야 하므로 약간 귀찮을 뿐더러 
뜻하지 않게 복잡해질 수 있다
----------------------------------------------------------------
useLoaderData()
  <Route index element={<BlogPostsPage />} loader={blogPostsLoader} />
와 같이 loader 지정하고 이 라우트로 탐색하면 React Router가 자동으로 해당 함수를 호출하겠죠
또 loader 함수가 반환하는 데이터를 자동으로 가져와 함수형 컴포넌트에서 사용할 수 있게 됨
,이 훅은 loaderData 에 액세스할 수 있게 만들고 loader 함수에 의해 데이터가 반환됩니다 
만약 loader 함수가 프로미스를 반환한다면 프로미스가 리졸브하게 되는 데이터를 말하는 거예요
지금 같은 경우 api.js 요청에 대한 응답이 반환한 데이터죠

-이때 게시물들은 React Router가 내부적으로 가져와서 자동으로 페이지 컴포넌트에 나타나도록 한 거예요
직접 데이터 페칭을 초기화하지 않아도 말이죠 useEffect를 사용하지 않아도 되고
로딩 상태를 관리하지 않아도 됩니다 데이터를 가져온 후에야 페이지 컴포넌트가 렌더링되기 때문에
작성해야 하는 코드가 줄어드는 거임
----------------------------------------------------------------
Outlet
-{/*RootLayout 이 자식 라우트를 지원하기 위해서는 RootLayout.jsx 로 가야 하는데 원한다면 pages 폴더로 옮긴 후
				그보다 중요한 건 children 부분을 제거하는 대신 react-router-dom 이 제공하는 특수 컴포넌트 Outlet 을 사용해
				중첩된 모든 자식 컴포넌트가 렌더링되어야 하는 위치를 표시해야 해요*/}
      {/*루트 Route 안에 정의된 모든 컴포넌트 즉 지금 선택한 컴포넌트들이 여기에 렌더링되도록 Outlet 컴포넌트로 정의*/}
      <Outlet />
      {/*<main>{children}</main>*/}
----------------------------------------------------------------
-function App() {
	/*js route 정의 몇가지 사용하기위해 배열 전달
	* jsx 에 라우트 정의한것처럼 createBrowserRouter 함수에 또 다른 함수를 전달할수있음 createRoutesFromElements
	* 이런 식으로 라우트를 설정할 때는 Routes 컴포넌트 대신 단수형인 Route 를 입력해야 해요
	* 다른 라우트들을 자식 라우트로 가지는 하나의 부모 라우트
	* 여기서 장점은 이제 부모 라우트가 다른 라우트를 포함한 레이아웃을 렌더링한다는 겁니다 이 경우 RootLayout 이죠
	*/

	const router = createBrowserRouter(createRoutesFromElements(
			/*부모 라우트 경로가 활성화되어 있다면 인덱스 라우트가 렌더링되는 디폴트 라우트가 됩니다*/
			<Route path="/" element={<RootLayout/>}>
				<Route index element={<WelcomePage/>}/>
				<Route path="/blog" element={<BlogLayout/>}>
					<Route index element={<BlogPostsPage/>} loader={blogPostsLoader}/>
					<Route path=":id" element={<PostDetailPage/>}/>
				</Route>
				<Route path="/blog/new" element={<NewPostPage/>}/>
			</Route>))

	return (
			<RouterProvider router={router}/>

			/*BrowserRouter 는 6.4 버전 새 기능 사용시 사용할 수 없음*/
			/*<BrowserRouter>
				<RootLayout>
					<Routes>
						<Route path="/" element={<WelcomePage />} />
						<Route path="/blog" element={<BlogLayout />}>
							<Route index element={<BlogPostsPage />} loader={blogPostsLoader} />
							<Route path=":id" element={<PostDetailPage />} />
						</Route>
						<Route path="/blog/new" element={<NewPostPage />} />
					</Routes>
				</RootLayout>
			</BrowserRouter>*/
	);
}
----------------------------------------------------------------
에러 상태 처리
-오류 상태를 직접 추적하는 대신 데이터 페칭을 수행하는 라우트에
errorElement 프로퍼티를 추가하면 돼요
문제가 없을 시 렌더링 될 보통의 컴포넌트를 정의하는 다른 element 프로퍼티처럼
문제가 있을 시 렌더링 될 컴포넌트나 jsx 코드를 정의함
--이때 꼭 로딩을 수행하는 라우트에 errorElement를 추가하지 않고
아무 부모 라우트에나 추가해도 됩니다
그럼 errorElement가 항상 부모 라우트를 대체하겠죠 따라서 루트 라우트 즉 RootLayout 라우트에 있는
루트 컴포넌트를 편집할 수도 있겠네요 또 pages 폴더에 ErrorPage 컴포넌트를 추가해
MainNavigation과 오류 메시지를 나타낸 후 ErrorPage 컴포넌트를 라우트 정의 내에 오류가 생길 시
폴백 컴포넌트로 사용하도록 합니다

useRoutError()
-추가적으로 제공되는 오류 데이터를 액세스할 수 있어요 이 경우에는
출력하고자 하는 메시지를 하나 더 설정해두었죠 React Router가 제공하는 특별한 훅인 useRouteError 훅을 사용
----------------------------------------------------------------
Form
-/*React Router가 인식하도록 모든 필드를 Form 컴포넌트로 래핑하세요 Form 컴포넌트에 method를 추가해
			get이나 post 뿐만 아니라 patch, put, delete도 가능합니다 저는 post로 하고 action도 정의하겠습니다
			action에는 요청이 전송될 경로를 정의*/
    <Form className={classes.form} method="post" action="/blog/new">

-React Router가 모든 양식 데이터를 포함한 요청 객체를 생성하는데
백엔드에 요청을 전송하지는 않습니다
대신 우리가 정의한 action 함수에 요청을 보낸 후 그걸 백엔드에 전달하거나 원하는 작업을 수행할 수 있다


action
-양식 제출 후에 수행하는 액션(action)에 관한 거죠 이 action 함수는 라우트 정의에 등록해야 하는데
이때 Form 컴포넌트를 통해 요청을 전송하는 라우트에 등록해야 해요
이 경우 /blog/new가 대상이었으니 해당하는 라우트 정의에 새 프로퍼티인 action을 추가합니다
여기서 포인터로 지정할 action 함수가 양식 제출 시 실행되면서 이 라우트 경로에 도달 (App.jsx 에 route 작성한 /blog/new 경로)

-양식이 제출될 때마다 action 함수가 실행되고 특정 데이터로 자동으로 생성된 객체를 가지게 될 겁니다
필요하다면 params도 가지지만 request 객체를 가지겠죠
자동으로 생성된 request 객체가 브라우저를 떠나지 않았어요 우리가 아직 브라우저 상에 있는 거니깐 중요합니다
자동으로 생성된 request 객체가 양식으로 제출된 데이터를 포함하고 있으니 양식의 입력값으로 지정된 이름을 이용해 데이터를 추출할 수 있어요
이름이 중요한 거죠 원래처럼 ref나 양방향 바인딩을 통해 양식에서 데이터를 직접 추출할 필요 없이 name 속성과
자동으로 생성된 요청의 일부인 자동으로 생성된 양식 제출 객체를 이용하면 됩니다


formData
-생성된 기본 request 객체에 내장되어 있는 formData 메서드가 양식의 일부였던 데이터에 액세스할 수 있도록 합니다
이걸 formData로 설정하세요 이제 post 객체를 생성하고 title 프로퍼티를 추가해 formData.get('title')에 액세스합니다
get 메서드는 formData 객체가 지원하는 메서드로 formData 객체는 대기 후 formData 메서드가 반환하는 객체죠
모두 디폴트 브라우저 API로 React Router가 활용하는 기본 request 객체의 일부예요
const formData = await request.formData();
const post = {
    /*이렇게 title 값을 받기 위해 양식에 정의한 이름을 값으로 전달한 겁니다 title이라는 이름이죠
      만약 메인 텍스트를 입력하려면 해당하는 이름인 post-text를 전달해야 해요
     *body를 식별자로 사용하는 이유는 나중에 api.js에서 입력값의 유효성을 검사할 때 사용하고 더미 백엔드 API가 받을 예정이기 때문*/
    title: formData.get("title"),
    body: formData.get("post-text"),
  };


useActionData()
-같은 페이지에 머물 때 반환된 데이터에 액세스하기 위해서는 useActionData 훅을 사용
-React Router가 제공하는 이 훅을 사용하면오류 데이터 등 액션이 반환하는 어떤 종류의 데이터든
UI에서 사용할 수 있어요 데이터가 설정됐는지 확인하고 설정된 데이터가 오류 상태인지 확인하면
오류가 일어났는지 알 수 있겠죠
ex 
const data = useActionData();
{data && data.status && <p>{data.message}</p>}
공식 문서
-이 후크는 이전 탐색 action결과 또는 undefined제출이 없는 경우 반환된 값을 제공합니다.
-이 후크의 가장 일반적인 사용 사례는 양식 유효성 검사 오류입니다. 양식이 올바르지 않으면 오류를 반환하고 사용자가 다시 시도하도록 할 수 있습니다.



useNavigation()
-useNavigate이 아니라 useNavigation으로 내비게이션 정보를 보여주는
객체를 만들어주는 훅이에요
-useNavigation을 사용하면 action 및 loader 함수가 현재 작업 중인지에 대한 정보를 줍니다
-이 객체에서 state 프로퍼티에 액세스하는데 idle, loading 혹은 submitting일 겁니다
이걸 이용해서 현재 제출 중 상태에 있는지 즉 action 함수가 작업을 수행하고 있는지 확인
-useState 와 같이 boolean type 반환토록하여 사용 가능한것같음
공식 문서
-사용자가 앱을 탐색할 때 페이지가 렌더링되기 전에 다음 페이지의 데이터가 로드됩니다. 앱이 응답하지 않는 것처럼 느껴지지 않도록 이 시간 동안 사용자 피드백을 제공하는 것이 중요합니다.
ex
function Root() {
  const navigation = useNavigation();
  return (
    <div>
      {navigation.state === "loading" && <GlobalSpinner />}





```