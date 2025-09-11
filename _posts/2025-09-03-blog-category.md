---
layout: single
title: "[jekyll] minimal-mistakes 테마의 디렉터리 구조 공부"
categories: jekyll
tag: [jekyll, minimal-mistakes, blog]
toc: true
excerpt: "minimal-mistakes 테마의 디렉터리를 구조 공부해보자"
---


블로그를 만들고 나면 방대한 파일들을 보고 놀라 막막해질 것이다.(경험담)<br>
그래서 minimal-mistakes 테마의 디렉터리를 구조를 공부해보려고 한다.

주로 minimal-mistakes 테마의 홈페이지를 참고했다.<br>
(2025.09.11 기준)
https://mmistakes.github.io/minimal-mistakes/docs/

## minimal-mistakes의 전체적인 디렉터리

테마를 설치하고 나면 기본적으로 들어있는 파일들은 다음과 같다.

~~~
minimal-mistakes
├── 📁_data                      # 사이트에서 반복적으로 쓰이는 데이터 관리
├── 📁_includes                  # 재사용이 잦은 HTML 파일들, Liquid 태그를 사용
├── 📁_layouts                   # 페이지 레이아웃 정의
├── 📁_sass                      # SCSS(Sass) 파일들, 테마 커스터마이징할 때 사용
├── 📁.github                    # GitHub Actions 등 CI/CD 워크플로우 설정 저장
├── 📁assets                     # 이미지, JS, CSS 등의 정적 리소스 저장
├── 📁docs                       # GitHub Pages 배포용 문서 루트
├── 📁test                       # 테스트 코드나 샘플 데이터 저장 (삭제해도 OK)
├── 📝_config.yml                # Jekyll 메인 설정 파일
├── ⚙️Gemfile                    # Ruby Gem 의존성 관리 파일
├── 📝index.html                 # 사이트 메인 페이지 설정
├── 📝package-lock.json          # Node.js 패키지 의존성 버전 잠금
├── 📝package.json               # Node.js 의존성 및 스크립트 정의
├── 📝README.md                  # 프로젝트 설명 문서 (GitHub 저장소 메인에 표시됨)
└── 📝staticman.yml              # Staticman 댓글 시스템 설정 파일
~~~

자주 사용해서 익숙한 폴더나 파일도 있지만, 낯선 파일들도 있을 것이다.<br>
이제 하나하나 살펴보자!


### 📁_data
**[✅]** 사이트에서 공통적으로 쓰이는 데이터를 모아두는 곳<br>
{: .notice}
~~~
📁_data
├── 📝navigation.yml
└── 📝ui-text.yml
~~~
YAML, JSON, CSV 파일을 넣어서 Liquid 태그를 사용해 변수처럼 사용할 수도 있다.

#### 📝navigation.yml
**[✅]** 블로그의 상단 메뉴 또는 카테고리 등에 대한 설정<br>
{: .notice}

기본적으로 블로그의 상단 메뉴바 설정이 들어있다.
~~~
# main links
main:
  - title: "Quick-Start Guide"
    url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
  # - title: "About"
  #   url: https://mmistakes.github.io/minimal-mistakes/about/
  # - title: "Sample Posts"
  #   url: /year-archive/
  # - title: "Sample Collections"
  #   url: /collection-archive/
  # - title: "Sitemap"
  #   url: /sitemap/
~~~

이후에 파일을 수정해서 상단 메뉴바를 수정하거나, 사이드 카테고리 등을 추가할 수 있는 파일이다.

#### 📝ui-text.yml
**[✅]** UI에 쓰이는 텍스트(ex. 다음 글, 이전 글 등)에 대한 파일<br>
{: .notice}

~~~
# User interface text and labels

# English (default)
# -----------------
en: &DEFAULT_EN
  skip_links                 : "Skip links"
  skip_primary_nav           : "Skip to primary navigation"
  skip_content               : "Skip to content"
  skip_footer                : "Skip to footer"
  page                       : "Page"
  ...
~~~

영어가 기본으로 설정되어 있고, Spanish, French, Turkish, Portuguese 등 다양한 언어들로 설정되어 있다.

한국어도 있으니 UI의 텍스트가 맘에 안든다면 여기서 Korean을 찾아 수정하면 된다.

### 📁_includes 
**[✅]** Jekyll 테마에서 핵심적인 구성요소 파일들이 모여있는 폴더<br>
{: .notice}

재사용 가능한 HTML 조각들이 모여 있는 폴더이다.
head, footer, category-list 등 많은 파일들이 모여있다!

~~~
📁_includes
├── 📁analytics-providers               # 다양한 웹 분석 도구(Google, Plausible 등) 설정 파일 모음
├── 📁comments-providers                # 댓글 시스템(Giscus, Disqus 등) 설정 파일 모음
├── 📁footer                            # 푸터 관련 구성 요소들
├── 📁head                              # <head> 태그 안에 들어갈 요소들 (메타 태그, 스타일 등)
├── 📁search                            # 검색 기능 관련 파일들 (Lunr.js 등)
├── 📝 after-content.html               # 본문 콘텐츠 아래에 삽입되는 콘텐츠 (예: 관련 글)
├── 📝 analytics.html                   # 웹사이트 분석 스크립트를 삽입하는 파일
├── 📝 archive-single.html              # 아카이브(목록) 페이지의 단일 포스트 표시용 템플릿
├── 📝 author-profile-custom-links.html # 저자 프로필에 커스텀 링크 추가
├── 📝 author-profile.html              # 저자 이름, 이미지, 바이오 등을 보여주는 컴포넌트
├── 📝 before-related.html              # 관련 글 섹션 위에 표시되는 콘텐츠
├── 📝 breadcrumbs.html                 # 현재 위치 경로를 보여주는 네비게이션 (bread crumbs)
├── 📝 category-list.html               # 카테고리 목록을 출력하는 컴포넌트
├── 📝 comment.html                     # 단일 댓글 항목 렌더링용 (구 버전 호환)
├── 📝 comments.html                    # 전체 댓글 영역 렌더링용
├── 📝 copyright.html                   # 저작권 정보 표시 (푸터에 사용됨)
├── 📝 copyright.js                     # 저작권 관련 JavaScript 처리
├── 📝 documents-collection.html        # 문서 유형 포스트 리스트 렌더링용
├── 📝 feature_row                      # 특화된 콘텐츠 행(그리드) 표시 (예: 홈페이지 섹션)
├── 📝 figure                           # 이미지/캡션 등 figure 처리용 include
├── 📝 footer.html                      # 사이트 푸터 전체 구조
├── 📝 gallery                          # 이미지 갤러리 컴포넌트
├── 📝 group-by-array                   # 배열 기반 데이터 그룹핑 처리용 include
├── 📝 head.html                        # <head> 영역 공통 처리 (SEO, 스타일 등)
├── 📝 masthead.html                    # 상단 네비게이션 및 로고 영역
├── 📝 nav_list                         # 네비게이션 리스트 렌더링용
├── 📝 page_date.html                   # 포스트 날짜 출력용
├── 📝 page_hero_video.html             # 비디오 배경 Hero 섹션 구성용
├── 📝 page_hero.html                   # 일반 Hero 섹션 (이미지, 텍스트 포함)
├── 📝 page_meta.html                   # 작성자, 날짜, 태그 등의 메타 정보 표시
├── 📝 page_related.html                # 관련 글 추천 영역 표시
├── 📝 page_taxonomy.html               # 태그 및 카테고리 등 분류 정보 표시
├── 📝 paginator-v1.html                # 기본 스타일 페이지네이션 (버전 1)
├── 📝 paginator-v2.html                # 대체 스타일 페이지네이션 (버전 2)
├── 📝 paginator.html                   # 공통 페이지네이션 처리
├── 📝 post_taxonomy.html               # 포스트의 태그/카테고리 표시용
├── 📝 post_pagination.html             # 이전/다음 포스트 네비게이션
├── 📝 posts-category.html              # 특정 카테고리의 포스트 목록 출력
├── 📝 posts-tag.html                   # 특정 태그의 포스트 목록 출력
├── 📝 posts-taxonomy.html              # 태그/카테고리별 포스트 리스트 구성용
├── 📝 schema.html                      # 구조화된 데이터 마크업 (JSON-LD)
├── 📝 scripts.html                     # 하단 스크립트 삽입 (JS 파일 등)
├── 📝 seo.html                         # SEO 관련 메타 태그 삽입
├── 📝 sidebar.html                     # 사이드바 구성 요소
├── 📝 skip-links.html                  # 키보드 접근성을 위한 '건너뛰기 링크'
├── 📝 social-share.html                # 소셜 공유 버튼 (트위터, 페이스북 등)
├── 📝 tag-list.html                    # 태그 리스트 출력 컴포넌트
├── 📝 toc                              # 목차(T.O.C) 관련 include (스크립트 or 구조)
├── 📝 toc.html                         # 본문 내 목차 표시용
└── 📝 video                            # 비디오 embed 처리용 include
~~~

#### 📁 analytics-providers
**[✅]** 웹 분석 도구(Google Analytics 등)에 대한 설정<br>
{: .notice}
~~~
📁analytics-providers                    
├── 📝 google.html                     # Google Analytics 기본 설정 파일
├── 📝 google-gtag.html                # 최신 Google Analytics를 위한 파일
├── 📝 google-universal.html          # 구버전 Google Universal Analytics 지원하는 파일
└── 📝 custom.html                     # Google 이외의 분석 도구를 직접 추가할때 사용
~~~

기본적으로 Google Analytics가 설정되어 있으며, 다양한 버전을 고려한 파일들이 들어있다.<br>
📝 custom.html에는 네이버 애널리틱스, 카카오 애널리틱스등의 분석 도구를 직접 설정해 사용할 수 있다.

#### 📁 comments-providers
**[✅]** 댓글 시스템(Giscus, Disqus 등) 설정<br>
{: .notice}
~~~
📁comments-providers
├── 📝 custom_scripts.html             # 사용자 정의 댓글 시스템 스크립트 삽입용
├── 📝 custom.html                     # 사용자 정의 댓글 시스템
├── 📝 discourse.html                  # Discourse 기반 댓글 시스템
├── 📝 disqus.html                     # Disqus 댓글 시스템
├── 📝 facebook.html                   # Facebook 댓글 시스템
├── 📝 giscus.html                     # Giscus 댓글 시스템
├── 📝 scripts.html                    # 댓글 시스템 관련 공통 스크립트
├── 📝 staticman_v2.html               # Staticman v2 기반 댓글 시스템
├── 📝 staticman.html                  # Staticman 기본 버전용 댓글 시스템
└── 📝 utterances.html                 # Utterances 댓글 시스템
~~~
댓글 시스템을 위한 파일들이 모여있는 곳이다.<br>
직접 커스텀해서 사용하는 것은 기본으로 가능하고, discourse, disqus, facebook, giscus(GitHub Discussions 기반), staticman, utterances(GitHub Issues 기반) 의 댓글 시스템에 대한 파일이 기본적으로 담겨 있다.

#### 📁 footer
**[✅]** 사이트의 하단 구조 설정<br>
{: .notice}
~~~
📁footer
└── 📝custom.html
~~~
사이트 하단에 원하는 내용을 직접 삽입할 수 있는 곳이다.<br>
안에는 아무런 내용이 없으며 파일을 직접 수정해서 사용한다.<br>
예: 카피라이트 문구, 추가 링크, 회사 주소, 저작권 배너 등<br>

#### 📁 head
**[✅]** HTML문서의 <head> 구성 설정<br>
{: .notice}
~~~
📁head
└── 📝custom.html
~~~
사이트의 <head> 태그 안에 사용자 정의 코드를 삽입할 수 있는 곳이다.<br>
footer와 마찬가지로 직접 커스텀해서 사용할 수 있다.<br>
예: 커스텀 폰트, 파비콘, SEO 메타 태그, 외부 스크립트 삽입 등<br>
Google Search Console 인증, Facebook meta 등 외부 서비스용 태그도 여기에 넣을 수 있다.<br>


#### 📁 search
**[✅]** 검색 기능 관련 스크립트 및 UI 구성<br>
{: .notice}
~~~
📁search
├── 📝 algolia-search-scripts.html    # Algolia 검색 엔진 설정
├── 📝 google-search-scripts.html     # Google 검색 엔진 설정
├── 📝 lunar-search-scripts.html      # Lunr.js 기반 클라이언트 검색 엔진 설정
└── 📝 search_form.html               # 검색 입력창(form) UI 렌더링용 파일
~~~
검색 기능 관련한 파일들이 있는 곳이다.<br>
Minimal Mistakes 테마는 기본적으로 클라이언트 사이드 검색(Lunr.js 사용)을한다.<br>
Algolia, Google CSE로 바꾸어 설정할 수 있도록 되어 있다.<br>

**~추후 추가 예정~**