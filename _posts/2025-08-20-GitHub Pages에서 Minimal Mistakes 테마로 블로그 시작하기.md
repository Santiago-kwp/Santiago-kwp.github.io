# GitHub Pages에서 Minimal Mistakes 테마로 블로그 시작하기: 디렉토리 구조 완벽 가이드

GitHub Pages와 Jekyll을 이용해 블로그를 만들 때 가장 인기 있는 테마 중 하나인 **Minimal Mistakes**를 처음 설정하는 것은 다소 복잡할 수 있습니다. 이번 포스트에서는 Minimal Mistakes 테마의 디렉토리 구조를 자세히 알아보고, 블로그를 성공적으로 시작하는 방법을 단계별로 설명하겠습니다.

## Minimal Mistakes 테마란?

[Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes)는 Michael Rose가 개발한 Jekyll 테마로, 깔끔하고 반응형 디자인을 제공하며 다양한 커스터마이징 옵션을 지원합니다. GitHub Pages에서 공식적으로 지원되는 테마는 아니지만, 많은 개발자들이 선호하는 테마입니다.

### 주요 특징
- 반응형 디자인 (모바일, 태블릿, 데스크톱 지원)
- SEO 최적화
- 다양한 레이아웃 옵션
- 소셜 미디어 통합
- 댓글 시스템 지원
- 검색 기능

## 설치 방법 선택

Minimal Mistakes 테마를 설치하는 방법은 여러 가지가 있습니다:

### 1. Fork 방식 (초보자 추천)
- 테마 저장소를 그대로 복사하는 방법
- 가장 간단하지만 업데이트가 어려움

### 2. Gem 방식
- Ruby Gem으로 설치하는 방법
- 로컬 개발 환경이 필요

### 3. Remote Theme 방식 (GitHub Pages 추천)
- `_config.yml`에서 원격 테마로 설정
- GitHub Pages에서 직접 지원

이 포스트에서는 **Remote Theme 방식**을 중심으로 설명하겠습니다.

## 기본 디렉토리 구조

Minimal Mistakes 테마를 적용한 블로그의 기본 디렉토리 구조는 다음과 같습니다:

```
your-blog/
├── _config.yml              # Jekyll 설정 파일 (가장 중요!)
├── _data/                   # 데이터 파일들
│   ├── navigation.yml       # 네비게이션 메뉴 설정
│   └── ui-text.yml         # 다국어 지원 텍스트
├── _includes/              # 재사용 가능한 HTML 조각들
│   └── custom.html         # 커스텀 HTML 추가용
├── _layouts/               # 페이지 레이아웃 템플릿
├── _pages/                 # 정적 페이지들
│   ├── about.md            # About 페이지
│   ├── archive.md          # 아카이브 페이지
│   └── tags.md             # 태그 페이지
├── _posts/                 # 블로그 포스트들
│   └── 2024-01-01-hello-world.md
├── _sass/                  # SCSS 스타일 파일들
│   └── minimal-mistakes/   # 테마 스타일
├── assets/                 # 정적 자원들
│   ├── css/
│   │   └── main.scss       # 메인 스타일 파일
│   ├── images/             # 이미지 파일들
│   └── js/                 # JavaScript 파일들
├── .gitignore              # Git 무시 파일 목록
├── Gemfile                 # Ruby 의존성 (로컬 개발용)
├── index.html              # 홈페이지
└── README.md               # 프로젝트 설명
```

## 핵심 파일별 상세 설명

### 1. `_config.yml` - 블로그의 심장 💜

이 파일은 Jekyll 사이트의 전체 설정을 담당하는 가장 중요한 파일입니다.

```yaml
# 테마 설정 (Remote Theme 방식)
remote_theme: "mmistakes/minimal-mistakes@4.24.0"

# 사이트 기본 정보
title: "내 블로그 제목"
subtitle: "블로그 부제목"
name: "작성자 이름"
description: "블로그에 대한 간단한 설명"
url: "https://username.github.io"
baseurl: ""
repository: "username/username.github.io"

# 작성자 정보
author:
  name: "홍길동"
  avatar: "/assets/images/profile.jpg"
  bio: "개발자입니다."
  location: "Seoul, Korea"
  links:
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/username"
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:email@example.com"

# 빌드 설정
markdown: kramdown
highlighter: rouge
lsi: false
excerpt_separator: "\n\n"
incremental: false

# 플러그인
plugins:
  - jekyll-paginate
  - jekyll-sitemap
  - jekyll-gist
  - jekyll-feed
  - jekyll-include-cache

# 페이지네이션
paginate: 5
paginate_path: /page:num/

# SEO 설정
locale: "ko-KR"
timezone: "Asia/Seoul"

# 댓글 설정 (선택사항)
comments:
  provider: "disqus"
  disqus:
    shortname: "your-disqus-shortname"

# 검색 설정
search: true
search_full_content: false

# 기본 설정
defaults:
  # _posts
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
  # _pages
  - scope:
      path: "_pages"
      type: pages
    values:
      layout: single
      author_profile: true
```

### 2. `_data/navigation.yml` - 네비게이션 메뉴

블로그의 상단 메뉴를 설정합니다.

```yaml
main:
  - title: "Home"
    url: /
  - title: "About"
    url: /about/
  - title: "Posts"
    url: /posts/
  - title: "Categories"
    url: /categories/
  - title: "Tags"
    url: /tags/
  - title: "Archive"
    url: /year-archive/
```

### 3. `_pages/` 디렉토리 - 정적 페이지들

#### `_pages/about.md`
```markdown
---
permalink: /about/
title: "About"
layout: single
author_profile: true
---

여기에 자기소개를 작성하세요.
```

#### `_pages/archive.md`
```markdown
---
title: "Posts by Year"
permalink: /year-archive/
layout: posts
author_profile: true
---
```

#### `_pages/categories.md`
```markdown
---
title: "Posts by Category"
layout: categories
permalink: /categories/
author_profile: true
---
```

#### `_pages/tags.md`
```markdown
---
title: "Posts by Tag"
permalink: /tags/
layout: tags
author_profile: true
---
```

### 4. `_posts/` 디렉토리 - 블로그 포스트

포스트 파일명은 `YYYY-MM-DD-제목.md` 형식을 따라야 합니다.

#### 예시: `_posts/2024-01-01-my-first-post.md`
```markdown
---
title: "첫 번째 포스트"
date: 2024-01-01
categories:
  - Blog
tags:
  - Jekyll
  - GitHub Pages
toc: true
toc_sticky: true
---

여기에 포스트 내용을 작성합니다.

## 소제목

내용...
```

### 5. `assets/` 디렉토리 - 정적 자원

```
assets/
├── css/
│   └── main.scss           # 메인 스타일시트
├── images/                 # 이미지 파일들
│   ├── profile.jpg         # 프로필 이미지
│   └── posts/              # 포스트용 이미지들
└── js/                     # JavaScript 파일들 (필요시)
```

#### `assets/css/main.scss`
```scss
---
# Only the main Sass file needs front matter (the dashes are enough)
---

@charset "utf-8";

// 커스텀 스타일을 여기에 추가
@import "minimal-mistakes/skins/{{ site.minimal_mistakes_skin | default: 'default' }}"; // skin
@import "minimal-mistakes"; // main partials

// 커스텀 CSS
.custom-class {
  // 스타일 정의
}
```

### 6. `index.html` - 홈페이지

```html
---
layout: home
author_profile: true
---
```

## 필수 초기 설정 단계

### 1단계: 저장소 생성
1. GitHub에서 `username.github.io` 이름으로 저장소 생성
2. 로컬에 클론 또는 GitHub에서 직접 파일 생성

### 2단계: 기본 파일 생성
1. `_config.yml` 파일 생성 및 설정
2. `Gemfile` 생성 (로컬 개발용)
3. `index.html` 생성

### 3단계: 디렉토리 구조 생성
```bash
mkdir -p _pages _posts _data assets/images assets/css
```

### 4단계: 기본 페이지 생성
- `_pages/about.md`
- `_pages/archive.md`
- `_data/navigation.yml`

### 5단계: 첫 포스트 작성
- `_posts/2024-01-01-hello-world.md`

## 로컬 개발 환경 설정 (선택사항)

로컬에서 블로그를 미리 확인하고 싶다면:

### `Gemfile` 생성
```ruby
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins
gem "jekyll-include-cache", group: :jekyll_plugins
```

### 로컬 실행
```bash
bundle install
bundle exec jekyll serve
```

브라우저에서 `http://localhost:4000`으로 접속하여 확인할 수 있습니다.

## 커스터마이징 팁

### 1. 테마 스킨 변경
`_config.yml`에서 스킨을 변경할 수 있습니다:

```yaml
minimal_mistakes_skin: "dark" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"
```

### 2. 커스텀 CSS 추가
`_sass/minimal-mistakes/_custom.scss` 파일을 생성하여 커스텀 스타일을 추가할 수 있습니다.

### 3. 구글 애널리틱스 설정
```yaml
# _config.yml
analytics:
  provider: "google-gtag"
  google:
    tracking_id: "G-XXXXXXXXXX"
    anonymize_ip: false
```

### 4. 폰트 변경
```scss
// assets/css/main.scss
$serif: "Noto Serif KR", serif;
$sans-serif: "Noto Sans KR", sans-serif;
$monospace: "D2Coding", Monaco, Consolas, monospace;
```

## 자주 하는 실수와 해결법

### 1. 테마가 적용되지 않는 경우
- `_config.yml`에서 `remote_theme` 설정 확인
- GitHub Pages 빌드 로그 확인
- 플러그인 설정 확인

### 2. 이미지가 표시되지 않는 경우
- 이미지 경로 확인 (`/assets/images/filename.jpg`)
- 파일명 대소문자 구분 확인
- 이미지 파일이 실제로 업로드되었는지 확인

### 3. 메뉴가 표시되지 않는 경우
- `_data/navigation.yml` 파일 존재 확인
- YAML 문법 오류 확인
- 들여쓰기 확인

## 다음 단계

기본 구조를 설정했다면 다음 단계로 넘어갈 수 있습니다:

1. **콘텐츠 작성**: 정기적인 포스팅 시작
2. **SEO 최적화**: 메타 태그, 구조화된 데이터 추가
3. **성능 최적화**: 이미지 압축, CDN 활용
4. **기능 추가**: 댓글, 검색, 소셜 공유 등
5. **분석 설정**: Google Analytics, Search Console 연동

## 결론

Minimal Mistakes 테마의 디렉토리 구조는 처음에는 복잡해 보일 수 있지만, 각 파일과 폴더의 역할을 이해하면 매우 체계적이고 유지보수하기 쉬운 구조임을 알 수 있습니다. 

가장 중요한 것은 `_config.yml` 파일을 올바르게 설정하는 것이며, 나머지는 필요에 따라 점진적으로 추가하고 커스터마이징하면 됩니다. 

이 가이드를 따라하시면 멋진 블로그를 성공적으로 시작할 수 있을 것입니다! 궁금한 점이 있으시면 언제든지 질문해 주세요.

---

## 참고 자료

- [Minimal Mistakes 공식 문서](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
- [Jekyll 공식 문서](https://jekyllrb.com/docs/)
- [GitHub Pages 문서](https://docs.github.com/en/pages)