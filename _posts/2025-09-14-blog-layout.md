---
layout: single
title: "[jekyll] minimal-mistakes 게시글 영역 설정"
categories: jekyll
tag: [jekyll, minimal-mistakes, blog]
toc: false

---

게시글의 영역이 너무 좁아서 글이 조금만 길어지면 스크롤이 길어져 보기 불편했다.<br>
그래서 게시글 영역을 늘려보려고 한다.


## _page.scss
이전의 블로그 카테고리 게시글을 참고 삼아 찾아보니, 페이지 설정에 대한 부분은 _page.scss에 있었다.

**[📂]** _sass / minimal-mistakes / _page.scss
{: .notice--info}

#main부분을 살펴보면 다음과 같다.

~~~scss
#main {
  @include clearfix;
  margin-inline: auto;
  padding-inline: 1em;
  -webkit-animation: $intro-transition;
  animation: $intro-transition;
  max-width: 100%;
  -webkit-animation-delay: 0.15s;
  animation-delay: 0.15s;

  @include breakpoint($x-large) {
    max-width: $max-width;
  }
}
~~~
코드를 살펴보면 기본적으로는 `max-width: 100%`로 부모요소의 100%보다 넓어지지 않게 제한되어 있었고

`$x-large` 사이즈(고정된 최대 넓이 값)보다 사이즈가 커질 경우, `$max-width` 이상으로 넓어지지 않도록 되어 있다.

그러므로 우리는 `$x-large`가 어디에 정의되어 있는지 찾아보면 될 것 같다.


## _variables.scss
`$x-large`에 대한 설정은 `_variables.scss` 파일에 있었다.

**[📂]** _sass / minimal-mistakes / _variables.scss
{: .notice--info}

파일의 Breakpoints 부분을 보면 다음과 같이 설정되어 있다.

~~~scss
/*
   Breakpoints
   ========================================================================== */

$small: 600px !default;
$medium: 768px !default;
$medium-wide: 900px !default;
$large: 1024px !default;
$x-large: 1280px !default;
$max-width: $x-large !default;
~~~

그러면 최소 게시글 영역부터 최대까지 설정되어 있는것을 볼 수 있다.<br>
나는 최대 영역을 수정하고 싶으니, x-large영역만 수정했다.

~~~scss
$x-large: 1600px !default;
$max-width: $x-large !default;
~~~

그러면 아래와 같이 영역이 늘어난다.

![2025-09-14-052032]({{site.url}}/images/2025-09-14-blog-layout/2025-09-14-052032.png){: .align-center}{:style="border:1px"}

![2025-09-14-052203]({{site.url}}/images/2025-09-14-blog-layout/2025-09-14-052203.png){: .align-center}{:style="border:1px"}


늘어난 것이 확연히 보인다!

## 마무리
아무래도 블로그의 가독성을 위해서는 꼭 필요한 설정이라고 생각한다.<br>
이외에도 가독성을 높이기 위해 좀더 공부해봐야겠다!