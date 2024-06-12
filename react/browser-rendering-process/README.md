# 🌲 Browser Rendering Process

### 🤍🩶용어 먼저 정리하기!🩶🤍&#x20;

🩶**파싱(parsing)**: 텍스트의 문자열을 분해하고 구조를 생성하는 일련의 과정 \
프로그래밍 언어의 문법에 맞게 작성된 텍스트 문서를 읽고, 실행하기 위한 과정

🤍**Rendering**: HTML, CSS, JS로 작성된 문서를 파싱하여 브라우저에 시각적으로 출력하는 것&#x20;

🩶**토큰**: 문법적으로 더 이상 나눌 수 없는 기본적인 언어 요소&#x20;

🤍**node**: 데이터 통신 네트워크 내에서 교차/연결 지점 ( = 컴퓨터 과학에 쓰이는 기초적인 단위) \
이후 DOM을 구성하는 기본 요소가 된다.&#x20;

🩶**DOM**: HTML 문서를 파싱한 자료구조 형태의 결과물\
HTML element들을 tree형태로 표현한 것\
\*자료구조 형태 - 노드들로 구성된 트리 자료구조

***

## ✅웹페이지 빌드 과정(브라우저가 렌더링 하는 과정)

### 1. DOM 트리 생성

문서를 읽어 들여 그것을 파싱하고 어떤 내용을 페이지에 렌더링할지 결정

* **Html 파싱 & DOM 생성** \
  (브라우저) html 파일 요청 \
  (서버) HTML 파일을 읽어 들여 메모리에 저장 후 바이트로 응답 \
  (브라우저) meta태그의 charset attribute로 지정해 둔 인코딩 방식(ex. UTF-8)을 기준으로 문자열로 변환 \
  '토큰(token)'들로 분해 \
  토큰들을 객체로 변환하여 노드 생성 \
  중첩관계가 형성되어 트리 자료구조를 구성 ⇒ DOM
* **HTML 문서 내에서 **<mark style="color:green;">**\<style>\</style>**</mark>** 만나면**\
  → **CSS 파싱 & CSSOM 생성** \
  렌더링 엔진은 위에서부터 순차적으로 파싱하며 DOM을 생성한다. \
  이때, 중간에 CSS를 로드하는 link나 style 태그를 만나면 DOM 생성을 일시 중단. \
  그 후 HTML과 동일한 파싱과정을 거쳐 CSSOM(CSS Object Model)을 생성. \
  파싱이 완료되면 HTML 파싱이 중단된 시점으로 돌아가 다시 HTML을 파싱.
* &#x20;<mark style="color:green;">**\<script>\</script>**</mark>** 만날 때**\
  → **JS 파싱 & 실행** \
  소스 코드를 토큰으로 분해 및 파싱 → AST(추상적 구문 트리) 생성 →  바이트코드를 생성 및 실행 (인터프리터가 읽을 수 있도록)

※ 자바스크립트 코드에 DOM이나 CSSOM을 변경하는 DOM API가 사용된 경우 \
DOM이나 CSSOM이 변경 변경된 DOM과 CSSOM은 다시 렌더 트리로 결합되며 리렌더링 \
⇒ reflow(레이아웃 다시 계산), repaint(재결합된 렌더 트리를 기반으로 다시 페인트)

### 2. Render tree 생성

최종 렌더링 트리 출력 \
DOM과 CSSOM은 렌더링을 위해 렌더 트리(Render Tree)로 결합 \
브라우저 화면에 렌더링 되는 노드만으로 구성 = 보이는 것만 포함 \
제외) HTML meta 태그, CSS의 display: none 등

HTML 요소의 레이아웃(위치와 크기)을 계산하는데 사용 \
브라우저 화면에 픽셀을 렌더링 하는 페인팅 처리에 입력된다.

### 3. Layout&#x20;

브라우저가 페이지에 표시되는 각 요소의 크기, 위치 계산 → 노드 배치

### 4. Paint

노드 UI 그리기 = 실제 화면에 그리기

### 5. Composition

Render tree에 있는 node를 순서대로 구성

### 6. 웹 사용자에게 결과 화면 출력

***

## #️⃣가상돔(Virtual Dom)&#x20;

실제 DOM을 메모리에 복사해둔 것

### 가상돔을 사용하는 이유&#x20;

DOM 조작(수정되어야 할 부분)은 HTML에서 element를 찾고 제거된 후 수정된 element로 교체한다. 트리에 있는 정보를 업데이트 시킨다는 점에서 무리 있는 작업은 아니다. \
하지만 이 작업이 반복된다면 무거워진다. (문제) \
그래서 직접 브라우저에 접근하는 것이 아닌 복사본인 가상돔을 사용하여 효율성을 높인다.

### 작동 방식&#x20;

state가 변경되면 가상돔은 리렌더링되고 이전에 생긴 가상돔과 비교하여 변경된 부분만 실제 DOM에 적용시킨다.\
\- 변경된 부분을 찾는 과정: **Diffing** \
\- 변경된 부분만 실제 돔에 적용시켜 주는 것: **재조정(reconciliation)**

### 효율적인 이유&#x20;

<mark style="background-color:purple;">**Batch Update**</mark>: 변경된 모든 Element들을 <mark style="background-color:red;">**집단화**</mark>시켜 이를 <mark style="background-color:red;">**한번에**</mark> <mark style="background-color:red;"></mark><mark style="background-color:red;">실제</mark> <mark style="background-color:red;"></mark><mark style="background-color:red;">**DOM에 적용**</mark>하는 방식&#x20;

DOM조작에 비용이 가장 많이 발생하는 지점은 브라우저에 화면을 그려주는 작업인 만큼 Batch Update는 변경된 Element를 별개로 그려주는 것이 아닌, 변경된 내용을 한 번에 받아와 이를 실제 DOM에 한번에 적용시켜준다는 점이 효율적이다.

***

## 정리

이전 가상 DOM과 비교하여 변경된 부분을 식별 \
변경된 부분만을 실제 DOM에 적용 → 필요한 최소한의 DOM 조작만을 수행\
이는 불필요한 작업을 최소화하고 성능을 향상시키는데 도움이 된다.

***

참고 사이트

[\[JavaScript\] 브라우저 렌더링 과정(원리) ](https://oliviakim.tistory.com/80)
