# 모니터링 - CloudWatch
> * 표준지표
>   * memory는 지표로 파악이 어렵다
> * 사용자 정의 지표
> * 경보
> * 알림

### 표준지표
* namespace별로 지표가 관리됨
* Dimension
* 15개월 저장

### 사용자정의 지표
* aws cli / API를 이용해서 cloudwatch에 직접 추가

### Events
* Source / target

# Log
> 구성
> 수집
> 분석

### CloudWatch - Log Stream

> 지표 - 서비스 (네임스페이스) - dimension(이단계에서 차트로 보임)

### CloudTrail
* 계정활동 기록
  * API 이벤트
* S3에 저장됨
* EC2 인스턴스 내 활동은 저장하지 않음

# AWS Config
> CloudTrail과 연계하여 서비스 제공
* 리소스 구성 / 보고
  * 규칙 정의
* 기록 제어
* 구성변경 모니터 < CloudTrail과 연동필요

-- CloudTrail / Config / 레벨?

# 보안
### Macie
### AWS KMS
* Master KEY 관리
* Storage 간 연계
### AWS HSM
* KMS + multi-tenant

# Amazon GuardDuty
> 위협탐지
> CloudTrail + VPC FlowLog 필요

# Resource
> 자원관리
> 카오스 엔지니어링
** 

### 비용 절감
* 코어 성능에 대한 테스트
  * t. 계열은 가용성 테스트에는 적절하지 않음
* 예약인스턴스 등
* 불필요한 자원 감축
* Lambda, Tag 등 이용

### Stopinator
* 자원 중지
  * Lambda를 이용하면 됨


# Trusted Advisor
> 비용에 대한 절감 지침 
* Enterprise / Business 에 따라 뷰가 달라짐


# Cloud Formation
* AMI + UserData
* 버전관리 필요함
* JSON / YAML 형태의 포맷으로 "Template" 작성
* 집합 단위(스택) 생성
* 드리프트 감지
  * 드리프트: 하위 변경 사항에 대한 상위 반영
* CloudFormer -> 구성 기반으로 template 작성
* CloudFormation Designer : GUI 기반


### AMI
* Region 단위
* Linux는 snapshot을 통한 버전관리가 가능함
* Windows 는 직접 생성 불가능
  * 네트워크 정보 제거 후 종료 시점에 버전관리 가능