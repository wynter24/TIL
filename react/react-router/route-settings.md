---
description: '라우터 설정: react에게 어떤 경로에서 어떤 컴포넌트를 로드할 건지 알려준다.'
---

# Route Settings

## BrowserRouter

React Router의 기본적인 라우터 구성 요소로 HTML5의 History API를 사용하여 URL 관리한다.

자식 요소로 `Route` 컴포넌트를 사용하여 라우팅을 설정한다.

<details>

<summary>코드</summary>

```jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}
```



</details>

***

## createBrowserRouter

React Router v6.4 이상에서 도입된 새로운 API로, 데이터 중심의 라우팅을 위해 설계되었다.

설정 객체를 받아서 라우터를 생성한다.

사용 예시) 페이지를 로드하기 전에 데이터를 미리 가져오는 기능을 쉽게 설정할 수 있다.

<details>

<summary>코드</summary>

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import { RouterProvider, createBrowserRouter } from 'react-router-dom';
import NewPost, { action as newPostAction } from './routes/NewPost.jsx';
import RootLayout from './routes/RootLayout.jsx';
import Posts, { loader as postsLoader } from './routes/Posts.jsx';

const router = createBrowserRouter([
  {
    path: '/',
    element: <RootLayout />,
    children: [
      {
        path: '/',
        element: <Posts />,
        loader: postsLoader,
        children: [
          { path: '/create-post', element: <NewPost />, action: newPostAction },
        ],
      },
    ],
  },
]);

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <RouterProvider router={router} />
  </React.StrictMode>
);
```



</details>

*   `RouterProvider`

    라우팅 활성화, react router에게 URL을 확인해 다른 경로에 있는 다른 컴포넌트를 렌더링하라고 명령한다.

    RouterProvider의 **router 속성**에 라우트 설정 객체를 값으로 넣어줘야 한다.

    이 설정 객체를 createBrowserRouter로 만든다.
*   `createBrowserRouter`

    **배열**을 인자로 받는다.

    라우트 정의는 **객체** 형태이다.

    * path: URL 주소 설정
    * element: 화면에 렌더링 될 JSX 요소 (컴포넌트)
    * loader: 해당 라우트가 로드 될 때마다 실행되는 함수로 필요한 데이터 미리 로드 가능
    * action: 해당 라우터에서 폼이 전송될 때 실행(함수)&#x20;

    각 객체가 하나의 라우트 즉, **하나의 경로**이며 해당 경로에서 로드해야 할 컴포넌트를 의미한다.

***

### BrowserRouter vs createBrowserRouter

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

간단한 애플리케이션에서 `BrowserRouter`를 더 많이 사용하지만 복잡한 데이터 로딩 및 라우팅 요구사항을 처리하기에는 `createBrowserRouter`가 더 적합하다.

최신 React Router 버전과 함께 제공되는 기능을 활용하기 위해 `createBrowserRouter`를 채택하는 추세가 늘어나고 있다.

***

참고 자료

[Udemy 강의 - \[Next.js 14 & React - 완벽 가이드\] ](https://www.udemy.com/course/nextjs-react-incl-two-paths/?couponCode=24T6MT62024)
