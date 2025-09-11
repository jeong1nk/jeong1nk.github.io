---
layout: single
title: "[jekyll] minimal-mistakes 테마의 디렉터리 구조 공부"
categories: jekyll
tag: [jekyll, minimal-mistakes, blog]
toc: false
excerpt: "minimal-mistakes 테마의 디렉터리를 구조 공부해보자"
---

블로그를 만들고 나면 방대한 파일들을 보고 놀라 막막해질 것이다.(경험담)

그래서 minimal-mistakes 테마의 디렉터리를 구조를 공부해보려고 한다.
(2025.09.11 기준)



## minimal-mistakes의 전체적인 디렉터리

~~~

minimal-mistakes
├── 📁_data                      # data files for customizing the theme
├── 📁_includes                  #
├── 📁_layouts                   #
├── 📁_sass                      # SCSS partials
├── 📁.github                    #
├── 📁assets                     #
├── 📁docs                       #
├── 📁test                       #
├── 📝_config.yml                # site configuration
├── 📝Gemfile                    # gem file dependencies
├── 📝index.html                 # paginated home page showing recent posts
├── 📝package-lock.json          #
├── 📝package.json               # NPM build scripts
├── 📝README.md                  #
└── 📝staticman.yml              #
~~~