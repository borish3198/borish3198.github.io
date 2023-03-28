---
layout: post
title : (Minishell) 들어가며 
subtitle : Minishell 작업일지
categories: STUDY
tags : [SPRING]
---

# Minishell 파싱부 개요

## 1. 미니쉘에 들어가며

---

: 이번 과제 미니쉘은 실행부와 파싱부로 역할을 나눠서 쉘을 만들어보는 팀 프로젝트이다. 실행부는 팀원을 통해 어떠한 식으로 진행되는지 과제 후에 알아볼 예정이고, 우선 내가 맡은 파싱부의 진행과정에 대해 정리하고자 한다.  

  미니쉘 과제 파싱부를 맡을 경우 컴파일러나 쉘에서 명령어를 어떻게 컴퓨터가 이해할 수 있도록 구조화하는지 심도 있게 알아볼 수 있다. 미니쉘을 힘들고 지루해보이는 과제로만 생각했는데 팀원 분인 mygo님이 보너스까지 하자고 독려해주셔서 알아보던 중 AST 트리와 같은 보너스 구현에 핵심적인 개념에 대해(개념이 존재한다는 사실) 알게 됐고, 이 개념들을 알아보다 보니 컴파일러 이론에까지 이르렀다(찍먹수준이지만).

  코딩, 개발 능력에만 집중하던 요즘, CS 지식에 한 층 더 다가갈 수 있는 기회라 생각했고, 과제의 핵심 개념들을 정리하면 파싱 부분을 해결하고자 한다. 추상 구문 트리, 하향 재귀 분석, LL 파싱 등 듣기만 해도 어렵지만 왠지 설레는 해당 개념들을 차근차근 정리해보자.

![http://www.korea-press.com/news/photo/201501/67324_40322_141.jpg](http://www.korea-press.com/news/photo/201501/67324_40322_141.jpg)