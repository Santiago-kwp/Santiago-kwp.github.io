# Jekyll에서 여러 게시판 만들기: 컬렉션(Collections) 활용 가이드

Jekyll의 컬렉션 기능을 사용하면 기본 블로그 포스트 외에도 다양한 종류의 게시판을 만들 수 있습니다. 예를 들어 "프로젝트", "튜토리얼", "리뷰" 등 각각 다른 성격의 콘텐츠를 분리해서 관리할 수 있습니다.

## 컬렉션이란?

컬렉션은 Jekyll에서 제공하는 기능으로, `_posts` 외에 추가적인 문서 그룹을 만들 수 있게 해줍니다. 각 컬렉션은 독립적인 게시판처럼 작동하며, 고유한 레이아웃과 설정을 가질 수 있습니다.

## 설정 방법

### 1. `_config.yml`에서 컬렉션 정의

```yaml
# 컬렉션 설정
collections:
  projects:
    output: true
    permalink: /:collection/:name/
  tutorials:
    output: true
    permalink: /:collection/:name/
  reviews:
    output: true
    permalink: /:collection/:name/

# 컬렉션별 기본 설정
defaults:
  # 기존 _posts 설정
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: true
      comments: true
      share: true
      related: true
      
  # _projects 컬렉션 설정
  - scope:
      path: ""
      type: projects
    values:
      layout: single
      author_profile: true
      share: true
      comments: true
      sidebar:
        nav: "projects"
        
  # _tutorials 컬렉션 설정  
  - scope:
      path: ""
      type: tutorials
    values:
      layout: single
      author_profile: true
      read_time: true
      toc: true
      toc_sticky: true
      
  # _reviews 컬렉션 설정
  - scope:
      path: ""
      type: reviews
    values:
      layout: single
      author_profile: true
      share: true
      related: true
```

### 2. 디렉토리 구조 생성

컬렉션명 앞에 언더스코어(`_`)를 붙여 폴더를 생성합니다:

```
your-blog/
├── _config.yml
├── _data/
│   └── navigation.yml
├── _pages/
│   ├── about.md
│   ├── projects-archive.md      # 프로젝트 목록 페이지
│   ├── tutorials-archive.md     # 튜토리얼 목록 페이지
│   └── reviews-archive.md       # 리뷰 목록 페이지
├── _posts/                      # 기본 블로그 포스트
│   └── 2024-01-01-hello-world.md
├── _projects/                   # 👈 프로젝트 게시판
│   ├── 2024-01-15-my-portfolio.md
│   └── 2024-02-01-spring-boot-app.md
├── _tutorials/                  # 👈 튜토리얼 게시판
│   ├── 2024-01-10-java-basics.md
│   └── 2024-01-20-spring-tutorial.md
├── _reviews/                    # 👈 리뷰 게시판
│   ├── 2024-01-05-book-review-clean-code.md
│   └── 2024-01-25-course-review-java.md
└── assets/
```

### 3. 네비게이션 메뉴 업데이트

`_data/navigation.yml`:

```yaml
main:
  - title: "Home"
    url: /
  - title: "Blog"
    url: /posts/
  - title: "Projects"
    url: /projects/
  - title: "Tutorials"  
    url: /tutorials/
  - title: "Reviews"
    url: /reviews/
  - title: "About"
    url: /about/

# 프로젝트 사이드바 네비게이션 (선택사항)
projects:
  - title: "프로젝트 목록"
    children:
      - title: "웹 개발"
        url: /projects/#web-development
      - title: "모바일 앱"
        url: /projects/#mobile-app
      - title: "오픈소스"
        url: /projects/#open-source
```

### 4. 컬렉션별 아카이브 페이지 생성

#### `_pages/projects-archive.md`
```markdown
---
title: "프로젝트"
permalink: /projects/
layout: collection
collection: projects
entries_layout: grid
author_profile: true
classes: wide
---

개발한 프로젝트들을 소개합니다.
```

#### `_pages/tutorials-archive.md`
```markdown
---
title: "튜토리얼"
permalink: /tutorials/
layout: collection
collection: tutorials
entries_layout: list
author_profile: true
---

단계별 학습 가이드를 제공합니다.
```

#### `_pages/reviews-archive.md`
```markdown
---
title: "리뷰"
permalink: /reviews/
layout: collection
collection: reviews
entries_layout: list
author_profile: true
---

책, 강의, 도구에 대한 리뷰입니다.
```

## 컬렉션별 포스트 작성 방법

### 1. 프로젝트 포스트 예시

`_projects/2024-01-15-spring-boot-ecommerce.md`:

```markdown
---
title: "Spring Boot 이커머스 프로젝트"
excerpt: "Spring Boot와 JPA를 활용한 온라인 쇼핑몰 구축"
date: 2024-01-15
header:
  teaser: /assets/images/projects/ecommerce-thumb.jpg
  overlay_image: /assets/images/projects/ecommerce-banner.jpg
  overlay_filter: 0.5
sidebar:
  - title: "기술 스택"
    text: "Spring Boot, JPA, MySQL, Thymeleaf"
  - title: "개발 기간"
    text: "2023.12 - 2024.01"
  - title: "GitHub"
    text: "[소스코드 보기](https://github.com/username/ecommerce)"
gallery:
  - url: /assets/images/projects/ecommerce-1.jpg
    image_path: /assets/images/projects/ecommerce-1.jpg
    alt: "메인 페이지"
  - url: /assets/images/projects/ecommerce-2.jpg
    image_path: /assets/images/projects/ecommerce-2.jpg
    alt: "상품 목록"
tags:
  - Spring Boot
  - JPA
  - MySQL
categories:
  - Web Development
---

## 프로젝트 개요

Spring Boot를 활용하여 구축한 이커머스 웹사이트입니다.

## 주요 기능

- 회원가입/로그인
- 상품 검색 및 필터링
- 장바구니 및 주문 관리
- 관리자 페이지

{% include gallery caption="프로젝트 스크린샷" %}

## 기술적 도전과 해결

### 1. 성능 최적화
- JPA N+1 문제 해결
- 쿼리 최적화
- 캐싱 적용

### 2. 보안
- Spring Security 적용
- CSRF 보호
- SQL Injection 방지

## 배운 점

이 프로젝트를 통해 실제 운영 환경에서의 고려사항들을 많이 배웠습니다...
```

### 2. 튜토리얼 포스트 예시

`_tutorials/2024-01-20-spring-boot-jpa-tutorial.md`:

```markdown
---
title: "Spring Boot JPA 완벽 가이드"
excerpt: "Spring Boot에서 JPA를 활용한 데이터베이스 연동 방법"
date: 2024-01-20
toc: true
toc_sticky: true
toc_label: "목차"
header:
  teaser: /assets/images/tutorials/jpa-thumb.jpg
difficulty: "중급"
estimated_time: "60분"
tags:
  - Spring Boot
  - JPA
  - Tutorial
categories:
  - Backend
  - Database
---

## 🎯 학습 목표

이 튜토리얼을 완료하면 다음을 할 수 있습니다:
- Spring Boot에서 JPA 설정하기
- Entity 클래스 작성하기
- Repository 패턴 활용하기

## 📋 사전 준비사항

- Java 8 이상
- Spring Boot 기본 지식
- 데이터베이스 기본 개념

## 1단계: 프로젝트 설정

### Maven 의존성 추가

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```

### application.yml 설정

```yaml
spring:
  datasource:
    url: jdbc:h2:mem:testdb
    driver-class-name: org.h2.Driver
  jpa:
    hibernate:
      ddl-auto: create-drop
    show-sql: true
```

## 2단계: Entity 클래스 작성

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(nullable = false)
    private String username;
    
    // getter, setter...
}
```

계속해서 단계별로 설명...
```

### 3. 리뷰 포스트 예시

`_reviews/2024-01-25-clean-code-book-review.md`:

```markdown
---
title: "클린 코드 - 애자일 소프트웨어 장인 정신"
excerpt: "로버트 C. 마틴의 클린 코드 리뷰"
date: 2024-01-25
rating: 5
author_name: "로버트 C. 마틴"
publisher: "인사이트"
pages: 584
header:
  teaser: /assets/images/reviews/clean-code-thumb.jpg
tags:
  - Book Review
  - Clean Code
  - Software Engineering
categories:
  - Book Review
---

## 📖 책 정보

- **저자**: 로버트 C. 마틴 (Uncle Bob)
- **출판사**: 인사이트
- **페이지**: 584페이지
- **난이도**: ⭐⭐⭐⭐ (4/5)
- **추천도**: ⭐⭐⭐⭐⭐ (5/5)

## 🎯 이 책을 읽어야 하는 이유

클린 코드는 모든 개발자가 반드시 읽어야 할 필독서입니다...

## 📝 주요 내용

### 1장: 깨끗한 코드
깨끗한 코드의 정의와 중요성에 대해 설명합니다...

### 2장: 의미 있는 이름
변수, 함수, 클래스명을 짓는 방법...

## ✅ 좋았던 점

1. 실제 코드 예시가 풍부함
2. 리팩토링 과정을 단계별로 보여줌
3. 실무에 바로 적용 가능한 내용

## ❌ 아쉬운 점

1. 일부 예시가 Java에 편중됨
2. 초보자에게는 다소 어려울 수 있음

## 🎯 추천 대상

- 코드 품질을 개선하고 싶은 개발자
- 팀 프로젝트를 진행하는 개발자
- 리팩토링에 관심이 있는 개발자

## 📊 평점

| 항목 | 점수 |
|------|------|
| 내용의 깊이 | ⭐⭐⭐⭐⭐ |
| 실용성 | ⭐⭐⭐⭐⭐ |
| 가독성 | ⭐⭐⭐⭐ |
| 예시의 질 | ⭐⭐⭐⭐⭐ |

**총점: 4.8/5**
```

## 고급 설정

### 1. 컬렉션별 레이아웃 커스터마이징

`_layouts/project.html`:

```html
---
layout: single
---

<div class="project-header">
  <h1>{{ page.title }}</h1>
  
  {% if page.tech_stack %}
  <div class="tech-stack">
    <h3>🛠 기술 스택</h3>
    <ul>
    {% for tech in page.tech_stack %}
      <li><span class="tech-badge">{{ tech }}</span></li>
    {% endfor %}
    </ul>
  </div>
  {% endif %}
  
  {% if page.demo_url %}
  <div class="project-links">
    <a href="{{ page.demo_url }}" class="btn btn--primary">🚀 Live Demo</a>
    {% if page.github_url %}
    <a href="{{ page.github_url }}" class="btn btn--info">📂 GitHub</a>
    {% endif %}
  </div>
  {% endif %}
</div>

{{ content }}
```

### 2. 컬렉션별 목록 페이지

#### `_pages/projects-archive.md`
```markdown
---
title: "프로젝트 포트폴리오"
permalink: /projects/
layout: collection
collection: projects
entries_layout: grid
classes: wide
sort_by: date
sort_order: reverse
author_profile: true
header:
  overlay_color: "#5e616c"
  overlay_image: /assets/images/projects-banner.jpg
---

개발한 프로젝트들을 소개합니다. 각 프로젝트를 클릭하면 상세 정보를 확인할 수 있습니다.

## 🔍 카테고리별 보기

- [웹 개발](#web-development)
- [모바일 앱](#mobile-app)  
- [데이터 분석](#data-analysis)
- [오픈소스](#open-source)
```

#### `_pages/tutorials-archive.md`
```markdown
---
title: "튜토리얼"
permalink: /tutorials/
layout: collection
collection: tutorials
entries_layout: list
author_profile: true
sidebar:
  nav: "tutorials"
---

단계별 학습 가이드를 제공합니다.

## 📚 난이도별 가이드

### 초급
기본 개념부터 차근차근 배워봅시다.

### 중급  
실무에서 필요한 핵심 기술들을 익혀봅시다.

### 고급
심화 내용과 최적화 기법을 다룹니다.
```

### 3. 사이드바 네비게이션 설정

`_data/navigation.yml`에 추가:

```yaml
# 메인 네비게이션 (기존)
main:
  - title: "Home"
    url: /
  - title: "Blog"
    url: /posts/
  - title: "Projects"
    url: /projects/
  - title: "Tutorials"
    url: /tutorials/
  - title: "Reviews"
    url: /reviews/
  - title: "About"
    url: /about/

# 튜토리얼 사이드바
tutorials:
  - title: "Backend"
    children:
      - title: "Java 기초"
        url: /tutorials/#java-basics
      - title: "Spring Boot"
        url: /tutorials/#spring-boot
      - title: "데이터베이스"
        url: /tutorials/#database
  - title: "Frontend"
    children:
      - title: "HTML/CSS"
        url: /tutorials/#html-css
      - title: "JavaScript"
        url: /tutorials/#javascript
      - title: "React"
        url: /tutorials/#react

# 프로젝트 사이드바
projects:
  - title: "카테고리"
    children:
      - title: "웹 개발"
        url: /projects/#web-development
      - title: "모바일 앱"
        url: /projects/#mobile-app
      - title: "데이터 분석"
        url: /projects/#data-analysis
```

### 4. 컬렉션 간 연관 관계 설정

포스트에서 관련 프로젝트나 튜토리얼을 참조할 수 있습니다:

```markdown
---
title: "Spring Boot 실전 가이드"
categories:
  - Backend
tags:
  - Spring Boot
  - Java
related_projects:
  - spring-boot-ecommerce
  - spring-boot-blog
related_tutorials:
  - spring-boot-basics
  - jpa-tutorial
---

이 포스트에서는 실제 프로젝트 경험을 바탕으로...

## 관련 자료

{% assign related_project = site.projects | where: "slug", "spring-boot-ecommerce" | first %}
{% if related_project %}
📁 **관련 프로젝트**: [{{ related_project.title }}]({{ related_project.url }})
{% endif %}

{% assign related_tutorial = site.tutorials | where: "slug", "spring-boot-basics" | first %}
{% if related_tutorial %}
📖 **관련 튜토리얼**: [{{ related_tutorial.title }}]({{ related_tutorial.url }})
{% endif %}
```

## 컬렉션별 RSS 피드 생성

각 컬렉션마다 별도의 RSS 피드를 만들 수 있습니다:

### `feed-projects.xml`
```xml
---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0">
  <channel>
    <title>{{ site.title | escape }} - Projects</title>
    <description>{{ site.description | escape }}</description>
    <link>{{ site.url }}{{ site.baseurl }}/</link>
    {% for project in site.projects limit:10 %}
      <item>
        <title>{{ project.title | escape }}</title>
        <description>{{ project.excerpt | escape }}</description>
        <pubDate>{{ project.date | date_to_rfc822 }}</pubDate>
        <link>{{ site.url }}{{ site.baseurl }}{{ project.url }}</link>
        <guid isPermaLink="true">{{ site.url }}{{ site.baseurl }}{{ project.url }}</guid>
      </item>
    {% endfor %}
  </channel>
</rss>
```

## 컬렉션 관리 팁

### 1. 일관된 Front Matter 사용
각 컬렉션마다 표준 Front Matter 템플릿을 만들어 사용하세요.

### 2. 파일명 규칙
```
_projects/YYYY-MM-DD-project-name.md
_tutorials/YYYY-MM-DD-tutorial-name.md
_reviews/YYYY-MM-DD-review-name.md
```

### 3. 태그와 카테고리 활용
컬렉션별로 고유한 태그/카테고리 체계를 만들어 분류하세요.

### 4. 크로스 링크
서로 다른 컬렉션 간에 연관된 콘텐츠를 링크로 연결하세요.

## 결론

Jekyll의 컬렉션 기능을 활용하면 단순한 블로그를 넘어서 다양한 형태의 콘텐츠를 체계적으로 관리할 수 있는 전문적인 웹사이트를 만들 수 있습니다. 

프로젝트 포트폴리오, 학습 자료, 리뷰 등 각각의 성격에 맞는 게시판을 분리함으로써 방문자들이 원하는 정보를 더 쉽게 찾을 수 있고, 콘텐츠 관리도 훨씬 수월해집니다.

처음에는 설정이 복잡해 보일 수 있지만, 한 번 구축해 놓으면 장기적으로 매우 유용한 구조가 될 것입니다!