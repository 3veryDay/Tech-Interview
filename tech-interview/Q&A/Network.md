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
혼잡 제어(congestion control)
<hr>
</details>

혼잡 제어는 기본적으로 Window SIze을 **AIMD**(Additive Increase Multiplicative Decrease) 방식으로 전송이 성공적으로 진행되면 1씩 증가, 실패하면 절반으로 감소하는 방식으로 진행된다.

하지만, 초기에는 window size을 1씩 증가시키면 최적점까지 가기까지 너무 오래 걸리기에 slow start라고 선송이 성공적으로 진행될 시, 2배씩 증가하도록 한다.

2배씩 증가하며 손실이 발생하면, 그때부터 AIMD 방식으로 손실이 발생했을 떄는 2분의 1, 성공 했을 때는 1씩 증가.
![image](https://github.com/user-attachments/assets/201679ea-3984-478e-a5a2-8dd4a175152a)

<details>
<summary>혼잡제어에서 Timeout이 발생했을 때와 패킷 손실이 발생했을 때, 윈도우 사이즈의 변화는 각각 어떨까요?</summary>

<hr>
Timeout은 네트워크 상에서 심각한 혼잡이라고 판단해, WIndow Size를 0으로 줄이고, 다시 slow Start하고 exponential하게 증가시킨다.

반면, 패킷 손실의 경우는 AIMD 방식대로 Window Size를 절반으로 줄인다

>Timeout이 발생해, window size을 0으로 줄이고, slow start을 하면 손실이 발생하기까지 window size를 2배 증가시키는 것이 아닌, Timeout이 발생한 지점의 절반 지점까지만 Exponential하게 2배씩 증가한다. 이를 Congestion Avoidance라고 한다.

<hr>
</details>

<details>
<summary>흐름제어기법 중 슬라이딩 윈도우 방식에대해 설명해주세요</summary>

<hr>
네트워크 상태가 안 좋으면, 패킷 유실 가능성이 커지므로 적절한 송신량을 결정해야 하는데, 한번에 데이터를 받을 수 있는 데이터 크기를 window size라고 하고, 네트워크 상황에 따라서 이 윈도우 사이즈를 조절하는 것을 sliding windwon라고 한다.

- 흐름 제어를 위한 프로토콜 중 가장 많이 사용된다.
- stop-and-wait 방식에서는 ACK을 받고 나서 다음 프레임을 전송해야 해서 비효율적인데, **sliding window에서는 송신자가 보낸 프레임에 대한 ACK을 받지 않더라도 위도우 내에 있는 다른 프레임을 전송할 수 있다는 이점이 있다.**
- sliding window는 데이터가 전송되었는지에 대한 ACK이 수신될 때마다 윈도우의 범위를 이동시키기에 슬라이딩 윈도우라고 부른다.
- 수신을 처리하고 프레임을 재전송하는 방법에 따라, Go-Back_N과 Selective Retransmission이 나뉘게 된다.

- GoBackN
  - 윈도우 내에 오류가 발생한 프레임 이후의 패킷은 모두 버리고, 재전송 하는 방식
 
- Selective Retransmission
  - 모든 패킷을 버리는 것이 아닌, 오류가 발생한 프레임만 선택적으로 재전송하는 방식.
<hr>
</details>


## Http/Https란?
<details>
<summary>HTTP란 무엇일까요?</summary>

<hr>

- 서버 클라이언트 모델을 따라 데이터를 주고 받기 위한 프로토콜이다.
- 인터넷 상에서 hypertext를 교환하기 위해서 **통신규약으로 80포트를 사용하고 있다.
- OSI 7계층 중에서는 7게층인 application layer에 속하며, TCP/IP 위에서 작동한다.
- 상태를 갖고 있지 않은 **stateless protocol**이며, Method, path, version, header, body 등으로 구성되어있다.  
<hr>
</details>

<details>
<summary>HTTP 1.0 vs HTTP 1.1 vs HTTP 2.0</summary>

<hr>

##HTTP 1.0
- 브라우저에 친화적인 protocol
- Method : **GET, HEAD, POST
- Connection 특성 : 응답 직후종료
> Connection을 응답 직후에 닫기 때문에, 각각의 요청마다 새로운 연결을 열고 닫으며불필요한 3-2T-HANDSHAKING을 하게 된다.

## HTTP 1.1
- 오늘날 가장 많이 사용되는 HTTP 버전
- 영구 및 `파이프 라인` 연결, 압축,압축해제, 가상 호스팅, 캐시 등이 추가 -> 응답 속도가 빨라지고, 대역폭이 절약되는 등 성능 최적화 및 기능 향상되었다.
- Method : GET, HEAD, POST **PUT, DELETE, TRACE, OPTIONS**
- Connection 특성 : Persistent Connection
  - 한번 Connection을 맺고, 해당 Connection이 열려있다면, Connection 을 통해 Request, response 작업을 진행한다.
  - `HTTP 1.1 Keep-alive pipelining` : Pipelining을 사용할 때, client는 여러 request를 response의 응답을 기다리지 않고 보낼 수 있다.
  -  HTTP 1.1 Keep-alive multiple connections : 클라이언트는 많은 양의 objects를 검색하는 성능을 높이기 위해서 TCP 다중 연결을 할 수 있다.
 
## HTTP 2.0
- HTTP 1.1 프로토콜을 계승하며 성능 향상에 초점을 맞췄다.
  - HTTP 1.1은 평문(plain text)을 사용하고, 개행으로 구별되었으나, 2.0은 바이너리 포맷으로 인코딩된 messgae, frame으로 구성된다.
- Connection : Multiplexed Streams
  - 한 Connection으로 동시에 여러 개 메시지를 주고 받을 수 있고, response는 순서에 상관없이 stream으로 주고받는다.
 
<hr>
</details>


<details>
<summary>HTTPS를 해야하는 이유에 대해 설명해주세요</summary>

<hr>

패킷 탈취, 클라이언트 위장할 수 있는 등의 **보안 문제**로부터 보호
<hr>
</details>

<details>
<summary>HTTP와 HTTPS의 차이점에 대해서 설명해주세요</summary>

<hr>
HTTP(Hypertext Transfer Protocol)은 client-server 통신에서 쓰이는 프로토콜이나 통신 규칙들이다.

웹사이트를 방문하게 되면, 내 브라우저는 웹 서버에게 HTTP 리퀘스트를 보내고, 웹 서버는 HTTP 리스폰스로 대답한다. 이렇게 웹 서버와 브라우저는 plaintext(평문)으로 소통하는 것이다.

짧게 말해서, 네트워크 통신이 가능하도록 하는 것이 HTTP 프로토콜이다.

이름에서 보이듯이 HTTPS(Hypertext Transfer Protocol Secure)은 조금더 안전한 버전, 또는 HTTP의 확장이라고 볼 수 있다. HTTPS에서는 브라우저와 서버가 안전하면서 encrypted 연결을 한 후에 데이터를 주고 받는다.

<hr>
</details>


<details>
<summary>stateful와 stateless의 차이점에 대해 설명하세요</summary>

<hr>

## Stateful(상태유지)
상태유지란, 클라이언트와 서버 관계에서 **서버가 클라이언트의 상태를 보존**함을 의미한다.
- 대표적으로 홈페이지에서 한번 로그인을 하면, 페이지를 이동해도 로그인이 풀리지 않고, 유지되는 것이 서버가 클라이언트 상태를 유지하고 있으니까 가능한 것이다.
- 클라이언트의 정보를 기억한다라는 말은 어딘가에 정보를 저장하고 통신할 때마다 읽는다는 것이다.
- 이러한 정보들은 일반적으로 브라우저의 쿠키(Cookie)에 저장되거나, 서버의 세션(Session) 메모리에 저장되어 상태를 유지하게 된다.
- TCP
- 
## Stateless(무상태)
무상태는 반대로 클라이언트와 서버 관계에서 **서버가 클라이언트의 상태를 보존하지 않음**을 의미한다
- Stateless 구조에서는 서버는 단순히 요청이 오면 응답하고, 상태관리는 전적으로 클라이언트 몫이다.
- 클라이언트와 서버간의 통신에 필요한 모든 상태 정보들은 클라이언트가 가지고 있다가, 서버와 통신할 때 데이터를 실어 보내는 것이다.
- 서버는 단순히 받고 응답하기에, 상태 유지에 대한 부하가 현저히 줄어들게 된다.
- 또한, 서버가 중간에 바뀌어도, 문제가 없다.
- **그래서 대량의 트래픽 발생시에도 서버 확장을 통해 대처를 수월하게 할 수 있다**
- HTTP, UDP

## Stateless와 Token
로그인 유지와 같은 상태는 stateful한 상태이어야 하는데, 서버에 부하가 생길 수 있다. 그래서 stateless 특징을 유지하면서 로그인 상태를 유지하도록 하는 기술이 JWT 토큰이다.

토큰은 클라이언트가 암호화된 로그인 정보들을 지니고 있다가 서버에 통신할 때 넘겨줌으로써 내가 로그인 됐음을 인증하는 방식이다.

##Stateless 와 HTTP/REST
HTTP는 stateless한 성격을 가진 protocol
REST는 stateless한 성격을 가진 **설계 구조**

<https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-Stateful-Stateless-%EC%A0%95%EB%A6%AC>
https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC

<hr>
</details>


<details>
<summary>SSL(Secure Socket Layer), TLS(Transport Layer Security)가 무엇인가요?</summary>

<hr>

HTTPS를 위해 사용되고 있는 **암호화 기반의 인터넷 보안 프로토콜**이다. 이는 전달되는 모든 데이터를 암호화하고, 사이버 공격도 차단한다.

둘의 차이는 SSL는 1996년 이후 업데이트가 되지 ㅇ낳고, 사라지고 있다. 그렇기에 취약성도 있기에 사용 중단을 권장하고 있다. 이를 대체하는 것이 TLS이다. TLS는 SSL의 업데이트 버전이다.
<hr>
</details>


<details>
<summary>SSL/TLS Handshaking에 대해 설명해보세요</summary>

<hr>
![image](https://github.com/user-attachments/assets/39857d39-b271-4e92-9ef6-7ca46a6f9b14)

1. **ClientHello(암호화 알고리즘 나열 및 전달)**
   클라이언트가 서버에 연결을 시도하면서 전송하는 패킷이다. 자신이 사용가능한 Cyper SUite 목록, SessionID, SSL 프로토콜 버전, Random Byte등이 전달된다.
   > Cyper Suite는 SSL 프로토콜 버전, 인증서 검정, 데이터 암호화 프로토콜, Hash 방식 등의 정보를 담고 있는 존재이다.
2. SererHello(암호화 알고리즘 선택)
   서버는 클라이언트가 보낸 Client Hello 패킷을 받아서 Cyper Suite 중 하나를 선택한 후, 자신의 SSL 프로토콜 버전 등과 함께 다음 클라이언트에게 전달한ㄷ.
   > Client Hello에서 보낸 Cyper SUite는 여러개이지만, SErverHello에서는 서버가 한개만 선택해서 보내기에 1개의 Cyper SUite이 있다.
3. Server Certificate(인증서 전달)
   Sever는 자신의 SErver가 발행한 공개키가 들어있는 SSL 인증서를 클라이언트에게 전달한다. 클라이언트는 서버가 보낸 CA의 개인 키로 암호화 된 SSL 인증서를 CA에 등록되어있는 공개키를 사용해서 복호화한다. 이에 성공하면 CA가 서명한 것이 맞으니, 유효성 검증이 완료.
   i. Server Key Exchange / ServerHello Done : 서버의 공개키가 SSL 인증서 내부에 없는 경우, 서버가 직접 전달하겠다는 뜻으로 공개키가 SSL 인증서 내부에 있을 경우 Server Key Exchange 과정은 생략된다.
   인증서 내부에 서버의 공개키가 있다면, 클라이언트 CA의 공개키를 통해 인증서를 복호화한 후 서버의 공개키를 확보할 수 있다. 그리고 서버가 작업을 마쳤다고 ServerHelloDone을 전달한다.
4. Client Key Exchange(데이터를 암호화 할 대칭키 전달)
   클라이언트는 데이터 암호화에 사용한 대칭키를 생성하고 SSL 인증서 내부에서 추출한 서버의 공개키를 이용해서 암호화 한 후 서버에 전달한다. 전달된 대칭키가 SSL Handshaking의 목적이자, 추후 데이터를 암호화할 대칭키이다.
5. CLient/ server hello done(정보 전달 완료)
6. ChangeCipherSpec/Finished
   Change Cipher Spec 패킷은 클라이언트와 서버 모두가 서로에게 보내는 패킷으로 교환할 정보를 모두 교환한 뒤 통신할 준비가 되었음을 알리는 패킷이다.
   이 후, finish 패킷을 보내서 SSL handshake을 종료한다. 
<hr>
</details>


<details>
<summary>HTTP 메서드와 이것이 하는 역할에 대해서 설명해보세요.</summary>

<hr>

HTTP 메소드는 `클라이언트가 웹 서버에게 사용자 요청의 목적이나 종류를 알리는 수단`이다.

- `GET` : 리소스 조회
- `POST ` : 요청 데이터 처리, 주로 데이터 등록에 사용
- `PUT` : 리소스를 대체, 해당 리소스가 없으면 생성
- `PATCH` : 리소스 일부 변경
- `DELETE` : 리소스 삭제
- `HEAD` : GET와 동일, 메시지 부분 제외하고 상태줄 과 헤더만 반환
- `OPTIONS` : 대상 리소스에 대한 토신 가능 옵션을 설명(주로 CORS에서 사용)
- `CONNECT` : 대상 자원으로 식별되는 서버에 대한 터널을 설정
- `TRACE` : 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트를 수행


<hr>
</details>


<details>
<summary>HTTP 상태코드란 무엇이며 어떤 것들이 존재하는지 설명해보시오.</summary>

<hr>

- **1xx** : Informational : 요청이 수신되어 처리중
- **2xx** : Successful : 요청 정상 처리
- **3xx** : Redirection : 요청을 완료하려면 추가 행동이 필요
- **4xx** : Client Error : 클라이언트 오류, 잘못된 문법등으로 서버가 요청을 수행할 수 없음
- **5xx** : Server Error

## 400번대가 Client, 500번대가 서버 에
<hr>
</details>

<details>
<summary>GET과 POST의 차이점에 대해서 설명해보세요.</summary>

<hr>
GET: 서버로부터 리소스를 가져오기 위해 사용된다.
POST: 서버로부터 리소스를 생성/변경하기 위해 사용된다.
차이

GET의 경우 요청에 대해 캐시가 가능하고 POST는 캐시가 불가능하다.
GET 요청은 멱등하나 POST는 서버에 리소스를 생성/업데이트 하여 멱등하다고 볼 수 없다.
<hr>
</details>


<details>
<summary>PUT과 PATCH의 차이에 대해 설명해주세요.</summary>

<hr>
PUT은 리소스의 모든 것을 업데이트하고, PATCH는 일부를 업데이트 한다.

PUT은 항상 전체 리소스를 포함해서 요청을 보내여, 멱등성(같은 요청을 여러번 수행해도 동일한 결과) 성질을 갖고 있지만, 
PATCH는 변경을 하고 싶은 일부 속서안을 변경하기에 상황에 따라서 멱등성을 보장할 수도, 보장하지 않을 수도 있다. 

ex)  PATCH 요청을 보낼 떄, 나이를 30으로 업데이트 하는 요청을 body에 age:30 과 같이 명시적으로 보내면 멱등성을 보장한다. 하지만 나이를 한 살 올리라는 의미로 value👍: 1 의 값을 body에 담아 보낼 경우, 멱등하지 않게 된다. 
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
