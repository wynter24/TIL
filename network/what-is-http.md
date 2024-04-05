# ↕️ What is HTTP?

## #️⃣HTTP(**HyperText** Transfer Protocol)&#x20;

웹브라우저와 서버 간에 데이터를 주고 받기 위해(웹 통신) 사용하는 \*프로토콜

* 클라이언트 ← (응답) HTTP 메세지 (요청) → 서버

_\*프로토콜: 네트워크 통신에 사용되는 통신 규약_



### 특징

#### **▸** 요청과 응답 메시지의 형식이 다름

<figure><img src="../.gitbook/assets/image (8).png" alt="" width="563"><figcaption></figcaption></figure>

<details>

<summary>요청과 응답 메시지 구조</summary>

**1. start line**

start line에는 **요청이나 응답의 상태**

* **항상 첫 번째 줄**에 위치한다.
* **응답에서는 status line**이라고 부른다.

#### **2. HTTP headers**

**요청을 지정**하거나, 메시지에 포함된 **본문을 설명하는 헤더의 집합**

#### **3. empty line**

**헤더와 본문을 구분하는 빈 줄**

#### **4. body**

* **요청과 관련**된 데이터나 **응답과 관련**된 **데이터 또는 문서를 포함**한다.
* **요청과 응답의 유형**에 따라 **선택적으로 사용**한다.

start line과 HTTP headers를 묶어 요청이나 응답의 헤드(head)라고 한다. \
payload는 body라고 한다.

</details>

<details>

<summary>요청(Request) 메시지</summary>

<img src="../.gitbook/assets/image (10).png" alt="" data-size="original">

**Method** : HTTP [메서드](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods)\
보통 클라이언트가 수행하고자 하는 동작을 정의한 `GET`, `POST`, `OPTIONS`, `HEAD`를 의미한다. 일반적으로, 클라이언트는 리소스를 가져오거나(`GET`) HTML 폼의 데이터를 전송(`POST`)한다.\
다른 경우에는 다른 동작이 요구될 수도 있다.

**Path** : 가져오려는 리소스의 경로\
프로토콜 `http://`, 도메인 (위 예제에서) `developer.mozilla.org`, 또는 TCP 포트 `80`인 요소들을 제거한 리소스의 URL이다.

**Version of the Protocol** : HTTP 프로토콜의 버전.

**Headers** : 서버에 대한 추가 정보를 전달하는 선택적 헤더들.

**etc** : POST와 같은 몇 가지 메서드를 위한, 전송된 리소스를 포함하는 응답의 본문과 유사한 본문.

</details>

<details>

<summary>응답(Response) 메시지</summary>

![](<../.gitbook/assets/image (12).png>)

**Version of the Protocol** : HTTP 프로토콜의 버전.

**Status Code** : 요청의 성공 여부와, 그 이유를 나타내는 상태 코드.

**Status Message** : 아무런 영향력이 없는, 상태 코드의 짧은 설명을 나타내는 상태 메시지.&#x20;

**Headers** : 요청 헤더와 비슷한, HTTP 헤더들.

**etc** : 선택 사항으로, 가져온 리소스가 포함되는 본문.

</details>

#### **▸** <mark style="background-color:orange;">무상태 프로토콜</mark> (ex. IP, UDP)&#x20;

상태를 가지지 않는다(stateless). = 이전 데이터 정보 확인X (기억X)&#x20;

다시 말해 서버가 여러 클라이언트들을 구별할 수 없다.

**- 장점**

* 불특정 다수를 대상으로 하는 서비스에 적합하다.
* 클라이언트와 서버가 최대 연결 수 보다 훨씬 많은 요청과 응답을 처리할 수 있다.

**- 단점**

* 연결이 끊어진 후에는 클라이언트가 이전에 무엇을 했는지 알 수 없다.\
  ⇒ 쿠키나 세션에 저장하여 상태를 유지할 수 있다.

> ↔ 상태 프로토콜 ex. TCP &#x20;

#### **▸** <mark style="background-color:orange;">비연결성</mark>(connectionless)&#x20;

실제로 요청을 주고 받을 때만 연결을 유지하고 응답을 주고 나면 서버와의 연결을 끊는다.

{% hint style="info" %}
HTTP 프로토콜은 각 요청 간에 독립적으로 처리되도록 하며, 서버는 이전 요청에 대한 상태를 유지하지 않는다.&#x20;

즉, 클라이언트가 서버에 요청을 보내면 서버는 해당 요청에 대한 응답을 보내고 연결을 끊는다.
{% endhint %}



### 요청 메서드(총 9가지)&#x20;

Get: 데이터 가져옴&#x20;

Post: 데이터 전송 to 서버 / 수정·삭제 가능&#x20;

Patch: 서버에게 지정한 URL의 데이터를 '부분적으로' 수정&#x20;

Put: 데이터 '전체' 수정

Delete: 서버에게 지정한 URL의 정보 삭제&#x20;

Head: HTTP 헤더 정보만 요청 (get보다 빠름 - 서버 상태 미리 확인할 때)&#x20;

Option: 해당 URL에서 지원하는 요청 메세지의 목록을 요청 ( = 사용 가능 메서드 확인)

(잘 사용하지 않는 메서드)\
Connect: 특정 종류의 프록시 서버에게 연결 요청 (양뱡향 연결 시작) \
Trace: 서버에게 송신한 요청의 내용 반환 요청 / 특정 데이터 경로 조회

***

### HTTP의 단점&#x20;

HTTP는 **암호화되지 않은 데이터를 전송**한다.&#x20;

즉, 브라우저에서 전송된 정보를 제3자가 가로채고 읽을 수 있다. 이 때문에 통신에 또 다른 보안 계층을 추가하기 위해 \*HTTPS로 확장되었다.&#x20;

보통 클라이언트와 서버 간의 모든 커뮤니케이션을 암호화 하기 위하여 [SSL](https://developer.mozilla.org/ko/docs/Glossary/SSL) 또는 [TLS](https://developer.mozilla.org/ko/docs/Glossary/TLS) 사용한다.

_\*HTTPS(HyperText Transfer Protocol Secure) : HTTP protocol의 암호화된 버전_



### HTTP보다 HTTPS를 선택해야 하는 이유 <a href="#seo-faq-pairs-why-choose-https-over-http" id="seo-faq-pairs-why-choose-https-over-http"></a>

#### **1. 보안**

HTTP 메시지 일반 텍스트이므로, 권한이 없는 당사자가 인터넷을 통해 쉽게 액세스하고 읽을 수 있다.&#x20;

반면, <mark style="color:green;background-color:yellow;">HTTPS</mark>는 모든 데이터를 <mark style="color:green;background-color:yellow;">암호화된 형태로 전송</mark>한다. \
사용자가 민감한 데이터를 제출할 때 제3자가 네트워크를 통해 해당 데이터를 가로챌 수 없다.&#x20;

신용카드 세부 정보 또는 고객 개인 정보와 같은 잠재적으로 민감한 정보를 보호하려면 HTTPS를 선택하는 것이 좋다.

#### **2. 권위**

검색 엔진은 HTTP의 신뢰성이 더 낮기 때문에 보통 HTTP 웹 사이트 콘텐츠의 순위를 HTTPS 웹 페이지보다 낮게 지정한다. 고객도 HTTP보다 HTTPS 웹 사이트를 더 선호한다.&#x20;

브라우저는 브라우저 주소 표시줄에서 웹 사이트 URL 옆에 있는 자물쇠 아이콘을 배치하여 사용자에게 HTTPS 연결을 표시한다. 사용자는 이러한 추가 보안 및 신뢰 요소 때문에 HTTPS 웹 사이트 및 애플리케이션을 선호한다.

#### **3. 성능 및 분석**

HTTPS 웹 애플리케이션은 HTTP 애플리케이션보다 <mark style="color:blue;background-color:purple;">로드 속도</mark>가 더 <mark style="color:blue;background-color:purple;">빠르다</mark>. \
<mark style="color:blue;background-color:purple;">참조 링크</mark>도 더 <mark style="color:blue;background-color:purple;">잘 추적</mark>한다.&#x20;

제 3자가 발생한 \*추천 트래픽은 동의 없이 사용자의 웹브라우징 활동을 추적해 표적 광고에 이용하는 문제가 있다. 따라서 분석 소프트웨어가 신뢰할 수 있는 트래픽 소스를 정확하게 식별하도록 하려면 HTTPS를 활성화해야 한다.

_\*추천 트래픽 : 광고 또는 소셜 미디어 백링크와 같은 서드 파티 소스에서 생성되는 웹 사이트 트래픽_



### &#x20;HTTP와 HTTPS의 차이점&#x20;

|         | HTTP                                               | HTTPS                                            |
| ------- | -------------------------------------------------- | ------------------------------------------------ |
| 의미      | Hypertext Transfer Protocol                        | Hypertext Transfer Protocol Secure               |
| 기본 프로토콜 | HTTP/1과 HTTP/2는 TCP/IP를 사용. HTTP/3은 QUIC 프로토콜을 사용. | HTTP 요청 및 응답을 추가로 암호화하기 위해 SSL/TLS와 함께 HTTP/2 사용 |
| 포트      | 기본 포트 80                                           | 기본 포트 443                                        |
| 용도      | 이전 텍스트 기반 웹 사이트                                    | 모든 최신 웹 사이트                                      |
| 보안      | 추가 보안 기능 없음                                        | 퍼블릭 키 암호화에 SSL 인증서 사용                            |
| 이점      | 인터넷을 통한 통신 지원                                      | 웹 사이트에 대한 권위, 신뢰성 및 검색 엔진 순위 개선                  |

<details>

<summary>HTTP/1, HTTP/2,  HTTP/3 차이점</summary>

**HTTP/1.1** &#x20;

1996\~1997년에 출시된 최초의 HTTP 버전&#x20;

**HTTP/2와 HTTP/3**&#x20;

프로토콜 자체를 업그레이드한 버전 \
데이터 전송 시스템을 수정하면서 효율성을 개선했다. \
예를 들어, HTTP/2는 텍스트 형식 대신, 바이너리로 데이터를 교환한다. 또한, 서버가 새 HTTP 요청을 기다리는 대신, 클라이언트 캐시에 응답을 사전에 전송할 수 있다.&#x20;

**HTTP/3**&#x20;

비교적 최근에 나온 버전이며, HTTP/2를 한 단계 더 발전시킨 것 \
HTTP/3의 목표는 실시간 스트리밍 및 기타 최신 데이터 전송 요구 사항을 보다 효율적으로 지원하는 것이다.

HTTPS는 HTTP에서 데이터 보안 문제를 우선시한다. 최신 시스템에서는 SSL/TLS와 함께 HTTP/2를 HTTPS로 사용한다. HTTP/3이 더욱 발전하면 브라우저 및 서버 기술도 결국 HTTPS에 통합될 것이다.

</details>

***

참고 자료

[MDN - HTTP개요](https://developer.mozilla.org/ko/docs/Web/HTTP/Overview#http\_%EA%B8%B0%EB%B0%98\_api)

[MDN - HTTPS](https://developer.mozilla.org/ko/docs/Glossary/HTTPS)

[\[ 웹(WWW) 기본 개념 \] URL, HTTP, IP, 도메인, 포트](https://all-young.tistory.com/20)

[HTTP와 HTTPS의 차이점은 무엇인가요?](https://aws.amazon.com/ko/compare/the-difference-between-https-and-http/)
