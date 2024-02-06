#  🗺️ POPPIN, 팝핀 ✈️

<img src="https://github.com/pop-pin/BackEnd/assets/118061713/c684f264-3218-42ed-8add-3667363d94ca.png" width="230" height="230"/>
<img src="https://github.com/pop-pin/BackEnd/assets/118061713/3310e77b-3739-461f-ab71-649926e6088c.png" width="230" height="230"/>

<br>

### 😭사람들이 겪는 문제점
- 우리는 새로운 장소로 여행을 떠날 때 마다 맛집, 카페 등등 어느 곳을 가야할지에 대한 계획과 고민을 하게 됩니다. 
- 하지만 정보를 탐색하며 계획을 세우다보면 여행동선을 짜기 위해 지도를 봐야하며, 
- 정보들이 한눈에 들어오지 않아 이를 다시 정리하는데 많은 시간을 쏟게 되고 그로 인해 여행을 가기 전부터 지치게 되는 경우가 발생합니다. 
- 더군다나 외국인이라면 한국 여러 지역에 대한 명칭을 제대로 인지하지 못해 정보를 탐색하고 여행 계획을 세우는데 더 많은 시간이 들게 될 것입니다.
<br>

### 🤔새로운 장소를 추천 받고 싶을 땐?

그래서 POPPIN은 **Mapbox를 사용한 지도 구성과 데이터 시각화**를 통해 많은 사람들이 추천하는 가게들을 **보기쉽게 한눈에** 보여주어 여행의 계획을 더 편하게 세울 수 있도록 합니다.

<br>

### 🎯타겟
- 새로운 지역으로 여행 온 내국인
- 한국이 익숙하지 않은 외국인

<br>

### 📱 주요 기능
- 사용자에게 추천 가게들은 한눈에 보여주는 지도
- 사용자 리뷰
- 제휴 가게들에 대한 쿠폰 발급

<br>

# 🔥 기능

### 📑기능 리스트
### Login
- 카카오 로그인
- 특정 사용자 정보 업데이트
- 특정 사용자 탈퇴

### Location
- 가게 검색
- 특정 가게 조회
- 위도, 경도에 따른 주변 가게 리스트 조회

 ### Review
- 리뷰 작성
- 특정 리뷰 가져오기
- 특정 리뷰 업데이트
- 특정 사용자가 작성한 리뷰 조회
- 특정 가게에 작성된 리뷰 조회
- 특정 리뷰 삭제

### Like
- 특정 가게 찜
- 특정 유저의 찜한 가게 목록 조회
- 특정 가게 찜 취소

<br>

### 📈 크롤링 및 알고리즘
### 1. 크롤링
Google map api를 통해 얻어진 가게 정보들을 메타데이터와 함께 mongodb에 저장합니다.

Google map api키는 팀원 모두의 키를 사용하였으며 API키의 과금 방지 및 키 교체를 위해 키 스케쥴링 알고리즘을 제작하여 사용합니다.

API키의 순서와 사용횟수를 활용하여 API키 여러개를 순차적으로 사용해 API 한계를 극한까지 활용할 수 있도록 API키를 스케줄링하는 알고리즘으로 크롤링을 진행했습니다.

<크롤링 결과>

![image](https://github.com/pop-pin/BackEnd/assets/118061713/3a79ac84-d76e-4f98-a66d-87542a59d005)

### 2. 평점 계산 알고리즘
사용자의 평가 기록을 기반으로 한 가중치를 적용하여 평점을 계산합니다.

예시) 평소 5점 주던 사람이 주는 3점 != 1점 주던 사람이 주는 3점


<br>

### 📱프론트 구현
### 1. 레이어링
GeoJSON을 기반으로 지역별 레이어링을 구현했습니다. 이를 통해 사용자들은 카테고리별로 지역 정보를 쉽게 파악할 수 있습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/cc5be6ec-b52c-42cc-a6d0-c8c6edd1c0db)

예시) 서울시의 여러 구 별로 가게들의 평균 평점을 계산하여 평균 평점이 높은 지역을 한눈에 확인 할 수 있도록 하였습니다.

### 2. Mapbox API활용
Mapbox를 사용하여 기본적인 지도 구성과 데이터 시각화를 구현했습니다. 사용자들은 지도 상에서 직관적으로 지역 정보를 파악할 수 있으며, 가게 데이터도 추가하여 각 장소에 대한 정보를 제공합니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/6ba8d784-bb9d-47d1-bf1b-32aa8b74113e)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/975c2acb-6440-4c3d-9526-a534ec910d21)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/0eed7894-6f39-410e-a59f-1513d092dd30)

### 3. 이외 다양한 기능 구현
지도, 추천, 리뷰, 마이 페이지 등 다양한 페이지 구현

![image](https://github.com/pop-pin/BackEnd/assets/118061713/905eb3e4-afcf-4ea2-93f0-e75bab8bd8f2)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/d462a5cf-0e53-4550-9101-31dc3789c71d)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/582e904a-5a7a-4fff-815c-c45d87680e2a)
![image](https://github.com/pop-pin/BackEnd/assets/118061713/27f50fde-07b7-4a63-b25e-96a0b7d5e9ea)

<br>

## 💻백엔드 구현
### 1. OAuth2.0 로그인 및 JWT 토큰
회원가입과 같은 불필요한 절차를 줄여 사용자의 편의를 높이기 위해 OAuth2.0 기반의 로그인 시스템을 구현했습니다. 또한 JWT토큰을 엑세스 토큰과 리프세쉬 토큰으로 나눠서 발급해 보안처리를 하였습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/daa299e1-d0dc-4074-9ee9-2c3fbc1242dd)

### 2. 마이크로서비스 및 API Gateway
서비스의 확장성과 관리 용이성을 위해 마이크로서비스 아키텍처를 채택하였습니다. 또한 API Gateway를 통해 요청이 들어올 때 필터를 통한 토큰의 유효성 검사를 진행하는 등 여러 마이크로서비스의 설정을 용이하게 하기 위해 사용하였습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/b837bf8a-f112-46fe-83da-624b6c64d261)

### 3. Aggregate 프레임워크
크롤링을 통해 MongoDB에 저장된 데이터를 Aggregate 프레임워크를 사용하여 서울시의 구별로 데이터를 분리하여 평균 평점을 계산하는 등의 서비스 로직을 구현하는데 사용하였습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/ffc124d9-0195-406a-9d43-11065e86e6a0)

### 4. Redis를 통한 성능 향상
사용자가 특정한 가게에 좋아요를 누르는 상황에서 Redis를 사용하여 사용자 경험을 크게 향상시키고자 하였습니다. 또한 데이터의 무결성을 보장하기 위해 주기적으로 데이터베이스로 동기화하는 기능도 구현하였습니다.

![image](https://github.com/pop-pin/BackEnd/assets/118061713/1384d82a-6733-4a8d-8bb4-7b0232c5b0a6)

<br><br>

# 🛠️ 기술 스택 
### 🖥️ Backend 

- ### 언어, 프레임워크
  ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white)
  ![Springboot](https://img.shields.io/badge/spring%20boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
  ![Spring](https://img.shields.io/badge/spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
  ![Gradle](https://img.shields.io/badge/Gradle-02303A.svg?style=for-the-badge&logo=Gradle&logoColor=white)
  

- ### 데이터베이스
  ![MySQL](https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&logo=mysql&logoColor=white)
  ![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white)
  ![Redis](https://img.shields.io/badge/MongoDB-%2347A248.svg?style=for-the-badge&logo=mongodb&logoColor=white)
  - msa의 이점을 활용하여 정형, 비정형 데이터베이스를 동시에 사용
  - redis를 통해 유저 리프레시 토큰 관리

- ### api 테스트, 명세서
  ![Notion](https://img.shields.io/badge/Notion-%23000000.svg?style=for-the-badge&logo=notion&logoColor=white)
  ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
  - 노션에 명세서 페이지 및 swagger를 동시에 활용함으로 프론트 개발자에게 편리성 제공

<br>

### 📊 배포 및 인프라
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


<br><br>

### ⭐ Code Convention

---

<details>
<summary style = " font-size:1.3em;">Naming</summary>
<div markdown="1">

- 패키지 : 언더스코어(`_`)나 대문자를 섞지 않고 소문자를 사용하여 작성합니다.
- 클래스 : 클래스 이름은 명사나 명사절로 지으며, 대문자 카멜표기법(Upper camel case)을 사용합니다.
- 메서드 : 메서드 이름은 동사/전치사로 시작하며, 소문자 카멜표기법(Lower camel case)를 사용합니다. 의도가 전달되도록 최대한 간결하게 표현합니다.
- 변수 : 소문자 카멜표기법(Lower camel case)를 사용합니다.
- ENUM, 상수 : 상태를 가지지 않는 자료형이면서 `static final`로 선언되어 있는 필드일 때를 상수로 간주하며, 대문자와 언더스코어(Upper_snake_case)로 구성합니다.
- DB 테이블: 소문자와 언더스코어로(lower_snake_case) 구성합니다.
- 컬렉션(Collection): **복수형**을 사용하거나 **컬렉션을 명시합니다**. (Ex. userList, users, userMap)
- LocalDateTime: 접미사에 **Date**를 붙입니다.


</div>
</details>
<details>
<summary style = " font-size:1.3em;">Comment</summary>
<div markdown="1">

### 1. 한줄 주석은 // 를 사용한다.

```java
// 하이~
```

### 2. Bracket 사용 시 내부에 주석을 작성한다.

```java
/*
   하이~!
*/
```

### 3. 주요 함수에 대한 주석

```java
/*
 * 입력 : 인덱스:Long
 * 기능 : 유저 인덱스로 db에 접근해 유저 객체를 반환한다
 * 출력 : 유저:User
 */
public User getUser(Long idx)
```

</div>
</details>
<details>
<summary style = " font-size:1.3em;">Import</summary>
<div markdown="1">

### 1. 소스파일당 1개의 탑레벨 클래스를 담기

> 탑레벨 클래스(Top level class)는 소스 파일에 1개만 존재해야 한다. ( 탑레벨 클래스 선언의 컴파일타임 에러 체크에 대해서는 [Java Language Specification 7.6](http://docs.oracle.com/javase/specs/jls/se7/html/jls-7.html#jls-7.6) 참조 )

### 2. static import에만 와일드 카드 허용

> 클래스를 import할때는 와일드카드(`*`) 없이 모든 클래스명을 다 쓴다. static import에서는 와일드카드를 허용한다.

### 3. 애너테이션 선언 후 새줄 사용

> 클래스, 인터페이스, 메서드, 생성자에 붙는 애너테이션은 선언 후 새줄을 사용한다. 이 위치에서도 파라미터가 없는 애너테이션 1개는 같은 줄에 선언할 수 있다.


### 4. 배열에서 대괄호는 타입 뒤에 선언

> 배열 선언에 오는 대괄호(`[]`)는 타입의 바로 뒤에 붙인다. 변수명 뒤에 붙이지 않는다.

### 5. `long`형 값의 마지막에 `L`붙이기

> long형의 숫자에는 마지막에 대문자 'L’을 붙인다. 소문자 'l’보다 숫자 '1’과의 차이가 커서 가독성이 높아진다.

</div>
</details>
<details>
<summary style = " font-size:1.3em;">URL</summary>
<div markdown="1">

### URL

URL은 RESTful API 설계 가이드에 따라 작성합니다.

- HTTP Method로 구분할 수 있는 get, put 등의 행위는 url에 표현하지 않습니다.
- 마지막에 `/` 를 포함하지 않습니다.
- `_` 대신 `-`를 사용합니다.
- 소문자를 사용합니다.
- 확장자는 포함하지 않습니다.


</div>
</details>

<br>

### ☀️ Commit Convention

---

<details>
<summary style = " font-size:1.3em;">Rules</summary>
<div markdown="1">

### 1. Git Flow

작업 시작 시 선행되어야 할 작업은 다음과 같습니다.


> 1. issue를 생성합니다.
> 2. feature branch를 생성합니다.
> 3. add → commit → push → pull request 를 진행합니다.
> 4. pull request를 develop branch로 merge 합니다.
> 5. 이전에 merge된 작업이 있을 경우 다른 branch에서 진행하던 작업에 merge된 작업을 pull 받아옵니다.
> 6. 종료된 issue와 pull request의 label을 관리합니다.

### 2. IntelliJ

IntelliJ로 작업을 진행하는 경우, 작업 시작 시 선행되어야 할 작업은 다음과 같습니다.

> 1. 깃허브 프로젝트 저장소에서 issue를 생성합니다.
> 2. IntelliJ의 git 탭 → local develop branch 우클릭 → update 를 진행합니다.
> 3. IntelliJ의 git 탭 → local develop branch 우클릭 → new branch from ‘develop’ 을 진행합니다.
> 4. 생성한 issue 번호에 맞는 feature branch를 생성함과 동시에 feature branch로 checkout 합니다.
> 5. feature branch에서 issue 단위 작업을 진행합니다.
> 6. 작업 완료 후, add → commit을 진행합니다.
> 7. push 하기 전, remote develop branch의 변경 사항을 확인하기 위해 2번 과정을 다시 수행합니다.
> 8. IntelliJ의 git 탭 → local develop branch 우클릭 → merge ‘develop’ into ‘4번 과정에서 생성한 feature branch’ 를 진행합니다.
> 9. 만약 코드 충돌이 발생하였다면, IntelliJ에서 코드 충돌을 해결하고 add → commit을 진행합니다.
> 10. push → pull request (feature branch → develop branch) 를 진행합니다.
> 11. pull request가 작성되면 작성자 이외의 다른 팀원이 code review를 진행합니다.
> 12. 최소 한 명 이상의 팀원에게 code review와 approve를 받은 경우 pull request 생성자가 merge를 진행합니다.
> 13. 종료된 issue와 pull request의 label과 milestone을 관리합니다.


### 3. Etc

준수해야 할 규칙은 다음과 같습니다.

> 1. develop branch에서의 작업은 원칙적으로 금지합니다. 단, README 작성은 develop branch에서 수행합니다.
> 2. commit, push, merge, pull request 등 모든 작업은 오류 없이 정상적으로 실행되는 지 확인 후 수행합니다.

</div>
</details>

<details>
<summary style = " font-size:1.3em;">Branch</summary>
<div markdown="1">

### 1. Branch

branch는 작업 단위 & 기능 단위로 생성하며 이는 issue를 기반으로 합니다.

### 2. Branch Naming Rule

branch를 생성하기 전 issue를 먼저 작성합니다. issue 작성 후 생성되는 번호와 domain 명을 조합하여 branch의 이름을 결정합니다. `<Prefix>/<Issue_Number>-<Domain>` 의 양식을 준수합니다.

### 3. Prefix

- `main` : 개발이 완료된 산출물이 저장될 공간입니다.
- `develop`: feature branch에서 구현된 기능들이 merge될 default branch 입니다.
- `feature`: 기능을 개발하는 branch 입니다. 이슈 별 & 작업 별로 branch를 생성 후 기능을 개발하며 naming은 소문자를 사용합니다.

### 4. Domain

- `user`, `home`, `error`, `config` 


### 5. Etc

- `feature/7-user`, `feature/5-config`


</div>
</details>

<details>
<summary style = " font-size:1.3em;">Issue</summary>
<div markdown="1">

### 1. Issue

작업 시작 전 issue 생성이 선행되어야 합니다. issue 는 작업 단위 & 기능 단위로 생성하며 생성 후 표시되는 issue number 를 참조하여 branch 이름과 commit message를 작성합니다.

issue 제목에는 기능의 대표적인 설명을 적고 내용에는 세부적인 내용 및 작업 진행 상황을 작성합니다.

issue 생성 시 github 오른편의 assignee, label을 적용합니다. assignee는 해당 issue 담당자, label은 작업 내용을 추가합니다.

### 2. Issue Naming Rule

`[<Prefix>] <Description>` 의 양식을 준수하되, prefix는 commit message convention을 따릅니다.

### 3. Etc

<aside>
[feat] 약속 잡기 API 구현
<br/>[chore] spring data JPA 의존성 추가

</aside>

---

</div>
</details>

<details>
<summary style = " font-size:1.3em;">Commit</summary>
<div markdown="1">

### 1. Commit Message Convention

`[<Prefix>] #<Issue_Number> <Description>` 의 양식을 준수합니다.

- **feat** : 새로운 기능 구현 `[feat] #11 구글 로그인 API 기능 구현`
- **fix** : 코드 오류 수정 `[fix] #10 회원가입 비즈니스 로직 오류 수정`
- **del** : 쓸모없는 코드 삭제 `[del] #12 불필요한 import 제거`
- **docs** : README나 wiki 등의 문서 개정 `[docs] #14 리드미 수정`
- **refactor** : 내부 로직은 변경 하지 않고 기존의 코드를 개선하는 리팩터링 `[refactor] #15 코드 로직 개선`
- **chore** : 의존성 추가, yml 추가와 수정, 패키지 구조 변경, 파일 이동 `[chore] #21 yml 수정`, `[chore] #22 lombok 의존성 추가`
- **test**: 테스트 코드 작성, 수정 `[test] #20 로그인 API 테스트 코드 작성`
- **style** : 코드에 관련 없는 주석 달기, 줄바꿈

</div>
</details>

<details>
<summary style = " font-size:1.3em;">Pull Request</summary>
<div markdown="1">

### 1. Pull Request

develop & main branch로 merge할 때에는 pull request가 필요합니다. pull request의 내용에는 변경된 사항에 대한 설명을 명시합니다.

### 2. Pull Request Naming Rule

`[<Prefix>] <Description>` 의 양식을 준수하되, prefix는 commit message convention을 따릅니다.

### 3. Etc

[feat] 약속 잡기 API 구현
<br/>[chore] spring data JPA 의존성 추가

</div>
</details>



