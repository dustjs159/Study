💻 AWS IAM
==============
# 💡 인증 & 인가

![](https://images.velog.io/images/dustjs159/post/d0ce58f3-cd3f-4145-92f6-4428175ce225/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-20%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.32.06.png)

* 인증(Authentication) : Who Are You?
  * 사용자가 누구인지 확인하는 절차
  * e.g. 회사 건물에 출입할 때 사원증 or 지문 등으로 출입하려는 자가 누구인지 확인
* 인가(Authorization) : Are you allowed to do that?
  * 사용자의 특정 행위에 대한 제어
  * e.g. 인증 절차를 통과한 후에 건물 출입은 가능하나 특정 사무실에는 출입할 수 없음
* 한국어로써 인증과 인가의 단어가 주는 느낌은 비슷할 수 있으나, 영어로 번역된 Authentication(인증)과 Authorization(인가)는 엄연히 다른 의미이므로 주의!

# 💡 AWS IAM

* AWS IAM(Identity & Access Management) : **AWS 내 다양한 서비스들과 그 서비스들의 리소스들에 대한 접근 제어 서비스**
* IAM의 접근 제어는 인증과 인가로 수행
  * 인증(Authentication): IAM 서비스를 통해 AWS 웹 콘솔에 로그인(Sign in)
    * AWS Web Console 로그인 : ID + Password + MFA Token(Optional)
    * API 호출 : Access Key + Secret Access key + MFA Token(Optional)
  * 인가(Authorization) : 로그인 한 사용자에 대해 서비스와 리소스 접근 권한 제어(Permission Control)

## 📌 IAM을 통해 할 수 있는 것
* API 호출 가능
  * IAM을 사용하여 Access Key를 발급받고 API 호출 가능
  * AWS CLI or SDK 사용 가능
* MFA(Multi-Factor Authentication) 사용 가능
  * 사용자에 대한 MFA 인증 절차를 통해 보안 강화(OTP, Yubikey)
* 외부 사용자(Federated User)도 접근이 가능하도록 설정 가능
  * 임시 권한 : Assume Role을 통해 다른 Account 에서도 리소스에 접근할 수 있음

# 💡 IAM 기본 개념

* IAM Resource : User, Group, Role, Policy
  * 다른 AWS 서비스들과 마찬가지로 생성, 변경, 삭제 가능
* IAM Entities : User, Role
  * IAM 리소스 중 AWS에 로그인(= Sign in)할 때 인증(Authentication)의 대상
  * 로그인 할 때 Group은 물어보지 않으므로 Group은 제외
* IAM Identities : User, Group, Role
  * IAM 리소스 중 정책을 통해 권한을 부여받을 수 있는(Authorization) 대상
* Principal
  * 보안 주체. AWS에 무언가를 Request하는 주체
  * AWS 웹 콘솔에서 클릭(Action)하는 User
  * AWS API를 호출하는 User or APP

# 💡 IAM Resource

* IAM Resource에는 User, Group, Role, Policy 네 가지가 있음

## 📌 User

* User : AWS로 요청을 하고 그에 대한 응답을 받는 Principal
![](https://images.velog.io/images/dustjs159/post/1a5b4f40-5196-41b1-b61e-b25c47ae3707/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-22%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.14.36.png)
* 최초에 AWS에 회원 가입을 하고 이메일과 비밀번호로 로그인을 하게되면 ``Root User``로 로그인을 하게 됨
* 일단 ``Root User``는 최초에 IAM User를 생성하는 경우를 제외하고는 사용 금지.
  * 왜? Root 권한으로는 할 수 있는 것이 너무 많고 보안에 취약하기 때문에.
* 그래서 ``Root User`` 로 IAM User를 생성하고, User에게 권한을 부여하는 방식으로 AWS를 사용하는 것을 권고

### ✔️ Federated User

![](https://images.velog.io/images/dustjs159/post/8fc3524d-ac59-4289-a316-16aeb4a90fac/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-22%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.20.22.png)

* 외부 조직에서도 AWS 계정 내 리소스에 접근이 가능함
* 임시 자격 증명을 통해 접근 권한을 얻을 수 있음(영구적인 권한 X)

## 📌 Group

* 동일한 Policy or Role의 적용을 받는 User들의 집합
* 인증 대상은 아님
  * 로그인 할 때 Group을 물어보지는 않으므로
* User당 속할 수 있는 Group의 수는 10개

## 📌 Role

* 특정 권한을 갖는 IAM Identity
* User와 유사


## 📌 Policy

* AWS 서비스 or 리소스에 대한 Access Management
* Principal의 Request를 허용(Allow)할지 거부(Deny)할지 결정
* JSON Format
* Policy 종류
  * Identity-based Policy
  * Resource-based Policy
  * Permission Boundary
  * SCP()
  * Session Policy


### ✔️ Policy 구조
``` json
{
"Version" : "2021-08-26",
"Statement" : [
	{
	"Effect":"Allow or Deny",
	"Principal":"principal",
	"Action":[
		...
			],
	"Resource":[
		...
			],
	"Condition":{
		...
			}
		}	
	]
}
```
- `Effect` : 허용(Allow) or 차단(Deny)
- `Principal` : 접근을 허용 or 차단하고자 하는 대상(보안 주체)
- `Action` : 리소스에 대한 작업(형식 : [서비스명]:[작업명]. Ex, s3:GetObject)
- `Resource` : 서비스에 대한 리소스들의 상세 조건. ARN(Amazon Resource Number)사용
- `Condition` : 어떤 조건에서


