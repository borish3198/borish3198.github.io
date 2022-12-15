---
layout: post
title : (Born2beroot) 파티션 & LVM
subtitle : Born2beroot 3일차 개념정리
categories: TIL
tags : [TIL]
---

# 파티션 & LVM 개념

## 1. 파티션 (디스크 파티션)

- 디스크 파티션이란
  > 하나의 디스크를 논리적으로 분할하여 여러 개의 저장 공간으로 사용하는 개념
  * Primary 파티션 : 운영체제가 설치 가능한 파티션, 하드디스크당 최대 4개까지 생성 가능
  * Extended 파티션 : 실제 데이터는 저장 불가능하며 논리 파티션의 정보를 담는 역할, 1개만 생성 가능
  * Logical 파티션 : 확장 영역이 갖는 범위 내에서 생성되며 실제 데이터를 저장 가능, 개수에 제한이 없음 
  
- 리눅스 파티션 특징
  * primay disk 뒤에는 숫자 1~4가 붙고, logical 파티션은 5 이후의 번호가 붙음.
  * scsi 디스크가 연결될 경우 sda1 ~ sda4 등의 이름이 붙음
  ![포트 이미지](https://github.com/borish3198/borish3198.github.io/blob/063288296706fae3eb3354e5be7b2da926ca7ee8/assets/images/post/linux_partition_img.png?raw=true)
  * root 파티션 : 핵심 시스템 파일 저장
  * boot 파티션 : 리눅스 커널 이미지, 맵, 파일 등을 저장
  * var 파티션 : Spool(메일, 프린트) 디렉토리와 로그 파일을 저장
  * tmp 파티션 : 사용자 응용 프로그램에서 임시 파일을 저장하는 곳
  * home 파티션 : 사용자의 홈 디렉토리를 위한 파티션
  * swap 파티션 : 가상 메모리를 저장 (보통 RAM 크기의 2배로 사용)
  
* * *

## 2. LVM (Logical Volume Manager)



