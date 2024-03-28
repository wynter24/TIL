# 4️⃣ TCP/IP 4계층

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

## TCP/IP 4계층

<figure><img src="../.gitbook/assets/image (3).png" alt="" width="563"><figcaption><p>OSI 7계층과 TCP/IP 4계층</p></figcaption></figure>

### OSI 7계층과의 차이점

<table><thead><tr><th width="130"></th><th>OSI 7계층</th><th>TCP/IP 4계층</th></tr></thead><tbody><tr><td>목적</td><td>호완성, 표준화</td><td>실무 적용</td></tr><tr><td>구성</td><td>역할 기반</td><td>프로토콜 기반</td></tr><tr><td></td><td>이론적 표준</td><td>실무적 표준</td></tr></tbody></table>

#### TCP/IP 4계층 특징

* 계층별 간섭 최소화 - 각 계층별 처리 역할이 다르기 때문
* 유지 보수 편리 - 특정 계층에서 문제 발생 시 해당 계층을 살펴보면 됨
* 데이터의 캡슐화와 은닉 - 다른 계층끼리 데이터의 전달 과정을 구체적으로 알 필요 X

### 1계층 : 네트워크 액세스 계층 (Network Access Layer or Network Interface Layer)

* OSI 7계층의 물리 계층(1)과 데이터 링크 계층(2)에 해당
* Node-To-Node간의 신뢰성 있는 데이터 전송을 담당하는 계층
  * TCP/IP 패킷을 네트워크 매체로 전달 & 네트워크 매체에서 TCP/IP 패킷을 받음
  * 데이터를 전기신호로 변환한 뒤, 물리적 주소인 MAC 주소를 사용해, 알맞은 기기로 데이터 전달
* 에러 검출 기능(Detecting errors), 패킷의 프레임화(Framing  packets)
* 네트워크 접근 방법, 프레임 포맷, 매체에 대해 독립적으로 동작하도록 설계
* LAN, 패킷망 등에 사용
* 프로토콜: Ethernet, Wi-Fi, PPP, Token Ring etc.

### 2계층 : 인터넷 계층 (Internet Layer)

* OSI 7계층의 네트워크 계층(3)에 해당
* IP 담당 및 패킷을 최종 목적지까지 라우팅하는 계층
  * 네트워크상 최종 목적지까지 정확하게 연결되도록 연결성 제공
* 기능: 어드레싱(addressing), 패키징(packaging), 라우팅(routing)&#x20;
* 프로토콜: IP, ARP, ICMP, RARP, OSPF

### **3계층 : 전송 계층 (Transport Layer)**

* OSI 7계층의 전송 계층(4)에 해당
* <mark style="background-color:red;">TCP,</mark> <mark style="background-color:red;">UDP</mark> 담당
* 프로세스 간 신뢰성 있는 데이터 전송 및 통신 노드 간의 연결을 제어하는 계층
* IP와 Port를 이용하여 프로세스와 통신
* 역캡슐화 과정에서, 포트 번호를 사용해 데이터를 정확한 애플리케이션에 전달하는 역할도 함
  * 네트워크 액세스 계층과 인터넷 계층을 통해, 데이터가 목적지 기기까지 정상적으로 도착하면,
  * 전송 계층은 포트 번호를 사용해, 데이터를 목적지 기기 내 적절한 애플리케이션으로 전달
* 애플리케이션 계층의 세션과 데이터그램(datagram) 통신서비스 제공
* 프로토콜: TCP, UDP, RTP, RTCP

### 4계층 : 애플리케이션 계층 (Application Layer)

* OSI 7계층의 세션 계층(5), 표현 계층(6), 응용 계층(7)에 해당
* 사용자와 가장 가까운 계층으로 프로그램(브라우저)가 직접 소통
  * 서버나 클라이언트 응용 프로그램이 이 계층에서 동작 (데이터를 처음으로 받는 곳)
* 다른 계층의 서비스에 접근할 수 있게 하는 애플리케이션을 제공
  * 애플리케이션들이 데이터를 교환하기 위해 사용하는 프로토콜을 정의
* TCP/UDP 기반의 응용 프로그램을 구현할 때 사용
* 프로토콜: HTTP, HTTPS, FTP, SSH, Telnet, DNS, SMTP

***

참고 자료

[TCP / IP 4계층 모델 - 핵심 총정리](https://inpa.tistory.com/329)

[\[Network\] TCP/IP 와 TCP/IP 4계층이란?](https://wooono.tistory.com/507)

[\[N/W\] OSI 7계층이란? - OSI 계층별 특징, TCP/IP 4계층](https://lxxyeon.tistory.com/155)

[\[네트워크  #6\] TCP/IP 4계층(TCP/IP 4 Layer)](https://m.blog.naver.com/doctor-kick/221950485931)
