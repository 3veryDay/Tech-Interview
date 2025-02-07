# 네트워크
## TCP & UDP
<details>
<summary>TCP와 UDP의 차이점에 대해 설명해주세요.</summary>

<hr>

- TCP는 Reciever와 Sender 사이에 연결을 만들고, 연결을 기반으로 데이터를 주고 받는 **연결 지향형 프로토콜** 이고, UDP는 연결 없이 전송하는 **비연결형 프로토콜** 이다.
- TCP는 데이터가 순차적으로 전송, 수신하고 UDP는 비순차적이다.
- TCP는 흐름제어(flow control)과 혼잡제어(congestion control)을 진행하고, UDP는 진행하지 않는다.
- UDP가 비연결형이기에 빠르다 -> 연속성이 중요한 스트리밍에 사용
- TCP는 연결형이어서, 신뢰성이 중요한 서비스에 사용된다.

![image](https://github.com/user-attachments/assets/764bd6de-e1b9-4de7-b8ff-99610a508af6)

<hr>
</details>


<details>
<summary>DNS와 DHCP는 UDP와 TCP중 어떤 프로토콜을 사용할까요?</summary>

<hr>
DNS(Domain Name System)은 UDP를 사용한다.

그 이유는 Sender와 REceiver 사이에 연결을 맺으면 보내고 받는 데이터 크기에 비해, 연결에 드는 비용이 크기 때문이다.

Root DNS같은 경우 모든 것들과 TCP로 연결을 맺게 되면 **부담이 크기 때문에** UDP 방식을 사용한다.
<hr>
</details>


<details>
<summary>UDP, TCP의 세그먼트(Segment)는 전송 과정 중 데이터의 변경이 없었다는 것을 어떻게 알까요?</summary>

<hr>
각각의 Segment는 헤더의 Checksum을 통해 데이터의 변경이 발생했는지 체크를 해준다.

- Sender는 세그먼트의 16-bit로 표현한 Content와 Header 필드 값을 더한 다음 1의 보수를 만들어서 checksum 필드에 추가한다.
- Reiceiver는 반대로 Content와 Header의 필드값을 16-bit로 변환하고, 더한후 1의 보수로 변경한 후,checksum과 동일한지 확인한다. 만약 다르면 세그먼트는 에러가 담겼을 것이라고 판단한다.
- 
<hr>
</details>


<details>
<summary>TCP 3 way handshake에 대해서 설명해주세요.</summary>

<hr>

TCP 3 way Handshake는 TCP 통신에서 **가상회선** 을 만드는 단계이다. 회선을 만드는 과정에서 SYN 패킷과 ACK 패킷을 통해서 회선을 만든다.

1. 클라이언트는 서버에 접속을 요청하는 SYN 패킷을 보낸다 .
클라이언트 -SYN-> 서버
2. 서버는 SYN을 받고, 클라이언트 요청을 수락한다는 ACK, 와 SYN FLAG가 설정된 패킷을 발송하고, 클라이언트가 다시 ACK으로 응답하기를 기다린다.
서버 -ACK, SYN FLAG PKT-> 클라이언트
3. 클라이언트는 서버에게 연결을 맺었다는 ACK을 보내고, 이후 연결이 이루어진다
클라이언트 -ACK-> 서버
![image](https://github.com/user-attachments/assets/5936ddb6-4459-4323-b66d-b6ef231185b8)


<hr>
</details>


<details>
<summary>TCP 4 way handshake에 대해서 설명해주세요.</summary>

<hr>

1. 클라이언트가 연결을 종료하겠다는 FIN 플래그 전송
2. 서버는 ACK을 보내고, 남은 데이터 이어서 전송
3. 서버가 통신이 끝났으면 연결이 종료되었다고 클라이언트에게 FIN 플래그 전송
4. 클라이언트는 확인했다는 메시지 보낸다.
![image](https://github.com/user-attachments/assets/4d9a04be-7e6d-41f6-b7db-b9338c67539e)

<hr>
</details>


<details>
<summary>왜 연결을 끊을 때는 4way handshke를 할까요?</summary>

<hr>

**양쪽 모두 연결을 종료할 준비가 되었음을 확실히 하기 위해서**

if 3 way handshake을 사용한다면 ?
- 클라이언트가 FIN을 보내고 서버가 FIN+ACK을 동시에 보내면 -> 서버가 아직 보낼 데이터가 남아있는 경우, 문제가 발생한다.
- 데이터가 손실될 위험이 있다.


Server가 아직 보낼 데이터가 남아있는데 CLient가 데이터 전송을 마쳤다고 연결을 끊으려고 할 때, 일단 FIn에 대한 ACK만 보내고, 데이터를 모두 전송한 후에 자신도 FIN 메세지를 보낸다. 
<hr>
</details>


<details>
<summary>Time-wait이란 무엇일까요?</summary>

<hr>
4way handshake에서 Server에서 FIN을 전송하기 전에 전송한 패킷이 Routing지연이나 패킷 유실로 인한 재전송 등으로 인해서 FIN보다 늦게 도착하는 상황이 발생하면, 이 패킷을 Drop되고, 데이터는 유실 될 것이다.

이러한 현상에 대비해서 Client는 Server로부터 FIN을 수신하더라도 일정 시간( 디폴트는 240초)동안 세션을 남겨놓고, 잉여 패킷을 기다리는 과정을 거치게 되는데, 이 과정을 Time_WAIT이라고 한다.

<hr>
</details>


<details>
<summary>TCP와 UDP 패킷구조에는 어떤 차이가 있을까요?</summary>

<hr>
UDP는 비연결형 통신이라 출발지와 목적지의 Port 정보, UDP Segment 길이, checksum, data(payload)만을 갖고 있다.

TCP는 연결형 통신, 데이터 전송 순서가 보장되어야 하기 떄문에, 추가 데이터(**sequence number, ACK number, recieve window** )이 들어간다.
<hr>
</details>

## 흐름제어와 혼잡제어
<details>
<summary>흐름제어와 혼잡 제어에 대해 설명해주세요</summary>

<hr>

### 흐름 제어(Flow Control)
데이터의 수신자가 송신자가 보내주는 데이터의 양을 수신자의 **버퍼사이즈**에 오버플로우가 발생하지 않도록 **속도를 조절**하는 방법이다.

전송 속도를 조절하는 방법으로는 상대방에게 응답을 할 때, TCP Header 중 하나인 RWND에 **남은 버퍼 사이즈 정보를 추가해서** 보내주고, 송신자는 해당 데이터를 보고 **in-flight data의 양**(전송 속도)를 조절한다.

### 혼잡 제어(Congestion Control)

**네트워크 내의 패킷 수가 넘치게 증가하는 혼잡 현상을 방지**하는 방법이다.
즉, 네트워크의 혼잡을 피하기 위해서, 송신 측에서 데이터의 전송 속도를 강제로 줄이는 작업니다.

송신자는 congestion window를 통해 시간에 따른 네트워크 혼잡도를 판단해서 Sending Rate을 변경한다.

Sender TCP Window = min(congestion window, recieve Window)
<hr>
</details>

<details>
<summary>혼잡제어에서 윈도우 사이즈가 상황에 따라 어떻게 변경되는지 설명해주세요</summary>

<hr>

<hr>
</details>

<details>
<summary>혼잡제어에서 Timeout이 발생했을 때와 패킷 손실이 발생했을 때, 윈도우 사이즈의 변화는 각각 어떨까요?</summary>

<hr>

<hr>
</details>

<details>
<summary>흐름제어기법 중 슬라이딩 윈도우 방식에대해 설명해주세요</summary>

<hr>

<hr>
</details>

## OSI 7계층
<details>

<summary>OSI 7계층에 대해 설명해주세요.</summary>

<hr>

<hr>
</details>

<details>
<summary>OSI 7계층은 왜 나눴을까요?</summary>

<hr>

<hr>
</details>

<details>
<summary>TCP/IP 4계층에 대해 설명해보세요.</summary>

<hr>

<hr>
</details>

<details>
<summary>인캡슐레이션과 디캡슐레이션에 대해 설명해주세요.</summary>

<hr>

<hr>
</details>


<details>
<summary>TCP/IP란 무엇일까요?</summary>

<hr>

<hr>
</details>

## Http/Https란?
<details>
<summary>HTTP란 무엇일까요?</summary>

<hr>

<hr>
</details>

<details>
<summary>HTTP 1.0 vs HTTP 1.1 vs HTTP 2.0</summary>

<hr>

<hr>
</details>


<details>
<summary>HTTPS를 해야하는 이유에 대해 설명해주세요</summary>

<hr>

<hr>
</details>

<details>
<summary>HTTP와 HTTPS의 차이점에 대해서 설명해주세요</summary>

<hr>

<hr>
</details>


<details>
<summary>stateful와 stateless의 차이점에 대해 설명하세요</summary>

<hr>

<hr>
</details>


<details>
<summary>SSL(Secure Socket Layer), TLS(Transport Layer Security)가 무엇인가요?</summary>

<hr>

<hr>
</details>


<details>
<summary>SSL/TLS Handshaking에 대해 설명해보세요</summary>

<hr>

<hr>
</details>


<details>
<summary>HTTP 메서드와 이것이 하는 역할에 대해서 설명해보세요.</summary>

<hr>

<hr>
</details>


<details>
<summary>HTTP 상태코드란 무엇이며 어떤 것들이 존재하는지 설명해보시오.</summary>

<hr>

<hr>
</details>

<details>
<summary>GET과 POST의 차이점에 대해서 설명해보세요.</summary>

<hr>

<hr>
</details>


<details>
<summary>PUT과 PATCH의 차이에 대해 설명해주세요.</summary>

<hr>

<hr>
</details>


<details>
<summary>HTTP keep-alive / TCP keep-alive</summary>

<hr>

<hr>
</details>


<details>
<summary>REST, RESTful이란 무엇일까요?</summary>

<hr>

<hr>
</details>


<details>
<summary>URL과 URI는 뭐가 다를까?</summary>

<hr>

<hr>
</details>

## 웹 통신 흐름

<details>
<summary>https://www.google.com/ 을 접속할 때 일어나는 일에 대해 설명해주세요</summary>

<hr>

<hr>
</details>


<details>
<summary>MAC 주소에 대해 설명해주세요.</summary>

<hr>

<hr>
</details>


<details>
<summary>MAC 주소가 존재하는데 왜 MAC주소로 통신을 안하고 IP주소로 통신할까요?</summary>

<hr>

<hr>
</details>

<details>
<summary>IP 주소에 대해 설명해주세요 (+ 서브넷 마스크까지)</summary>

<hr>

<hr>
</details>

<details>
<summary>허브, 스위치, 라우터에 대해 설명해주세요</summary>

<hr>

<hr>
</details>

<details>
<summary>스위치는 어떻게 브로드캐스트가 아닌 목적지인 MAC주소로만 유니캐스트로 데이터를 전송할 수 있을까요? 또한 데이터 전송 외에 스위치가 갖는 기능은 무엇이 있을까요? (Switch 내용 심화)</summary>

<hr>

<hr>
</details>

<details>
<summary>라우터의 동작 방식과 역할에 대해 설명해주세요 (Router 내용 심화)</summary>

<hr>

<hr>
</details>

<details>
<summary>ARP에 대해 설명해주세요</summary>

<hr>

<hr>
</details>


<details>
<summary>GARP와 RARP에 대해 설명해주세요</summary>

<hr>

<hr>
</details>

<details>
<summary>DNS에 대해 설명해주세요</summary>

<hr>

<hr>
</details>


<details>
<summary>DHCP에 대해 설명해주세요</summary>

<hr>

<hr>
</details>

## ETC

<details>
<summary>LAN, MAN, WAN의 차이에 대해 설명해주세요.</summary>

<hr>

<hr>
</details>

<details>
<summary>NIC(Network Interface Card)란 무엇일까요?</summary>

<hr>

<hr>
</details>

<details>
<summary>유니캐스트, 멀티캐스트, 브로드캐스트, 애니캐스트에 대해 설명해주세요.</summary>

<hr>

<hr>
</details>

<details>
<summary>Cookie, Session, JWT의 차이점에 대해 설명해주세요</summary>

<hr>

<hr>
</details>

<details>
<summary>이더넷(Ethernet)이란?</summary>

<hr>

<hr>
</details>

<details>
<summary>RPC란?</summary>

<hr>

<hr>
</details>

<details>
<summary>gRPC란?</summary>

<hr>

<hr>
</details>

<details>
<summary>NAT(Network Address Translation)이란?</summary>

<hr>

<hr>
</details>

<details>
<summary>공인 IP와 사설 IP란 무엇일까요?</summary>

<hr>

<hr>
</details>
