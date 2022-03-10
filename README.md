# 나를 위해 작성하는 Tech-interview

### keyword

> 프로세스와 스레드 Process & Thread

프로세스는 운영체제로부터 할당 받은 자원을 이용하는 작업의 단위이고, 스레드는 프로세스로부터 할당 받은 자원을 이용하는 실행의 단위입니다.

하나의 프로세스는 여러 스레드를 가질 수 있고, 각 스레드는 개별 스택을 가지며 프로세스의 전역 메모리 공간을 공유하며 프로그램을 실행합니다.

</br>

> 멀티

일반적으로 하나의 프로세스는 하나의 스레드를 가지고 있습니다.

1. 멀티 스레드 : 하나의 프로세스안에서 여러개의 스레드가 동시에 작업을 수행하는 것을 의미합니다.
2. 멀티 프로세스 : 여러개의 cpu가 여러개의 프로세스들을 동시에 수행하는 것을 의미합니다.
3. 멀티 테스크 : 운영체제가 cpu에게 작업을 줄때 시간을 잘게 배분하는 기법(시분할 기법)

멀티 프로세스는 각 프로세스들이 독립적인 메모리를 가지고 수행하지만, 멀티 스레드는 자신이 속한 프로세스의 메모리를 공유하며 수행합니다.

</br>

> 교착 상태 DeadLock

프로세스가 필요한 자원을 얻지 못해 계속 대기 상태에서 다음 과정을 처리하지 못하는 상태를 말합니다.

주로 멀티 프로그래밍 환경에서 한정된 자원을 가지고 경쟁하는 상황에 발생합니다.

</br>

> 교착 상태 발생 필요 조건

1. 상호 배제 : 자원은 한 번에 하나의 프로세스만 사용할 수 있다.
2. 비선점 : 사용하고 있는 자원은 강제로 빼앗을 수 없다.
3. 점유와 대기 : 하나의 프로세스는 하나의 자원을 점유하고 있으며, 다른 프로세스가 사용하고 있는 자원을 사용하기 위해 대기하고 있어야 한다.
4. 환형 대기 : 프로세스 집합에서 순환 형태로 자원을 대기하고 있어야 한다.

4가지를 모두 만족한다면 데드락이 발생할 가능성이 있다. 하나라도 만족하지 않으면 절대 발생하지 않는다.

</br>

> 교착 상태 처리 방법

1. 예방 : 교착 상태 조건을 하나씩 제거하면서 예방한다.
2. 회피 : 교착 상태가 일어나면 피해나가는 방법, 은행원 알고리즘이 대표적이다.
3. 탐지 & 회복 : 교착 상태를 허용한 후, 자원 할당 그래프를 통해 교착 상태를 탐지한 후, 교착 상태의 원인이 되는 자원을 해제시키거나 프로세스를 종료한다.

</br>

> 은행원 알고리즘

자원의 할당 허용 여부를 결정하기 전에, 자원의 가능한 할당량을 모두 시뮬레이션하여 안전 여부를 검사한다.

시스템을 항상 안정 상태로 유지시켜 데드락 발생을 막는다.

하지만, 시스템을 계속 감시하므로 오버헤드가 많다. 또한, 안전한 수행 순서가 존재하지 않더라도 데드락이 아닐 수도 있다.

</br>

> 레이스 컨디션 Race Condition

다수의 프로세스가 동일한 자원을 할당 받기 위해 경쟁하는 상태

</br>

> 동시성과 병렬성

동시성 : 하나의 cpu가 여러개의 프로세스를 context switching하며 프로세스를 조금씩 돌리면서 동시에 처리하는 것처럼 보이는 것

병렬성 : 여러개의 cpu가 여러개의 프로세스를 처리하는 것

</br>

> 컨택스트 스위칭 Context Switching

어떤 프로세스가 실행되고 있는 상태에서 인터럽트 요청에 의해 다음 프로세스가 실행되어야 할 때, 현재 프로세스의 값과 상태를 저장하고 다음 프로세스의 값과 상태로 교체하는 작업이다.
나가는 프로세스는 PCB에 지금까지의 작업 내용을 저장하고, 실행 상태로 들어오는 PCB의 내용으로 cpu가 다시 셋팅된다.

</br>

> PCB Process Control Block

cpu에 의해 실행되고 있는 프로세스의 정보를 포함하고 있는 운영체제 커널의 자료 구조이다.

</br>

> 프레임워크와 라이브러리

프레임워크 : 소프트웨어의 설계와 구현을 재사용할 수 있도록 협업화된 형태로 클래스나 인터페이스를 제공하는 것

라이브러리 : 자주 사용하는 로직을 재사용할 수 있도록 잘 정리해둔 코드들의 집합

</br>

> 가비지 컬렉터

프로그램이 동적으로 할당했던 메모리 영역 중에서 필요없게 된 영역을 해제하는 기능.

가비지 컬렉터가 있는 언어는 managed language라고 한다.

- mark and sweep : 아직 필요한 것들만 마크한 다음에 마크안된 것은 버린다.
- reference counting : 한 요소가 다른 요소에게 몇 번이나 참조 되는지 카운트하여 0번 이면 버린다.

</br>

> 동기와 비동기

동기 : 요청에 대한 응답을 기다린 후, 응답이 오면 다음 요청을 진행

- 순서대로 실행이 가능하지만, 여러 일을 동시에 실행하는 멀티태스킹은 불가능.

비동기 : 요청에 대한 응답을 기다리지 않고, 다음 요청을 진행

- 동시에 여러 일을 수행할 수 있지만, 요청량이 많아질 경우 부하가 발생할 수 있고, 뜻하지 않은 응답 순서를 받을 수 있다.

</br>

> OSI 7 Layer

물리 - 데이터링크 - 네트워크 - 전송 - 세션 - 표현 - 애플리케이션

</br>

> TCP/IP 4 Layer

링크 - 네트워크 - 전송 - 애플리케이션

- 링크 : 이더넷, DSL, 5G 등이 있다.
- 네트워크 : ip 프로토콜이 정의되어 있다. ip 패킷을 만들어준다.
- 전송 : TCP, UDP 프로토콜이 정의되어 있다. 세그먼트를 만들어준다.
- 애플리케이션 : http, smtp(전자 우편 전송 프로토콜), ftp(파일 전송 프로토콜), ssh 프로토콜 등이 정의되어 있다.

</br>

> TCP와 UDP 프로토콜

TCP : 전송 계층의 연결형 프로토콜이며 흐름제어, 오류제어를 하므로 신뢰성이 좋지만 전송 속도가 UDP보다 느리다.
3-way-handshaking 과정을 통해 연결을 설정하고 4-way-handshaking을 통해 해제한다.

- 연결과 해제 과정에서 차이가 나는 이유는 클라이언트 측에서 데이터 전송을 마쳤다 하더라도 서버 측은 아직 보낼 데이터가 남아있을 수 있기 때문이다.

UDP : 전송 계층의 비연결형 프로토콜이며 흐름제어, 오류제어를 하지 않아 신뢰성이 낮으나 전송 속도가 TCP보다 빠르다.
정보를 주고 받을 때, 정보를 보내고 받는다는 신호 절차가 없고, 헤더의 checksum 필드를 통해 최소한의 오류만 검출한다.

</br>

> CORS (cross-origin-resource-sharing)

도메인 또는 포트가 다른 서버의 지원을 요청하는 매커니즘을 말한다.

CORS가 발생하면 SOP(same-origin-policy) 브라우저의 동일 출처 정책으로 인해 외부 서버에 요청한 데이터를 브라우저에서 보안 목적으로 차단한다. 허가 방법으로 응답 헤더에 ACAO(acess-control-allow-origin)을 추가하여 특정 호스트와 포트를 허용시킬 수 있다.

</br>

> SOP (same-origin-policy)

서버에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 보안 방식이다.
이것은 잠재적인 악성 문서를 격리하여 공격 경로를 줄이는 데 도움이 된다.

</br>

> SQL & NOSQL (structured query language)

SQL : 정해진 데이터 구조에 따라 저장, 조회, 수정, 삭제를 할 수 있습니다. 관계를 통해서 여러개의 테이블로 분산시킬 수 있다.

NOSQL: 구조와 관계가 없는 비관계형 데이터베이스이다. sql에서는 특정 데이터 구조를 따르지 않는다면 데이터를 추가할 수 없지만, nosql에서는 다른 구조의 데이터를 같은 컬렉션에 추가할 수 있다.

</br>

> Cookie와 Session

cookie : 서버를 대신해서 인증 정보를 클라이언트에 저장시키고, 인증이 필요할 때 쿠키를 보낸다. 무거운 트래픽과 보안이 취악하다는 단점이 있다.

session : 쿠키의 단점을 보완하고자, 서버에 인증 정보를 저장하는 방식이며, 클라이언트에게 서버의 세션을 알 수 있게, 세션 id를 제공한다. 세션 id를 쿠키로 가지고 있어서, 둘은 하나의 인증 형태로 사용되고 있다.

</br>

> HTTP & HTTPS

html 문서와 같은 리소스들을 가져올 수 있도록 해주는 통신 프로토콜 tcp/id 위에서 동작한다. 기본 포트는 80번이다. 이전 상태를 기억하지 못하는 비상태성이고, 비연결형 프로토콜이다.

HTTP : 암호화가 되지 않는 평문 데이터를 전송하므로 보안에 취약하다.

HTTPS : 암호화가 추가된 프로토콜이며 공개키/개인키 암호화 방식을 이용하여 암호화한다. 기본 포트는 443번이다.

- HTTP 0.9 : 헤더가 없으며 GET방식 요청만 가능하고 응답으로는 html문서만 받는다.
- HTTP 1.0 : 헤더가 있고, POST방식이 추가됐으며, 문서 html이외의 문서도 전송가능하다.
- HTTP 1.1 : patch, put, delete가 추가 되었으며 현재 표준으로 사용되는 버전이다. 파이프라이닝이 추가되었다.

</br>

> 공개키/개인키 암호화

대칭키의 단점을 보완한 비대칭키, 공개키와 비밀키로 이루어져있고 공개키로 암호화하면 비밀키로 복호화하는 방식이다.

</br>

> HTTP status code

1xx : 조건부 응답, 요청을 받았으며 작업을 계속한다.

2xx : 성공, 클라이언트가 요청한 동작을 수신하여 이해했고 승락했으며 성공적으로 처리했음을 알린다.

3xx : 리다이렉션 완료, 클라이언트는 요청을 마치기 위해 추가 동작을 진행해야한다.

- 304 : 마지막 요청 이후, 요청한 페이지는 수정되지 않았다.

4xx : 요청 오류, 클라이언트에 오류가 있음을 나타낸다.

- 401 : Unauthenticated, 인증이 필요하다는 것을 나타낸다.
- 403 : Forbidden, 예를 들어 사용자가 리소스에 대한 권한을 가지고 있지 않을 경우 요청을 거부한다.
- 404 : Not Found, 서버가 요청한 페이지를 찾을 수 없다.

5xx : 서버 오류, 서버가 유효한 요청을 수행하지 못했음을 나타낸다.

</br>

> 객체 지향 프로그래밍 object-oriented-programming

여러개의 독립된 단위들의 모임을 지향하는 프로그래밍이다. 코드의 재사용성과 유지보수가 장점이다.
추상화, 캡슐화, 정보은닉, 상속, 다형성

</br>

> 오버로딩, 오버라이딩

오버로딩 : 같은 이름의 메소드가 여러개 있고, 매개변수의 타입이나 갯수로 구분하는 기술

오버라이딩 : 상위 클래스가 가지고 있는 메소드를 하위 클래스에서 재정의하는 기술

</br>


### data structure

> 힙(Heap)

완전 이진 트리의 일종으로 우선순위 큐를 위해 만들어진 자료구조. 최대 힙과 최소 힙을 구할 수 있다.
완전 이진 트리에서 자식 노드가 모두 채워져 있으면 포화 이진 트리라고 할 수 있다.

> 큐

먼저 들어간 데이터가 먼저 나오는 선입선출 자료구조.

> 깊이 우선 탐색(DFS)

루트 노드에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방법

> 너비 우선 탐색(BFS)

루트 노드에서 시작해서 인접한 노드를 먼저 탐색
