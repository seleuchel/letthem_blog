---
layout: post
title: Encoding
categories: [WEB]

---
## 종류
* HTML 인코딩 
&#x0A; -> 개행을 의미

* UTF-8

* 유니코드

* URL Encoding


## 입력, 출력인코딩 
* GET : 요청정보 헤더 
브라우저 HTML에서 
```
<meta charset="UTF-8"> # 웹에서 이렇게 띄워줌
<form method="post" accept-charset="euc-kr" > ## euc-kr 인코딩으로 데이터를 전송할거다. </form>
** 자고로 브라우저마다 기본 인코딩이 다름.. 이거는 이전 서블릿 강의 참조 ㄲ 
아니면
document.formname.accpetCharset="utf-8" # js
$("form[name='formname']").attr("accept-charset") = "utf-8"; # jquery

IE용
document.charset="euc-kr";
document.forname.submit()
```

서버에서
```
서블릿의
resp.setContentType("text/html;charset=UTF-8"); # 서버에서 응답을 이렇게 출력하겠다.
req.setCharacterEncoding("UTF-8") # 요청받은 문자열을 이렇게 인코딩해서 받겠다.
```

* POST : 요청정보 몸체

참고
* https://ifuwanna.tistory.com/198

제이쿼리 왜써여 - 코드 속성 바로바로 고치려구