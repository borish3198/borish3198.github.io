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

- 정적 컨텐츠
  * 1. 클라이언트에서 정적 컨텐츠인 html 파일을 요구
  * 2. 내장 톰캣 서버에서 이를 스프링 컨테이너로 전달 후 해당 페이지 관련 컨트롤러 유무 확인
  * 3. 없을 경우 해당 html을 그대로 반환


- MVC와 템플릿 엔진
  > MVC : Model, View, Controller의 앞글자를 따오고 각각의 기능을 분리하여 웹 서비스를 구현하는 일종의 아키텍처를 말함.
  ![MVC 순서도](https://mblogthumb-phinf.pstatic.net/MjAxNzAzMjVfMjUw/MDAxNDkwNDM4NzI4MTIy.4ZtITJJKJW_Nj1gKST0BhKMAzqmMaYIj9PobYJMFD4Ig.xTHT-0qyRKXsA4nZ2xKPNeCxeU2-tLIc-4oyrWq5WBgg.PNG.jhc9639/mvc_role_diagram.png?type=w800)
  <center>출처 : https://mblogthumb-phinf.pstatic.net</center>
  
  * 1. 클라이언트에서 th(템플릿 엔진)이 포함된 html 파일을 요구 
  * 2. 내장 톰캣 서버에서 이를 컨테이너로 전달 후 해당 파일 컨트롤러를 통해 모델 객체에 필요로 하는 데이터를 전달
  * 3. 모델은 데이터베이스 등에 접근하여 필요로 한 데이터를 다시 컨트롤러로 전달
  * 4. 모델로부터 전달받은 데이터로 컨트롤러는 뷰(html)를 viewResolver를 통해 업데이트
  * 5. 유저에게 수정된 뷰를 전달
 

- API
> 클라이언트와의 통신뿐 아니라 서버끼리와의 통신에도 사용됨
- API
  * 1. 클라이언트에서 GET 메서드를 전송
  * 2. 내장 톰캣 서버에서 이를 스프링 컨테이너로 전달 후 해당 이름의 GET 메서드와 매핑되는 컨트롤러로 연결
  * 3. @ResponseBody를 통해 viewResolver로 연결되지 않고 JsonConver/StringConverter로 연결
  * 4. 해당 데이터(객체)를 json/String으로 변환하여 html의 body에 해당 내용을 직접 반환함
