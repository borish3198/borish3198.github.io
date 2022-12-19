---
layout: post
title : (Born2beroot) 리눅스 환경에서의 서버 구현 원리(워드프레스)
subtitle : Born2beroot 4일차 서버 환경에 대한 이해
categories: TIL
tags : [TIL]
---

# 리눅스 환경에 서버 구현 하기

> 리눅스(데비안os)에 워드프레스 서버를 설치하는 과정에서 필요한 프로그램과 그 역할에 대해 알아보자
![연결도](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FO8FJ4%2FbtrGQEJJmV8%2FTODP0UaDtvkyVVbM8Fz2uK%2Fimg.png)
출처 : https://eunbin00.tistory.com/106

<center> 데이터베이스 제외 해당 연결도의 순서에 따라 각 프로그램들의 역할을 알아보고 서버의 작동 원리를 종합해보자! </center>


## 1. Web Server Software - lighttpd

- 웹 서버
  > 클라이언트들로부터 HTTP 요청을 받으면 해당 클라이언트가 요청된 정보를 웹 페이지 형태로 반환해주는 소프트웨어
  * 서버 소프트웨어의 종류
    : Apache, IIS, Nginx, lighttpd 등 다양한 소프트웨어가 존재하며 점유을이 가장 큰 소프트웨어는 apache, 성능이 가장 좋은 것은 Nginx로 알려져 있다.
  * 정적인 웹 vs 동적인 웹
    - 정적인 웹 : 클라이언트가 요구한 HTML문서만을 사용자에게 제공함, 아파치 웹 서버 하나면 구현 가능
    - 동적인 웹 : 사용자의 요구에 따라 다양한 웹 페이지를 제공하고, 이를 위해 php와 Mysql 데이터 베이스를 연계하여 사용함. ex)매번 새롭게 최신화되는 댓글 창

* * *

## 2. CGI / FastCGI - PHP-fpm
- 공용 게이트웨이 인터페이스 Common Gateway Interface
  > 웹 서버 프로그램(미리 준비된 정보를 클라이언트에게 보내는 기능에 한정)에 더해, 웹 서버 상에서 데이터를 조합하기 위해 웹서버와 외부 프로그램을 연결하기 위한 연계방법
- FastCGI
  > CGI는 요청이 들어올 때 마다 프로세스의 생성과 삭제를 반복하기 때문에 속도가 느려짐. 이를 보완하기 위한 것이 FastCGI이며, 이는 요청이 들어올 때마다 이미 만들어진 프로세스를 바탕으로 새로운 요청들을 처리해 나감 
  * php-fpm(Fast Process Manager) : 동적인 웹페이지 구성을 위해 필요한 외부 프로그램으로 php-fpm은 FastCGI를 활용하는 외부 프로그램

* * *

## 3. 워드프레스는 어디에?
- 
