Chapter 3 실습 - Auto Sacaling

# Serverless

### MSA
* ECS - 컨테이너
* ECR - 레지스트리
* ECS - Fargate
* EKS

### Container Management
* 사용량
* 버전
* 소유권
* 좀비
* 분실

### Lambda Function
> 훅+트리거링 -> script 실행
> 비용 효율화
> Free Tier 있음!!

### 배포
* Lambda 핸들러 클래스 생성
* AWS Lambda Function 생성
* IAM ROLE
*
*
*
> 운영 자동화!

### 제한
* memory 제한: 3GB
  * vCPU가 메모리에 따라 증가함 
* 실행 제한: 15분
* 기간 제한: 
* 배포 제한:
* 제한걸리면 실패 + CloudWatch 에 등록

# API Gateway
* Edge 서비스
* API 개발간소화
* DDoS 제한 적용되어있음
* Swagger -> import 가능

# AWS Batch
* Lambda -> Gatesway+batch -> Service

# Database
### 비강경 데이터베이스
> * Oracle / Mysql / PostgreSQL
> * NoSQL
>   * Key-value 형태

### 관리형 데이터베이스 / 비관리형 데이터베이스

### AWS DB
#### 관리형 
* RDS
* Aurora
  * MySQL, PostgreSQL
* Redshift
  * 관리형
#### 관계형
* DynamoDB
* Neptune
  * GraphDB
* ElastiCache
  * Redis

### Amazon RDS
* 
### Aurora

### DynamoDB
* Partition Key
* Accellator

### ElasticCache
* in-memory DB
* Redis

### Amazon DMS
* DB 이전지원 -> 양쪽중 하나는 AWS에 있어야됨

# Network
> * Internet Gateway
> * Route Table
>    * Route Rule
>    * subnet 
> * Public IP

### NAT
* Instance
* Gateway

### VPC Endpoint
* S3, DynamoDB 등 VPC 밖의 서비스와 연계

### virtual private gateway
* Custom Gateway - AWS Virtual Gateway
* DX - DirectConnect 전용선 이용 가능

### VPC peering => 백본 네트워크 사용
* Peering + routing table 설정 필요
* VPC 마다 internet gateway 필요
* NAT 도 이웃 VPC 사용 불가
  * Interface
  * Gateway
  * Fort-forwarding에 따른 차이
* cross-account, cross-region 지원
* Transit Gateway
  * Attachment 생성 <- 하나의 VPC 에 종속적임
    * endpoint마다 하나씩 만들어야 함
  * 각 VPC에 routing table 설정
    * 10.0.0.8/8 -> transit gateway
  * Transit Gateway에 통합 routing table 적용

### Edge location
* Shield
  * Standard 가 있으며, 비용 올라가면 추가 서비스 지원
*
*
*

### 보안그룹
* inbound 거부
* outbount 허용
* NACL
  * 양방향 허용
  * 상태 비저장
* Bastion Host (Jump host)
  * Agent forwarding
    * Linux 에서 사용 가능
    * client 가 public / private 전부 갖고있음


# Storage
> * 휘발성 여부
>   * Instance Store
>   * EBS
> * Storage Type
>   * EBS : Block Storage
>   * S3 : Object Storage

### S3
* 무제한 저장
* 최대 5TB
* 내구성 거의 무제한
* 가용성 높다
* EBS 스냅샷 저장
* AMI 저장
* Bucket
  * Region 단위 선택
* 인터넷용 스토리지
  * 이터넷에서 직접 접근 가능
* Path 방식 / Domain 방식
  * Domain 방식으로 변화중
* ACL 직접 제어 가능
* IAM에서 관리가능
* 정접 웹 호스팅 가능
* 용도: Write Once, Read Many
* Version관리 가능
  * 기능 선택 가능
  * 기본적으로 비활성화, 활성화 가능, 이후엔 중지만 가능
* 객체 잠금 기능
* 비용
  * GB단위
  * Request 단위
  * outbound
* Standard
* Standard-IA
* Glacier
  * Vault / Archive
  * Log 저장에 활용
* object Lifecycle

### 그 외
* EFS
  * NFS
  * 인스턴스당 하나
* FXS
  * SMB
  * AD 적용 필요함
  * for windows file server
  * for lustre
* Storage Gateway
  * On-Prem 에 AWS 스토리지 데이터를 가져오는용도
    * File send
    * mount
  * AWS Transferto SFTP
* Datasync
  * On-Prem의 데이터를 online으로 빠르게 올리는용도
* Snowball
  * Edge - 컴퓨팅 활용 랙 1개쯤?
  * Mobile - 차로 옮김