![](https://velog.velcdn.com/images/krylo71911/post/158344bd-0efb-4308-b2af-1dff639a6ff6/image.jpeg)
# Chapter 06 | 메모리와 캐시 메모리
## 06-1 RAM의 특징과 종류
>RAM의 특징
- RAM에는 실행할 프로그램의 명령어와 데이터가 저장된다.
- 휘발성 저장 장치이다.
- RAM 용량이 크면 많은 프로그램들을 동시에 빠르게 실행하는 데 유리하다.

>RAM의 종류
- DRAM : Dynamic RAM의 준말. 저장된 데이터가 동적으로 변하는 RAM. 데이터의 소멸을 막기 위해 일정 주기로 데이터를 재활성화해야 한다. 대용량으로 설계하기 용이.
- SRAM : Static RAM의 준말. 시간이 지나도 저장된 데이터가 사라지지 않는다. DRAM보다 속도도 더 빠르다. 대신 집적도가 낮고, 소비 전력도 크며, 가격도 더 비싸다. '대용량으로 만들어질 필요는 없지만 속도가 빨라야 하는 저장 장치' 가령 캐시 메모리에 사용된다. 
- SDRAM : SRAM과 관계 없다. 클럭에 맞춰 동작하며 클럭마다 CPU와 정보를 주고받을 수 있는 DRAM이다. 
- DDR SDRAM : 대역폭을 넓혀 속도를 빠르게 만든 SDRAM. 대역폭이란 '데이터를 주고받는 길의 너비'를 의미한다. 

## 06-2 메모리의 주소 공간
주소에는 물리 주소와 논리 주소가 있다.
- 물리 주소 : 메모리 하드웨어가 사용하는 주소.
- 논리 주소 : CPU와 실행 중인 프로그램이 사용하는 주소. CPU가 이해하는 주소가 논리 주소라고는 해도 CPU가 메모리와 상호작용하려면 논리 주소와 물리 주소 간의 변환이 이루어져야 한다. 논리 주소와 물리 주소 간의 변환은 CPU와 주소 버스 사이에 위치한 메모리 관리 장치(MMU)라는 하드웨어에 의해 수행된다.

베이스 레지스터는 프로그램의 가장 작은 물리 주소, 즉 프로그램의 첫 물리 주소를 저장하는 셈이고, 논리 주소는 프로그램의 시작점으로부터 떨어진 거리인 셈. 

다른 프로그램의 영역을 침범할 우려가 있는 명령어는 위험하므로 논리 주소 범위를 벗어나는 명령어 실행을 방지하고 실행 중인 프로그램이 다른 프로그램에 영향을 받지 않도록 보호할 방법이 필요한데 이는 한계 레지스터가 담당한다. 즉, 논리 주소의 최대 크기를 저장한다. 프로그램의 물리 주소 범위는 베이스 레지스터 값 이상, 베이스 레지스터 값 + 한계 레지스터 값 미만이 된다. 

## 06-3 캐시 메모리
CPU가 연산을 빨리 해도 메모리에 접근하는 시간이 느리면 의미가 없다. 이를 극복하기 위한 저장 장치가 캐시 메모리이다. 캐시 메모리를 이해하려면 저장 장치 계층 구조라는 개념을 이해해야 한다. 

#### 저장 장치 계층 구조
컴퓨터가 사용하는 저장 장치들은 'CPU로부터 얼마나 가까운가'를 기준으로 계층적으로 나타낼 수 있다. 
빠르면서도 용량이 큰 저장장치는 양립하기 어렵다. 
- CPU와 가까운 저장 장치는 빠르고, 멀리 있는 저장 장치는 느리다.
- 속도가 빠른 저장 장치는 저장 용량이 작고, 가격이 비싸다.

#### 캐시 메모리
CPU와 메모리 사이에 위치하고, 레지스터보다 용량이 크고 메모리보다 빠른 SRAM 기반의 저장 장치. CPU의 연산 속도와 메모리 접근 속도의 차이를 조금이나마 줄이기 위해 탄생. (마트와 편의점의 차이)

#### 참조 지역성 원리
- 캐시 히트 : 자주 사용될 것으로 예측한 데이터가 실제로 들어맞아 캐시 메모리 내 데이터가 CPU에서 활용될 경우.
- 캐시 미스 : 자주 사용될 것으로 예측하여 캐시 메모리에 저장했지만, 예측이 틀려 메모리에서 필요한 데이터를 직접 가져와야 하는 경우. 캐시 메모리의 이점을 활용할 수 없고 당연히 캐시 미스가 자주 발생하면 성능이 떨어지게 된다. 
- 캐시 적중률 : 캐시가 히트되는 비율
> 참조 지역성의 원리 : CPU가 메모리에 접근할 때의 주된 경향을 바탕으로 만들어진 원리. 캐시 메모리는 참조 지역성의 원리에 따라 데이터를 예측하여 캐시 적중률을 높인다.
CPU는 최근에 접근했던 메모리 공간에 다시 접근하려는 경향이 있다.(시간 지역성)
CPU는 접근한 메모리 공간 근처를 접근하려는 경향이 있다.(공간 지역성)

# Chapter 07 | 보조기억장치
## 07-1 다양한 보조기억장치
#### 하드 디스크
자기적인 방식으로 데이터를 저장하는 보조기억장치. 
- 플래터 : 실질적으로 데이터가 저장되는 곳. 여러 겹으로 이루어져 있다. 트랙과 섹터라는 단위로 데이터를 저장한다. 
- 스핀들 : 플래터를 회전시키는 구성 요소.
- 헤드 :  플래터를 대상으로 데이터를 읽고 쓰는 구성 요소.
- 디스크 암 : 원하는 위치로 헤드를 이동시키는 구성 요소.
- 실린더 : 여러 겹의 플래터 상에서 같은 트랙이 위치한 곳을 모아 연결한 논리적 단위 

하드 디스크가 저장된 데이터에 접근하는 시간은 크게 탐색 시간, 회전 지연, 전송 시간으로 나뉜다.
- 탐색 시간 : 접근하려는 데이터가 저장된 트랙까지 헤드를 이동시키는 시간을 의미.
- 회전 지연 : 헤드가 있는 곳으로 플래터를 회전시키는 시간을 의미.
- 전송 시간 : 하드 디스크와 컴퓨터 간에 데이터를 전송하는 시간을 의미.

> 단일 헤드 디스크 : 플래터의 한 면당 헤드가 하나씩 달려있는 하드 디스크. 이동 헤드 디스크라고도 부른다. 
다중 헤드 디스크 : 헤드가 트랙별로 여러 개 달려 있는 하드 디스크. 탐색 시간이 들지 않기 때문에 탐색 시간이 0이다. 고정 헤드 디스크라고도 부른다.  

#### 플래시 메모리
전기적으로 데이터를 읽고 쓸 수 있는 반도체 기반의 저장 장치.(USB 메모리, SD 카드, SSD 등) 크게 NAND 플래시 메모리와 NOR 플래시 메모리가 있다. 단위로는 셀이 있는데 플래시 메모리에서 데이터를 저장하는 가장 작은 단위이다. 
- SLC 타입 : 한 셀에 1비트를 저장할 수 있는 플래시 메모리. 빠른 입출력 가능. 수명도 길다. 하지만, 용량 대비 가격이 높다. 데이터를 읽고 쓰기가 매우 많이 반복되며 고성능의 빠른 저장 장치가 필요한 경우에 사용한다. 
- MLC 타입 : 한 셀에 2비트를 저장할 수 있는 플래시 메모리. 한 셀로 네 개의 정보를 표현할 수 있다. SLC 타입보다 대용량화하기 유리하다. 한 집에 두 명 살기. 주거 비용을 나눠 내는 것과 마찬가지로 용량 대비 가격이 저렴하다. 시중의 많은 플래시 메모리들이 MLC나 TLC 타입으로 만들어진다. 
- TLC 타입 : 한 셀에 3비트를 저장할 수 있는 플래시 메모리. 한 셀로 여덟 개의 정보를 표현할 수 있으므로 대용량화 하기 유리하다. 일반적으로 수명과 속도가 상기의 두 타입보다는 떨어지지만 용량 대비 가격이 저렴하다. 
- QLC 타입 : 한 셀에 4비트를 저장할 수 있는 플래시 메모리

플래시 메모리의 가장 작은 단위인 셀보다 더 큰 단위에 대해 알아보자. 
- 페이지 : 셀들이 모여 만들어진 단위. 세 개의 상태를 가질 수 있다. (Free, Valid, Invalid)
Free 상태 - 어떠한 데이터도 저장하고 있지 않아 새로운 데이터를 저장할 수 있는 상태.
Valid 상태 - 이미 유효한 데이터를 저장하고 있는 상태.
Invalid 상태 - 쓰레기값이라 부르는 유효하지 않은 데이터를 저장하고 있는 상태.
- 블록 : 페이지가 모여 만들어진 단위. 블록이 모여 플레인plane, 플레인이 모여 다이die가 된다. 

플래시 메모리는 하드 디스크와 달리 덮어쓰기가 불가능하여 Valid 상태인 페이지에는 새 데이터를 저장할 수 없다.
최근 SSD를 비롯한 플래시 메모리는 쓰레기 값을 정리하기 위해 가비지 컬렉션 기능을 제공한다. 가비지 컬렉션은 유효한 페이지들만을 새로운 블록으로 복사한 뒤, 기존의 블록을 삭제하는 기능이다. 플래시 메모리의 읽기와 쓰기는 페이지 단위로, 삭제는 블록 단위로 이루어진다. 

## 07-2 RAID의 정의와 종류
RAID란 보조기억장치를 더욱 안전하고 빠르게 활용하는 방법이다. 데이터의 안전성 혹은 성능을 위해 여러 개의 물리적 보조기억장치를 마치 하나의 논리적 보조기억장치처럼 사용하는 기술을 의미한다. 

#### RAID의 종류
RAID의 구성 방법을 RAID 레벨이라 표현
- RAID 0 : 여러 개의 보조기억장치에 데이터를 단순히 나누어 저장하는 구성 방식. 단점은 저장된 정보가 안전하지 않다. RAID 0으로 구성된 하드 디스크 중 하나만 문제가 생겨도 다른 모든 하드 디스크의 정보를 읽는 데 문제가 생길 수 있다. 
> 스트라입 : 줄무늬처럼 분산되어 저장된 데이터
> 스트라이핑 : 분산하여 저장하는 것
데이터가 분산되어 저장되면(스트라이핑되면), 저장된 데이터를 읽고 쓰는 속도가 빨라진다. 

- RAID 1 : RAID 0의 단점을 보완하였으나 속도는 느리다. 거울처럼 완전한 복사본을 만드는 방식(미러링). 복구가 매우 간단하다는 장점이 있다. 하지만 하드 디스크 개수가 한정되었을 때 사용 가능한 용량이 적어지는 단점이 있다. (4TB 중 2TB만 사용 가능)
- RAID 4 : RAID 1처럼 완전한 복사본을 만드는 대신 오류를 검출하고 복구하기 위한 정보(패리티 비트)를 저장한 장치를 두는 구성 방식. 패리티를 저장한 장치를 이용해 다른 장치들의 오류를 검출하고 오류가 있다면 복구하는데 그러므로 RAID 1보다 적은 하드 디스크로도 데이터를 안전하게 보관할 수 있다. 
> 패리티 비트
1 RAID 4에서는 패리티 정보를 저장한 장치로써 나머지 장치들의 오류를 검출, 복구한다.
2 패리티 비트는 본래 오류 검출용 정보지만, RAID에서는 오류 복구도 가능하다.

- RAID 5 : 패리티 정보를 분산하여 저장하는 방식, RAID 4의 병목 현상을 해소. 
- RAID 6 : RAID 5와 같으나 서로 다른 두 개의 패리티를 두는 방식. 즉 안전한 구성이다. 다만 새로운 정보를 저장할 때마다 함께 저장할 패리티가 두 개이므로 쓰기 속도는 RAID 5보다 느리다. 안전성을 추구할 때 사용하는 방식. 

각 RAID 레벨마다 장단점이 있기에 상황, 우선순위에 따라 최적의 RAID 레벨이 달라진다.

# Chapter 08 | 입출력장치
## 08-1 장치 컨트롤러와 장치 드라이버
입출력장치는 컴퓨터와 외부에 연결되는 장치이다. 
#### 장치 컨트롤러
입출력 제어기, 입출력 모듈 등으로 불린다. 입출력장치를 연결하기 위한 하드웨어적인 통로.
입출력 장치가 CPU, 메모리보다 다루기 까다로운 이유?
1. 종류가 너무 많다.
2. 일반적으로 CPU와 메모리의 데이터 전송률은 높지만 입출력장치의 데이터 전송률은 낮다. 여기서 전송률이란 데이터를 얼마나 빨리 교환할 수 있는지를 나타내는 지표. 
> 장치 컨트롤러의 역할
1 CPU와 입출력장치 간의 통신 중개
2 오류 검출
3 데이터 버퍼링 (전송률이 높은 CPU와 일반적으로 전송률이 낮은 입출력장치와의 전송률 차이 완화)

> 장치 컨트롤러 내부 구조
1 데이터 레지스터 : CPU와 입출력장치 사이에 주고받을 데이터가 담기는 레지스터
2 상태 레지스터 : 입출력장치가 입출력 작업을 할 준비가 되었는지, 입출력 작업이 완료되었는지, 입출력장치에 오류는 없는지 등의 상태 정보가 저장되는 곳.
3 제어 레지스터 : 입출력장치가 수행할 내용에 대한 제어 정보와 명령을 저장.

#### 장치 드라이버
장치 컨트롤러의 동작을 감지하고 제어함으로써 장치 컨트롤러가 컴퓨터 내부와 정보를 주고받을 수 있게 하는 프로그램. 입출력장치를 연결하기 위한 소프트웨어적인 통로.

## 08-2 다양한 입출력 방법
장치 컨트롤러가 CPU와 정보를 주고받는 방법에는 3가지가 있다.
1. 프로그램 입출력
2. 인터럽트 기반 입출력
3. DMA 입출력

#### 프로그램 입출력
프로그램 속 명령어로 입출력장치를 제어하는 방법
>메모리 맵 입출력 : 메모리에 접근하기 위한 주소 공간과 입출력장치에 접근하기 위한 주소 공간을 하나의 주소 공간으로 간주하는 방법.
고립형 입출력 : 메모리를 위한 주소 공간과 입출력장치를 위한 주소 공간을 분리하는 방법.

#### 인터럽트 기반 입출력
CPU가 인터럽트 요청을 받을 때까지 온전히 다른 일에 집중할 수 있다. CPU는 인터럽트 간에 우선순위를 고려햐여 우선순위가 높은 인터럽트(NMI가 발생한 경우) 순으로 여러 인터럽트를 처리할 수 있다. (프로그래머블 인터럽트 컨트롤러)
> 폴링 : 입출력장치의 상태는 어떤지, 처리할 데이터가 있는지 주기적으로 확인하는 방식. 인터럽트 방식보다 CPU의 부담이 더 크다. 

#### DMA 입출력
프로그램 기반 입출력과 인터럽트 기반 입출력의 공통점 : 입출력장치와 메모리 간의 데이터 이동은 CPU가 주도, 이동하는 데이터도 반드시 CPU를 거친다. DMA 는 이름 그대로 직접 메모리에 접근할 수 있는 입출력 기능이다. DMA 입출력을 하기 위해서는 시스템 버스에 연결된 DMA 컨트롤러라는 하드웨어가 필요하다. CPU는 오로지 입출력의 시작과 끝에만 관여한다. 인터럽트만 받으면 되므로 작업 부담도 줄일 수 있다. 다만, 시스템 버스는 공용 자원이기에 DMA 컨트롤러가 시스템 버스를 사용할 때는 CPU가 시스템 버스를 사용할 수 없다. (사이클 스틸링)
- 입출력 버스 : DMA의 과도한 시스템 버스 점유빈도를 줄여준다. PCI 버스, PCI Express(PCle)버스 등의 종류가 있다. 
