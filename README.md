# IAM Role

Account -

### User
 - Management console
 - Progmatic Access <- CLI / SDK 

Access Key
 - Accesskey ID
 - Secret Access Key
 - IAM 은 Accesskey랑 Policy를 갖고있다.

### Policy
  - type: json
  - permission
     - AWS 관리형
     - AWS 고객관리형
  - Condition ex 1) MFA
  - Conditoin ex 2) Source IP


### Group / 최소권한 정책
1) User 는 기본적으로 권한이 없음
2) Group 에 policy 적용 
3) User 를 Group 에 추가

### Role
| 제일 중요함
* 


# 실습

### system manager
* CH01/aws-system-manager.json 은 다음과 같이 정의된다.
* aws ssm send-command --document-name "qls-2188369-0002f472c1a537b6-InstallDashboardApp-1432WY6TEDGXZ" --document-version "1" --targets "Key=instanceids,Values=i-014fa12f676c33183" --parameters '{}' --timeout-seconds 600 --max-concurrency "50" --max-errors "0" --region ap-northeast-1
  * System Manager 내에서 확인 가능
