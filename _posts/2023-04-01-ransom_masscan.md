---
layout: post
title: Ransom Masscan
categories: [Mal]

---
### 유형
* 랜섬웨어

### 타겟
- 불특정 다수 db 

### 공격시나리오
1. mysql sa 계정 bruteforce (1433)
2. mysql에서 xp_cmdshell로 공격계정 생성
3. 포트스캔 -> FW vpn 터널 포트(501/tcp) -> netsh로 포트변경
4. 공격계정으로 원격 로그인
5. 활동
- 측면이동, 스캐닝, 권한 상승, 로그 제거, 프로세스 중지 등
- 랜섬웨어를 통한 파일 암호화

### 특징
- 공개도구 사용
- 암호화 정보 별도 보관
- tool/prog : anydesk*, HRSword, 

### 동작


* 암호화
- rsa 공개키, aes 대칭키

## 추가 확인
* xp_cmdshell?
-> ms에서 os cmd 실행 가능하도록 하는 명령

* netsh?




### 참고
* FSI Intelligence Report Masscan Ransomware