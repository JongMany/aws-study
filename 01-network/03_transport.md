# Transport Layer

- 통신 주체끼리 데이터 전달의 신뢰성을 확보하는 방법을 정의
- 주요 단위: 세그먼트
- 주요 구성요소
  - TCP/UDP
- 주요 특징
  - Network Layer로 성립된 통신 위에서 실질적인 활용을 위한 다양한 기능을 정의
    - 패킷의 순서 보장, 에러 처리, 포트 기반 분할 등

## TCP

- Transmission Control Protocol
- 패킷의 전달 과정에서 순서를 보장하고 유실되지 않도록 보장할 수 있는 통신 규약
  - 패킷 안에 세그먼트를 담아 주고 받아서 로직을 처리
- 연결 지향
  - 지속적으로 채널을 수립하여 전달 여부를 확인하고 무결성을 확인
  - 지속적으로 무결성을 확보하는 과정에서 비교적 느리고 복잡한 과정 필요
- 주요 사용 사례
  - 웹 페이지(HTTP/HTTPS)
  - 이메일
  - 파일 전송
  - SSH 등

## 세그먼트

- TCP/UDP의 데이터 전달 단위
- TCP 세그먼트 주요구성
  - Port (source/destination)
  - Sequence/Acknowledgement Number: 통신 주체끼리 데이터를 주고 받았는지 확인에 사용
  - Flags: Segment의 목적 등을 정의(예: ACK,SYN,FIN)
  - Window Size: 세그먼트를 만든 주체가 얼마나 많은 데이터를 받을지 전달
  - Urgent Pointer: 세그먼트의 중요도를 설정 (먼저 처리해야하는 세그먼트 등)
  - 기타 (checksum 등)
  - 실제 데이터

## Port

- IP 프로토콜에서 패킷을 올바른 프로세스로 라우팅하기 위한 논리적 단위
- TCP Port / UDP Port로 구분
  - 각각 0~65535 까지 정수 범위
- Well Known Port: 주로 서버에서 사용하는 어플리케이션 / 프로토콜 별로 미리 지정된 포트
  - 주요 사용에 따라 표준으로 공통적으로 사용
  - 예:
    - 80: HTTP
    - 443: HTTPS
    - 22: SSH
    - 3306: MySQL
- Ephemeral Port(임시 포트): 클라이언트에서 사용하는 포트로 연결할 때마다 임의로 저장

## TCP Handshake

- TCP Protocol에서 통신을 수립하고 서로를 인식하는 첫 과정
- Three Way Handshake로 부르며 3가지 과정으로 구분
  - Syn(Synchronize): 첫 요청으로 사용할 첫 클라이언트 Sequence Nmber(CS)를 전달
  - Syn-ACK(Synchronize-Acknowledge): Sync에 대한 응답으로 CS + 1과 서버 Sequence Number(SS)를 전달
  - ACK(Acknowledge): 마지막 단계로 연결이 수립되었음을 알려주며 CS+1과 SS+1을 전달

## UDP

- User Datagram Protocol
- 빠르고 간단하게 데이터를 주고 받을 수 있는 방법을 정의
- Connectionless
  - 연결 지향과 달리 데이터의 무결성, 순서, 전달여부를 체크하지 않음
  - 패킷이 순서대로 오지 않거나 중복되거나 아예 전달되지 않을 수 있음
- 빠르고 간단함
- 주요 사용 사례

  - 스트리밍
  - 보이스톡
  - 온라인 게임

  ⇒ 패킷이 누락되더라도 영향을 크게 느끼지 않을 수 있음

## 주요 프로토콜

- TCP
  - HTTP/HTTPS: TCP / 80, 443
  - FTP: TCP / 20, 21
  - SSH : TCP / 22
  - DNS: TCP / 53
- UDP
  - DNS: UDP / 53
  - DHCP: UDP / 67, 68
  - VoIP: UDP / 5060

## Network Load Balancer

- OSI의 4번째 레이어(Transport) 에서 운영중
- Application Load Balancer는 Layer 7에서 운영
