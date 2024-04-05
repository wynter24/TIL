# 👩‍🔧 Firebase로 구글 로그인하기

## 프로젝트 생성

#### 1. Firebase와 연결하기

* [Firebase 훔페이지](https://firebase.google.com/?\_gl=1\*10vm6s0\*\_up\*MQ..\*\_ga\*MzExNTk1MDEwLjE3MTAyNTM1NDA.\*\_ga\_CW55HF8NVT\*MTcxMDI1MzU0MC4xLjAuMTcxMDI1NDA5NC4wLjAuMA..\&hl=ko)에서 프로젝트 생성
  * 상단에 Go to console 클릭
* 원하는 앱 클릭(ios/android/web)
* vscode에 firebase 설치
  * 여기서부터 사이트에서  보여주는 코드 복붙하면 된다.
* src 폴더 아래 firebase.js 파일 생성해서 코드 복붙하고 마지막 줄에 export default app 입력

#### 2. provider 설정

build > Authentication > 사용하려는 provider(구글) 선택 > 허용 > 지원 이메일 설정 > 저장&#x20;

(필요한 provider는 위 같은 방식으로 모두 추가)

***

## 로그인

#### 1. import하기&#x20;

`import { getAuth, signInWithPopup, GoogleAuthProvider } from 'firebase/auth';`

#### 2. auth, provider 설정&#x20;

`const auth = getAuth(app);`\
`const provider = new GoogleAuthProvider();`

(app은 firebase 사이트에서 프젝 생성 후 firebase.js 파일에 복붙한 코드 / export default app)

#### 3. 로그인 팝업 띄우기(로그인 클릭 시 구글 로그인 팝업창 뜨게 하기)&#x20;

`signInWithPopup(auth, provider)`

#### 4. user 로그인 상태 확인하기&#x20;

\*onAuthStateChanged: 페이지가 refresh 되면 실행된다.\
`useEffect(() => {` \
&#x20;`const unsubscribe = onAuthStateChanged(auth, (user) => {` \
&#x20; `if (!user) {` \
&#x20;  `navigate('/login');` \
&#x20; `} else if (user && pathname === '/login') {` \
&#x20;  `navigate('/');` \
&#x20; `}` \
&#x20;`});` \
&#x20;`return () => {` \
&#x20; `unsubscribe(); // 더 이상 사용 안 할 때 닫는다`\
&#x20;`};` \
`}, [pathname]);`

#### 로그인 시 발생하는 에러

🔻error: Cross-Origin-Opener-Policy policy would block the window.close call. \
google provider 사용 시 발생하는 보안 관련 에러로 firebase에서 해결하려고 노력 중이라고 한다. \
(아직 해결 못함..ㅎ)&#x20;

***

## 로그아웃&#x20;

\*signOut 함수 사용(firebase에서 지원) \
`const handleLogout = () => {`\
&#x20;`signOut(auth)` \
&#x20; `.then(() => { setUserData({});`\
&#x20;  `})` \
&#x20; `.catch((error) => {`\
&#x20;  `alert(error.message);`\
&#x20; `});`\
`};`

***

참고 사이트

[자바스크립트로 Google을 사용하여 인증](https://firebase.google.com/docs/auth/web/google-signin?hl=ko#web-modular-api)

[파이어베이스 구글 로그인 COOP](https://velog.io/@b\_d\_o\_o/%ED%8C%8C%EC%9D%B4%EC%96%B4%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EA%B5%AC%EA%B8%80-%EB%A1%9C%EA%B7%B8%EC%9D%B8-COOP)

[패스트캠퍼스 - 프론트엔드 패키지](https://fastcampus.co.kr/dev\_online\_frontend)
