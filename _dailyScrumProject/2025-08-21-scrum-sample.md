---
title: "Java & 운영체제 학습 스크럼(샘플)"
excerpt: "스크럼 샘플입니다."
date: 2025-08-21 10
tags: [java, operating-system, sprint, team-learning]
author: kiwoong-park
author_profile: true
layout: single
---

## 📋 Sprint Goals

### 🎯 주요 목표
- **Java 객체지향 프로그래밍** 핵심 개념 마스터
- **운영체제 프로세스 관리** 이해 및 실습
- **팀 코드 리뷰** 문화 정착
- **기술 블로그 포스팅** 1인 1포스트 작성

### 🔥 성공 지표
- [ ] 각자 Java 미니 프로젝트 1개 완성
- [ ] 운영체제 이론 퀴즈 80점 이상
- [ ] 팀원 간 코드 리뷰 5회 이상
- [ ] 학습 내용 블로그 포스팅 4개 작성

---

## 📚 학습 목표 & 내용

### ☕ Java 학습 목표

#### **1주차 완료 항목**
- [x] Java 기본 문법 (변수, 조건문, 반복문)
- [x] 배열과 문자열 처리
- [x] 메소드 작성과 호출

#### **이번 주 목표**
- [ ] **객체지향 프로그래밍 (OOP) 4원칙**
  - 캡슐화 (Encapsulation)
  - 상속 (Inheritance) 
  - 다형성 (Polymorphism)
  - 추상화 (Abstraction)

- [ ] **클래스와 객체**
  - 클래스 설계 원칙
  - 생성자와 소멸자
  - 접근 제어자 (private, protected, public)
  - static 키워드 활용

- [ ] **예외 처리**
  - try-catch-finally 구문
  - 커스텀 예외 클래스 생성
  - 예외 전파와 처리 전략

#### **실습 프로젝트**
```java
// 이번 주 미니 프로젝트: 도서관 관리 시스템
public class Library {
    private List<Book> books;
    private List<Member> members;
    
    public void addBook(Book book) {
        // 도서 추가 로직
    }
    
    public boolean lendBook(String isbn, String memberId) {
        // 도서 대출 로직
        try {
            // 예외 처리 포함
        } catch (BookNotAvailableException e) {
            // 커스텀 예외 처리
        }
    }
}
```

### 🖥️ 운영체제 학습 목표

#### **1주차 완료 항목**
- [x] 운영체제 개요 및 역할
- [x] 컴퓨터 시스템 구조
- [x] 시스템 호출 (System Call)

#### **이번 주 목표**
- [ ] **프로세스 관리**
  - 프로세스 vs 스레드 개념
  - 프로세스 생명주기 (Life Cycle)
  - Process Control Block (PCB)
  - 프로세스 스케줄링 알고리즘

- [ ] **CPU 스케줄링**
  - FCFS (First Come First Served)
  - SJF (Shortest Job First)
  - Round Robin
  - Priority Scheduling
  - 멀티레벨 큐 스케줄링

- [ ] **프로세스 동기화**
  - 임계 구역 (Critical Section)
  - 뮤텍스 (Mutex)
  - 세마포어 (Semaphore)
  - 데드락 (Deadlock) 개념

#### **실습 내용**
```bash
# Linux 프로세스 모니터링 실습
ps aux | grep java
top -p [PID]
kill -9 [PID]

# 스케줄링 알고리즘 시뮬레이션
# Python으로 Round Robin 구현
```

---

## 👥 이번 주 계획

### 👨‍💻 김개발
**Focus**: Java OOP 심화 + 미니 프로젝트
- **월요일**: 캡슐화, 상속 개념 학습
- **화요일**: 다형성, 추상화 실습
- **수요일**: 도서관 시스템 설계
- **목요일**: 예외 처리 구현
- **금요일**: 코드 리뷰 및 리팩토링

### 👩‍💻 이자바  
**Focus**: Java 예외처리 전문가 되기
- **월요일**: try-catch 심화 학습
- **화요일**: 커스텀 예외 클래스 설계
- **수요일**: 예외 처리 베스트 프랙티스 연구
- **목요일**: 팀 프로젝트에 예외 처리 적용
- **금요일**: 예외 처리 가이드 블로그 포스팅

### 👨‍💻 박운영
**Focus**: 운영체제 프로세스 관리 마스터
- **월요일**: 프로세스 생명주기 정리
- **화요일**: CPU 스케줄링 알고리즘 학습
- **수요일**: 스케줄링 시뮬레이션 구현
- **목요일**: Linux 프로세스 실습
- **금요일**: 운영체제 개념 정리 포스팅

### 👩‍💻 최시스템
**Focus**: 프로세스 동기화 및 데드락
- **월요일**: 임계구역 개념 학습
- **화요일**: 뮤텍스, 세마포어 실습
- **수요일**: 데드락 시나리오 분석
- **목요일**: 동기화 문제 해결 실습
- **금요일**: 동기화 메커니즘 정리

---

## 📈 Daily Standup 현황

### 🗓️ 8월 21일 (수요일) 스탠드업

#### 어제 한 일 (Yesterday)
- **김개발**: Java 상속 개념 학습, Animal-Dog 클래스 실습 완료
- **이자바**: 커스텀 예외 클래스 3개 구현 (`InvalidAgeException`, `BookNotFoundException`, `MembershipExpiredException`)
- **박운영**: FCFS, SJF 스케줄링 알고리즘 이론 학습 및 Python 시뮬레이션 50% 완성
- **최시스템**: 임계구역 개념 정리, Producer-Consumer 문제 분석

#### 오늘 할 일 (Today)
- **김개발**: 다형성 실습, 도서관 시스템 클래스 다이어그램 작성
- **이자바**: 예외 전파 메커니즘 학습, 도서관 프로젝트에 예외 처리 적용
- **박운영**: Round Robin 스케줄링 구현, Linux `ps`, `top` 명령어 실습
- **최시스템**: 뮤텍스 vs 세마포어 차이점 정리, 데드락 예방 기법 학습

#### 장애물/도움 필요 (Blockers)
- **김개발**: 인터페이스 vs 추상클래스 차이가 헷갈림 → 이자바가 오후에 설명 예정
- **박운영**: Python 멀티스레딩 구현에서 막힘 → 최시스템과 페어 프로그래밍 계획
- **이자바, 최시스템**: 특별한 장애물 없음

---

## 🏆 이번 주 성과

### ✅ 완료된 작업들
1. **Java OOP 기초** - 전 팀원 완료
2. **예외 처리 메커니즘** - 이자바 리드로 팀 학습 완료  
3. **프로세스 스케줄링 시뮬레이션** - 박운영 구현 완료
4. **코드 리뷰 문화** - 총 8회 리뷰 진행 (목표 대비 160%)

### 📊 학습 진도율
- **Java**: 75% ✅
- **운영체제**: 70% ✅  
- **팀 프로젝트**: 60% 🚧
- **블로그 포스팅**: 50% 🚧

### 🎉 팀 하이라이트
- 이자바의 예외 처리 가이드가 팀 전체 코드 품질 향상에 크게 기여
- 박운영의 스케줄링 시뮬레이션이 이론 이해에 실질적 도움
- 최시스템의 동기화 예제가 복잡한 개념을 쉽게 설명

---

## 🔄 회고 (Retrospective)

### 😊 잘된 점 (Keep)
- **페어 프로그래밍** 효과가 좋았음 - 계속 진행
- **Daily Standup**으로 진도 공유가 원활
- **실습 중심 학습**이 이해도를 크게 향상

### 😅 아쉬운 점 (Problem)  
- **이론과 실습의 균형** - 실습에 치우쳐 이론 정리가 부족
- **시간 관리** - 일부 팀원이 과도한 완벽주의로 시간 지연
- **문서화** - 학습 내용 정리가 개인별로 편차 존재

### 💡 개선 방안 (Try)
- **타임박싱** 도입 - 각 학습 토픽별 시간 제한 설정
- **템플릿 제공** - 학습 정리 양식 통일
- **중간 점검** - 수요일 오후 추가 체크인 미팅

---

## 📅 다음 스프린트 미리보기

### Week 4 Sprint (8월 26일 ~ 9월 1일)
**주제**: Java 컬렉션 프레임워크 & 운영체제 메모리 관리

#### 예상 학습 내용
- **Java**: ArrayList, HashMap, Iterator, Generic
- **운영체제**: 가상 메모리, 페이징, 세그멘테이션
- **팀 프로젝트**: 도서관 시스템 완성 및 배포

---

## 📞 연락처 & 리소스

### 🔗 유용한 링크
- [팀 GitHub 저장소](https://github.com/Santiago-kwp/Santiago-kwp.github.io)
- [Java 공식 문서](https://docs.oracle.com/javase/8/docs/)
- [운영체제 개념 정리 노션](https://www.notion.so/os-concepts)
- [팀 슬랙 채널](https://teamworkspace.slack.com)

### 📚 추천 학습 자료
- **Java**: "자바의 정석" (남궁성)
- **운영체제**: "Operating System Concepts" (Silberschatz)
- **온라인**: 백기선의 Java 라이브 스터디

---

**Keep Learning, Keep Growing! 🌱**

*마지막 업데이트: 2025년 8월 21일 오전 9시*