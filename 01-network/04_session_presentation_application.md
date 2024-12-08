**Session Layer**

- 터미널 끼리의 통신을 구분하기 위한 방식
- 통신 주체끼리 연결이 유지할 수 있는 방법을 정의
- 예전의 컴퓨팅 환경에서 Layer 1, 2, 3, 4 이외의 차원에서 지속적인 연결(세션)이 수립될 수 있는 방법을 제공
  - MAC Address(2)와 IP 주소(3)와 포트(4)가 동일한 상황에서 어떻게 유저를 구분할 것인가
- 현대에서도 Layer 4 이상의 추가적인 차원에서 지속적인 연결(세션)을 수립할 수 있는 방법을 포함
  - 예시) HTTP Cookie
    - 브라우저와 서버 간의 주고받는 데이터(정보)
- IP가 변경되더라도 연결을 유지할 수 있게 된다.
- 몇몇 프로토콜의 경우 Session Layer 자체를 구현하지 않음
  - 예시) FTP
    - IP 변경 시 재인증을 해야한다

**Presentation Layer**

- 받은 데이터를 해석하는 방법을 정의 - 파싱, 압축 해제, 복호화 등 Application Layer에서 사용할 수 있는 형식으로 변환을 담당 - HTTP을 기준으로 바이너리 데이터를 String으로 파싱해준다.
  **Application Layer**

- 실제 받은 데이터를 처리하는 방법을 정의
  - 데이터를 가지고 어떻게 처리할지에 관한 레이어
- HTTP의 경우
  - Method
  - Status Code
  - Header
    - Host
    - User-Agent
    - Authorizations
    - Accept-Encoding
    - Content-Type
- Application Load Balancer
  - 도메인 기반의 의사결정
  - Application Layer의 정보를 기반으로 의사결정을 한다.
  - 일반적으로 3계층이 더 높으므로, Network Load Balancer보다 더 느리다.
    - 많은 정보를 기준으로 라우팅을 한다.
