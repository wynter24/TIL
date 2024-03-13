# 🟨 What is Firebase?

## #️⃣Firebase란?

구글(Google)이 소유하고 있는 모바일 애플리케이션 개발 플랫폼

**서비스형 백엔드**(**BaaS**, [backend as a service](https://en.wikipedia.org/wiki/Mobile\_backend\_as\_a\_service)) or **서비스형 플랫폼**(**PaaS**, [platform as a service](https://en.wikipedia.org/wiki/Platform\_as\_a\_service))이라고도 한다.&#x20;

\-> Apple, Android, JavaScript, C++ 등을 위한 SDK를 제공하여 프론트엔드 개발에 집중하면서 백엔드에서 인프라를 쉽게 확장할 수 있는 플랫폼

~~Firebase 개발자~~ [~~Doug Stevenson~~](https://medium.com/@CodingDoug?source=user\_profile-------------------------------------) ~~저렇게 분류하고 싶지 않다고 한다. Firebase는 그냥 firebase...~~ \
~~그냥 전반적인 기능이 저렇고 쉽게 이해하기 위해 썼다.~~

***

### ⚒️핵심 기능&#x20;

* 데이터베이스 관리, 파일 스토리지, 클라우드 코드, 분석, 확장 가능한 호스팅 및 머신 러닝이 포함하고 있다.
* 클라우드 호스팅 서비스이므로 개발자는 백엔드 코딩 없이 거의 전적으로 온디맨드 확장을 수행할 수 있다.

#### 지원 환경

iOS / 안드로이드(Android) / 웹(web) 기반의 개발 / 플러터(Flutter) / 유니티(Unity) / C++

#### 제품

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="563"><figcaption></figcaption></figure>

개발하기, 개선하기, 키워가기 중에&#x20;

**개발하기 알아보기**

1. 인증(Authentication): 사용자 로그인 및 ID 관리
2. 클라우드 함수(Cloud Functions): 서버 없이 이벤트 위주로 동작하는 백엔드
3. 클라우드 파이어스토어(Cloud Firestore): 클라우드에 호스팅 된 실시간의 비관계형(NoSQL) 데이터베이스
4. 클라우드 스토리지(Cloud Storage): 거대하게 확장할 수 있는 파일 스토리지
5. 파이어베이스 호스팅(Firebase Hosting): 전 세계를 대상으로 한 웹 호스팅
6. 머신러닝 키트(ML Kit): 일반적인 머신러닝(ML) 작업을 위한 SDK
7. 실시간 데이터베이스(Realtime Database): 클라우드에 호스팅 된 실시간의 비관계형(NoSQL) 데이터베이스

***

### 🧐사용하는 이유

* 인증, 배포 등을 쉽게 할 수 있고 푸시 알림, 스토리지, 실시간 데이터베이스, 호스팅 등 사용 가능
* 파이어베이스가 제공하는 클라이언트 \*SDK가 이런 백엔드 구성요소들과 직접 상호작용 하며, 우리가 만든 앱과 서비스 사이에는 그 어떤 \*미들웨어도 구축할 필요가 없다.
* <mark style="background-color:orange;">쉽게 말해 백엔드(Node.js, DB, soket.io)부분을 firebase로 손쉽게 구성할 수 있다. (간단, 편함)</mark>

\*_SDK(Software development kit): 소프트웨어 개발 도구_

_\*미들웨어(middleware): 소프트웨어와 그것이 운영되는 환경 사이에서 원활하게 통신이 이루어질 수 있도록 도와주는 시스템_

#### 기존 방식과 Firebase의 차이점

<figure><img src="../.gitbook/assets/image.png" alt="" width="563"><figcaption><p>전통 방식과 Firebase 비교</p></figcaption></figure>

**전통적인 방법**

일반적으로 프론트엔드와 백엔드 양쪽 모두에서 쿼리를 작성해야만 했다. 프론트엔드의 코드는 백엔드의 API(응용프로그램 인터페이스)만을 호출할 뿐, 실제로 작업을 수행하는 것은 백엔드의 코드이다.

**Firebase**

이러한 백엔드 쪽의 작업을 건너뛰고, 그 일을 클라이언트(단말) 쪽으로 넘길 수 있다. 이러한 관리자 기능은 ‘firebase’의 콘솔(console, 입출력 도구) 창을 통해서 수행할 수 있다.

***

참고사이트

['파이어베이스'(Firebase)란 무엇인가?](https://blog.wishket.com/%ED%8C%8C%EC%9D%B4%EC%96%B4%EB%B2%A0%EC%9D%B4%EC%8A%A4firebase%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-%ED%8C%8C%EC%9D%B4%EC%96%B4%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%8B%AC%EC%B8%B5-%ED%83%90-2/)

[What is Firebase? The complete story, abridged.](https://medium.com/firebase-developers/what-is-firebase-the-complete-story-abridged-bcc730c5f2c0)&#x20;

[Firebase란 무엇입니까?](https://developer.oracle.com/ko/learn/technical-articles/what-is-firebase)
