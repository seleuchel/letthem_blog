---
layout: post
title: Mail Analysis
categories: [Analy]

---
# Mail 분석
### 위험성
* 공격자가 초기 시스템 침투 시 사용(ATT&CK: Initial Access, T1566.001)
* 피싱 url, 악성 첨부파일(문서, 실행파일) 등이 삽입됨 
* 관련용어 : BEC(Business Email Compromise) 

# Mail 기술
## 1. Mail protocol
* **SMTP(TCP 25)**
    - 평문
    - ex. sendmail

* **POP3(TCP 110) POP3S(TCP 995:SSL) : 읽으면 사라져**
    - 메시지 접근 에이전트 
    - USSER, PASS명 송신 
    - POP3원리: https://darksoulstory.tistory.com/66
    - EX. OUTLOOK

* **IMAP4(TCP 143) (TCP 993:SSL) : 읽어도 안사라져(서버에 메일 남음)**
    - 헤더검사
    - 내용검색
    - 부분 내려받기

# 2. Mail 동작 
**(송신자:MUA)** --<span style='color: #fff5b1'>SMTP</span>--> **(메일서버<송신자>:MSA)** **(메일서버 간의 포워딩)** --<span style='color: #fff5b1'>SMTP</span>-->  --<span style='color: #fff5b1'>SMTP</span>--> **(메일서버<수신자>:MTA)** --<span style='color: #ffdce0'>POP3/IMAP4</span>--> **(수신자:MUA)**

###용어
* MUA(Mail Use Agent): e-mail client SW
* MTA(Mail Transfer Agent): 메일서버(SMTP 사용)
* MSA(Mail Submission Agent): 메일을 MTA로 전달
* MDA(Mail Delivery Agent): 메일을 MUA(수신자)로 전달

## 3. Mail 전달방식
- SPF(Sender Policy Framework)
- DKIM(Domain Keys Identified Mail)
- DMARC(Domain-based Message Authentication, Reporting & Conformance)

# Mail 분석
## 1.Mail Protocol
- 준비중. 이메일 프로토콜의 구성

## 2.Mail
### 1) Message Envelope
* MAIL FROM : <송신자> (SPF. 신뢰가능)
* RCPT TO : <수신자>


### 2) MESSAGE HEADER 
* Received : 
* Message-Id : 
* Delivered-To : 수신자
* Received-SPF : 
* Authentication-Results : 
* X-Original-SENDERIP: 송신자 IP?
* X-Original-SENDERCOUNTRY: KR, South Korea 
* X-Original-MAILFROM: 송신자
* X-Original-RCPTTO: 수신자
* DKIM-Signature : 
* DomainKey-Signature : 
* Content-Type : 
* Date : 보낸날짜
* From : 송신자 MAIL FROM과 다를 수 있음(DMARC. 신뢰가능)
* To : 수신자 RCPT TO와 다를 수 있음
* Subject : 제목


### 3) MESSAGE BODY
info (Base64 Encoded picture)
* X-MsgID:


## ※ 분석하기 좋은 도구
- SysTools EML Viewer Pro (유료)
- free-eml-viewer.exe (사용안해봄)
- https://github.com/cyberdefenders/email-header-analyzer (메일헤더 분석기)


# 실습
1) DNS 서버 구축
2) 메일 서버 구축 
3) 메일 송수신


### 참고
https://www.iana.org/assignments/message-headers/message-headers.xhtml
https://www.ahnlab.com/kr/site/securityinfo/secunews/secuNewsView.do?menu_dist=3&cmd=scrap&seq=8494
