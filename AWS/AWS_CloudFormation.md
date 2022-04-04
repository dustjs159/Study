💻 [AWS] CloudFormation
===============
# 💡 IaC(Infra as a Code)

* IaC(Infra as a Code) : 코드로 인프라를 구축, 관리하기 위한 도구
  * 인프라 구축을 위한 리소스들을 프로비저닝하고 관리하는데 용이
* IaC 도구에는 구성 조정(Configuration Orcherstration)에 초점을 맞춘 툴과 구성 관리(Configuration Management)에 초점을 맞춘 두 가지 유형의 툴이 있는데 CloudFormation은 구성 조정에 조금 더 비중을 두고 있음
  * 구성 조정 툴은 인프라 구축에 비중을 두고 있고 구성 관리 툴은 인프라 관리에 비중을 두고 있음
  * 두 유형의 툴은 서로 어느 정도의 기능을 수행할 수 있음
  * 구성 조정 툴에는 AWS CloudFormation, Terraform 등이 있고 구성 관리 툴에는 Ansible 등이 존재


# 💡 AWS CloudFormation

* AWS CloudFormation : AWS 제공하는 IaC 도구
* 코드로 인프라 구성을 작성하고 작성한 인프라를 구축하기 위해 필요한 AWS 서비스들을 프로비저닝 + 구축
  * AWS 웹 콘솔에서 인프라를 구축하거나 수정할 때 일일이 손으로 직접 클릭하지 않아도 됨!
* **`JSON` or `YAML`** 포맷으로 작성
* CloudFormation 비용은 **무료**이나 스택을 구성하는 리소스들의 비용은 부과됨

## 📌 CloudFormation 작동 방식

* 인프라의 생성, 수정 및 삭제가 **템플릿(Template)** 을 통해 진행
* `JSON` or `YAML`로 템플릿(코드)을 작성
* 작성한 템플릿 저장 및 실행, **스택(Stack)** 생성
  * Local or **S3 버킷**에 저장
* 생성한 스택을 통해 프로비저닝 및 구축 작업

## 📌 CloudFormation Resource

* Template
  * Stack을 구성할 리소스를 프로비저닝하고 구축
  * 인프라 구축을 위한 리소스들이 설명되어 있는 파일(Parameter 정의)
  * `JSON` or `YAML` 로 작성된 코드
* Stack
  * 인프라 구축에 필요한 AWS 서비스들을 관리할 수 있는 단위
  * 스택 생성, 삭제 및 수정을 통해 인프라 **변경 사항 반영 가능**
  * 스택 삭제 시 리소스들이 전부 삭제
* Cloudformation
  * Stack 변경 사항 체크 및 업데이트
  * 에러 감지 시 롤백 지원

## 📌 Template 구성
* `JSON` 기준으로 작성

```json
{
   "AWSTemplateFormatVersion" : "version date",

   "Description" : "JSON string",

   "Metadata" : {
       
   },
   "Parameters" : {

   },
   "Rules" : {

   },
   "Mappings" : {

   },
   "Transform" : {

   },
   "Conditions" : {

   },
   "Resources" : {

   },
   "Outputs" : {

   }
}
```

* `Resources` 를 제외한 나머지는 옵션.
* `AWSTemplateFormatVersion` : 템플릿 버전
* `Description` : 템플릿 설명
* `Metadata` : 템플릿에 대한 추가 정보
* `Parameters` : 템플릿 실행 시 전달 할 parameter
* `Rules` : 
* `Mappings` : 템플릿 실행 시 선택하게 되는 값(특정 리전, AZ 등)
* `Conditions` : 생성 조건 판단
* `Transform` : Serverless App 전용
* `Resources` **(필수)** : EC2 인스턴스, S3 버킷 등의 리소스
* `Outputs` : 템플릿 실행 후 만들어지는 자원 결과값(인스턴스 ID, Private IP 등)