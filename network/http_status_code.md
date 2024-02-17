# HTTP 상태코드

상태코드는 클라이언트의 요청에 따른 서버의 응답 상태를 세 자리 숫자로 나타낸 것입니다.



먼저 첫 번째 숫자에 따라 5개의 클래스로 구분합니다.

* **1XX: Informational(정보 제공)**
  * 조건부 응답으로, 서버가  현재의 요청을 받았으며 작업을 계속 진행하고 있다는 의미입니다.
  * HTTP/1.1 클라이언트에게만 보낼 수 있으며 응답은 바디 없이 상태 라인, 헤더(생략 가능), 빈 줄로 종료됩니다.
* **2XX: Success(성공)**
  * 클라이언트의 요청이 서버에서 성공적으로 처리되었다는 의미입니다.
* **3XX: Redirection(리다이렉션)**
  * 완전한 처리를 위해서 추가 동작(재전송)이 필요한 경우입니다.&#x20;
  * 예를 들어 공유용 짧은 주소로 접근하면 3XX 클래스상태 코드로 응답하고, 헤더에 긴 URI 값은 넣어 전달합니다.
* **4XX: Client Error(클라이언트 에러)**
  * 클라이언트 측에 오류가 있음을  의미합니다.
* **5XX: Server Error(서버 에러)**
  * 서버가 요청을 수행하지 못한 경우입니다.&#x20;
  * 서버의 부하, DB 처리 과정 오류, 서버에서 exception(예외)이 발생하는 경우를 의미합니다.

***

## **1XX: Informational(정보 제공)**

<table><thead><tr><th width="123">상태 코드</th><th width="179">상태 텍스트</th><th width="139">한국어 뜻</th><th>서버 측면에서의 의미</th></tr></thead><tbody><tr><td>100</td><td>Continue</td><td>계속</td><td><p><strong>계속 진행해라.</strong></p><p>서버가 첫 번째 요청을 받았으며 클라이언트가 계속해서 요청을 하거나 이미 요청을 완료한 경우에는 무시해도 되는 것을 알려줍니다.</p></td></tr><tr><td>101</td><td>Switching Protocols</td><td>프로토콜 전환</td><td><strong>프로토콜을 전환하라.</strong><br>프로토콜을 HTTP 1.1에서 업그레이드할 때 Upgrade 응답 헤더에 표시합니다. 현재는 HTTP 1.1이 최신이므로 사용할 일이 없습니다.</td></tr><tr><td>102</td><td>Processing</td><td>처리중</td><td><strong>(WebDAV) 처리 중이다.</strong><br>서버가 처리하는 데 오랜 시간이 예상되어 클라이언트에서 타임 아웃이 발생하지 않도록 이 응답 코드를 보냅니다.<br>쉽게 말해 서버가 요청을 수신하여 이를 처리하고 있지만, 아직 제대로 된 응답을 알려줄 수 없음을 알려줍니다.</td></tr><tr><td>103 ~ 199</td><td>Unassigned</td><td> </td><td>현재 할당되지 않은 상태 코드입니다.</td></tr></tbody></table>



## **2XX: Success(성공)**

<table><thead><tr><th width="123">상태 코드</th><th width="173">상태 텍스트</th><th width="149">한국어 뜻</th><th>서버 측면에서의 의미</th></tr></thead><tbody><tr><td><mark style="background-color:green;"><strong>200</strong></mark></td><td>OK</td><td>성공</td><td><strong>서버가 요청을 성공적으로 처리.</strong></td></tr><tr><td><mark style="background-color:green;"><strong>201</strong></mark></td><td>Created</td><td>생성됨</td><td><strong>요청이 처리되어 새로운 리소스 생성.</strong><br>데이터가 생성 되었음을 의미하며 POST 요청 또는 일부 PUT 요청 이후 나타납니다.</td></tr><tr><td><mark style="background-color:orange;"><strong>202</strong></mark></td><td>Accepted</td><td>허용됨</td><td><strong>요청은 접수했지만, 처리가 완료X.</strong><br>응답 헤더의 Location, Retry-After를 참고하여 클라이언트는 다시 요청을 보냅니다.</td></tr><tr><td>203</td><td>Non-Authoritative<br>Information</td><td>신뢰할 수 없는<br>정보</td><td><strong>응답 헤더가 오리지널 서버로부터 제공된 것이 아니다.</strong><br>프록시 서버가 응답 헤더에 주석을 덧붙인 경우가 하나의 예입니다.</td></tr><tr><td>204</td><td>No Content</td><td>콘텐츠 없음</td><td><strong>처리를 성공하였지만, 클라이언트에게 돌려줄 콘텐츠가 없다.</strong><br>응답에는 헤더만 있고 바디는 없습니다. DELETE 요청에 대한 응답에 많이 사용됩니다.</td></tr><tr><td>205</td><td>Reset Content</td><td>콘텐츠 재설정</td><td><strong>처리 성공! 브라우저의 화면을 리셋해.</strong><br>예를 들어 브라우저가 입력 폼을 보여 주고 있을 때 이 응답 코드를 받으면 브라우저는 모든 입력 항목을 리셋하고 재입력  할 수 있는 상태가 됩니다.</td></tr><tr><td>206</td><td>Partial Content</td><td>일부 콘텐츠</td><td><strong>콘텐츠의 일부만을 보낸다.</strong><br>응답 헤더의 Content-Range에 응답 콘텐츠의 범위를 기록합니다. 예를 들어 1,500 바이트의 리소스 중에서 처음의 500바이트만을 보낼 때 사용할 수 있습니다.</td></tr><tr><td>207</td><td>Multi-Status</td><td>다중 상태</td><td><strong>(WebDAV) 처리 결과의 상태가 여러 개이다.</strong><br>207 응답은 성공을 뜻하지만, 각각의 처리 결과가 성공인지는 바디를 봐야 알 수 있습니다.</td></tr><tr><td>208 ~ 299</td><td>Unassigned</td><td> </td><td>현재 할당되지 않은 상태 코드입니다.</td></tr></tbody></table>



## **3XX: Redirection(리다이렉션)**

<table data-full-width="false"><thead><tr><th width="122">상태 코드</th><th width="167">상태 텍스트</th><th width="150">한국어 뜻</th><th>서버 측면에서의 의미</th></tr></thead><tbody><tr><td>300</td><td>Multiple Choices</td><td>여러 선택항목</td><td><strong>선택 항목이 여러 개 있다.</strong><br>지정한 URI에 대해서 콘텐츠 협상을 수행한 결과 서버에서 콘텐츠를 결정하지 못하고 클라이언트에게 복수 개의 링크를 응답할 때 사용 (반드시 하나 선택).</td></tr><tr><td><strong>301</strong></td><td>Moved Permanently</td><td>영구 이동</td><td><strong>요청한 리소스의 URI가 변경됨을 의미.</strong><br>리디렉션 상태 응답 코드는 요청한 리소스가 <code>Location</code> 헤더에 주어진 URL로 완전히 옮겨졌습니다.</td></tr><tr><td>302</td><td>Found</td><td>다른 위치 찾음</td><td><strong>요청한 리소스를 다른 URI에서 찾았다.</strong> <br>헤더에 지정된 URL로 일시적으로 이동되었음을 나타냅니다.<br><a href="https://developer.mozilla.org/ko/docs/Web/HTTP/Methods/GET"><code>GET</code></a> 또는 <a href="https://developer.mozilla.org/ko/docs/Web/HTTP/Methods/HEAD"><code>HEAD</code></a> 메서드에 대한 응답으로만 설정하고 이 경우 메서드 변경이 명시적으로 금지되므로 307를 대신 사용하는 것이 좋습니다.</td></tr><tr><td><strong>303</strong></td><td>See Other</td><td>다른 위치 보기</td><td><strong>다른 위치로 요청하라.</strong><br>클라이언트가 요청한 리소스를 다른 URI에서 GET 요청을 통해 얻어야 할 때, 서버가 클라이언트로 직접 보내는 응답입니다.</td></tr><tr><td>304</td><td>Not Modified</td><td>수정되지 않음</td><td><strong>마지막 요청 이후 요청한 페이지 수정되지 않았다.</strong><br>캐시를 목적으로 사용되며 클라이언트에게 응답이 수정되지 않았음을 알려줍니다. 그러므로 클라이언트는 계속해서 응답의 캐시된 버전을 사용할 수 있습니다. 이 응답 코드에는 바디가 없습니다.</td></tr><tr><td>305</td><td>Use Proxy</td><td>프록시 사용</td><td><strong>지정한 리소스에 액세스하려면 프록시를 통해야 한다.</strong><br>응답 헤더 Location에 프록시의 URI를 기록합니다.</td></tr><tr><td>306</td><td>(Unused)</td><td> </td><td>예전 버전에서 사용하다가 현재는 사용하지 않는 상태 코드입니다.</td></tr><tr><td><mark style="background-color:orange;"><strong>307</strong></mark></td><td>Temporary Redirect</td><td>임시 리다이렉션</td><td><strong>임시로 redirect 요청이 필요하다.</strong><br>기존 페이지에서 접속 이슈로 임시로 생성한 새로운 URL로 redirect하고 싶을 때 사용합니다.</td></tr><tr><td><mark style="background-color:orange;"><strong>308</strong></mark></td><td>Permanent Redirect</td><td>영구 리다이렉션</td><td><strong>HTTP 응답 헤더의 <code>Location:</code> 에 영구히 다른 URI에 위치하고 있다.</strong><br>기존 접속자를 새로 생성한 URL로 redirect할 때 사용합니다.</td></tr><tr><td>309~399</td><td>Unassigned</td><td> </td><td>현재 할당되지 않은 상태 코드입니다.</td></tr></tbody></table>

```
301, 302 대신 307, 308을 사용하는 이유

301, 302는 redirect시킬때 최초의 요청 방법 (GET or POST)을 유지하지 않고  
무조건 GET 으로 변경하고 body를 버립니다. 이때 예상치 못한 일들이 발생할 수 있습니다.

반면307, 308은 기존 method (GET, POST)를 유지하면서 body를 버리지 않습니다.
따라서 사용한 요청방법을 유지하기 위해 307, 308을 사용합니다.
```

{% embed url="https://velog.io/@himprover/Nextjs-Redirect-%EC%98%B5%EC%85%98%EC%97%90-Permanent%EB%8A%94-%EB%AD%90%EC%A7%80" %}
참고 사이트
{% endembed %}



## **4XX: Client Error(클라이언트 에러)**

<table><thead><tr><th width="123">상태 코드</th><th width="158">상태 텍스트</th><th width="160">한국어 뜻</th><th>서버 측면에서의 의미</th></tr></thead><tbody><tr><td>400</td><td>Bad Request</td><td>잘못된 요청</td><td><strong>클라이언트의 요청 내용이 잘못되었다.</strong><br>잘못된 문법으로 인하여 서버가 요청을 이해할 수 없음을 의미합니다.</td></tr><tr><td><mark style="background-color:red;"><strong>401</strong></mark></td><td>Unauthorized</td><td>권한 없음</td><td><strong>지정한 리소스에 대한 액세스 권한이 없다.</strong><br>클라이언트는 요청한 응답을 받기 위해서는 반드시 스스로를 인증해야 합니다. 응답 헤더 WWW-Authenticate에 필요한 인증 방식을 지정합니다.</td></tr><tr><td>402</td><td>Payment Required</td><td>결제 필요</td><td><strong>지정한 리소스를 액세스하기 위해서는 결제가 필요하다.</strong><br>디지털 결제 시스템에 사용하기 위하여 만들어졌지만 지금 사용되고 있지는 않습니다.</td></tr><tr><td><mark style="background-color:red;"><strong>403</strong></mark></td><td>Forbidden</td><td>금지됨</td><td><strong>클라이언트는 콘텐츠에 접근할 권리를 가지고 있지 않습니다.</strong> <br>예를 들어 미승인  되었을 때 서버는 거절을 위한 응답을 보냅니다. <br>401과 다른 점은 서버는 클라이언트가 누구인지 알고 있다는 것입니다.</td></tr><tr><td><mark style="background-color:red;"><strong>404</strong></mark></td><td>Not Found</td><td>찾을 수 없음</td><td><p><strong>서버는 요청 받은 리소스를 찾을 수 X.</strong><br>서버 자체는 존재하지만 서버에서 요청한 것을 찾을 수 없을 때 나타납니다.</p><p>사용자가 요청하는 페이지나 파일을 찾을 수 없을 때 가장 많이 발생합니다.</p><p>가장 자주 발생하는 원인은 페이지가 이동되거나 삭제된 경우입니다.<br>서버들은 인증받지 않은 클라이언트로부터 리소스를 숨기기 위하여 이 응답을 403 대신에 전송할 수도 있습니다!</p></td></tr><tr><td>405</td><td>Method Not Allowed</td><td>허용되지 않은<br>메소드</td><td><strong>요청한 URI가 지정한 메소드를 지원하지 않는다.</strong><br>요청한 메소드는 서버에서 알고 있지만, 제거되어 사용할 수 없습니다.</td></tr><tr><td>406</td><td>Not Acceptable</td><td>수용할 수 없음</td><td><strong>헤더값 존재X -> 사람 접속X 라고 판단</strong><br>접속자가 사람임을 알리기 위해 헤더 값을 입력해야 합니다.</td></tr><tr><td>407</td><td>Proxy Authentication<br>Required</td><td>프록시 인증 필요</td><td><strong>클라이언트는 프록시 서버에 인증이 필요하다.</strong><br>401과 비슷하지만 프록시에 의해 완료된 인증이 필요합니다.</td></tr><tr><td>408</td><td>Request Timeout</td><td>요청 시간 초과</td><td><strong>요청 기다리다 서버에서 타임 아웃  함.</strong></td></tr><tr><td>409</td><td>Conflict</td><td>충돌</td><td><strong>서버가 요청 수행 중에 충돌 발생.</strong><br>예를 들어 사용자명을 new_name으로 변경하려 했지만, 서버에 이미 new_name이라는 사용자가 존재하는 경우입니다. 응답 헤더 Location에는 충돌이 발생한 리소스의 URI 기록.</td></tr><tr><td>410</td><td>Gone</td><td>사라짐</td><td><strong>지정한 리소스가 이전에는 존재하였지만, 현재는 존재하지 않는다.</strong><br>예를 들어 기간이 한정된 프로모션 사이트가 사라진 경우 사용할 수 있는 응답 코드입니다.</td></tr><tr><td>411</td><td>Length Required</td><td>길이 필요</td><td><strong>요청 헤더에 Content-Length를 지정해야 한다.</strong></td></tr><tr><td>412</td><td>Precondition Failed</td><td>사전 조건 실패</td><td><strong>클라이언트의 헤더에 있는 전제조건이 서버와 맞지 않는다.</strong></td></tr><tr><td>413</td><td>Request Entity<br>Too Large</td><td>요청 객체가<br>너무 큼</td><td><strong>요청 메시지가 너무 크다.</strong><br>서버는 접속을 끊거나 <code>Retry-After</code> 헤더 필드로 돌려보냅니다.</td></tr><tr><td>414</td><td>Request-URI<br>Too Large</td><td>요청 URI가<br>너무 긺</td><td><strong>요청 URI가 너무 길다.</strong></td></tr><tr><td>415</td><td>Unsupported<br>Media Type</td><td>지원되지 않는<br>미디어 유형</td><td><strong>클라이언트가 지정한 미디어 타입을 서버가 지원하지 않는다.</strong><br>예를 들어 서버가 지원하는 이미지는 JPG, PNG뿐인데 클라이언트가 GIF 형식의 이미지를 요청하는 경우입니다.</td></tr><tr><td>416</td><td>Range Not Satisfiable</td><td>처리할 수 없는<br>요청 범위</td><td><strong>클라이언트가 지정한 리소스의 범위가 서버의 리소스 사이즈와 맞지 않는다.</strong></td></tr><tr><td>417</td><td>Expectation Failed</td><td>예상 실패</td><td><strong>클라이언트가 지정한 Expect 헤더를 서버가 이해할 수 없다.</strong></td></tr><tr><td>418 </td><td>I'm a teapot</td><td> 만우절 장난</td><td><strong>서버가 찻주전자이기 때문에 커피 내리기를 거절했다.</strong></td></tr><tr><td>421</td><td>Misdirected Request</td><td>잘못된 요청</td><td><strong>요청이 응답을 생성할 수 없는 서버로 전달되었다.</strong><br>연결을 재사용하거나 대체 서비스를 선택한 경우</td></tr><tr><td>422</td><td>Unprocessable Entity</td><td>처리할 수 없는<br>엔티티</td><td><strong>(WebDAV) 클라이언트가 송신한 XML이 구문은 맞지만, 의미상 오류가 있다.</strong></td></tr><tr><td>423</td><td>Locked</td><td>잠김</td><td>(WebDAV) 지정한 리소스는 잠겨있다.</td></tr><tr><td>424</td><td>Failed Dependency</td><td>의존 관계로 실패</td><td><strong>(WebDAV) 다른 작업의 실패로 인해 본 요청도 실패하였다.</strong></td></tr><tr><td>426</td><td>Upgraded Required</td><td>업그레이드 필요</td><td><strong>클라이언트의 프로토콜의 업그레이드가 필요하다.</strong><br>응답에 Upgrade 헤더를 보내 필요한 프로토콜을 알려 줍니다.</td></tr><tr><td>428</td><td>Precondition Required</td><td>사전 조건 필요</td><td><strong>If-Match와 같은 사전조건을 지정하는 헤더가 필요하다.</strong><br>If-Match 헤더가 있지만, 맞지 않는 경우는 412 응답을 보냅니다.</td></tr><tr><td>429</td><td>Too Many Requests</td><td>너무 많은 요청</td><td><strong>클라이언트가 주어진 시간 동안 너무 많은 요청을 보냈다.</strong><br>요청의 속도를 제한할 때 사용합니다.  응답에 Retry-After 헤더를 보내 얼마나 기다릴지를 알려 줄 수 있습니다.</td></tr><tr><td>431</td><td>Request Header Fields Too Large</td><td>너무 큰 헤더</td><td><strong>헤더의 길이가 너무 크다.</strong><br>헤더의 전체 크기가 크거나 또는 하나의 헤더가 매우 큰 경우입니다. 보통 Referer URL이 길거나 쿠키 항목이 많은 경우입니다.</td></tr><tr><td>444</td><td>Connection Closed Without Response</td><td>응답 없이<br>연결 닫음</td><td>(NGINX) 응답을 보내지 않고 연결을 종료하였다.<br>보통 악의적인 요청에 대해서 사용하며 클라이언트에서는 응답을 볼 수 없고 Nginx 로그에는 나타납니다.</td></tr><tr><td>451</td><td>Unavailable For Legal Reasons</td><td>법적 사유로 불가</td><td>법적으로 문제가 있는 리소스 요청함.</td></tr><tr><td>452 ~ 499</td><td>Unassigned</td><td> </td><td>현재 할당되지 않은 상태 코드입니다.</td></tr></tbody></table>



## **5XX: Server Error(서버 에러)**

<table><thead><tr><th width="122">상태 코드</th><th width="163">상태 텍스트</th><th width="182">한국어 뜻</th><th>서버 측면에서의 의미</th></tr></thead><tbody><tr><td><mark style="background-color:orange;"><strong>500</strong></mark></td><td>Internal Server Error</td><td>내부 서버 오류</td><td><strong>서버에 에러가 발생하였다.</strong><br>서버 에러를 총칭하는 (catch-all) 일반적인 응답입니다.<br>이는 보통 서버가 응답할 좀 더 좋은 5xx 에러 코드를 찾지 못한것을 의미합니다.</td></tr><tr><td><mark style="background-color:orange;"><strong>501</strong></mark></td><td>Not Implemented</td><td>구현되지 않음</td><td><strong>요청한 URI의 메소드에 대해 서버가 구현되어 있지 않다.</strong></td></tr><tr><td><mark style="background-color:orange;"><strong>502</strong></mark></td><td>Bad Gateway</td><td>불량 게이트웨이</td><td><strong>게이트웨이(</strong>서로 다른 프로토콜을 연결해주는 장치) <strong>또는 프록시 역할을 하는 서버가</strong> 잘못된 프로토콜을 연결하거나, 어느쪽 프로토콜에 문제가 있어 통신이 제대로 되지 않을 때 발생하는 코드입니다.</td></tr><tr><td>503</td><td>Service Unavailable</td><td>서비스 제공불가</td><td><strong>현재 서버에서 서비스를 제공할 수 없다.</strong><br>보통은 서버의 과부하나 서비스 점검 등 일시적인 상태입니다.</td></tr><tr><td>504</td><td>Gateway Timeout</td><td>게이트웨이 시간초과</td><td><strong>게이트웨이 또는 프록시 역할을 하는 서버가 upstream 서버로부터 응답을 기다리다 타임아웃이 발생.</strong></td></tr><tr><td>505</td><td>HTTP Version Not Supported</td><td>HTTP 버전<br>미지원</td><td><strong>클라이언트가 요청에 사용한 HTTP 버전을 서버가 지원하지 X.</strong></td></tr><tr><td>506</td><td>Variant Also Negotiates</td><td> 변형 또한 협상</td><td><p><strong>서버에 내부 구성 오류가 있다.</strong> </p><p>선택한 변형 리소스가 투명한 콘텐츠 협상 자체에 참여하도록 구성되었으므로 협상 프로세스의 적절한 종료 지점이 아닙니다.</p></td></tr><tr><td>507</td><td>Insufficient Storage</td><td>용량 부족</td><td><strong>(WebDAV) 서버에 저장 공간 부족으로 처리에 실패하였다.</strong></td></tr><tr><td>508</td><td>Loop Detected</td><td>루프 탐지</td><td>서버가 요청을 처리하는 동안 무한 루프를 감지</td></tr><tr><td>509</td><td>Not Extended</td><td>확장되지 않음</td><td>서버가 요청을 이행하려면 요청에 대한 추가 확장이 필요</td></tr><tr><td>511</td><td>Network Authentication Required</td><td>네트워크 인증 필요</td><td>클라이언트가 네트워크 액세스를 얻기 위해 인증을 받아야 한다.</td></tr><tr><td>512 ~ 599</td><td>Unassigned</td><td> </td><td>현재 할당되지 않은 상태 코드.</td></tr></tbody></table>



{% embed url="https://developer.mozilla.org/ko/docs/Web/HTTP/Status#%EC%84%B1%EA%B3%B5_%EC%9D%91%EB%8B%B5" %}
참고 사이트
{% endembed %}

