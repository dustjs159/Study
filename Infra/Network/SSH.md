💻 [Network] SSH
=================

# 💡 SSH(Secure Shell) 
* 안전한 서버 원격 접속을 위한 프로토콜
* 포트번호는 22번을 사용
* config 파일 위치
  * `/etc/ssh/sshd_config`
  * `/etc/ssh/ssh_config`
  * `sshd_config` 파일은 현재 시스템이 SSH 서버가 될 때(Inbound) 참조하는 설정 파일이며 `ssh_config` 파일은 현재 시스템이 SSH 클라이언트가 될 때(Outbound) 참조하는 설정 파일

## 📌 SSH 동작 원리
* 클라이언트 - 서버 모델로 동작
* 각각 SSH 클라이언트 및 데몬이 설치되어 있어야 함 - Port 22
* 서버 인증 : 클라이언트는 접속하고자 하는 서버가 정상적인 서버인지 검증
  * **공개키 암호화 방식(Two Key)** 사용
* 클라이언트 인증 : 서버는 클라이언트가 서버에 접근할 수 있는지 검증
  * **공개키 암호화 방식(Two Key)** 사용
* 클라이언트와 서버가 성공적으로 검증 절차를 통과하게 되면 생성되는 세션 키를 통해 전송하는 데이터를 암호화하여 안전하게 전송
  * **대칭키 암호화 방식(One Key)** 사용

## 📌 SSH 동작 과정 

* 서버 인증 과정
  * SSH 데몬이 설치된 서버는 클라이언트의 SSH 접속 요청을 기다리는 sshd 데몬이 실행 중
* SSH 클라이언트가 `ssh-keygen` 으로 Public Key, Private Key를 생성
* 접속하고자 하는 SSH 서버의 `~/.ssh/authorized_keys` 파일에 클라이언트의 Public Key를 등록
* SSH 클라이언트가 접속 시도(인증 좀 해줘)
* SSH 서버는 `~/.ssh/authorized_keys` 에 등록된 Public Key를 클라이언트에게 전달(이거 복호화 해봐)
* 클라이언트는 Private Key로 전달 받은 Public Key를 복호화
* 인증 성공 시, 접속 허용

## 📌 sshd_config 파일 주요 옵션
* `PermitRootLogin`
  * `root` 계정으로 SSH 접속을 허용하는지 여부
  * `root` 계정 접속을 막는 것을 권고 ( `PermitRootLogin : no` )
