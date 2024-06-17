# Client-Side Routing & Server-Side Routing

### Client-Side Routing (클라이언트 사이드 라우팅)

웹 애플리케이션에서 페이지 전환을 처리하는 방법 중 하나로 주로 SPA에서 사용된다.

전통적인 서버 사이드 라우팅과는 다르게, 브라우저에서 JS를 사용하여 페이지를 전환한다. 이를 통해 전체 페이지를 다시 로드하지 않고도 URL을 변경하고, 필요한 콘텐츠를 동적으로 로드 할 수 있다.

#### 특징 및 장점

* **URL 변경 관리**
  * 브라우저의 주소창에 URL이 변경되지만 실제로는 새로운 페이지를 요청하지 않는다.
  * 자바스크립트를 통해 URL 변경을 감지하고, 해당 URL에 맞는 콘텐츠를 동적으로 로드한다.
*   **빠른 페이지 전환**

    페이지 간 이동 시 서버에 새로운 HTML을 요청하지 않고, 자바스크립트로 필요한 데이터를 <mark style="background-color:orange;">비동기적으로</mark> 가져와 현재 페이지의 <mark style="background-color:orange;">일부분만 업데이트</mark>한다.\
    →  전체 페이지가 <mark style="color:red;background-color:yellow;">새로고침되지 않아</mark> 전환이 빠르고 부드럽다.
* **애플리케이션 상태 유지** \
  페이지 전환 시에도 애플리케이션의 상태 유지 가능.

#### 단점

*   **긴 초기 로드 시간**

    초기 로드 시 자바스크립트 파일을 모두 받아와야 하므로, 초기 로드 시간이 길어질 수 있다.

    _BUT,_ 초기 로드가 끝난 후에는 사용자 경험이 매우 부드럽고 빠르다.
*   **SEO 문제**

    초기 HTML에 콘텐츠가 없고, 자바스크립트를 통해 동적으로 콘텐츠를 로드하므로 검색 엔진이 콘텐츠를 크롤링하기 어려울 수 있다. ⇒ 검색 엔진 최적화(SEO)가 어려울 수 있다.

#### **사용 사례**

주로 <mark style="background-color:purple;">SPA</mark>(Single Page Application)에서 사용.\
예) React, Vue.js, Angular 같은 프레임워크와 라이브러리에서 사용

***

### Server-Side Routing (서버 사이드 라우팅)

서버에서 각 페이지 요청에 대해 별도의 HTML 파일을 생성하여 클라이언트에 전달하는 방식이다.

**작동 방식**

* **URL** **요청 처리**
  * 사용자가 URL을 통해 페이지를 요청할 때마다, 서버는 해당 경로에 맞는 HTML 파일을 생성하거나 미리 준비된 HTML 파일을 반환한다.
  * 페이지 전환 시  브라우저는 서버에서 전체 HTML 페이지를 받아와 전체 페이지를 다시 로드한다.&#x20;

**단점) 완전히 페이지 새로고침** →  페이지 전환이 클라이언트 사이드 라우팅에 비해 느릴 수 있다.

#### 장점

* **빠른 초기 로드**
  * 서버에서 미리 생성된 HTML을 전달하므로, 초기 로드 시간이 빠르다.
  * 초기 로드 시 자바스크립트를 모두 로드하고 실행할 필요가 없다.
* **SEO 친화적**
  * 서버에서 완성된 HTML을 제공하므로, 검색 엔진이 콘텐츠를 쉽게 크롤링할 수 있다.
  * SEO가 용이하다.

**사용 사례**

전통적인 MPA(Multi-Page Application)에서 사용.\
예) 서버 렌더링을 사용하는 웹 프레임워크(Django, Ruby on Rails, ASP.NET 등)와 Next.js에서 <mark style="background-color:purple;">SSR</mark>(Server-Side Rendering)을 사용하는 경우

***

### 비교 요약

<table><thead><tr><th width="311">Client-Side Routing </th><th>Server-Side Routing</th></tr></thead><tbody><tr><td>브라우저에서 자바스크립트로 URL 변경 관리</td><td>서버에서 각 페이지 요청에 대해 HTML 파일을 생성하여 제공</td></tr><tr><td>일부분만 업데이트</td><td>완전한 페이지 새로고침</td></tr><tr><td>초기 로드 시간이 길어질 수 있음</td><td>초기 로드 시간이 빠름</td></tr><tr><td>SEO에 불리함</td><td>SEO에 유리함</td></tr><tr><td>주로 SPA에서 사용</td><td>주로 MPA에서 사용</td></tr></tbody></table>
