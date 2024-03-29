![](https://velog.velcdn.com/images/krylo71911/post/65f8a72d-aa5e-41e4-8234-5f7006b5c50b/image.jpeg)
# 네트워크 연결과 구성 요소
## 네트워크 연결 구분
네트워크는 규모와 관리 범위에 따라 3가지로 구분된다.
- LAN (Local Area Network)
비교적 소규모의 네트워크
- MAN (Metro Area Network)
수 ~ 수십km 범위의 한 도시를 네트워크로 연결하는 개념
- WAN (Wide Area Network)
먼 거리의 네트워크를 연결하기 위해 사용. 자신이 소유한 땅이나 건물이 아닌 곳을 원격지로 통신해야 할 때 사용. 
## 네트워크 회선
### 인터넷 회선
인터넷 접속을 위해 통신사업자와 연결하는 회선을 인터넷 회선이라고 부른다. 항상 모든 사람이 최대 속도로 인터넷을 접속하는 것이 아니므로 공유 구간은 사용자 최대 속도를 보장하지 않도록 구축하는 것이 일반적이다. 
### 전용 회선
가입자와 통신사업자 간에 대역폭을 보장해주는 서비스를 대부분 전용 회선이라고 부른다. 음성 전송 기술 기반의 저속 회선과 메트로 이더넷이라는 고속 회선으로 분류할 수 있다. 
- 저속: 음성 전송 기술 기반
결재 승인과 같은 전문(Clear Text) 전송을 위한 VAN(Value Added Network)사나 대외 연결에 사용. 이 기술을 사용하려면 원격지 전송 기술로 변환할 수 있는 라우터가 필요하다. 
- 고속: 메트로 이더넷 
대부분 광케이블 기반의 이더넷을 사용. 다양한 가입자 접속 기술을 하나의 기술을 통합하기 위한 기술이 사용됨. 

> LLCF(Link Loss Carry Forward)
한쪽 링크가 다운되면 이를 감지해 반대쪽 링크도 다운시키는 기능. 

### 인터넷 전용 회선
인터넷 연결 회선에 대한 통신 대역폭을 보장해주는 상품.

### VPN
Virtual Private Network. 물리적으로는 전용선이 아니나 가상으로 직접 연결한 것 같은 효과가 나도록 만들어주는 네트워크 기술.

### DWDM
Dense Wavelength Division Multiplex: 파장 분할 다중화 전송기술. 먼거리를 통신할 때 케이블 포설 비용이 매우 많이 들고 관리가 어려운 문제를 극복하기 위해 개발되었다. 

## 네트워크 구성 요소
### 네트워크 인터페이스 카드(NIC)
컴퓨터를 네트워크에 연결하기 위한 하드웨어 장치.
주요 역할은 다음과 같다.
- 직렬화
- MAC 주소
- 흐름 제어

### 케이블과 커넥터
케이블에는 트위스티드 페어 케이블, 동축 케이블, 광케이블 3가지가 있다. 
#### 이더넷 네트워크 표준
현재 가장 많이 사용된느 네트워크 기술은 이더넷 방식. 일반 PC와 같은 종단은 기가비트 이더넷을, 데이터 센터의 서버와 같은 종단은 기가비트나 10기가비트 이더넷을 주로 사용하고있다. 이더넷에서도 케이블의 종류, 인코더의 종류 등으로 세분화해 여러 표준으로 나뉜다. 
- 1,000BASE-T/10GVASE-T
- 1,000BASE-SX/10GBASE-SR
- 1,000BASE-LX/10GBASE-LR

#### 케이블, 커넥터 구조
케이블은 물리적으로 케이블 본체, 커넥터, 트랜시버와 같은 여러 요소로 나뉜다. 
#### 케이블 - 트위스티드 페어 케이블
가장 흔히 사용하는 케이블. 쉴드를 장착한 STP/FTP 케이블과 종류와 쉴드가 없는 UTP 케이블이 있다. 

#### 케이블 - 동축 케이블
#### 케이블 - 광케이블
높은 대역폭을 요구하거나 먼 거리를 통신해야 하는 네트워크 장비 간의 통신에 주로 사용. 싱글모드, 멀티모드 2가지로 나뉜다. 

#### 커넥터 
케이블의 끝부분으로 네트워크 장비나 네트워크 카드에 연결되는 부분. 

#### 트랜시버
다양한 외부 신호를 컴퓨터 내부의 전기 신호로 바꾸어준다.

### 허브
케이블과 동일한 1계층에서 동작하는 장비이다. 거리가 멀어질수록 줄어드는 전기 신호를 재생성해주고 HUB라는 용어 그대로 여러 대의 장비를 연결할 목적으로 사용된다.

### 스위치
허브와 동일하게 여러 장비를 연결하고 통신을 중재하는 2계층 장비. 스위칭 허브로도 불린다. 허브와 달리 MAC 주소를 이해할 수 있어 목적지 MAC 주소의 위치를 파악하고 목적지가 연결된 포트로만 전기 신호를 보낸다. 

### 라우터
OSI 7계층 중 3계층에서 동작하면서 먼 거리로 통신할 수 있는 프로토콜로 변환한다. 정확한 방향으로 패킷이 전송되도록 경로를 지정하고 최적의 경로로 패킷을 포워딩한다. 

### 로드 밸런서
OSI7계층 중 4계층에서 동작한다. 

### 보안장비(방화벽/IPS)
대부분의 네트워크 장비는 정확한 정보 전달에 초점이 맞추어져 있지만 보안 장비는 정보를 잘 제어하고 공격을 방어하는데 초점이 맞추어져 있다. 방화벽은 OSI7계층 중 4계층에서 동작해 방화벽을 통과하는 패킷의 3, 4계층 정보를 확인하고 패킷을 정책과 비교해버리거나 포워딩한다. 

### 기타(모뎀/공유기 등)