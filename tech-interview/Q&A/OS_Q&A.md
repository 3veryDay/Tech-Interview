# Operating System

## 운영체제 기초
<details>
<summary>운영체제란 무엇일까요?</summary>

<hr>
운영체제란 컴퓨터 시스템의 자원을 효율적으로 관리하며 사용자가 컴퓨터를 편리하고 효과적으로 사용할 수 있는 환경을 제공하는 여러 프로그램들의 모임이다.
또한, 응용 프로그램과 하드웨어 간의 인터페이스이다.

넓은 의미에서 커널 뿐만 아니라, 시스템을 위한 유틸리티를 포함하는 개념이며, 좁은 의미에서는 메모리에 올라가 있는 커널을 의미한다.
커널은 전체 운영 체제 코드 중 메모리에 올라가있는 부분이다.

<hr>
</details>

<details>
<summary>운영체제는 어떤 기능을 하는지 설명해주세요</summary>

<hr>
 1. CPU 스케줄링
 
 2. 메모리 관리

 3. 파일 관리
 
 4. 입출력 관리
 
 5. 프로세스 관리
 
 6. 네트워킹
 
 7. 보호

  - 시스템의 오류를 검사하고 복구한다.
    
  - 자원 보호 기능을 제공한다.
<hr>
</details>

<details>
<summary>운영체제가 관리하는 5가지 지원에 대해 설명해주세요</summary>

<hr>
프로세스, 저장장치, 네트워킹, 주변 장치, 사용자 이렇게 5가지 지원을 한다.

1. 프로세스 관리

프로세스의 스케줄링과 동기화 관리를 담당한다.
프로세스의 생성과 제거, 시작과 정지, 메시지 전달 등의 기능을 담당한다.

2. 저장장치 관리

저장 장치에는 메인 메모리인 1차 저장장치와 하드디스크, NAND 등인 2차 저장장치가 있다.
운영체제는 이러한 저장장치를 관리하며, 프로세스에게 메모리 할당 및 회수, 파일 생성과 삭제, 변경 유지 등의 관리를 한다.
  - 1차 저장장치(Main Memory)
    프로세스에 할당하는 메모리
    영역의 할당과 해제각 메모리 영역 간의 침범 방지
    메인 메모리의 효율적인 활용을 위해서 가상 메모리 기능도 제공
  - 2차 저장장치(HDD, NAND Flash Memory 등)
    파일 형식의 데이터 저장
    이런 파일 데이터 관리를 위한 파일 시스템이 있는데, 이를 OS에서 관리
    FAT, NTFS, EXT2, JFS, XFS 등 많은 파일 시스템이 개발되어서 사용 중

##### HDD와 NAND Flash Memory에 대해서
메모리 반도체는 무조건 스위칭 기능과 데이터 저장 기능을 갖는다.

DRAM은 스위칭 기능이 빠르고, NAND Flash Memory는 데이터 저장 기능이 월등하다. NAND Flash Memory는 전원이 꺼져도 창고라는 공간에 저장된 데이터가 존재하므로 '비휘발성 메모리'라고 하고, DRAM은 전원이 꺼지면 데이터는 무조건 소멸하기 때문에 '휘발성 메모리'라고 부른다.

3. 네트워킹

TCP/IP 기반의 인터넷에 연결하거나 응용 프로그램이 네트워크를 사용하면 OS에서 네트워크 프로토콜을 지원한다.
이처럼 OS는 응용 프로그램과 하드웨어 사이의 인터페이스 역할을 하면서 하드웨어를 소프트웨어적으로 제어 및 관리를 하고 있다.

4. 주변 장치 관리

입출력 장치의 스케줄링 및 전반적인 관리를 담당한다.
디바이스 드라이버를 OS가 관리해서 여러 하드웨어를 사용할 수 있도록 해준다


##### 디바이스 드라이버
디바이스란 하드 디스크, USB, 프린터, 단말기, 네트워크 어댑터, 터치 스크린, 오디오 등 컴퓨터 시스템 이외의 다른 주변 장치들을 말한다.

디바이스 드라이버(DD) 란 위의 디바이스들을 동작시키기 위해서 필요한 구동용 소프트웨어이다.
응용 프로그램에서 하드웨어 장치를 이용해서 데이터를 접할 때, DD를 사용한다.

5. 사용자 관리

사용자별 계정을 관리할 수 있는 사용자 관리 기능을 제공한다.
<hr>
</details>

<details>
<summary>시분할 시스템, 다중 프로그래밍 시스템, 대화형 시스템은 각각 무엇을 의미할까요?</summary>

<hr>
시분할 시스템이란 CPU 작업시간을 여러 프로그램이 나누어 쓰는 시스템이다.

다중 프로그래밍 시스템은 메모리 공간을 분할해 여러 프로그램들을 동시에 메모리에 올려서 처리하는 시스템이다.

대화형 시스템은 사용자 관점에서 각 프로그램에 대한 키보드 입력의 결과를 곧바로 화면에 보여주 시스템이다.

3 시스템 모두 하나의 컴퓨터에서 여러 프로그램이 동시에 실행되는 **다중 작업용 운영체제**에 속한다.

<hr>
</details>

<details>
<summary>인터럽트란 무엇일까요?</summary>

<hr>

 CPU가 프로그램을 실행하고 있는 중, 예기치 않은 상황이나 먼저 수행해야할 일이 발생한 경우, 현재 실행중인 작업을 즉시 중단하고, 발생한 상황이 먼저 처리되어야 함을 CPU에게 알리 것이다.

 인터럽트는 크게 Hardware Interrupt와 Software Interrupt가 있다.

 하드웨어 인터럽트는 각각의 하드웨어 I/O device에서 발생한 인터럽트다.

 - 입출력 인터럽트
 - 정전 전원 이상 인터럽트
 - 기계 착오 인터럽트 = CPU의 기능적인 오류
 - 외부 신호 인터럽트

소프트웨어 인터럽트가 더 중요하다. (Trap)

CPU 내부에서 자신이 실행한 명령이나 CPU 명령 실행에 관련된 모듈에서 오류가 생기거나 System call을 호출할 때 발생한다.
- System Call : 애플리케이션이 커널의 함수를 실행하기 위해서 발생시킨다.
- Exception : divide by zero, overflow, underflow ...

d
<hr>
</details>

<details>
<summary>폴링(Polling)이란 무엇일까요?</summary>

<hr>
인터럽트처럼 CPU가 다른 프로세스를 실행하는 동안 디바이스로부터 발생하는 이벤트를 처리하는 방법 중 하나이다.

폴링 방식은 특정 주기마다 CPU가 디바이스들이 serving이 필요한지 체크하기 때문에 CPU 사이클 낭비가 발생한다.
 ( 폴링은 특정 주기마다 CPU가 디바이스를 poll해야지 serving이 가능하지만, 인터럽트는 언제든지 발생할 수 있다)
또한, 인터럽트와 다르게 폴링은 소프트웨어적으로 시그널을 확인하는 방식이다.

폴링은 구현이 쉽고, 우선순위의 변경이 용이하기 때문에 쓰인다. 

>인터럽트는 폴링 방식과 다르게 하드웨어로 지원을 받아야한다는 제약이 있다. 하지만, 폴링 방식보다 신속하게 대응하는 것이 가능해서 필수적인 기능이다. 즉, 인터럽트는 상황을 예측하기 힘든 경우 컨트롤러가 가장 빠르게 대응할 수 있는 방식이다. 
<hr>
</details>

<details>
<summary>Mode bit이란 무엇일까요?</summary>

<hr>
Mode BIT는 사용자 장치의 잘못된 수행으로 다른 프로그램 및 운영체제에 피해가 가지 않도록 하는 보호 장치이다.

Mode BIT은 하드웨어적으로 두가지 모드의 operation 을 지원한다.
- 0이면 Kernel mode( OS 코드 수행 )
- 1이면 User mode( 사용자 프로그램 수행 )

Privileged Instruction는 파일을 다루거나 I/O에게 request를 하는 등, OS만 실행할 수 있는 Instruction으로 Kernel Mode에서만 수행이 가능하다.

이를 User Mode에서 실행하려고 하면, 프로그램을 종료하고 Software Interrupt가 발생한다. 

User program이 하드웨어에 접근하려면 **system call**을 통해서 실행해야 한다.

<hr>
</details>

<details>
<summary>System Call이란 무엇일까요?</summary>

<hr>
System Call이란 (User program이 접근하지 못하는) OS만의 privileged Instruction을 실행하기 위해서는 OS에게 특정 일들을 수행해달라고 요청하는 것으로 **Software Interrupt의 일종**이다.

User program과 OS사이의 인터페이스를 제공한다.

System Call 발생 -> mode bit 0으로 변경 -> 요청 작업 처리 -> mode bit 1로 변경 -> 유저 프로세스 수

<hr>
</details>

<details>
<summary>System Call과 Function Call의 차이점에 대해 설명해주세요</summary>

<hr>
![image](https://github.com/user-attachments/assets/41117340-62cb-489f-9dcc-8521115589cd)

System call은 OS의 도움을 받아 OS의 function을 불러서 수행하는 것이다.

Function call으 같은 프로세스 내에서 프로세스 내에 있는 function을 불러서 수행하는 것이다.
<hr>
</details>

<details>
<summary>DMA란 무엇일까요?</summary>

<hr>
DMA(DIrect Memory Access)

등장 배경

모든 메모리의 접근은 CPU에 의해 접근을 해야하며, 메모리의 접근을 위해서는 CPU에게 인터럽트를 발생시킨 후, 부탁해야 했다. 그렇기 때문에, 모든 메모리 연산에는 interrupt을 발생시키고, CPU는 interrupt을 처리하기 위해서 local buffer와 memory 사이에서 데이터를 옮기는 일까지 진행했다. 이는 CPU 효율성을 많이 떨어뜨렸고, 이를 극복하기 위해서 CPU이외에 메모리 접근이 가능한 장치인 DMA이 등장했다.

DMA 설명

DMA는 일종의 컨트롤러 장치로, CPU가 입출력 장치들의 메모리 접근 요청에 의해 자주 인터럽트를 당하는 것을 막아주는 역할을 한다.

보통 CPU가 처리하는 로컬 버퍼에서 메모리로 데이터를 읽어오는 작업을 DMA가 대행하게 된다.

DMA는 바이트 단위가 아닌 블록 단위로 데이터를 메모리로 읽어온 후!! CPU에게 인터럽트를 발생시켜서 작업 완료를 알린다. 이는 CPU 인터럽트 빈도를 줄여서 효율성을 높인다.

<hr>
</details>

## 프로세스와 스레드
<details>
<summary>프로세스와 프로세서의 차이에 대해 설명해주세요.</summary>

<hr>
프로세스는 코드로 작성된 프로그램이 메모리에 적재되어 사용할 수 있는 상태가 된 것이다.
즉, 메모리 상에서 실행중인 프로그램을 프로세스라고 하고

프로세서는 CPU를 의미한다.

<hr>
</details>

<details>
<summary>프로세스와 스레드의 차이를 설명해주세요</summary>

<hr>
참고 자료 : <https://inpa.tistory.com/entry/%F0%9F%91%A9%E2%80%8D%F0%9F%92%BB-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%E2%9A%94%EF%B8%8F-%EC%93%B0%EB%A0%88%EB%93%9C-%EC%B0%A8%EC%9D%B4> 
프로세스는 운영체제로부터 자원을 할당받은 작업의 단위이고,
스레드는 프로세스가 할당받은 자원을 이용하는 실행 흐름의 단위이다.

프로그램을 실행하게 되면, 파일(코드)는 컴퓨터 메모리에 올라가게 되고, OS로부터 시스템 자원(CPU)를 할당받아서 프로그램 코드를 실행시키면, 그것이 프로세스다.(실행되어 작업중인 컴퓨터 프로그램)

|프로그램|프로세스|
|----|----|
|어떤 작업을 하기 위해 실행할 수 있는 파일| 실행되어 작업중인 컴퓨터 프로그램|
|파일이 저장 장치에 있지만 메모리에는 올라가 있지 않은 **정적**인 상태|메모리에 적재되고 CPU 자원을 할당받아 프로그램이 실행되고 있는 상태|
|코드 덩어리| 코드 덩어리 실행한 것 |

프로세스를 여러 개 만들면 메모리 차지가 비효율적이고, CPU 할당 자원도 중복되기에 등장한 것이 Thread이다.

스레드는 *프로세스 내에서 동시에 진행되는 작업 갈래, 흐름의 단위*를 말한다.

프로그램이 실행되어 프로세스가 만들어지면 Text, Data, Heap, Stack으로 구성된 메모리 영역으로 할당 받는다. 여기서 Heap, Stack은 프로세스가 실행되는 동안 크기가 동적으로 바뀐다.

각 프로세스마다, 이 4개가 각각 생성된다.

스레드는 프로세스가 할당 받은 자원을 이용하는 실행의 단위로, 스레드가 여러개가 있기 때문에 하나의 Chrome을 가지고 웹서핑, 음악, 게임, 다운로드를 동시에 할 수 있는 것이다.

스레드끼리 프로세스의 자원 중 Code, Data, Heap은 공유하고, 스레드마다 Stack은 따로 할당받는다. heap 메모리를 통해서 서로 다른 스레드와의 소통도 가능한 것이다.

이렇게 구성했기 때문에, 자원을 공유하고 자원의 생성과 관리의 중복성을 최소화하여 수행 능력을 올릴 수 있다.



<hr>
</details>

<details>
<summary>프로세스의 주소 공간은 어떻게 이루어져 있을까요? 그리고 각각의 주소 공간에는 어떤 데이터가 저장될까요?</summary>

<hr>
1. Text(Code) : 코드 자체를 구성하는 메모리 영역
2. Data (data + bss + rodata)  : 번역 변수, 정적 변수, 배열과 같은 static data(global variable)
초기화된 데이터는 data영역에 저장하며 초기화되지 않은 데이터는 BSS 영역에 저장한다.(bss = block started by symbol)

const와 같은 상수 키워드 선언된 변수나 문자열 상수는 .rodata에 저장한다. 
-> 왜 data와 bss 구분을 하지?
세그먼트에 따라서 RAM, ROM 어디에 저장할지 결정해야한다.

3. Heap : run time동안 생성자, 인스턴스와 같은 동적으로 할당되는 데이터들을 위해 존재하는 공간이다. 동적으로 할당되고 해제된다.

4. Stack : 지역 변수, 매개변수, 리턴 값과 같은 데이터를 저장하는 임시 메모리 영역이다.함수 호출에 할당되고, 함수의 호출이 완료되면 소멸한다. 만일 stack 영역을 초과하면 stack overflow 에러가 발생한다. 

(RAM은 Random Access Memory, 내용을 자유롭게 읽고 쓰고 지울 수 있는 기억 장치, 책상에 비유, 휘발성 메모리
이며, 보통 컴퓨터의 주 기억장치인 하드 디스크에서 자주 사용하는 데이터를 불러와서 CPU가 빠르게 처리할 수 있는 중간 다리 역할. 
SRAM, DRAM, PRAM, SDRAM, DDRSDRAM 등이 있음

ROM은 Read-Only Memory로 저장한 데이터를 빠른 속도로 읽을 수 있지만, 다시 기록할 수는 없기 때문에 많이 사용하지는 않는다. 그래서 컴퓨터에서는 BIOS(Basic Input Output System)를 저장하거나, 에어컨 냉장고에서 많이 쓰인다. )
<hr>
</details>

<details>
<summary>프로세스 주소 공간을 나눈 이유는 무엇일까요?</summary>

<hr>
최대한 데이터를 공유하면 메모리 사용량을 줄일 수 있기 때문이다.

Code는 공유하고, Stack, Data는 스택 구조의 특성과 전역 변수의 활용성을 위해서 나누게 되었다.

<hr>
</details>

<details>
<summary>프로세스의 상태에는 어떤 것이 있을까요?</summary>

 
|프로세스 상태| 설명 |
 |---|--------|
 |생성(new)|프로세스가 생성되고 아직 준비가 되지 않은 상태 |
 |준비(ready)|프로세스가 실행을 위해 기다리는 상태, CPU를 할당받을 수 있는 상태이며, 언제든지 실행될 준비가 되어있다|
 |실행 (running)|프로세스가 CPU를 할당받아 실행되는 상태|
 |대기 (waiting)|프로세스가 특정 이벤트(입출력 요청 등)가 발생하여 대기하는 상태CPU를 할당받지 못하며, 이벤트가 발생하여 다시 READY 상태로 전환될 때까지 대기한다.|
|종료 (terminated)|프로세스가 실행을 완료하고 종료된 상태더 이상 실행될 수 없으며, 메모리에서 제거되게 된다|


<hr>
</details>

<details>
<summary>프로세스의 Running State에서 CPU 자원을 뺐기는 3가지 상황에 대해 설명해주세요</summary>

<hr>
1. Interrupt가 발생했을 때(timer도 포함)
2. I/O request 를 하기 위해 system call을 하여 watiting 상태로 넘어가는 경우
3. Process의 수행이 끝나서 terminated로 되는 경우
<hr>
</details>

<details>
<summary>OS는 프로세스의 정보를 어떻게 관리하며 어떤 데이터들을 저장하고 있는지 설명해주세요 (hint.PCB)</summary>

<hr>
각각의 process들을 OS의 관리를 받게 되는데, 이때 OS는 process의 현재 정보들을 알기 위해서 PCB(Process Control Block)을 사용한다.

PCB는 아래의 정보를 저장하고 있다.
1. process state
2. process number : process id(Pid)
3. Program Counter(PC)
4. CPU register - contes of registers in CPU
5. etc ( Owner, CPU usage, memory usage, process priority, IO status info)

<hr>
</details>

<details>
<summary>PCB가 왜 필요할까요?</summary>

<hr>
CPU core는 여러 개의 프로세스가 공유해서 사용한다. 이때 프로세스의 교체 (Context Switching)이 발생할 때마다 실행중인 CPU에 올라간 프로세스의 정보를 변경해야 하고, 프로세스들은 추후 CPU 이용 순서가 왔을 때, 이전 작업 내용을 이어서 하기 위해 정보를 저장해야할 필요가 있다. OS는 프로세스의 정보를 PCB를 통해 저장하고 관리하고 있다.

Context Switching이 발생할 때, PCB의 값들을 변경하게 되며 PCB의 정보를 통해 연산을 이어서 한다. 새로 해야할 작업의 상태를 알아야 하기 때문에 존재하는 프로세스에 관한 모든 정보를 저장하는 임시 저장소이다. (프로세스가 생성되면 메모리에 해당 프로세스의 PCB가 함께 생성되고, 종료 시 삭제된다. )

따라서, OS는 PCB에 담긴 프로세스 고유 정보를 통해 프로세스를 관리하며, 프로세스의 실행 상태를 파악하고, 우선순위를 조정하며 스케줄링을 수행하고, 다른 프로세스와의 동기화를 제어한다.

이러한 PCB를 통한 Context Switching은 사용자에게 빠른 반응성과 동시성을 제공하지만, switching 되는 순간, 발생하는 살짝의 간극을 context switching overhead라고 한다. 

이 overhead는 다음과 같은 행위에서 발생된다.
1. PCB 저장 및 복원
2. CPU 캐시 메모리 무효화에 딸ㄴ 비용
3. 프로세스 스케줄링 비용


<hr>
</details>

<details>
<summary>PCB는 어떻게 관리될까요??</summary>

<hr>
커널의 data 영역에는 CPU, memory, disk 등이 있다. 그리고 각각의 process 의 정보들을 갖고 있는 PCB가 존재한다. 즉, PCB는 커널의 data영역에서 관리된다.

이때 PCB들은 linked list 방식으로 관리가 된다. PCB List head에 PCB가 생성될 때마다 붙게 된다. 주소값으로 연결이 이루어져있는 연결 리스트이기 때문에 삽입 삭제가 용이하다.

프로세스가 생성되면 동시에 PCB도 생성되고, 프로세스가 종료되면 동시에 PCB도 제거된다.
![image](https://github.com/user-attachments/assets/24d7f63a-b07a-41aa-9fb7-fb17cbac88a4)

<hr>
</details>

<details>
<summary>Process Context란 무엇일까요?</summary>

<hr>
Process Context란 프로세스가 현재 어떤 상태에서 수행되고 있는 지 정확하게 규명하기 위해 필요한 정보를 의미한다.

시분할 시스템에서는 CPU의 제어권을 공유하기 때문에, 프로세스를 재개하는 시점에 대한 정보를 알기 위해서 process context를 사용한다.

process context에는 프로세스의 주소공간, 레지스터의 값, 시스템 콜 등을 통해 커널에서 수행한 일의 상태, 프로세스에 관해 커널이 관리하고 있는 각종 정보등을 포함한다.

process context의 내용은 크게 3가지로 나뉜다.
1. 하드웨어 문맥 : CPU의 수행상태로, PC와 register에 저장한 값들
2. 프로셋 주소 공간 : 코드, 데이터 스택으로 구성되는 주소 공간
3. 커널 상의 문맥 : PCB, kernel stack와 같은 자료 구

<hr>
</details>

<details>
<summary>IPC란 무엇일까요?</summary>

<hr>
OS가 제공하는 프로세스간 협력 메커니즘, Inter-Process Communication이다. 즉, IPC란 하나의 컴퓨터 안에서 실행중인 서로 다른 프로세스 간 발생하는 통신이다.

IPC는 대표적으로 Shared Memory와 Message Passing이 있다.

Message Passing은 두 프로세스 사이에 communication link을 생성해서 커널의 send(), recieve() 연산을 토해 메시지를 주고 받는다. 그리고 send와 recieve 연산은 system call을 통해 사용한다.

메시지 전달은 전송 대상이 다른 프로세스인지, 아니면 메일 박스라는 일종의 저장공간인지에 따라서 직접 통신과 간접 통신으로 나뉜다. 

Shared Memory는 데이터 자체를 공유하도록 지원하는 것이다. 

Shared Memory를 사용하면 특수한 공간이 생겨, process들이 각자 자신의 공간이라고 생각하면서 사용한다. 프로세스가 공유 메모리 할당을 커널에 요청하면 커널은 해당 프로세스에 메모리 공간을 할당해주고, 이후 모든 프로세스는 해당 메모리에 접근할 수 있다. 

이는 중개자 없이 곧바로 메모리에 접근할 수 있기 때문에 IPC 중에서 가장 빠르게 작동한다. 하지만, 2개 이상의 process가 동시에 접근하려는 process syncronization 문제와 multi processor에서의 Cache Coherence Problem이 발생한다. 
<hr>
</details>

<details>
<summary>스레드란 무엇일까요?</summary>

<hr>
CP가 동작하는 가장 작은 단위를 THREAD라고 한다. 

하나의 process는 한개 이상의 thread로 구성된다.

IPC 없이 바로 shared memory에 접근이 가능하다

process들끼리 바꾸는 context switching보다 thread을 변경하는 것이 overhead이 적다.

새로운 thread을 만들 때에는 pc, register, stack에 대한 공간만 만들면 되기 때문에 process을 만드는 것보다 memory와 time 측면에서 이점이 있다. 
<hr>
</details>

<details>
<summary>하나의 프로세스 안에서 만들어진 스레드들간 공유하는 공간과 독립적으로 할당하는 공간은 각각 무엇이 있을까요?</summary>

<hr>
공유 : Code, Data (OS resource)
각자 관리 : PC, Register, Stack (TCB로 관리)
<hr>
</details>

<details>
<summary>커널 스레드와 유저 스레드란 무엇일까요?</summary>
 
#### 커널 스레드
 - 운영체제가 직접 관리하는 스레드
 - 논리적 코어와 매핑되는 시스템의 실제 스레드
 - 커널 영역에서 스레드의 생성, 관리, 수행
 - 커널이 각 스레드를 개별적으로 관리
 - 프로세스 내 스레들이 병령 수행 가능
 - 하나의 스레드가 block되어도 다른 스레드는 계속 작업 가능

 - parallelism과 Concurrency를 지원하지만, kernel thread은 kernel을 통해서 operation을 하기에 무겁다
   
#### 유저 스레드
 - 유저 영역의 **라이브러리**로 구현된 스레드
 - 커널은 프로세스 내 유저 스레드를 알지 못한다.

 - user space 안 thread library에 의해서 관리되기 때문에, system call이 필요하지 않기에 빠르지만, 하나의 user thread가 system call을 만들면 전체 thread가 blocked 상태가 된다. 또한 Parallelism을 지원하지 않는다.
<hr>

<hr>
</details>

<details>
<summary>TCB란 무엇일까요?</summary>

<hr>
TCB(Thread Control Block)는 스레드를 관리하는 구조이다. ( 프로세스를 PCB를 통해 관리하는 것처럼)
- TCB의 정보는 PCB 안에 있다.
-각각의 kernel Thread에만 생성된다.
-PC, register의 정보를 갖고 있다.
-ready queue는 CPU를 기다리고 있는 TCB의 리스트로 context switch을 할 때마다 TCB들에 있는 PC, register정보로 변경한다.
<hr>
</details>

<details>
<summary>멀티 스레드의 장단점에 대해 설명해주세요.</summary>

<hr>
멀티 스레드란 하나의 프로세스에 여러 스레드로 자원을 공유하며 작업을 나누어 수행하는 것입니다.

### 장점

- 독립적으로 프로세스를 하나하나 생성하는 것에 비해 **PC, Register, Stack **에 대한 공간만 만들면 되기 때문에 memory와 time 측면에서 이점이 있다.
- 시스템의 처리율이 향상된다.
- 스레드 간 데이터를 주고 받는 것이 간단하고, 시스템 자원 소모가 준다.
- 스레드 사이의 작업량이 적어서 Context Switching이 빠르다(캐시 메모리를 비울 필요가 없다)
  - Non-blocking system call을 하여 효율적이다.
     - Single thread는 I/O작업을 하면 process전체가 waiting으로 가게 되는 blocking system인데 multi-thread process같은 경우는 하나의 thread가 I/O작업을 하여 해당 thread가 waiting으로 가더라도 다른 thread가 CPU를 할당받아 사용할 수 있는 Non-blocking system이다.
 - IPC 없이 Shared Memory에 접근 가능하기 때문에 응답 시간과 통신 비용이 단축된다.

### 단점

- 자원을 공유하기에 bottle neck, deadlock와 같은 동기화 문제가 발생할 수 있다.
- 주의 깊은 설계가 필요하고, 디버깅이 어렵다.
- 하나의 스레드가 전체 프로세스에 영향을 준다.
- 단일 프로세스 시스템의 경우 필요 없다.
<hr>
</details>

<details>
<summary>멀티 스레드와 멀티 프로세스의 차이에 대해 설명해주세요</summary>

<hr>
> 멀티 프로세스는 하나의 프로그램을 여러개의 프로세스로 구성해서 각 프로세스가 하나의 작업을 처리하는 것이다.
> 멀티 스레드는 하나의 프로세스에 여러 스레드가 자원을 공유하며 작업을 나누어 수행하는 것이다.

차이 

|멀티 프로세스 | 멀티 스레드 | 
|-------|-------|
| | 작은 메모리 공간 차지, Context Switching이 빠르다.|
| | 동기화 문제, 하나의 스레드 장애가 전체 스레드 종료로 이어질 수도 있다|
|프로세스 끼리 영향을 주지 않아 안정성이 높다.| |
| 많은 메모리 공간과 CPU 시간을 차지한다. | |
|동시에 여러 작업 수행| 동시에 여러 작업 수행|


<hr>
</details>

## CPU 스케줄링
<details>
<summary>장기, 중기, 단기 스케줄러에 대해 설명해주세요.</summary>

<hr>

#### 장기 스케줄러(job scheduler, 작업 스케줄러)

어떤 프로세스를 준비 큐에 진입시킬지 결정한다.

레디 큐에 있는 작업들은 CPU에서 실행되기 위해 프로세스 메모리를 보유하여야 하여, 장기 스케줄러는 메모리를 할당하는 문제에 관여한다 -> 메모리 할당 승인을 결정

메모리에 올라가 있는 프로세스의 수를 조절한다.
>현대의 시분할 시스템의 OS에서는 프로세스가 시작 상태가 되면 장기 스케줄러 없이 곧바로 프로세스에 메모리를 할당해서 준비큐에 넣어준다. -> 장기 스케줄러 대신 중기 스케줄러 사용


#### 단기 스케줄러( CPU scheduler)

Ready Queue의 프로세스 중에서 어떤 프로세스를 다음 번에 실행 상태로 만들 것인지 결정

시분할 시스템에서는 타이머가 인터럽트를 발생하면 단기 스케줄러 호출


#### 중기 스케줄러

현대 시분할 시스템용 OS에서는 중기 스케줄러를 더 많이 둔다(장기 스케줄러 대신)

너무 많은 프로세스에게 메모리를 할당해, 시스템의 성능이 저하되는 경우를 해결하기 위해 적재된 프로세스의 수를 동적으로 저절하기 위해 추가된 스케줄러이다. 

프로세스 당 보유 메모리양이 지나치게 적어진 경우, 일부 프로세스를 메모리에서 Swap out시키는 역할을 수행한다.

<hr>
</details>

<details>
<summary>선점과 비선점 스케줄링의 차이에 대해 설명해주세요</summary>

<hr>

### Non-Preemptive

- proess가 CPU를 스스로 놔줄 때까지 기다리는 스케줄링 방식이다.
- Process들은 종료 또는 I/O 작업을 하기 전까지는 CPU를 지속적으로 사용할 수 있다.
- context switch가 적게 일어나기 때무에 Overhead가 적다.
- 새로운 작업을 요청해도 자신의 순서까지 오래 기다려야 할 수도 있기 때문에 response time이 오래 걸린다.
- 바로바로 반응해야 하는 프로그램에는 좋지 않다.

### Preemptive

- interrupt을 통해 **강제로** CPU를 뺏는 방법이다.
- 현대 대부분의 OS는 Preemptive이다.
- race condition 이 발생한다.

> Race Condition이란 둘 이상의 입력 또는 조작의 타이밍이나 순서 등이 결과 값에 영향을 줄 수 있는 상태
> 두개 이상의 프로세스가 공유 자원에 접근할 때, 결과값에 영향을 줄 수 있는 상황으로, 동시 접근 시 자료의 일관성을 해치는 결과가 나타난다.

>이를 예방하기 위해서는 세마포어나 뮤텍스를 사용해야한다.

|Semaphore | Mutex | 
|------|------|
|동기화를 위한 도|동기화를 위한 도구|
|Signaling 메커니즘|Locking 메커니즘|
|Lock을 걸지 않은 Thread도 signal을 통해 Lock 해제 가능 | Locking 메커니즘으로 Lock을 걸은 Thread만이 임계 영역을 나갈 때 Lock을 해제|
Semaphore는 Signaling 메커니즘을 사용한다.

락을 걸지 않은 쓰레드도 Signal을 해제할 수 있기 때문에 wait 함수를 호출한 Thread만이 signal 함수를 호출할 수 있는 뮤텍스와 다르다.

wait을 호출하면 Semaphore의 카운트를 1 줄이고, Semaphore의 카운트가 0보다 작거나 같아질 경우에 Lock이 실행된다.

뮤텍스는 자원에 대한 접근을 동기화하기 위해 사용되는 상호배제 기술이다. 뮤텍스는 Locking 메커니즘으로 오직 하나의 Thread만이 동일한 시점에 Mutex를 얻어 임계 영역에 들어올 수 있고, 이 Thread 만이 임계 영역에서 나갈 때 뮤텍스를 해제할 수 있다.

<hr>
</details>

<details>
<summary>CPU Scheduling을 측정하는 척도에는 무엇이 있을까요?</summary>

<hr>
1. CPU utilization : CPU를 얼마나 사용하는지 => 높을 수록 효율적이다.
2. Throughput : 시간당 수행한 작업의 양
3. Turnaround Time : 프로세스가 생성되고 종료되기까지 걸린 시간, waiting 시간, 실행 시간 다 합친 것
4. Waiting Time : ready queue에서 기다린 총 시간, waiting queue에서 기다린 전체 시간
5. Response time : 프로세스가 생성되고 **첫번째 응답**이 있기까지 걸린 시간, Interactive and real time system 프로그램 측정에 사용된다. 

<hr>
</details>

<details>
<summary>CPU Scheduling의 종류에는 무엇이 있을까요?</summary>

<hr>
여기 시간 들여
<hr>
</details>

<details>
<summary>Starvation은 어떤 스케줄링에서 발생하는 문제일까요?</summary>

<hr>
Priority Scheduling에서 우선 순위가 높은 process들이 계속 들어오면 우선순위가 낮은 process는 실행되지 않고, 무한정 대기하게 되는 이러한 문제를 Starvation이라고 한다.

priority Scheduling, SJF Scheduling에서 발생한다.
<hr>
</details>

<details>
<summary>Aging이란 무엇일까요?</summary>

<hr>
Aging이란 Starvation을 해결하는 방법 중 하나로, process마다 시간이 지나면 지날수록 우선순위를 높여주는 방식이다.
<hr>
</details>

<details>
<summary>선점 스케줄링과 비선점 스케줄링에는 각각 어떤 것이 있을까요?</summary>

<hr>

#### 선점 스케줄링
- SRTF
- RR
- Multi level Queue
- 다단계 피드백 큐

#### 비선점 스케줄링
- FCFS
- SJF
- Priority
- HRN
<hr>
</details>

## Synchronized
<details>
<summary>경쟁 상태(Race Condition)이란 무엇이며 언제 발생할까요?</summary>

<hr>
multicore CPU에서 두개 이상의 프로세스가 parallel하게 실행되는 경우, 또는 두개 이상의 프로세스가 하나의 single core에서 concurrently하게 실행되는 등 **공유 자원에 동시 접근하는 경우, 두개 이상의 프로세스를 두고 경쟁하는 문제를 Race Condition**이라고 한다.

### Race condition이 발생하는 경우

1. Kernel작업 중, **Interrupt**

문제점 : 커널 모드에서 데이터를 로드하여 작업을 수행하다가 인터럽트가 발생해서 같은 데이터를 조작하는 경우

해결법 : 커널 모드에서 작업을 수행하는 동안, Interrupt을 disable시켜, CPU 제어권을 가져가지 못하도록 한다. 

2. 프로세스가 System Call을 해서 커널모드로 진입하여 작업 수행 도중 **Context Switching**이 발생했을 경우

문제점 : P1이 커널모드에서 데이터를 조작하는 도중, 시간이 초과되어 CPU제어권이 P2로 넘어가 데이터를 조작하는 경우

해결법: 프로세스가 커널모드에서 작업을 하는 경우 시간이 초과되어도 CPU 제어권이 다른 프로세스에게 넘어가지 않도록 함

3. 멀티 프로세서 환경에서 **공유 메모리 내의 커널 데이터에 접근**할 때

문제점 : 멀티 프로세서 환경에서 2개의 CPU까 동시에 커널 내부의 공유 데이터에 접근.조작하는 경우

해결법 : 커널 내부에 있는 공유 데이터에 접근할 때마다, 그 데이터에 대해서 lock/unlock을 함

<hr>
</details>

<details>
<summary>임계영역(Critical Section)에 대해 설명해주세요</summary>

<hr>
각각의 process들은 shared data를 접근하는 부분에 critical section이라고 불리는 code segment을 가지고 있다.

동시간대에 하나의 process만 critical section을 실행할 수 있다.

각각의 process들은 critical section에 들어갈 때 `entry section`에서 permission에 대해 물어보고 사용한다. 실행을 마치면 `exit section`을 통해 사용을 마쳤다는 것을 알리고, `remainder section`을 이어서 실행시킨다.

Critical section에는 필요 조건이 있다.

1. **Mutual Exclusion** : 하나의 프로세스가 들어오면 다른 프로세스는 못 들어온다
2. **Progress** : Critical Section을 실행하는 프로세스가 없을 때는 원하는 프로세스는 누구나 들어갈 수 있다.
3. **Bounded** **Waiting** : 각각의 process들은 몇번의 시도안에 Critical Section에 들어갈 수 있어야 한다.

-> Critical Section은 Mutex Lock또는 Semaphore로 구현된다.

<hr>
</details>

<details>
<summary>Mutex Lock과 Semaphore에 대해 설명해주세요. (+ 둘은 어떤 차이가 있나요?)</summary>

<hr>
많은 시스템들은 syncronization을 위해서 atomic hardware instruction의 도움을 받는다. Atomic Instruction은 interrupt을 발생하지 않는다.

Mutex Lock과 Semaphore는 atomic instruction을 사용하기 위한 tool이다. 둘은 atomic instruction의 지원을 받아서 Critical Section을 구현한다.

## Mutex Lock

- (동기화 대상이 하나) 임계 구역을 가진 Thread들의 실행시간이 겹치지 않고, 각각 단독으로 실행되게 하는 기술이다.
- 공유된 자원의 데이터 혹은 Critical Section등에 하나의 Process 혹은 Thread만 접근하도록 지원한다.
- **Mutual Exclusion**의 약자이다.
- 해당 접근을 조율하기 위해 lock과 unlock을 사용한다. 누군가 lock을 가지면 다른 process들은 critical section에 들어가지 못한다.
   - lock : Critical Section에 들어갈 권한을 얻는다.
   - unlock : Critical Section을 모두 사용했음을 알린다.
 

 ## Semaphore

- (동기화 대상이 하나 이상) 공유된 자원의 데이터 혹은 Critical Section등에 *정해진 수의* process 혹은 Thread만 접근하도록 지원한다.
- Semaphore의 S라는 integer variable을 갖고 Critical Section을 관리한다.
- Wait(S)와 signal(S)는 atomic instruction이다.
- Semaphore 는 mutex lock보다 활용도가 높다.
- Semaphore의 크기에 따라 Binary와 Counting가 존재한다.
- Deadlock과 Priority Inversion의 문제가 발생한다.

#### Binary Semaphore
Semaphore 값이 0,1로 Mutex Lock과 동일하다.

누가 쓰면 semaphore는 0, 안 쓰면 1

#### Counting Semaphore
Semaphore의 값이 다양해서, 여러 개의 thread과 resource를 동시에 이용할 수 있게 해준다.

## 둘의 차이
|Mutex|Semaphore|
|-----|------|
|동기화 대상이 하나|동기화 대상이 하나 이상|
|자원을 소유하는 게 가능|자원 소유는 불가능|
|상태가 0,1이기에 Lock 가능, 소유하고 있는 Thread만이 Mutex해제 가능 | Semaphore를 소유하지 않고 있는 Thread도 Semaphore 해제 가능|
|프로세스 범위를 갖는다|시스템 범위에 걸쳐 있다.|
|프로세스 종료 시, 자동으로 Clean up|파일 시스템 상으로 파일로 존재|


<hr>
</details>

<details>
<summary>Priority Inversion은 무엇일까요?</summary>

<hr>
Priority Inversion은 Priority Scheduling에서 발생할 수 있는 문제로, 우선 순위가 높은 프로세스가 필요로 하는 자원을 우선순위가 낮은 프로세스가 lock을 걸고 있을 때 발생하는 문제이다. 

![image](https://github.com/user-attachments/assets/34b5a0a8-588e-4edc-83a1-c34519f91087)

- 낮은 우선순위를 가진 L이 resource R을 이용중이다.
- 높은 우선순위를 가진 H가 ready queue에 추가되면서 먼저 수행을 하려고 한다.
- 하지만 L이 interrupt을 발생시키지 못하도록 semaphore에 접근중이라서 H는 L의 수행이 완료 될 때까지 대기한다. (이건 Priority inversion 아님)
- 이때 R에 접근 하지 않고 싶어하는 M이 ready queue에 추가되면 R에 관련없는 M은 preemption을 발생시켜 L을 종료 시키고 M을 수행한다. M이 preemption이 발생해서, H가 M까지 기다리게 하는 일이 priority inversion이다. 
<hr>
</details>

<details>
<summary>데드락(Deadlock)이란 무엇이며 언제 발생할까요?</summary>

<hr>
데드락은 두개 이상의 process나 Thread가 서로 자원을 얻지 못해서 다음 작업을 하지 못해, 무한히 다음 자원을 기다리는 상태이다.

자원의 종류로는 
1. Physical resource Type : I/O device, memory space, CPU Cycle등
2. Logical resource Type : semaphore, mutex lock, file 과 같이 물리적으로 존재하지 않지만, 여러 process가 같이 사용하는 자원

   ## 데드락이 발생하는 조건
데드락이 발생하기 위해서는 4가지 조건을 만족해야 한다.

1. Mutual Exclusion
   자원에 대해서 한개의 process만이 점유할 수 있다.
2. Hold and Wait
   최소한 하나의 자원을 점유하고 있으면서, 다른 프로세스에 할당되어 사용하고 있는 자원을 추가로 점유하기 위해서 대기하는 프로세스가 존재해야 한다.
3. No Preemption
   강제로 뺏기 불가능
4. Circular wait
   사이클 존재

<hr>
</details>

<details>
<summary>데드락 예방, 회피, 무시에 대해 각각 설명해주세요.</summary>

<hr>

## 데드락 예방 ( Prevention)
데드락 발생 조건 4가지 중 하나만 없애도 Deadlock을 예방할 수 있다.하지만, 실현 불가능한 case들이 존재하고 resource 낭비가 심해져서 utilizatin이 낮아진다.

1. No mutual Exclusion

- 같은 시간에 자원을 공유 가능하도록 한다.

##### Problem : Mutual Exclusion을 없애면 deadlock을 예방하지만, race condition이 발생한다.

-> 공유 할 수 없는 자원(Mutex lock, printer)도 존재하기도 하여서, mutual exclusion을 없애는 건 어렵다.

2. No Hold and Wait

- 프로세스가 resource을 요청할 때마다 다른 리소스를 보유하지 않도록 보장한다.
- Total Allocation : 필요로 하는 자원들을 모두 이요할 수 있을 때까지 기다렸다가 한번에 allocation 받아서 hold and wait을 없앤다.

##### Problem : 작업이 끝난 resource도 가지고 있어서, resource Utilization이 떨어진다.

3. Allow Preemption

- Preemption을 허용한다.(RR)

###### Problem : CPU같은 경우에는 괜찮지만, Semaphore는 불가능하다.

4. No Circular Wait
- Total Ordering : 자원 타입별로 전체적인 순서를 정하고, order의 수를 높여가며 자원을 요청해서 없앤다.\

##### Problem : 항상 순서에 따라 자원을 요청해야 한다.


## 데드락 회피

요청이 왔을 때, safe 상태면 받는다.(safe = 절대 데드락이 일어나지 않는 상태)

만약, unsafe면 요청을 거부한다.

instance 수에 따라서 Resource-Allocation Graph Algorithm,과 Banker's Algorithm이 존재한다.


## 데드락 무시

Ostrich Algorithm : Ignore the problem and pretend that deadlocks never occur in the system.

실제 시스템에서는 deadlock prevention,이나 avoidance는 overhead가 커서 안 쓴다.

실제는 ignorance가 더 많이 쓰인다.

만약 deadlock에 빠지면 DEADLOCK RECOVERY(재부팅, 프로세스 종료, resource 강제로 빼앗기)등 한다.

- Deadlock Detection : 자원 할당 그래프를 통해서 데드락 탐지

- Recovery : 프로세스 종료, 자원 선점. 

<hr>
</details>

## 메모리
<details>
<summary>메모리 계층 구조를 설명해주세요</summary>

<hr>
메모리 게층 구조란, 메모리를 필요에 따라 (CPU가 메모리에 더 빠르게 접근하기 위해서) 여러 가지 종류로 나누어 둠을 의미한다.

메모리 계층 구조를 바탕으로 컴퓨터를 설계해, 여러 상황에 맞는 여러 저장 장치를 각각의 역할이나 특징을 기반으로 사용하여 최적의 효울을 낼 수 있도록 한다.
![image](https://github.com/user-attachments/assets/afcaa1e3-44da-4f5b-8bab-1b4ef2f8131f)
### Register
- CPU가 요청을 처리하는데 필요한 데이터를 **일시적**으로 저장하는 기억 장치이다.
- CPU 안에 존재한다.

### Cache
- 캐시는 지역성의 원리를 사용해서 얻고자 하는 데이터를 필요한 순간마다 데이터가 저장되어 있는 저장소에서 가져오는 일에 대한 시간을 줄일 때 사용되는 임시 저장소이다.
- 메인 메모리의 접근을 빠르게 하기 위한 CPU CACHE, 하드 디스크에 내장된 DISK CACHE(== DISK BUFFER), PAGE CACHE(TLB) 등이 존재한다.

### Main Memory
- 1차 기억장치(주 기억장치)로, 실행중인 프로그램이 올라가는 메모리 공간이다.
- 휘발성 장치인 RAM과 고정 장치인 ROM이 존재한다.

### Hard Disk Drive(HDD)
- **비휘발성**으로 순차 접근이 가능한 **보조 기억 장치** 이다

## 메모리 계층 구조의 목적
- 전체 기억 장치를 구성하는데 있어, 가격은 최소화하면서 빠른 접근 속도와 대용량의 크기를 제공하는 입출력의 경제성을 확보를 목적으로 두고 있다.
- 자주 쓰이는 데이터만 자주 쓰이는 지역성 특징 때문에 자주 쓰이는 데이터들은 메모리에서 CACHE로 올린다.
- 메모리는 상위 계층으로 갈 수록 비싸다. 그렇기에, 계층적으로 구성하여 효율적인 구동을 위해 필요한 데이터들만 상위 계층으로 올린다. 
<hr>
</details>

<details>
<summary>가상 주소는 왜 사용할까요?</summary>

<hr>
Logical Adrress는 메모리의 공간이 한정적이기 때문에, 사용자에게 더 많은 메모리를 제공하기 위해서 등장했다. 가상 주소는 프로그램 상에서 사용자가 보는 주소 공간이다. 각각의 process들은 실제 physical memory address를 사용하지 않고, logical address를 사용한다. 
<hr>
</details>

<details>
<summary>주소 바인딩(Address Binding)의 3가지 방법은 무엇이 있으며 각각의 특징에 대해 설명해주세요.</summary>

<hr>
주소 바인딩은 CPU가 기계어 명령을 수행하기 위해서 논리적 주소를 통해 메모리 참조를 하게 되면 논리적 주소가 물리적 메모리와 매핑된다. 이렇게 논리적 주소를 물리적 주소와 연결 시켜주는 것이 Adress Binding 이다.

이에는 Compile time Binding, Load Time Binding, Execution Time Binding(Run Time Binding) 이 있다. 

### 1. Compile Time Binding
- 컴파일 하는 시점에 해당 프로그램의 물리적 메모리의 위치가 결정된다.
- 프로그램이 절대 주소를 적재시키는 절대코드를 생성한다.
- 프로그램이 올라가 있는 물리적 메모리 위치를 변경하고 싶다면 다시 컴파일 해야 한다.
     - 이러한 이유 때문에 시분할 컴퓨팅 환경에서 잘 사용하지 않는다.


### 2. Load Time Binding
- 프로그램이 실행이 시작될 때, 물리적 메모리 주소가 결정된다.
- 프로그램을 메모리에 적재시키는 프로그램인 Loader의 책임 하에 물리적 메모리 주소가 부여되며, 프로그램이 종료될 때 까지 물리적 메모리 상의 위치가 고정된다.
- 컴파일러가 재배치 가능 코드를 생성한 경우에 가능한 방식이다.
  > 재배치 가능 코드란 프로그램이 실행될 때, 적재되는 순간에 주어진 메모리 주소(base + 10...)에 맞춰서 조정될 수 있는 코드이다.
- 물리적 메모리 위치를 변경하고 싶다면 Reload를 해야 한다(recompile보다는 소모가 적다)

### 3. Execution Time Binding
- 프로그램이 시작한 후에도 프로그램이 위치한 물리적 메모리상의 주소가 변경될 수 있다.
- CPU가 주소를 참조할 때마다 해당 데이터가 물리적 메모리의 어느 위치에 있는지, address mapping table을 이용해서 바인딩을 점검해야 한다.
- 실시간 바인딩이 가능하기 위해서는 **base register** 와 **limit register**를 포함해서 **MMU(Memory Management Unit** 이라는 하드웨어적인 자원이 필요하다.
- 대부분의 OS가 이 방법을 사용한다.
- 물리적 메모리 위치를 바꾸고 싶다면 relocation Register의 값만 바꾸면 된다. (매우 간편)
<hr>
</details>

<details>
<summary>MMU란 무엇일까요?</summary>

<hr>
MMU는 논리적 주소를 물리적 주소로 매핑해주는 하드웨어 장치이다.

CPU가 특정 프로세스의 논리적 주소를 참조하려고 할 때, MMU 기법은 해당 주소값에 기준 레지스터의 값을 더해서 물리적 주소값을 얻어낸다.
- 이때 프로세스의 물리적 메모리 시작 주소인 기준 레지스터를 **Relocation register(재배치 레지스터)** 라고 한다.

![image](https://github.com/user-attachments/assets/739da2be-0da8-48df-b2fd-e05127dbc039)

- process 마다 각기 다른 relocation register, limit register를 갖고 있으며, 이를 통해서 logical address space를 정의한다. 이는 PCB에 저장
  - Context Switching으로 CPU에서 수행중인 프로세스가 바뀔 때마다, **Relocation Register의 값을 해당 프로세스에 해당하는 값으로 재설정함** 으로써 프로세스 별로 adress binding을 올바르게 할 수 있다.
- MMU는 권한이 없는 다른 프로세스의 물리적 주소 공간으로의 침범을 막기 위해서 Limit Register(한계 레지스터)를 이용해서 메모리 보안을 한다.
  if 논리적 주소 < Limit Register에 저장된 프로세스의 크기 :
    논리적 주소 += relocation register -> 물리적 주소룰 찾는다
  else :
    TRAP! -> 프로세스 강제 종료

##정리
1. 논리적 주소 -> 물리적 주소 매핑
2. 메모리 보호!

<hr>
</details>

<details>
<summary>캐시란 무엇일까요?</summary>

<hr>
주기억 장치에 저장된 내용의 일부를 임시로 저장해서, CPU와 주기억장치의 속도 차이로 성능 저하를 방지해준다.

CPU에서 메인 메모리에 접근하기 이전에 먼저 Cache를 확인하고, 만약 데이터가 존재한다면 Cache hit-> 바로 해당 명령어 사용, 데이터가 존재하지 않는다면 Cache miss -> Main memory 접근

이를 통해서 메모리 접근 비용을 아낄 수 있다.

Cache Hit을 극대화 시키기 위해서는 지역성의 원리를 이용한다.
<hr>
</details>

<details>
<summary>지역성(Locality)이란 무엇일까요?</summary>

<hr>
기억 장치 내의 정보를 균일하게 access하는 게 아니라, 한순간에 특정 부분을 집중적으로 참조하는 특성을 의미한다.

#### -시간 지역성
 최근에 참조된 주소의 내용은 곧 다음에도 참조된다는 특성

#### - 공간 지역성
 실제 프로그램이 참조된 주소와 인접한 주소의 내용이 다시 참조되는 특성

<hr>
</details>

<details>
<summary>동적 로딩과 동적 연결에 대해 각각 설명해주세요</summary>

<hr>

### 동적 로딩(dynamic loading)

- 동적 로딩은 여러 프로그램이 동시에 메모리에 올라가서 수행되는 다중 프로그래밍 환경에서 메모리 사용의 효율성을 높이기 위해 사용하는 기법 중 하나이다.
- 프로세스가 시작될 때 프로세스의 주소 공간 전체를 메모리에 다 올리는 것이 아닌 실행에 필요한 부분이 실제로 불릴 때마다 해당 부분만을 메모리에 적재하는 방식으로 동작한다.
- 기존 방식에 비하여 더 많은 프로그램을 메모리에 적재할 수 있어 효율성이 향상된다.
- 운영체제의 특별한 지원 없이 프로그램 자체에서 구현이 가능하며 운영체제가 라이브러리를 통해 지원할 수도 있다.

### 동적 연결(dynamic linking)

> Linking은 프로그래머가 작성한 소스코드를 컴파일하여 생성된 object 파일과 이미 컴파일된 library file들을 묶어 하나의 실행파일을 생성하는 과정을 말한다.
>
- 컴파일을 통해 생성된 object 파일과 라이브러리 파일 사이의 연결을 프로그램의 실행 시점까지 지연시키는 기법이다.
- 기존의 방식(정적 연결, static linking)에는 동일한 라이브러리를 각 프로세스별로 메모리에 적재하느라 물리적 메모리의 낭비가 발생하였다. 하지만 동적 연결은 라이브러리가 실행시점에 연결되어 실행코드가 포함되지 않으며 다수의 프로그램이 사용하는 라이브러리를 메모리에 한번만 적재하여 메모리 효율성을 높일 수 있다.
- 동적 연결을 가능하기 위해 실행파일의 라이브러리 호출 부분에 해당 라이브러리의 위치를 찾기 위한 스텁(stub)이라는 작은 코드를 둔다. 라이브러리 호출 시 스텁을 통해 해당 라이브러리가 메모리에 이미 존재하는지 살펴보고 그럴 경우 해당 주소의 메모리 위치에서 직접 참조하며, 그렇지 않을 경우 디스크에서 동적 라이브러리 파일을 찾아 메모리로 적재한 후 수행하게 된다.
- 동적 연결 기법은 운영체제의 지원을 필요로 한다.


<hr>
</details>

<details>
<summary>스와핑(Swapping)에 대해 설명해주세요</summary>

<hr>

- 스와핑이란 메모리에 올라온 프로세스의 주소 공간 전체를 디스크의 스왑 영역(Swap area)에 일시적으로 내려놓는 것을 말한다.
  - 스왑 영역을 백킹 스토어(backing store)라고도 부르며 디스크 내에 파일 시스템과는 별도로 존재하는 일정 영역이다.
    - 스왑 영역은 프로세스가 수행중인 동안에만 일시적으로 저장하는 공간인 저장 기간이 짧은 공간이다.
- 프로세스가 종료되어 주소 공간을 디스크로 내쫓는 것이 아니라 특정한 이유로 수행 중인 프로세스의 주소 공간을 일시적으로 메모리에서 디스크로 내려놓는 것이다.
- 발생하는 과정
  1. 스와퍼(swapper)라고 불리는 중기 스케줄러에 의해 스왑아웃 프로세스를 선정
  2. 스왑 아웃 대상으로 선정된 프로세스에 대해서는 메모리에 올라가 있는 주소 공간의 내용을 통째로 디스크 스왑 영역에 스왑아웃
- 스와핑은 메모리에 존재하는 프로세스의 수를 조절하며 다중 프로그래밍 정도를 조절한다.

> compile time binding과 load time binding 방식에서는 스왑 아웃된 프로세스가 다시 스왑 인 될 때에는 원래 존재하던 메모리 위치로 다시 올라가야한다. 하지만 run time binding의 경우 빈 메모리 영역 아무 곳에나 프로세스를 올릴 수 있다.

<hr>
</details>

<details>
<summary>메모리의 연속 할당과 불연속 할당에 대해 설명해주세요</summary>

<hr>
각각의 프로세스를 물리적 메모리의 연속 공간에 올리는 방식이다.

물리적 메모리를 다수의 분할로 나누어, 하나의 분할에 하나의 프로세스가 적재되도록 한다.

물리적 메모리를 분할하는 방식에 따라, 고정 분할과 가변 분할 방식으로 나뉜다.

#### Fixed Partition allocation(고정 분할)
- 물리적 메모리를 고정된 크기의 분할로 미리 나누어두고, **각 분할에 하나의 프로세스**를 실행시키는 방식이다.
- 분할의 크기는 모두 동일하게, 다르게 설정 가능하다.
- 하나의 분할에 하나의 프로그램만 적재할 수 있어, 메모리에 올릴 수 있는 프로그램 수가 제한된다.
- 문제 : **Internal Fragmentation(내부 단편화)** 가 발생할 수 있다.

#### Variable Partition allocation(가변 분할)
- 미리 나누지 않고, 프로그램이 실행되고 종료되는 순서에 따라 분할을 관리하는 방식이다.
- 메모리에 적재되는 프로그램의 크기에 따라 분할의 크기, 개수가 동적으로 변한다.
- 문제 : **External Fragmentation(외부 단편화)** 가 발생할 수 있다.

프로세스를 메모리에 올릴 때, 물리적 메모리 내 가용 공간 중 어떤 위치에 들어갈 지 결정하는 **Dynamic Storage-allocation Problem** **(동적 메모리 할당 문제)** 가 중요한 쟁점이다.

1. First Fit : 스캔을 하며 프로그램을 적재할 수 있는 최초의 가용 공간에 적재
2. Best Fit : 모든 공간 스캔, 최적의 공간에 적재( 시간적 오버헤드, 공간 측면에서는 효율적)
3. Worst Fit : 가용 공간 중 가장 크기가 큰 곳에 새로운 프로그램을 할당

외부 조걱을 해결하기 위해서 사용중인 메모리 영역을 한곳에 몰아두는 **Compaction** 을 실행한다.
> Compaction은
> - process의 memory 공간을 옮겨서 하나의 큰 공간을 만들어 준다.
> - compile/load time binding에서는 recompile, reload을 해야해서 비효율적이다.
> - Executiaon TIme Binding 할 때만 적합하다.


#### 연속 할당의 장단점

장점
- 단순한 연산을 통해서 할당, 빠르고 편함
- 연산에 필요한 하드웨어는 Limit Register, Relocation Register 두개 뿐이다.

단점
- 연속적으로 할당을 하니, process가 더 많은 공간을 할당 받기 위해서는 process의 위치를 옮기는 어려움이 있다.
- 자신만의 virtual address를 physical address로 할당받아서 사용하기에, 메모리 공유가 어렵다. (프로세스는 base ~ limit 사이의 주소 접근만 가능해서 shared memory로 접근할 방법이 없다.
- external fragmentation이 발생한다.

## 불연속 할당
- 하나의 프로세스를 물리적 메모리의 여러 영역에 분산해서 적재하는 방식이다.
- 대부분의 현대 OS
- 1. 프로그램을 동일한 크기로 나누어 메모리에 올리는 **Paging**
  2. 크기는 일정하지 않지만, 의미 단위로 나누어 메모리에 올리는 **Segmentation**
  3. Segmentation 기본, 다시 동일 크기의 페이지로 나누어 메모리에 올리는 **Paged Segmentation**

<hr>
</details>

<details>
<summary>페이징(Paging)에 대해 설명해주세요</summary>

<hr>

- 프로세스의 주소 공간을 동일한 크기의 페이지 단위로 나누어 물리적 메모리의 서로 다른 위치에 페이지들을 저장하는 방식이다.
- 프로세스의 주소 공간 전체를 올릴 필요 없이 일부는 Backing Store에, 일부는 물리적 메모리에 혼재 시키는 것이 가능하다.
- 물리적 메모리는 고정된 사이즈의 physical frame으로, 논리적 메모리는 고정되 사이즈의 virtual page로 나뉘게 된다. frame size와  page size는 동일
  - 동일한 크기의 프레임을 가져, 가변 분할의 동적 메모리 할당 문제가 발생하지 않는다.
- External Fragmentation 는 발생하지 않고, Internal Fragmentation이 발생한다.
- **Page Table** 은 논리적 주소 -> 물리적 주소
   - 논리적 주소 -> 페이지 번호 + 페이지 오프셋, -> address allocation -> Page Table 접근 Indx : 페이지 번호, 해당 인덱스의 Entry(항목)에는 그 페이지의 물리적 메모리의 기준 주소(Base address)가 저장된다.
   - 페이지 번호(P)를 통해서 base address를 알 수 있고, base address +  offset => 물리적 주소
 - Page Table이 MMU 역할을 한다. 
> MMU(Memory Management Unit)는 **논리적 주소를 물리적 주소로 매핑해주는 하드웨어 장치**이다.

- Page Table 접근
  - 현재 CPU에서 실행중인 프로세스의 Page Table에 접근하기 위해서 OS는 **PTBR(Page Table Base Register)** 와 **PTLR(Page Table Length Register)** 을 사용한다.
    - PTBR = 메모리 내에서 페이지 테이블의 시작 위치
    - PTLR = 페이지 테이블의 크기
  - 페이징 기법에서 메모리 접근 연산은 주소 변환을 위한 페이지 테이블 접근, 변환된 주소를 통한 실제 데이터 접근으로 2번의 메모리 접근이 필요하다. 이러한 페이지 테이블 접근 오버헤드를 줄이고 메모리 접근 속도를 향상 시키기 위해서 주소 변환용 하드웨어 캐시인 **TLB(Translation Look-aside Buffer)** 를 사용한다.
 
  - **TLB** 는 비싸기 때문에, 빈번하게 참조되는 페이지에 대한 주소 변환 정보만 담는다.
  - 프로세스 별로 주소 변환 정보가 달라서 context switching이 발생하면 이전 프로세스의 주소 변환 정보를 담고 있는 TLB 내용을 지운다.
  - 프로세스의 주소 공간이 커지면 Page Table 크기도 커져서, 주소 변환을 위한 메모리 공간 낭비가 심해지고, 이를 위해 2,3,4... 단계의 다단계 Page Table이 필요하게 된다.
  - 다단계 Page Table은 메모리 공간 소모는 줄이지만, 메모리 접근 횟수가 많아지는 문제가 있다.
  - 이는 TLB를 사용하면 메모리 접근 시간에 대한 시간적 효율성도 얻을 수 있다. (다단계 페이지는 공간적인 이득, TLB는 접근에 대한 이득)

 - 여러 프로세스에 의해 공유되는 페이지를 물리적 메모리에 하나만 적재하여 메모리를 조금 더 효율적으로 사용할 수 있다.
 - 공유 페이지는 읽기 전용 성질을 가지고, 모든 프로세스의 논리적 주소 공간안에서 동일한 위치에 존재해야 한다는 제약이 있다.

- Protection Bit(보호 비트)를 통해서 프로세스 내에서 읽기-쓰기/ 읽기 전용 등의 접근 권한 설정 가능
- Valid-Invalid Bit(유효-무효 비트)를 통해서 해당 페이지가 메모리에 존재하는지, 존재하지 않는지에 대한 정보를 나타낸다.

## Paging이 필요한 이유(장점)
1. Provides Transparency
2. No external fragmentation
> Noncontinuous Memory allocation을 사용하기에 external fragmentation은 없지만, 정해진 사이즈의 page 내의 빈 공간이 발생해서 Internal Fragmentation은 생긴다.
> page size을 줄이면 internal fragmentation이 줄어드나, page 수가 증가해서 page table의 크기 증가 -> page 탐색 시간 증가 -> disk transfer 증가(일반적으로는 4kb 사용)
> page size와 internal fragmentation, page table size, disk IO efficiency는 Trade OFF한 관계이다. 

3. provides protection to memory
4. provides shared memory

<hr>
</details>

<details>
<summary>TLB에 대해 설명해주세요</summary>

<hr>
TLB(Translation Look-aside Buffer)는

페이징 기법에서 메모리 접근 연산은 주소 변환을 위해서 Page table 접근, 변환된 주소를 통한 실제 데이터 접근으로 2번의 메모리 접근이 필요하다. 

이러한 Page table 접근 오버헤드를 줄이고, 메모리 접근 속도 향상시키는 **주소 변환용 하드웨어 캐시** 인 TLB를 사용한다.

- TLB는 비싸서, 페이지의 모든 정보가 아닌 빈번하게 참조되는 페이지에 대한 주소 변환 정보만 담는다.
- process별로 주소 변환 정보가 다르기에 Context Switching이 발생하면 TLB에 있는 내용도 다 지워야 한다. 
<hr>
</details>

<details>
<summary>세그먼테이션(Segmentation)에 대해 설명해주세요</summary>

<hr>
Paging은 프로세스를 물리적으로 일정한 크기로 나눠서 메모리에 할당, Segmentation은 프로세스의 주소 공간을 code, data, stack와 같은 논리 단위 기능 단위로 나누어 저장하는 방식이다. 

Segmentation은 크기가 균일하지 않다.

논리적 주소가 `<세그먼트 번호, 오프셋>`으로 나누고, 주소 변환을 위해서는 Segmentation Table을 사용한다.
- Segment 별로 크기가 다르기 때문에 Segment Table은 각 항목은 Base(기준점)과 Limit(한계점)을 갖는다.
- Segmentation은 STBR, STLR(Paging에서는 PTLR, PTBR) 사용한다.
   - STBR : CPU에서 실행중인 프로세스의 Segment Table이 위치한 메모리 주소의 시작 위치
   - STLR : Segment 개수

- 보호 비트, 유효 비트 갖고 있고, 공유 세그먼트 사용 가능
- Segment는 의미 있는 단위로 나누기에 **공유와 보안** 측면에서 효과적이다.
- External Fragmentation 발생, Internal Fragmentation 안 발생( Paging과 반대)
- 메모리 연속 할당의 **Dynamic Storage-Allocation Problem** 이 발생한다. (동적 메모리 할당 문제) 
<hr>
</details>

<details>
<summary>페이지드 세그먼테이션(Paged Segmentation)이란 무엇일까요?</summary>

<hr>
꼭 알아야 하는 이론은 아닙니다.

페이징과 시그먼테이션의 장점만을 취하는 주소 변환 기법이다.

세그먼테이션과 마찬가지로 프로그램을 의미 단위의 세그먼트로 나눈다. 하지만 세그먼트가 임의의 길이를 갖는 것이 아닌 동일한 크기의 페이지들의 집합으로 구성된다.

하나의 세그먼트 크기를 페이지 크기의 배수가 되도록 함으로써 세그먼테이션 기법에서 발생하는 외부조각의 문제점을 해결하며 동시에 세그먼트 단위로 프로세스 간의 공유나 프로세스 내의 접근 권한 보호가 이루어지도록 함으로써 페이징 기법의 약점을 해소한다.

주소 변환을 위해 외부의 세그먼트 테이블과 내부의 페이지 테이블을 이용한다.(2개 이용)
<hr>
</details>

<details>
<summary>페이징과 세그먼테이션의 차이점에 대해 설명해주세요</summary>

<hr>

| Paging | Segmentation | 
| ----- | ----- |
| - | 보호, 공유 에서 유리|
|code, data, stack 부분이 일정한 크기로 나뉘기 때문에 영역이 섞여, 비트를 설정하기 까다롭다 | 권한을 논리적으로 나누고, 해당 정보를 테이블에 추가하는데 비트를 설정하기 간단하고 안전하다. |
|페이지 안에서 Internal Fragmentation|세그먼트 크기가 일정치 않아 External Fragmentation|
| - | Dynamic Storage Allocation Problem | 
|그래서 더 많이 사용 | - |

<hr>
</details>

<details>
<summary>가상 메모리란 무엇일까요?</summary>

<hr>

- 현대 컴퓨터 환경에서 가장 널리 사용되는 **메모리 관리 기법** 이다
- 물리적 메모리보다 더 큰 프로그램이 실행 지원
- 물리적 메모리와 독립적으로 0번지부터 시작하는 자신만의 가상메모리 주소를 갖고, OS는 가상 메모리의 주소를 물리적 주소로 매핑하는 기술을 사용해서 주소를 변환해, 프로그램을 물리적 메모리에 올린다.
- 프로그램이 돌아갈 때는 전체 프로그램을 메모리에 올리는 것이 아니라, 현재 필요한 부분만 올리고, 나머지는 Hard Disk와 같은 보조 기억장치(swap area)에 저장해뒀다가, 필요할 때 적재한다. -> **Demand paging** or **Demand Segmentation**


<hr>
</details>

<details>
<summary>외부 단편화(External Fragmentation)와 내부 단편화(Internal Fragmentation)에 대해 설명해주세요</summary>

<hr>

#### External Fragmentation
hole들이 조각나 있어서, 빈공간이 있음에도 불구하고, 새로운 process가 들어갈 공간이 없게 되는 현상

Segmentation, Continuous Memory Allocatin 의 **가변 분할** 등에서 발생


#### Internal Fragmentation
Page와 같이 정해진 크기로 나눠진 공간에 데이터를 넣다보면, 마지막 페이지의 경우 남은 공간이 발생한다.

Paging, Continuous Memory Allocation의 **고정 분할** 등에서 발생 
<hr>
</details>

<details>
<summary>Demand Paging에 대해 설명해주세요</summary>

<hr>

<hr>
</details>

<details>
<summary>페이지 교체(Page fault 처리)의 전반적인 순서에 대해 설명해주세요</summary>

<hr>

<hr>
</details>

<details>
<summary>페이지 교체 알고리즘은 어떤 것이 있을까요?</summary>

<hr>

<hr>
</details>

<details>
<summary>페이지의 전역 교체와 지역 교체에 대해 설명해주세요</summary>

<hr>

<hr>
</details>

<details>
<summary>스레싱(Thrashing)이란 무엇일까요?</summary>

<hr>

<hr>
</details>

<details>
<summary>워킹셋 알고리즘과 페이지 부재 빈도 알고리즘에 대해 설명해주세요.</summary>

<hr>

<hr>
</details>
