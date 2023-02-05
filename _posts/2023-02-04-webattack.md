---
layout: post
title: (Web) param
categories: [Web]

---

요청 시에 사용하는 파라미터에는 생각보다 많은 것을 넣을 수 있음 

### ?test= 에 넣을 수 있는 것
* script (for xss)
* sql query (for sqli)
* 파일명(for file up/download)
* 타 사이트의 resource (ex. immalicious.com/mal.js)
* 동일 사이트의 작업(for csrf, ex. samedomain.com/changepw?pw=1111)
* 서버 내부 resource(for ssrf, http://사설ip대역:1111/secret.js))
* 다양한 프로토콜(ex.ldap://작업, file:///작업, ftp://작업 )

### 무슨 동작이 일어나?
* 파일읽기
* 파일쓰기
* 악의적 동작 실행(client의)
* 악의적 동작 실행(server의)
* 정보 노출
* 정보 유출

### 방어하기
* 사용자의 입력을 믿으면 안됨
- 입력값 이스케이프
- 화이트리스트로 허용된 것만
- 자원 무결성
- 자원 신뢰성(저 host의 자원을 믿어도 됨?)

* 서버는 사용자를 믿으면 안됨
- 서비스 권한 최소화
- 실행 권한 최소화(쓰기, 실행 권한을 안주면 돼)

* 서버는 정보를 드러내면 안됨
- 중요 정보 get 통해 노출 금지
- 잘못된 설정을 통한 헤더/에러 코드 등으로 서버 정보 노출
- 암호화 잘 걸려있니? 취약한 암호화 방식이니?

* 시큐어코딩
- 개발 시 시큐어코딩을 적용(개발단계부터 적용하지 않으면 개발 이후 적용 시 비용(시간,예산,인력)이 어마어마하다)

-끗-