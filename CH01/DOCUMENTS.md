# Global infrastructure
* Region
* Edge Location
  * Route 53, CloudFront
  * Caching

# Scope
* Global
* Region
* AZ (가용영역)

# IAM Role
> Account / User

### User
 - Management console
 - Access key given by each user
 - Progmatic Access <- CLI / SDK 

Access Key
 - Accesskey ID
 - Secret Access Key
 - IAM 은 Accesskey랑 Policy를 갖고있다.

### Policy
  - type: json
  - permission
     - 자격
     - 자원
  - AWS 관리형
  - AWS 고객관리형
  - Condition ex 1) MFA
  - Conditoin ex 2) Source IP

### Role
  - 임시자격증명
  - Single Sign On
  - Cross-Account Access
    - EC2 - Instance Profile

### Group / 최소권한 정책
1) User 는 기본적으로 권한이 없음
2) Group 에 policy 적용 
3) User 를 Group 에 추가

# Organization
* Account
* Service policy

# 실습

### system manager
* CH01/aws-system-manager.json 은 다음과 같이 정의된다.
* aws ssm send-command --document-name "qls-2188369-0002f472c1a537b6-InstallDashboardApp-1432WY6TEDGXZ" --document-version "1" --targets "Key=instanceids,Values=i-014fa12f676c33183" --parameters '{}' --timeout-seconds 600 --max-concurrency "50" --max-errors "0" --region ap-northeast-1
  * System Manager 내에서 확인 가능


# Instance 구성
* Machine Image
* Instance Type
* network
* security group

# CLI
* aws configure 
  * ~/.aws/credentials
  * ~/.aws/cnofig

# System Manager
#CloudFormation
#OpsWorks

#EC2
* 휘발성 / 항시성 데이터에 대해서 판단 필요
### AMI - Amazon Machine Image
* 공개된 이미지 / 직접 생성 등 가능
* 재사용 가능하게 / provisioning
* marketplace도 있음

### Instance Type
* t2.micro ...

### Storage
* EBS
* instance store

### Netowrk
* VPC, subnet, ...

### Security group
* 재사용 가능
* 포트 / 소스(접근가능한) address

### Instance Profile
* IAM Role

### (Optional) User Data
* 사용자가 직접 추가하는 데이터
  * 설치용  bash script 등

* Instance 구성 뒤 start->pending -> running -> stop -> pending -> running -> stop -> Terminate
> pending 이후 metadata 초기화

# Pricing
* On-demand
* spot
* Dedicated-instances

# Elastic Block Store
 * 네트워크 분리 가능

# Elastic Load Balancing
* Application / network / classig

# Auto Scaling
* Launch Configuration
* Launch Template
* Min/Max/Desired
* Instance Lifecycle Hook
