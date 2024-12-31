---
title: 소프트웨어 설계의 정석 스터디 - 4
author: Ariel
date: 2024-12-31 18:00:00 +0900
categories: [Study, Software Architecture]
tags: [Algorithm, Software Architecture, agile, waterfall]
---
이 포스트는 '소프트웨어 설계의 정석(한빛미디어)' 도서를 읽고 작성했습니다.
---

# 아키텍처의 목적

## 아키텍처란
1. 정의 
   * 시스템의 요소, 관계, 설계 및 진화 원칙에 의해 구현된 환경에서의 시스템의 기본 개념 또는 속성
2. 기대효과
   * 유지보수성 향상
     * 아키텍처를 정비하면 큰 시스템을 작은 단위로 개발 가능하여 복잡성 감소
   * 적합성 향상
   * 견적에 활용
   * 기술 리스크 최소화
   * 소스 코드 자동 생성에 적용
   * 프레임워크에 적용


---

# 아키텍처 설계 접근법

> 아키텍처 설계는 개발 과정에서 발생하는 문제에 대해 시스템 전체가 어떻게 해결할 수 있는지를 미리 통찰하는 것에서 시작합니다

1. 객체지향 설계
   * 아키텍처 설계의 핵심은 '처리의 공통화', '인터페이스와 구현의 분리', '블랙박스'
   * 이는 객체지향 설계의 포인트와 동일하며, 객체지향 설계를 통해 아키텍처 설계를 수행하는데 도움이 됨
2. 서브시스템 분할
   * 시스템은 규모에 따라 복잡성이 증가함
   * 시스템의 복잡성을 억제하기 위해서는 시스템의 규모를 제한해야 하지만, 시스템의 규모는 요구사항 정의에 따라 결정되는 것이므로 개발자의 편의에 따라 조정할 수 없음
   * 요구사항을 설계 단계에서 미리 분할하여 시스템의 규모를 제한할 수 있음
   * 이렇게 분할하여 설계한 시스템을 서브시스템이라고 함
   * 이 때 결합도가 높게되면 분할한 의미가 없어지므로, 서브시스템 간의 결합도를 낮추는 것이 중요함
3. 레이어(직교화)
   1. 레이어란
      * 시스템을 여러 계층으로 나누어 각 계층이 독립적으로 동작하도록 하는 설계 방법
      * 레이어의 개념은 스택 호출과 동일함
      * 상위 레이어는 하위 레이어만 알면 되며, 계층을 건너 뛰어 접근할 수 없음
      * 이 때 접근할 수 없는 영역을 블랙박스라고 함
   2. 자바에서의 이용
      * 패키지 구성을 이용하여 레이어 구분 가능
      * ex) com.example.app.controller, com.example.app.service, com.example.app.dao
4. 처리 공통화(DRY)
   * DRY(Don't Repeat Yourself)는 처리의 공통화를 의미
   * 처리의 공통화는 시스템의 복잡성을 줄이는 핵심
   * 처리의 공통화를 통해 시스템의 복잡성을 줄이고, 유지보수성을 향상시킬 수 있음
5. 설계 및 프로그램 추적성
   * 설계와 프로그램은 항상 일치해야 함
   * 설계와 프로그램이 일치하지 않으면 유지보수성이 떨어지고, 시스템의 복잡성이 증가함
6. 의존성 주입
   * 클래스 간 의존성을 정리하기 위한 방법
   * 의존성 주입을 통해 클래스 간의 의존성을 명확하게 하고, 시스템의 복잡성을 줄일 수 있음
   * 대표적으로 스프링 프레임워크에서 사용
7. 마이크로서비스
   * 마이크로서비스는 서비스를 작은 단위로 나누어 개발하는 방법
   * 시스템을 분할하고, 분할한 것을 느슨한 결합으로 다시 연결하는 것
   * 공통 폐쇄 원칙에 따라 컴포넌트에는 같은 이유로 변경하는 것만 포함하고, 다른 이유로 변경하는 것은 다른 컴포넌트에 포함 시켜야 함