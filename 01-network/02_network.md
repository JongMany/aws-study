# Network Layer

- 여러 노드의 경로를 찾고 올바르게 전달될 수 있는 기능과 수단을 정의
- 주요 단위: 패킷
- 주요 구성 요소
  - Router
  - IP
  - ARP
- 주요 특징
  - 서로 떨어진 Local Network 간의 통신을 지원
    - Inter Network → Internet
    - 중간 중간 Node들을 거쳐 목적지까지 도달할 수 있는 방법을 지원

## IP Address

- 인터넷 프로토콜 상에서 통신 주체를 식별하기 위한 아이디
- 두가지 종류
  - IPv4
    - 아이피를 최대로 활용하기 위해 사설 IP와 공인 IP로 분류
  - IPv6
    - 사설 IP가 필요 없음
- MAC Address와 다르게 수시로 변동 가능

## CIDR

- Classless Inter Domain Routing
- IP는 주소의 영역을 여러 네트워크 영역으로 나누기 위해 IP를 묶는 방식
- 여러 개의 사설망을 구축하기 위해 망을 나누는 방법

### CIDR Notation

- IP 주소의 집합
- 네트워크 주소와 호스트 주소로 구성
- 각 호스트 주소 숫자만큼의 아이피를 가진 네트워크 망 형성 가능
- A.B.C.D/E 형식
  - 예시) 10.0.1.0/24
  - A,B,C,D: 네트워크 주소 + 호스트 주소 표시
  - E: 0~32: 네트워크 주소가 몇 bit인지 표시

### CIDR Block

- 호스트 주소 비트만큼 IP 주소를 보유할 수 있음.
- 예: 192.168.2.0/24
  - 네트워크 비트 = 24
    - 네트워크 비트의 역할은 같은 네트워크(로컬 네트워크)임을 보장
  - 호스트 주소 = 32 - 24 = 8
    ⇒ 2^8 = 256 개의 IP 주소 보유

## Subnet Mask

- 어느 부분이 호스트 비트인지, 어느 부분이 네트워크 비트인지 구분해주는 Mask
  - AND 연산을 활용해 네트워크 주소를 필터링
- 네트워크 비트 수만큼 1을 보유한 마스크를 IP에 적용하면 네트워크 비트만 추출 가능

## 라우터

- 네트워크 간 패킷을 주고받는 Layer 3 장치
- IP 대역별 최적 경로를 수집 및 관리
  - 어떤 경로의 노드를 경유해야 가장 효율적으로 대상에 도착하는지 알고 있음 (Route Table)
  - 이 경로를 바탕으로 특정 IP 주소가 대상인 패킷의 전달을 요청받을 때 해당 경로로 요청
- 로컬 네트워크는 자신의 로컬 네트워크 주소가 아니라면 라우터로 전달
  - 로컬 네트워크인지 확인 방법: 네트워크 주소가 같은지 확인 (subnet mask)
  - 이후 Router는 패킷을 Frame 안에 넣어서 최적 경로에 따른 다른 Router로 전달
    - Frame에는 MAC Address가 필요하다.
    - IP 주소에 따른 Frame(MAC Address)확인 방법: ARP

## ARP(Address Resolution Protocol)

- IP로 MAC Address를 찾는 프로토콜
- 순서
  - Broadcast(MAC Address FF:FF:FF:FF:FF:FF)로 IP 요청
  - 응답 받은 IP MAC Address를 기반으로 MAC 확정 후 테이블에 저장

## 다른 로컬 네트워크에 전달 과정

- 라우터까지 데이터 전달하기
  - IP 대상(Subnet Mask, 네트워크 비트)이 로컬이 아닌 것 식별
    - 네트워크 주소가 다름
  - 같은 네트워크가 아니라면 라우터로 전달
    - 하지만 라우터의 IP는 알지만 MAC 주소를 모름
  - ARP(Address Resolution Protocol) 활용
    - IP ↔ MAC Address를 찾는 프로토콜
  - 이후 해당 MAC Address로 Frame 생성 후 전달

## Network Layer 정리 및 해결하지 못한 문제

- 한 번에 하나의 통신만 가능
  - 한 디바이스에 여러 애플리케이션이 동시에 통신 불가능
- 패킷 등의 순서 보장 / 유실에 대한 대응 불가능
