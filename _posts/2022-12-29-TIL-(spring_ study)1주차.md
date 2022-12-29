---
layout: post
title : (Spring Study) 1주차 
subtitle : backend 개발자 한 걸음
categories: STUDY
tags : [SPRING]
---

# 자바 스프링 스터디 시작!

## 1. 스프링 이해에 필요한 개발 상식

- Spring Boot : Spring을 더 쉽게 이용하기 위한 도구이자 웹 어플리케이션 프레임워크, Spring 프레임워크에 톰캣 서버를 내장하고 많은 부분을 자동화한 것이 Sprinb Boot이다.

![sping](https://melonicedlatte.com/assets/images/2021_3Q/spring_architect.png)
<center>출처 : https://melonicedlatte.com/assets/images/2021_3Q/spring_architect.png</center>

- Gradle : Gradle 은 거의 모든 종류의 언어를 지원하는 오픈소스 빌드 자동화 툴이다.
  * 빌드 : 소스코드 파일을 실행가능한 소프트웨어 산출물로 만드는 일련의 과정 (컴파일링, 링크 등의 과정을 통틀어 말함 / Makefile와 같은 역할을 수행한다고 생각하면 된다.)

![gradle](https://github.com/gradle/gradle/raw/master/gradle.png)
<center>출처 : https://github.com/gradle/gradle/raw/master/gradle.png</center>

- Thymeleaf : 서버 사이드 템플릿 엔진
  * 템플릿 엔진 : html의 고정된 파트를 템플릿으로 만들고 db에서 데이터를 가져와야하는 부분들을 가져와 html을 그리는 역할을 수행

![템플릿 엔진](https://velog.velcdn.com/images/hi_potato/post/f80ea247-368e-41ee-b5c8-6e1baee7458c/image.png)
<center>출처 : https://velog.velcdn.com/images/hi_potato/post/f80ea247-368e-41ee-b5c8-6e1baee7458c/image.png</center>

- JPA : 자바 진영에서 만든 ORM 기술 표준
  * ORM (Object-Relational Mapping) : 애플리케이션의 class와 관계형 데이터베이스의 테이블을 매핑함으로써 SQL이 아닌 객체 중심으로 개발을 함
  * 매핑 : 객체의 참조와 테이블의 외래 키를 매핑하는 것?

- HIBERNATE : 자바의 ORM 프레임워크 중 하나

* * *

## 2. 스프링 웹 개발 기초
- 웹 서비스를 가능하게 하는 세 가지 기본 방식에 대해 알아보자!

#### 1. 정적 컨텐츠
