Linux Directory Structure
====================================
# Summary
- Last Updated : 21.06.17 Thu   
- Updated by : 윤연선
-----------------------------------

# 리눅스의 디렉토리 구조
   
<img width="588" alt="스크린샷 2021-05-23 오후 4 41 07" src="https://user-images.githubusercontent.com/57285121/119252174-ae3bed80-bbe5-11eb-978c-9184f9707f62.png">
   
## '/'
* root
* 최상위 디렉토리
* 모든 디렉토리의 시작점
* root 사용자만 쓰기 권한이 있음

## /bin
* 아주 기본적인 프로그램이 위치
* 일반적인 사용자가 사용하는 명령어들이 위치

## /sbin
* 시스템 바이너리
* 시스템 관리자가 사용하는 명령어들이 위치

## /etc
* 설정 파일
* 프로그램이 동작하는 방법을 설정

## /dev
* 장치 파일

## /proc 

## /var

## /usr
* 시스템이 아닌 사용자가 사용할 프로그램들이 저장되는 디렉토리
* /usr/bin   
> * 일반적인 유틸리티, 프로그래밍 툴 등과 함께 대부분의 사용자 명령어가 위치   
* /usr/lib   
> * 사용자를 위한 라이브러리가 위치   
* /usr/local   
> * 기본 OS에서는 필요하지 않는 실행 가능 파일들이 위치   
* /usr/share   
> * 독립된 데이터 파일들이 위치(vim, zsh 등)