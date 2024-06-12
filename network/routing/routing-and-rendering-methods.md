# Routing and rendering methods

## 라우팅과 렌더링 방식

### **SPA (Single Page Application)와 CSR (Client-Side Rendering)**

* **동적 라우팅**을 사용
  * 자바스크립트를 통해 브라우저에서 라우팅 관리
  * URL 변경을 감지하고, 필요한 데이터를 자바스크립트로 동적으로 로드하고 화면을 업데이트
  * 클라이언트 사이드에서 동적으로 라우트를 처리하기 때문에 빠른 페이지 전환 가능

### **SSR (Server-Side Rendering)**

* **동적 라우팅**과 **정적 라우팅** 모두 사용 가능
  * 동적 라우팅: 서버가 요청을 받을 때마다 HTML을 동적으로 생성하여 응답
  * 정적 라우팅: 서버에서 미리 생성된 HTML 파일을 제공할 수 있다.
  * Next.js 같은 프레임워크에서는 `getServerSideProps`를 사용하여 동적 라우팅을 처리할 수 있다.

### **SSG (Static Site Generation)**

* **정적 라우팅**을 사용
  * 빌드 시점에 모든 페이지가 미리 생성되어 정적 파일로 저장
  * 예를 들어, 블로그 시스템에서는 모든 포스트의 페이지가 미리 생성되어 `/post/123`, `/post/124` 등의 경로에 대한 정적 HTML 파일이 존재한다.
  * Next.js 같은 프레임워크에서는 `getStaticProps`와 `getStaticPaths`를 사용하여 정적 라우팅을 처리할 수 있다.

***

### 정리

* **SPA (Client-Side Rendering)**:
  * **동적 라우팅**: 브라우저에서 자바스크립트를 통해 라우팅을 동적으로 관리.
  * 빠른 페이지 전환, 초기 로드가 길어질 수 있음, SEO 어려움.
* **SSR (Server-Side Rendering)**:
  * **동적 라우팅**: 서버에서 요청을 받을 때마다 동적으로 HTML 생성.
  * **정적 라우팅**: 서버에서 미리 생성된 HTML 제공 가능.
  * 빠른 초기 로드, SEO 친화적, 서버 부하가 높을 수 있음.
* **SSG (Static Site Generation)**:
  * **정적 라우팅**: 빌드 시점에 모든 페이지가 정적으로 생성되어 저장.
  * 매우 빠른 로드 속도, SEO 친화적, 콘텐츠가 자주 변경되지 않는 경우 적합.
