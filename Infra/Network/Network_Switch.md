Network Switch
=====================================

# Switch
* 호스트와 호스트간 네트워크 통신이 가능하게 서로 묶어주는 역할

# L2 Switch : **MAC Address**
* 일반적으로 부르는 스위치가 L2 스위치. 허브의 상위 장비
* 느리고 충돌이 생기는 허브의 단점을 개선
* 수신한 데이터 패킷의 목적지를 찾는데, 이 때 **MAC주소**를 기반으로 목적지를 찾고 해당 목적지에만 패킷 전송
* 연결되는 장비의  IP주소는 알 수 없음
* 동일 네트워크 내에서만 사용 가능
* 기본적으로 라우팅 기능 제외
* 상위 계층 프로토콜을 이용한 스위칭 불가(동일 프로토콜 간 스위칭만 가능)
* 데이터 링크 계층(L2)에서 사용
* 기능
> * Learning : 출발지 주소가 MAC테이블에 없으면 MAC테이블에 MAC주소 저장   
> * Flooding : 목적지 주소가 MAC테이블에 없으면 Broadcast   
> * Forwarding : MAC테이블을 참조한 후 목적지 주소가 있을 경우 목적지 포트에 1:1로 전송(Unicast)   
> * Filtering : 목적지 주소와 출발지 주소가 같을 경우 프레임 차단   
> * Aging : 일정한 시간이 지나면 MAC테이블의 활동이 없는 MAC주소 삭제   
* 동작 절차   
![l2switch1](https://user-images.githubusercontent.com/57285121/115484298-86c3cf00-a28d-11eb-94f9-45cb2bee2012.PNG)   
> 1. 포트 1번에 연결된 PC1(MAC주소 A)에서 PC2(MAC주소 B)로 프레임 전송   
> 2. L2 스위치의 MAC테이블에 PC1의 포트번호와 MAC주소 저장(Learning)   
> 3. 목적지 PC2의 MAC주소가 MAC테이블에 없으므로 모든 포트에 연결되어있는 PC에 프레임 전송(flooding)   
> 4. 포트 4번에 연결된 PC2(MAC주소 B)에서 PC1(MAC주소 A)로 프레임 전송   
> 5. L2 스위치의 MAC테이블에 PC2의 포트번호와 MAC주소 저장(Learning)   
> 6. 목적지 PC1의 MAC주소가 MAC테이블에 있으므로 해당 목적지(PC1)에 프레임 전송(forwarding)   
* 전송 방식
> * Cut-through : 프레임의 목적지 주소만 확인 후 전송. 프레임 처리 속도는 빠르지만 오류 감지는 어려움   
> * Store-and-forwarding : 프레임의 목적지 주소 뿐만 아니라 프레임 전체를 체크한 후 전송. 프레임 처리 속도는 상대적으로 느리지만 오류를 잘 감지할  수 있다.   
> * Fragment Free : 프레임의 일부분만 체크한 후 전송. Cut-through와 Store-and-forwarding방식을 적절히 혼합하여 사용하기 때문에 적당한 속도와 오류 감지가 가능하다.   
* 부가기능
> * VLAN : 가상의 LAN 생성, VLAN간 프레임 전송 구분   
> * Ling Aggregation : 단일 스위치의 물리적인 포트를 하나의 논리적인 포트로 만들어서 성능 향상   
> * Port Mirroring : 특정 트래픽 분석을 위해 프레임을 다른 포트로 복사   
* 장점 : 구조가 간단하고 가격이 저렴하여 구성이 쉬움
* 단점 : broadcast패킷에 의해 성능 저하가 발생할 수 있고, 라우팅이 불가능하다.

# L3 Switch : **IP Address**
* L2 스위치에 라우터 기능을 추가
* 서로 다른 네트워크 연결 가능
* 수신한 데이터 패킷의 목적지가 내부에는 없는 외부의 IP주소일 때 해당 패킷을 외부와 연결되어 있는 라우터
에 전송
* 패킷의 **IP주소**를 읽어 해당 목적지의 IP주소에 패킷 전송
* L2 Switch의 모든 기능을 사용할 수 있고 **라우팅** 기능이 추가됨
* 네트워크 계층(L3)에서 사용
* L3 스위치와 라우터의 차이점   
   
|항목|라우터|L3 스위치|   
|:----------:|:-------------:|:------:|   
|목적|네트워크 간 패킷 전송|네트워크 내/외부로 패킷 전송|   
|포트 수(규모)|10개 이내(소규모)|24개 이상(대규모)|   
|기능|오직 라우팅 기능만|라우팅 뿐만 아니라 스위칭 포함|   
|구현기반|Software + CPU|Hardware(ASIC chip)|   
|성능|상대적으로 느림|빠름|   
   
> * L3 스위치의 발전으로 라우터와 큰 차이가 없고 대부분 L3 스위치를 사용함
* 장점 : broadcast패킷에 의한 성능 저하 방지, 트래픽 체크 기능 추가
* 단점 : 특정 프로토콜을 이용해야 스위칭이 가능

# L4 Switch : **Port Number + IP Address**
* L3 Switch의 상위 장비
* L4 스위치는 TCP/IP 기반으로 동작하고, TCP의 **Port번호**와 IP의 IP주소를 기반으로 목적지를 찾음
* 데이터 패킷의 IP주소와 **Port번호**를 찾아서 해당 목적지에만 패킷 전송
* **Load Balancing(부하 분산)** 기능 추가
* **보안성** 향상
* 프로토콜의 헤더를 보고 프로토콜의 종류를 확인하고 어떤 처리를 먼저 진행할 것인지 판단할 수 있음
* 전송 계층(L4)에서 사용
* 장점 : 트래픽 분산이 가능하다(로드밸런싱), 보안성이 높다.
* 단점 : 프로토콜에 의존적이고, 가격이 비싸다.

# L4 Switch 자세히 알아보기 
* 부하 분산 : 해야할 작업을 나누어 부하를 분산시키는 것
* 보안성 향상 : 외부의 공격으로부터 보호
* 세션 관리 : Sticky Session
![l4switch1](https://user-images.githubusercontent.com/57285121/115341997-80c5e380-a1e4-11eb-8fad-8fed34bafc4f.PNG)
* 운영중이던 서버를 증설할 경우에 새로운 서버를 만들고 IP를 할당을 했을 때 서버를 증설했음에도 불구하고 사용자들은 기존 운영중이던 서버에만 접속을 하게될 수도 있음
* 이 때 L4 스위치가 증설한 서버에도 요청을 보내서 요청을 분산시킴
* 일일이 서버에 요청을 전달할 필요 없이 L4 스위치에 모든 요청을 전달하고 L4 스위치가 증설한 서버들에게 까지도 요청을 전송 →  부하 분산
* 이렇게 되면 서버들은 일일이 공인 IP를 가질 필요가 없고 L4 스위치 하나만 공인 IP가 있으면 됨
* 외부에서는 서버들의 IP를 알 수 없으니 서버에 악의적인 공격을 할 수 없게 됨 →  보안성 향상
* 하나의 서버에서는 여러 port번호를 이용해 종류별로 다양한 서비스를 제공을 하게 됨
* port번호를 모르는 상태에서 IP만 가지고 접속을 하면 어느port로 접속해야할 지 모르기 때문에 L4 스위치에는 외부에서 접속할 IP뿐만 아니라 port번호까지도 명시

![l4switch2](https://user-images.githubusercontent.com/57285121/115347104-f71a1400-a1eb-11eb-9214-abccd34cbb95.PNG)
* 외부에서 접속할 때 사용하는 IP와 port번호를 갖고있는 L4 스위치의 구성요소를 **Virtual Server**라고 함
* Virtual Server의 IP를 VIP(Vitrual IP)라고 함. L4 스위치는 다수의 Virtual Server를 가질 수 있음
* Virtual Server은 받은 요청들을 서버들의 집합에 전달하게 되는데 이 집합을 Pool이라고 하고 그 Pool을 구성하는 서버들을 Pool 멤버라고 부름(Pool은 다수의 Pool 멤버로 구성)
* Pool 멤버들은 단순 IP가 아니라 IP와 port번호로 구성된 서버.(IP가 같아도 port번호가 다르면 다른 멤버)

* Stciky Session : 세션을 이용하여 트래픽 분산.
> * 로그인 했던 서버와 다른 서버에 접속하게 되면 세션이 공유되지 않아 무한 로그인 요청 발생
> * 쿠키 또는 세션을 사용하여 트래픽 분산
> * 사용자가 처음 로그인(접속)했던 서버로 계속해서 접속하게 함
> * 로드밸런싱이 제대로 동작하지 않을 수 있다는 단점이 존재

# L7 Switch : **URI(컨텐츠)**
* 네트워크 보안장비의 역할을 함
* L4 스위치에 실제 데이터를 확인하여 패킷을 처리하는 기능 추가
* 데이터 패킷의 컨텐츠(실제 데이터)를 기반으로 해당 목적지에 패킷 전송
* 실제 데이터(HTTP의 쿠키, URL 등)를 분석해 **보안에 더 유리하고 정교한 로드밸런싱**이 가능해짐
* L4 스위치가 TCP/IP를 기반으로 스위칭을 했다면 L7 스위치는 URL기반으로 스위칭을 함
* HTTP, FTP, SMTP, DNS등 상위 계층의 프로토콜에서도 스위칭이 가능함
* 서비스 단위로 트래픽을 분산시킴
* 7계층(응용계층)에서 사용
* 장점 : 상위 프로토콜에서 사용할 수 있고, 보안성이 매우 높다
* 단점 : 가격이 비쌈

# L7 Switch Load Balancing
* URL 로드밸런싱 : URL의 문자열을 검사하고 검사한 문자열을 기준으로 트래픽 분산
> * 패킷의 요청을 확인하여 요청 URL에 따라 트래픽을 분산
> * jpg가 있으면 이미지 웹서버, mp4가 있으면 동영상 웹서버 등
* Cookie 로드밸런싱 : 헤더의 쿠키정보를 확인하여 트래픽 분산
> * 헤더의 쿠키정보를 확인하고 동일 서버에만 계속 트래픽을 할당하는 방식
* Context 로드밸런싱 : 클라이언트가 요청한 특정 리소스에 대해서 특정 서버에 트래픽을 할당하는 방식
> * 확장자를 참조하여 별도의 리소스 서버에 트래픽 할당

# L4 & L7 스위치 비교 분석
* L4 스위치 : 4계층. 포트 기반 트래픽 제어 네트워크 스위칭 장비
* L7 스위치 : 7계층. 컨텐츠 기반 트래픽 제어 네트워크 스위칭 장비   
   
|항목|L4 스위치|L7 스위치|
|:----------:|:-------------:|:------:|
|목적|로드밸런싱(포트 기반), 보안성 향상, 세션 관리|L4 스위치의 목적 + 컨텐츠 기반 로드밸런싱|
|포트 수(규모)|10개 이내(소규모)|24개 이상(대규모)|
|보안 기능|포트 기반 보안|컨텐츠 기반 보안|
|장점|L7 스위치보다 상대적으로 저비용|URL등 컨텐츠 분석을 통해 좀 더 정교한 로드밸런싱과 보안성 향상|
|단점|URL등 컨텐츠 기반 제어 불가|L4 스위치보다 상대적으로 고가|
   
> * 기본적으로 L7 스위치는 L4 스위치의 상위 장비이다. L4 스위치의 기능을 모두 사용 가능하고 추가적으로  실제 컨텐츠(URL 등)를 기반으로 정교한 로드밸런싱이 가능하며 컨텐츠를 분석하여 외부의 공격을 차단하는 필터링 기능까지 제공이 가능한다. 
> * 따라서 상대적으로 저렴하고 단순히 서버 부하분산만 필요한 경우에는 L4 스위치를 사용하도록 하며 비용은 조금 더 들더라도 컨텐츠 기반 부하 분산을 통해 Qos를 향상시키고 외부로 부터의 공격을 차단하는 등의 향상된 보안성이 필요하다면 L7 스위치를 사용하도록 한다.

