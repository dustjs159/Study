Disk
====================================
Disk - HDD / SSD
------------------------------------
# Disk
* 전자 기록물의 저장 매체   

# HDD(HarD Disk)
* 보조기억장치. 비 휘발성 데이터 저장소 역할을 한다.   
* 데이터 저장소 가운데 가장 대중적이고 용량 대비 가격이 저렴함    
* 크게 플래터(Platter), 스핀들(Spindle), 액추에이터(Actuator) 3가지로 구성   
* 스핀들이라는 회전축이 플래터라는 납작한 원판을 회전시키고 액추에이터가 플래터 위에서 수직으로 움직이며 플래터에 데이터를 입력하는 원리   
* 플래터는 자성 물질이므로 플래터 위에 자석을 흔들면 데이터가 손실될 위험이 있음
   
# HDD 구조
1. 플래터(Platter)   
> 납작한 원반모양(CD랑 비슷하게 생김). 플래터는 Sector / Track / Cylinder로 구성
> - Sector : 여러 가지 조각들로 구성. 디스크를 구성하는 물리적 최소 단위이며 크기는 보통 512byte.   택
> - Track : 플래터의 동심원에 기록되는 데이터. 같은 둘레의 Sector들을 묶어놓은 것. 저장 할 데이터를 Sector단위로 나눈 후 같은 반지름 상 가까운 위치의 Sector(Track)에 저장한다.   
> - Cylinder : 같은 반지름의 Track들을 원통형으로 묶어놓은 것
2. 액추에이터(Actuator)   
> 플래터의 데이터를 읽거나 쓰는 역할을 함. 헤드(head)와 암(arm)으로 구성되어 있고 헤드 부분을 통해 수직으로 플래터에 데이터 읽기 및 쓰기 작업을 한다.
3. 스핀들(Spindle)   
> 플래터를 돌리기 위한 축. 모터로 플래터를 회전시키며 모터의 회전속도(RPM)이 빠를수록 HDD의 성능이 좋다.

# HDD 종류
1. PATA HDD : Parallel Advanced Technology Attachment HDD   
> 병렬 구조로 데이터의 경로를 여러 개로 분산 시켜 성능을 높임   
> 하지만 핀 개수가 많고 복잡하기 때문에 데이터 전송 시 오류 위험이 있기 때문에 잘 사용하지 않는다   
2. SATA HDD : Serial Advanced Technology Attachment HDD
> PATA 인터페이스를 극복하고자 나온 것. 핀 개수가 적어지며 크기가 줄어들고 데이터 전송 안정성과 속도가 향상됨    
> SATA 1, 2, 3이 있고 3이 가장 성능이 좋음   
3. SAS HDD : Serial Attached SCSI HDD   
> SATA보다 성능이 높지만 가격이 비싸기 때문에 주로 서버용도로 사용되는 HDD.   
> SAS1.0, 2.0, 3.0이 있고 3.0이 가장 성능이 좋음

# SSD(Solid State Drive)
> 고체(트랜지스터) 상태 기억장치.   
> SSD는 HDD의 물리적인 방식(자성을 이용한)에 반해 전자적인 방식(플래시 메모리)으로 데이터를 읽고 쓴다(HDD와 마찬가지로 기억장치이지만 구조부터 매우 다르다)   
> HDD의 단점을 개선하기 위해 만들어짐
1. 발전 할 만큼 발전됨 → 발전 속도가 더딤
2. 물리적 충격에 약함. 크기가 크고 무거움
3. 병렬 처리가 어려움(헤드의 수가 1개 혹은 2개로 제한적이기 때문)

# SSD 구조
> NAND Flash : 데이터를 저장하는 칩. 이 칩은 블록으로 구성되어있고, 데이터를 읽고 쓰고 수정하는 단위인 블록과 페이지로 구성되어 있음   
> 블록은 페이지로 구성되어 있음   
> 페이지는 데이터 저장의 최소 단위(HDD의 Sector)

# SSD 장점
1. 물리적인 방법으로 데이터를 읽고 쓰는 방식의 HDD와는 다르게 전기적인 방식으로 데이터를 읽고 쓰기 때문에 속도가 훨씬 빠르다.(무언가를 움직여서 데이터를 읽을 필요가 없음)

2. 크기가 작고 가벼우며 외부의 충격으로부터 데이터가 손상될 가능성이 적다.(별도의 물리적 장치를 이용하지 않고 데이터를 읽고 쓰기 때문)   
(HDD는 물리적 장치가 조금이라도 손상이 나면 데이터 손실 가능성이 있다)

3. 병렬 처리가 쉬움
HDD에서 물리적으로 데이터를 읽고 쓰기 위한 헤드가 없기 때문에 다수의 NAND Flash에 동시에 요청을 보낼 수 있음

# SSD 단점
1. 배드블록으로 인해 수명이 HDD보다 상대적으로 짧음.
2. 전기적 신호를 통해 데이터를 읽고 쓰기 때문에 해당 블록 주변의 블록이 전기의 영향을 받아서 데이터가 변질될 수 있음
3. 블록에 전기적 신호를 통해 데이터를 저장을 할 때 전자들이 들어가게 되는데 이 때 SSD를 오랫동안 사용하지 않고 방치해 두면 전자들이 탈출을 하여 데이터의 손실 가능성이 있음.(리텐션 에러)

# SSD 종류
1. 2.5 SATA SSD : 2.5인치 SATA SSD
2. mSATA SSD : mini-SATA
> 휴대성과 무게를 고려하여 노트북에 사용하기 좋은 SSD. 하지만 기존 2.5인치 SATA SSD에 비해 성능과 용량이 부족   
3. m.2 SSD
> 기존 SSD들에 비해 크기가 작아지고 데이터 전송속도도 빨라져서 가장 널리 쓰이는 SSD. 제조사에 따라 SATA와 PCle 인터페이스 두 가지 종류가 있다   
> PCle 인터페이스가 읽기 및 쓰기 속도가 빠르긴 하지만 발열이 심하고 무엇보다 가격이 비싸니 용도에 맞게 선

