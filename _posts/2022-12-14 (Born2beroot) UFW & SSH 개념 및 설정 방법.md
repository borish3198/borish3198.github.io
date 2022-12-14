---
layout: post
title : (Born2beroot) UFW & SSH 개념 및 설정 방법
subtitle : Born2beroot 2일차 개념정리
categories: TIL
tags : [TIL]
---

# UFW & SSH 개념 및 설정 방법

## 1. UFW (Uncomplicated Firewall)

- 방화벽이란
  > 방화벽은 미리 정의된 보안 규칙에 기반해 들어오고 나가는 네트워크 트래픽을 모니터링하고 제어하는 네트워크 보안 시스템
- 작동원리
  * 기본적으로 방화벽은 모든 접근을 거부한 후 허용할 접근만 단계적으로 허용하는 방식 (공항처럼)
  * 방화벽은 기본적으로 통신 포트(네트워크를 통해 데이터가 이동하는 통로) 모두를 차단
  * 이 중 일부 포트만을 접근 허용 가능하도록 열어둔다.

- 포트란
  > 포트란 외부의 다른 장비와 접속할 때 해당 장비에서 실행중인 프로그램들을 식별하기 위해 필요한 프로세스의 논리 단위이다.
  ex) 한국(ip)에서 일본(ip)의 도쿄를 방문하기(프로그램) 위해 하네다 공항(포트)을 통해 일본으로 향했다.
  ex) 이번엔 한국(ip)에서 일본(ip)의 오사카를 방문하기(프로그램) 위해 오사카 공항(포트)를 이용했다.
  * 총 가용한 포트의 개수는 : 65535개
  * well-known port
  ![포트 이미지](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F991F92475B25CF7124)
  
* * *
