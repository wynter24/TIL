# React Router

## What is React Router?

[클라이언트 사이드 라우팅](../network/routing/client-side-routing-and-server-side-routing.md)을 구현하기 위한 React 라이브러리이다.

React 애플리케이션 내에서 URL과 UI 상태를 동기화하는데 사용된다.

URL 경로에 따라 다른 컴포넌트를 렌더링하고, 페이지 전환 시 전체 페이지를 다시 로드하지 않고 필요한 컴포넌트만 업데이트할 수 있다.

1. **라우트 정의** \
   `Route` 컴포넌트를 사용하여 특정 URL 경로에 따라 렌더링 할 컴포넌트를 정의
2. **내비게이션** \
   `Link` 컴포넌트를 사용하여 사용자에게 페이지 전환을 위한 내비게이션 링크를 제공
3. **동적 라우트 매칭** \
   URL 파라미터를 사용하여 동적으로 경로를 매칭하고, 이를 통해 데이터를 주고받을 수 있다.
4. **리디렉션 및 보호된 라우트** \
   특정 조건에 따라 리디렉션을 설정하거나 보호된 라우트를 구현할 수 있다.

***

### 설치

React에는 router 기능이 없으므로 패키지를 설치해야 한다.

```jsx
npm install react-router-dom
```
