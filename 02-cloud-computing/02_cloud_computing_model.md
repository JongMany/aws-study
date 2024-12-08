# 클라우드 컴퓨팅의 유형

## 1. 클라우드 컴퓨팅 모델

- 어플리케이션의 구성
  - 어플리케이션
  - OS: Windows/Linux
  - Computing: CPU + RAM
  - Storage: HDD/SSD
  - Network: 랜카드/랜선
- IaaS(Infrastructure as a Service)
  - 인프라만 제공
    - Network + Storage + Computing만 제공
  - OS를 직접 설치하고 필요한 소프트웨어를 개발해서 사용
  - 즉 가상의 컴퓨터를 하나 임대하는 것과 비슷
    ex) Amazon EC2
- PaaS(Platform as a Service)
  - 인프라 + OS + 기타 프로그램 실행에 필요한 부분(런타임)
  - 바로 코드만 올려서 돌릴 . 수있도록 구성
    ex) Firebase, Google App Engine 등
- SaaS(Software as a Service)
  - 인프라 + OS + 애플리케이션
  - 서비스 자체를 제공
  - 다른 세팅 없이 서비스만 이용
    ex) Gmail, Dropbox, Slack, Google Docs

## 2. 클라우드 컴퓨팅 배포 모델

- 공개형(클라우드)
  - 모든 부분이 클라우드에서 실행
  - 낮은 비용
  - 높은 확장성
- 혼합형(하이브리드)
  - 폐쇄형과 공개형의 혼합
  - 폐쇄형에서 공개형으로 전환하는 과도기에 사용
  - 폐쇄형의 백업으로 사용
- 온-프레미스(폐쇄형)
  - 모든 부분을 사설 데이터센터에서 실행
  - 높은 수준의 커스터마이징 가능
  - 초기 비용이 비쌈
  - 유지보수 비용이 비쌈
  - 높은 보안
