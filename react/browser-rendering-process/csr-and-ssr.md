# 🎏 CSR & SSR

## CSR (Client-Side Rendering)

브라우저에서 자바스크립트를 사용하여 콘텐츠를 동적으로 로드하고 렌더링하는 방식

### **작동 방식**

1.  **초기 요청**

    브라우저가 서버에서 단일 HTML 파일과 자바스크립트 번들 파일을 요청
2.  **초기 로드**

    브라우저가 HTML과 자바스크립트 파일을 받으면, 자바스크립트를 실행하여 페이지의 콘텐츠를 동적으로 생성하고 렌더링
3.  **라우팅**

    사용자가 페이지 간 이동을 할 때, 자바스크립트가 URL 변화를 감지하고, 필요한 데이터와 컴포넌트를 로드하여 화면을 업데이트

{% tabs %}
{% tab title="장점" %}
* **빠른 페이지 전환** \
  초기 로드 이후에는 페이지 전환이 빠르고 부드럽다.
* **리치 인터랙션** \
  클라이언트 측에서 많은 로직을 처리할 수 있어, 복잡한 사용자 인터페이스와 인터랙션을 구현할 수 있다.
{% endtab %}

{% tab title="단점" %}
* **초기 로드 시간** \
  모든 자바스크립트 파일을 로드하고 실행해야 하므로, 초기 로드 시간이 길어질 수 있다.
* **SEO 문제** \
  초기 HTML에는 콘텐츠가 없고, 자바스크립트를 통해 동적으로 생성되므로, 검색 엔진이 콘텐츠를 크롤링하기 어려울 수 있다.
*   **너무 커지는 자바스크립트 파일의 사이즈**

    클라이언트 측에서 많은 로직을 처리할 수 있다는 것은 많은 코드를 가지고 있다. 즉, JS 파일이 커짐을 의미한다. 이는 클라이언트 측이 무거워진다(\*부하가 커질 수 있다)\


    _<mark style="color:blue;">\*부하: 컴퓨터 내부 혹은 네트워크등 하드웨어에 생기는 처리의 지연</mark>_

    _<mark style="color:blue;">≒ 트래픽: 네트워크단에서 데이터를 처리하고 주고받는 통신</mark>_

    _<mark style="color:blue;">트래픽이 생긴다(X) 트래픽이 과부화(O): 말 그대로 네트워크 상 처리 지연</mark>_
{% endtab %}
{% endtabs %}

***

## SSR (Server-Side Rendering)

서버에서 HTML을 동적으로 생성하여 클라이언트에 전달하는 방식

### **작동 방식**

1.  **초기 요청**

    브라우저가 서버에 페이지 요청
2.  **서버에서 HTML 생성**

    서버가 요청을 받고, 필요한 데이터를 가져와서 HTML을 생성
3.  **초기 로드**

    서버에서 완성된 HTML을 브라우저에 전달. 브라우저는 이 HTML을 즉시 렌더링
4.  **추가 로직**

    이후 자바스크립트 파일을 로드하여 클라이언트 측에서 추가적인 인터랙션을 처리 가능

{% tabs %}
{% tab title="장점" %}
서버에서 완성된 HTML을 제공하여,

**→ 빠른 초기 로드:** 브라우저가 HTML을 즉시 렌더링할 수 있어 초기 로드 시간이 짧다.

**→ SEO 친화적:** 검색 엔진이 쉽게 콘텐츠를 크롤링할 수 있다.
{% endtab %}

{% tab title="단점" %}
* **서버 부하** \
  모든 요청에 대해 서버가 HTML을 동적으로 생성해야 하므로, 서버에 부하가 증가할 수 있다.
* **페이지 전환** \
  서버에서 HTML을 새로 받아와야 하므로, CSR에 비해 페이지 전환이 느릴 수 있다. \
  (단, Next.js와 같은 프레임워크는 이 문제를 해결하기 위해 하이브리드 접근 방식을 사용)
{% endtab %}
{% endtabs %}

***

## 비교 요약

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
