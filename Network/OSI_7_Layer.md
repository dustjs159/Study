OSI 7 Layer
=================================

# OSI 7 Layer
* 다른 시스템 간 원활한 통신을 위해 ISO(국제 표준화 기구)에서 제안한 통신 규약(Protocol)
* 네트워크가 통신하는 구조를 계층으로 구분하여 각 계층간 상호 작동하는 방식을 정해놓은 규약
* 서로 다른 컴퓨터 간 원활한 데이터 통신이 목적
   
![osi1](https://user-images.githubusercontent.com/57285121/115154807-b28d5c00-a0b7-11eb-833d-ba61fac04bf2.png)


# 1. 물리 계층(Physical Layer)
* 데이터 전송을 위한 물리적 연결을 담당
* 물리적 매체를 정의(랜선, 동출케이블 등)
* 데이터를 전기적 특성(ON/OFF, 0 or 1)을 이용하여 물리적 매체를 통해 전송할 수 있도록 함
* 데이터 전송 단위 : bit
* 사용되는 네트워크 장비 : 리피터, 허브 

# 2. 데이터 링크 계층(Data Link Layer)
* 근접한 시스템 간에 신뢰성 있는 정보를 전송
* Flow contorl, Framing, Error control, Sequence Contorl
