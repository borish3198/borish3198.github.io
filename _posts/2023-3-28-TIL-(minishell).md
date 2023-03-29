---
layout: post
title : (Minishell) 1일차 나만의 쉘 BNF 정리하기 
subtitle : Minishell 작업일지
categories: STUDY
tags : [SPRING]
---

# Minishell 파싱부 개요

## 2. 파싱부 구현 과정

---

1. **Bash 명령어 BNF 형식으로 정규화**
2. **토크나이저 구현**
    1. 명령어 String → whitespace 기준 split
    2. $? 환경변수 내용 처리하기 (토크나이저인지 파서에서 처리하는지 잘 모르겠음)
3. **파서 구현 (햐향식 재귀 분석 - LL파서)**

### 2-1 Bash 쉘 BNF 정규화

- BNF란?

> **배커스-나우르[[주해 1]](https://ko.wikipedia.org/wiki/%EB%B0%B0%EC%BB%A4%EC%8A%A4-%EB%82%98%EC%9A%B0%EB%A5%B4_%ED%91%9C%EA%B8%B0%EB%B2%95#cite_note-1) 표기법**(Backus–Naur form), 약칭 **BNF**는 [문맥 자유 문법](https://ko.wikipedia.org/wiki/%EB%AC%B8%EB%A7%A5_%EC%9E%90%EC%9C%A0_%EB%AC%B8%EB%B2%95)을 나타내기 위해 만들어진 표기법이다. [존 배커스](https://ko.wikipedia.org/wiki/%EC%A1%B4_%EB%B0%B0%EC%BB%A4%EC%8A%A4)와 [페테르 나우르](https://ko.wikipedia.org/wiki/%ED%8E%98%ED%85%8C%EB%A5%B4_%EB%82%98%EC%9A%B0%EB%A5%B4)의 이름을 따서 부른다.
> 
> 
> BNF는 기본적으로 다음의 문법을 사용한다.
> 
> ```bash
> # 16진수 표현 BNF 문법 
> 
>  <**digit**> ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"
>  <**letter**> ::= "A" | "B" | "C" | "D" | "E" | "F"
>  <**number**> ::= <**digit**> | <**letter**>
>  <**integer**> ::= <**number**> | <**number**><**integer**>
> ```
> 

BNF는 한 언어의 문법을 표현하는 방식의 일종이며 이러한 방식으로 쉘 명령어의 문법을 정의해두는 과정이 필요하다. 위의 예시를 보면 <integer> ::= <number> | <number><integer> 형식으로 표현되는데, <number>는 다시 digit, letter로 정의돼 있는 것을 볼 수 있다. 

이런식으로 정의한 문법을 바탕으로 토큰의 의미를  부여하고 AST 트리로 만들어가는 과정이 이후에 진행할 **하향 회귀 파싱**에 해당하게 된다. 하향 재귀의 뉘앙스를 위 BNF 문법 예시를 통해 간접적으로나마 알아볼 수 있, 파서에서 실질적으로 구현해야할 부분이 BNF 형식으로 정의된 문법 내용이라는 추측을 할 수 있었다.

- Minishell에서 요구하는 쉘 BNF

> https://github.com/Swoorup/mysh
> 
> 
> ```bash
> <command line>	::	<job>
> |	<job> '&'
> | <job> '&' <command line>
> |	<job> ';'
> |	<job> ';' <command line>
> 
> <job>		::=	<command>
> |	< job > '|' < command >
> 
> <command	::=	<simple command>
> |	<simple command> '<' <filename>
> |	<simple command> '>' <filename>
> 
> <simple command>::=	<pathname>
> |	<simple command>  <token>
> ```
> 
> 쉘을 구현한 한 개발자의 BNF 예시이다. 기본적인 연산자들이 포함돼 있지만 과제에서 요구하는 ‘>>’ , ‘<<’ 등의 리다이렉션 연산자와 논리 연산자 등이 포함돼 있지 않다.
> 

```bash

```

- minishell BNF ver.1

```bash
<command_line>     ::= <pipeline>
							   		| <pipeline> '&&' <command_line>
							  		| <pipeline> '||' <command_line>

<pipeline>         ::= <command>
								  	| <pipeline> '|' <command>

<command>          ::= <simple_command>
								  	| <simple_command> <redirection_list>
								  	| <subshell>

<redirection_list> ::= <redirection>
										| <redirection_list> <redirection>

<redirection>      ::= '>' <word>
								  	| '<' <word>
								  	| '>>' <word>
								  	| '<<' <word>

<subshell>         ::= '(' <command line> ')'

<simple_command>   ::= <word>
									  | <simple_command> <word>

<word>             ::= <string>
									  | <option>
						  			| <wildcard_pattern>
											# wildcard 구현 방법은 감이 오지 않는데 BNF 수정이 필요할 경우 수정 예정
```

: 기존 쉘의 것들을 많이 참조하여 작성했다. 여러개의 리다레익션이 중첩되는 경우, 소괄호 안의 명령어의 경우 subshell을 통해 처리하는 케이스를 위한 문법도 추가돼 있다. 실제 쉘에선 word를 character와 number 단위 까지 쪼개고, 심지어 single quote, double quote 으로 시작하는 문자열도 나누곤 하는데 해당 부분은 토큰화 단계에서 처리할 예정으로 따로 표기하지는 않았다. 

팀원과 문법 상의 누락된 부분은 없는지 살펴 볼 예정이며 구현과정에서 수정사항은 현재 페이지 하단에 버전으로 나누어 추가할 예정이다.