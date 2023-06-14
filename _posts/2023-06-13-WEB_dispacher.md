---
layout: post
title: [SPRING] 필터, 디스패처, 인스팩터
categories: [WEB]

---

![IMG](/letthem_blog/assets/images/spring_1.PNG)
* KISA 소프트웨어 보안약점 진단 가이드(2021)의 spring MVC request life cycle

입력값을 믿지 못하니.. 필터를 사용한다.
기준은 Spring.
만능은 아니다. 

# 단계
Request -> Filter -> DispacherServlet -> Interceptor -> Handler(Controller) -> Data binding/Validation/Logic -> HandlerExceptionResolver -> Interceptor -> DispacherServlet -> Filter -> Response

## 1. Filter : 거르다.
* 안전한 값만 전달한다.
* 관리자 : tomcat 등 웹컨테이너
* 커버범위 : ALL
* 주역할 : 치환, 인코딩
* 주방어 : XSS, sqli
* 구성 : ServletRequest, ServletResponse

## 2. DispacherSevlet

## 3. Interceptor : 입력값을 검증하여 안전하지 않은 입력값은 요청 차단
* 관리자 : Spring
* 커버범위 : 특정 클라요청 관련 전역
* 주역할 : 인증, 인가, 정보 가공
* 구성 : HttpServletRequest, HttpServletResponse

## 4. Handler

## 5. Data binding/Validation/Logic : 라이브러리 또는 Validator 컴포넌트를 이용하여 입력값 검증
* 입력값을 검증하는 Validator 컴포넌트를 공통코드로 생성해 입력값의 검증작업을 하도록 한다.
* HttpServletRequest, HttpServletResponse

### 추천 프레임웍, 라이브러리(SQL)
* Hibernate
* MyBatis
* JPA
* (.NET) AntiSQLi
* (php) MeekroDB
* HTML Purifier

### 추천 프레임웍, 라이브러리(LDAP)
* LDAP Syntac Filters







