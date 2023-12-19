# 1. 프로젝트 개요
"Poppin'" 프로젝트는 혁신적인 방식으로 새로운 지도 서비스를 제공해 보자는 생각으로부터 진행되었습니다. 이 프로젝트의 핵심은 유동인구 데이터의 수치화와 시각화에 있으며, 이를 통해 사용자들에게 이전에는 경험해 볼 수 없던 지도 사용 경험을 제공합니다. 이 프로젝트는 멀티플랫폼 지원을 위해 Flutter를 사용하며, 백엔드 서버는 Kubernetes 위에서 관리되는 Spring Boot로 구현되었습니다. 사용자들은 익숙한 지도 서비스 UI를 통해 공공데이터를 기반으로 한 밀도 높은 정보를 제공받습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/c684f264-3218-42ed-8add-3667363d94ca)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/3310e77b-3739-461f-ab71-649926e6088c)

---

# 2. 프로젝트 진행 내용
## 2.1 빅데이터 활용
### 2.1.1 유동인구 분석
유동인구 분석 알고리즘은 지하철, 버스와 같은 정부 데이터를 활용하여 주요 지역의 유동인구를 분석합니다. 미래의 유동인구 예측을 위해 간단한 머신러닝 기법을 적용했습니다.

서울교통공사_역별 일별 시간대별 승하차인원 정보 활용
-> 역의 위치, 시간대, 인구수 등 세 가지 주요 요소를 기준으로 유동인구를 판단합니다.

### 2.1.2 크롤링
Google Map API를 활용하여 지도 데이터를 크롤링합니다. 이렇게 수집된 데이터는 MongoDB에 저장되어 관리됩니다.

<크롤링 순서>

a. 원하는 지역 설정
전국, 서울, 경기도 등 원하는 지역을 설정합니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/06772470-8644-49a9-8a6f-af95b5d30058)

b. 크롤링 범위 설정
1. 지역을 일정 간격으로 나누어 포인팅하고 그 주변을 크롤링 타겟으로 지정합니다.
2. 폴리곤의 가로, 세로 최소/최대의 좌표를 구하고, x,y 좌표를 각각 일정한 간격으로 나눕니다.
3. 각 좌표마다 API를 subprocess로 호출하여 프로세스를 분리하여 향상된 속도로 크롤링을 진행합니다.

c. 데이터 크롤링
Google map api를 통해 얻어진 가게 정보들을 메타데이터와 함께 mongodb에 저장합니다.
Google map api키는 팀원 모두의 키를 사용하였으며 API키의 과금 방지 및 키 교체를 위해 키 스케쥴링 알고리즘을 제작하여 사용합니다.

API키의 순서와 사용횟수를 활용하여 API키 여러개를 순차적으로 사용해 API 한계를 극한까지 활용할 수 있도록 API키를 스케줄링하는 알고리즘으로 크롤링을 진행했습니다.

<크롤링 결과>

![image](https://github.com/pop-pin/BackEnd/assets/118061713/3a79ac84-d76e-4f98-a66d-87542a59d005)

### 2.1.3 평점 계산 알고리즘
사용자의 평가 기록을 기반으로 한 가중치를 적용하여 평점을 계산합니다.
예시) 평소 5점 주던 사람이 주는 3점 != 1점 주던 사람이 주는 3점

---

## 2.2 시각화
### 2.2.1 레이어링
GeoJSON을 기반으로 지역별 레이어링을 구현했습니다. 이를 통해 사용자들은 카테고리별로 지역 정보를 쉽게 파악할 수 있습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/cc5be6ec-b52c-42cc-a6d0-c8c6edd1c0db)

예시) 서울시의 여러 구 별로 가게들의 평균 평점을 계산하여 평균 평점이 높은 지역을 한눈에 확인 할 수 있도록 하였습니다.

### 2.2.2 Mapbox API활용
Mapbox를 사용하여 기본적인 지도 구성과 데이터 시각화를 구현했습니다. 사용자들은 지도 상에서 직관적으로 지역 정보를 파악할 수 있으며, 가게 데이터도 추가하여 각 장소에 대한 정보를 제공합니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/6ba8d784-bb9d-47d1-bf1b-32aa8b74113e)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/975c2acb-6440-4c3d-9526-a534ec910d21)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/0eed7894-6f39-410e-a59f-1513d092dd30)

### 2.2.3 이외 다양한 기능 구현
지도, 추천, 리뷰, 마이 페이지 등 다양한 기능들이 구현하였습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/905eb3e4-afcf-4ea2-93f0-e75bab8bd8f2)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/d462a5cf-0e53-4550-9101-31dc3789c71d)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/582e904a-5a7a-4fff-815c-c45d87680e2a)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/27f50fde-07b7-4a63-b25e-96a0b7d5e9ea)

---

## 2.3 백엔드 및 배포
### 2.3.1 OAuth2.0 로그인 및 JWT 토큰
회원가입과 같은 불필요한 절차를 줄여 사용자의 편의를 높이기 위해 OAuth2.0 기반의 로그인 시스템을 구현했습니다. 또한 JWT토큰을 엑세스 토큰과 리프세쉬 토큰으로 나눠서 발급해 보안처리를 하였습니다.
![image](https://github.com/pop-pin/BackEnd/assets/118061713/daa299e1-d0dc-4074-9ee9-2c3fbc1242dd)

### 2.3.2 마이크로서비스 및 API Gateway
서비스의 확장성과 관리 용이성을 위해 마이크로서비스 아키텍처를 채택하였습니다. 또한 API Gateway를 통해 요청이 들어올 때 필터를 통한 토큰의 유효성 검사를 진행하는 등 여러 마이크로서비스의 설정을 용이하게 하기 위해 사용하였습니다.
![image](https://github.com/pop-pin/BackEnd/assets/118061713/b837bf8a-f112-46fe-83da-624b6c64d261)

### 2.3.3 Aggregate 프레임워크
크롤링을 통해 MongoDB에 저장된 데이터를 Aggregate 프레임워크를 사용하여 서울시의 구별로 데이터를 분리하여 평균 평점을 계산하는 등의 서비스 로직을 구현하는데 사용하였습니다.
![image](https://github.com/pop-pin/BackEnd/assets/118061713/ffc124d9-0195-406a-9d43-11065e86e6a0)

### 2.3.4 Redis를 통한 성능 향상
사용자가 특정한 가게에 좋아요를 누르는 상황에서 Redis를 사용하여 사용자 경험을 크게 향상시키고자 하였습니다. 또한 데이터의 무결성을 보장하기 위해 주기적으로 데이터베이스로 동기화하는 기능도 구현하였습니다.
![image](https://github.com/pop-pin/BackEnd/assets/118061713/1384d82a-6733-4a8d-8bb4-7b0232c5b0a6)

---

## 2.4 배포 인프라
a. Kubernetes를 통한 서비스 매니지먼트 
Kubernetes를 통해 서비스 컨테이너들을 관리하며, Istio와 같은 Service Mesh, ELK, Grafana를 활용한 모니터링을 통해 디버깅에 필요한 시간을 단축하여 개발자의 편의를 향상시킵니다. 또한 iptables을 IPVS로 대체하여 기존의 Kubernetes Cluster에서 Chain으로 인하여 발생하는 성능이슈를 해소했습니다.
![image](https://github.com/pop-pin/BackEnd/assets/118061713/b498ad32-e1a1-4d39-9060-2ade2469aa2e)

b. Git을 활용한 코드 및 클러스터 관리
현재 ArgoCD로 GitOps를 활용하여 클러스터를 관리중이며 Github Actions을 통해 Git 레포지토리에서 클러스터의 상태 및 백엔드 마이크로서비스 컨테이너 이미지를 동기화하고 있습니다. 또한 MongoDB, Redis 등의 다양한 오픈소스를 활용하여 클러스터를 구성했습니다. 이를 활용해 배포와 운영에 드는 시간을 최소화하고 에자일한 서비스 개발에 집중했습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/ba60f52e-7331-4e25-a976-464906daf95d)

c. ELK, Grafana를 활용한 모니터링 대시보드 구축

![image](https://github.com/pop-pin/BackEnd/assets/118061713/4d1c5a0e-505d-43d6-874a-b2a997ea5370)

ELK, Prometheus을 활용하여 클러스터 내부의 Node 및 Daemon을 모니터링하고 있습니다. 또한 Grafana의 알람 기능을 통해 이상상황에 신속하게 대처할 수 있도록 여러 규칙을 추가했습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/a31fabad-57ad-412d-8058-6f0f66d4aaba)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/cad7f3a5-71d9-4203-a7bb-07e9e8db1762)




