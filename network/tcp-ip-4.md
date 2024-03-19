# TCP/IP 4계층

## ❇️기본 개념

### IP (Internet Protocol)

&#x20;'패킷'을 정해진 <mark style="background-color:red;">최대한 빨리</mark> 목적지로 운반&#x20;

* "패킷 전달" 과정에서 패킷의 손실, 중복 확인 X \
  ⇒ 비신뢰성, 비연결성&#x20;

\*패킷: 데이터의 작은 조각

∴ TCP가 멀쩡한지 확인

#### ▸버전&#x20;

IPv4 / IPv6

***

### TCP(Transmission Control Protocol)&#x20;

<mark style="background-color:orange;">신뢰성</mark> 있는 데이터 통신을 위한 프로토콜 \
'<mark style="background-color:purple;">연결형 프로토콜</mark>'이라고도 한다 ← (클라이언트와 서버의) 통신 상태 미리 확인

* 패킷마다 번호 부여한다.
* TCP 데이터 안에 전송 제어, 순서, 정보들이 있다 → 패킷을 순서대로 제어\
  그래서 TCP는 신뢰할 수 있는 프로토콜이라고 한다.

#### TCP 3 way handshake (메세지)&#x20;

본격적으로 상대 클라이언트와 연결되기 전, 가상 연결해서 패킷으로 보내 확인하는 동작.&#x20;

헤더에 '플래그'(flag)에서 메세지 넣어 전달한다.\
\- SYN: 연결 요청 \
\- ACK: 접속 수락\
\- FIN: 연결 해제

* (서버 → 클라) 데이터 받은 후 (클라 → 서버) 잘 받음 메세지 보냄 \
  메세지 여부에 따라 오류 여부 판단

**when use?** HTTP, Email, File transfer

***

### UDP(User Datagram Protocol)&#x20;

비 연결지향적 프로토콜

신뢰성 보장X \
데이터 전달 보증 X \
순서 보장 X

목적: 빠르게 패킷 전달

**when use?** 실시간 스트리밍, 온라인 게임



***

참고 자료

[TCP / IP 4계층 모델 - 핵심 총정리](https://inpa.tistory.com/329)
