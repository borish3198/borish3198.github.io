---
layout: post
title : (minitalk) 
subtitle : minitalk 1일차
categories: TIL
tags : [TIL]
---

# 리눅스 환경에 서버 구현 하기

## 1. Web Server Software - lighttpd

- 웹 서버
  > 클라이언트들로부터 HTTP 요청을 받으면 해당 클라이언트가 요청된 정보를 웹 페이지 형태로 반환해주는 소프트웨어
  * 서버 소프트웨어의 종류
    : Apache, IIS, Nginx, lighttpd 등 다양한 소프트웨어가 존재하며 점유을이 가장 큰 소프트웨어는 apache, 성능이 가장 좋은 것은 Nginx로 알려져 있다.
  * 정적인 웹 vs 동적인 웹
    - 정적인 웹 : 클라이언트가 요구한 HTML문서만을 사용자에게 제공함, 아파치 웹 서버 하나면 구현 가능
    - 동적인 웹 : 사용자의 요구에 따라 다양한 웹 페이지를 제공하고, 이를 위해 php와 Mysql 데이터 베이스를 연계하여 사용함. ex)매번 새롭게 최신화되는 댓글 창

* * *
