---
title: "[Introduction to Structured Query Language] - MySQL 기본"
date: 2023-05-21 19:33:00 +0900
categories: ["강의 노트", "Web Applications for Everybody"]
tags: ["web", "coursera"]
---

> 이 포스팅은 Charles Severance 교수(이하 척 아저씨)의 Coursera 강의 ["Introduction to Structured Query Language"](https://www.coursera.org/learn/intro-sql) Week 2 에서 다룬 내용을 정리합니다.



(*end of post*)

---

[^1]: 사실 HTML 특유의 문법을 빡세게 잡지 않는 풍조는 지금도 약간 남아있는게, 여타 다른 언어는 문법 오류 하나 때문에 멀쩡한 프로그램도 컴파일 시켜주지 않는게 대부분이지만 HTML 기반의 웹 페이지는 문법 오류가 있어도 일단 화면에 뭘 띄워주긴한다.  

[^2]: 텔넷은 과거에 원격 서버에 데이터를 전송하거나 불러올 때 사용했던 프로토콜이다. 현재는 서버들이 보안이 허술한 텔넷을 더이상 지원하지 않는 추세로 돌아서기 때문에 기본적으로 텔넷 사용은 권장되지 않는다. 

[^3]: Port 80은 서버가 클라이언트의 HTTP 요청을 받아들이는 용도로 사용하는 기본(default) 포트이다. 요즘 흔한 HTTPS 요청은 기본적으로 Port 443을 이용한다. 

[^4]: Status를 나타내는 숫자에는 규칙이 있는데, 400번대의 숫자는 클라이언트의 요청에 문제가 있을 때, 500번대의 숫자는 서버에 문제가 있을 때 볼 수 있다. 대표적인 예시로 에러코드 404는 클라이언트가 존재하지 않는 content를 요청했을 때 볼 수 있다. 

[^5]: 단위는 바이트(byte) 이다. 