---
title: 소프트웨어 설계의 정석 스터디 - 2
author: Ariel
date: 2024-11-01 21:25:00 +0900
categories: [Study, Software Architecture]
tags: [Algorithm, Software Architecture, agile, waterfall]
---
이 포스트는 '소프트웨어 설계의 정석(한빛미디어)' 도서를 읽고 작성했습니다.
---

# 외부 설계

## 외부 설계란
> 시스템의 기능을 명세화하여 시스템의 외형을 파악할 수 있도록 함<br>
> 요구사항 정의에서 명확하지 않은 시스템 기능을 검토

* 외부 설계의 과정에서는 사용자 또는 사용자 기업이 속한 산업에 대한 업무 지식(도메인 지식)이 중요
* 도메인에 대한 높은 이해도는 원할한 시스템 설계 및 개발에 도움이 되며, 사용자와의 소통은 부족한 도메인 이해도를 향상하는데 도움이 됨

## 1. 유스케이스

* 유스케이스는 사용자가 시스템을 사용하는 시나리오를 표현한 것
  * 유스케이스의 사용자에는 외부 시스템을 포함하여 시스템의 접근하는 모든 사용자를 포함
* 유스케이스느 '회원은 주문을 등록한다'와 같은 문장으로 작성할 수 있음
* 유스케이스에는 최소 아래 네가지 내용을 작성해야 함
  * 유스케이스 명
  * 주요 액터
  * 주요 시나리오
  * 확장 시나리오
* 유스케이스를 작성할 때는 주요 액터와 시스템이 번갈아가며 무언가의 동작을 수행하는 시나리오의 형태로 작성
* 시나리오는 정상적으로 진행하여 성공하는 케이스는 물론, 실패 케이스도 고려
* 유스케이스에서는 화면 전환에 대해서는 설명하지 않으며 동작 중심으로 설계함
* 비즈니스 규칙을 별도로 정의하여 유스케이스를 보완할 수 있음
  * 유스케이스에서 설명하기 어려운 비즈니스적인 요소를 놓치지 않도록 보완할 수 있음

## 2. 개념 모델링
* 유스케이스가 시스템의 동적 행위를 나타내는 것이라면, 개념 모델링은 시스템의 정적인 구조를 나타냄
* 개념 모델은 데이터의 구조를 나타냄
  * 개념 모델을 기반으로 데이터베이스 논리 설계를 수행
* 개념 모델로 표현하는 것
  * 개념 이름 정리하기
  * 개념의 연관성 정리하기
  * 개념 간 연관성의 다중성(복수성) 정리하기
* 개념 모델링에는 다양한 개념과 속성이 등장하게 되며, 이해하기 어려운 업계 용어를 사용해야 하는 경우 용어집을 만들어 정리하는 것이 도움이 됨
* 개념 모델링의 주의점
  * 연관성 정리
    * 연관성 중복을 조심해야함
      * 순환참조와 같은 문제가 생김
  * 다중성 정리
    * 주로 1대1 다중성과 다대다 다중성을 주의해야 함
    * 1대1 다중성에서 개념의 속성이 너무 많거나 개념의 의미가 다르면, 가시성을 고려하여 1대1 다중성을 무시하고 분리하기도 함
    * 다대다 다중성에서는 정말 필요한가, 연관성 사이에 새로운 개념이 존재하진 않는가를 확인해야 함
* 개념 모델링을 끝내는 기준
  * 유스케이스 설명에 등장하는 개념이 모두 표현되어 있는지
  * 화면 설계에 등장하는 개념이 기본적으로 표현되어 있는지
  * 외부 시스템 I/F 설계에 등장하는 개념이 표현되어 있는지
  * 관리자의 승인을 받았는지

## 3. 화면 설계
* 화면 설계는 시스템 담당자가 기술적인 관점에서 설계
* UI설계 정책을 수립
  * 전제 조건
  * 화면 레이아웃 패턴
  * 화면 기능 패턴
  * 화면 항목 패턴
* 화면 전환도 작성
  * 화면 기능 패턴과 유스케이스 설명을 사용하여 화면 전환 다이어그램을 작성
  * like 스토리보드
* 화면 목록 작성
  * 화면 전환도에 등장한 화면들을 정리하여 화면 목록 작성
* 화면 목업 작성
  * 디자인 정책과 화면 전환도를 이용하여 목업을 제작
  * 퍼블리싱 가이드를 생각하면 이해하기 쉬움
* 화면 입력 검사 명세서 작성
  * 화면 목업을 따라 화면 입력 항목의 입력 검사 명세를 정리

## 4. 외부 시스템 I/F 설계
* 네트워크, 파일 교환 등을 통해 외부 시스템과 데이터를 교환하는 부분
* 웹 API는 비동기로 동작하며, 무상태성을 특징으로 가짐
* 다음의 항목을 고려하여 설계
  * 연결 대상
  * 프로토컬 및 수단
  * 타이밍
  * 인터페이스 항목 명세
  * 인증 및 보안
  * 예외 처리

## 5. BATCH 설계
* BATCH는 주기적으로 실행되는 프로그램
* 서버 프로그램처럼 메모리에 상주되지 않으며, 정해진 시간 또는 수동으로 실행
* 주요 설계 항목
  * 실행 타이밍
  * 실행 제어, 작업 제어
  * 트랜잭션
  * 복구
* 배치는 정해진 시간 내에 대량의 데이터를 처리해야 하므로, 성능을 고려하여 설계해야 함

## 6. 장표 설계
* 각종 보고서, 서면 등의 장표 출력을 설계

## 7. 데이터베이스 논리 설계
* 개념 모델링을 기반으로 데이터베이스 논리 설계를 수행
* 데이터베이스 논리 설계는 데이터베이스의 테이블, 컬럼, 제약 조건 등을 정의
* ER 다이어그램을 이용하여 작성하며 정규화를 수행
