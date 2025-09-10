---
layout: single
title: "[Git] 깃헙 블로그 실시간 업데이트 확인"
categories: Git
tag: [minimal-mistakes, blog, Git]
toc: true
excerpt: "깃허브 블로그 업데이트 시 실시간으로 확인하기 위한 설정"
---

블로그 글을 작성하고, 저장, 커밋, 푸시를 하고 나면 실제로 페이지에 반영되기까지 시간이 꽤 걸려서 답답했다. <br>
그래서 실시간으로 수정한 부분을 확인할 방법이 없나 찾아보다 알게된 정보를 정리해보려 한다.<br>


* * *


먼저 minimal-mistakes 테마의 경우 jekyllrb를 사용했기 때문에, [https://jekyllrb.com/docs/](https://jekyllrb.com/docs/) 사이트에서 Quickstart를 확인한다.

![2025-08-31-210054]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-210054.png)

- Ruby v2.7.0 버전 이상
- RubyGems
- GCC and Make

이렇게 세가지가 필요하다고 되어있다. 


* * *

## 1. Ruby(루비) 설치

[https://www.ruby-lang.org/ko/documentation/installation/](https://www.ruby-lang.org/ko/documentation/installation/)

루비 홈페이지에 접속해 루비를 다운로드 하고 설치한다.<br>

![2025-08-31-210957]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-210957.png)

나는 윈도우를 이용중이고, 인스톨러가 편하기 때문에 아래로 쭉 내리면 있는 인스톨러로 설치하려고 한다.<br>

![2025-08-31-211210]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-211210.png)


Installer를 누르면 해당 페이지로 이동하는데 다운로드를 누른 뒤<br>

![2025-08-31-211255]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-211255.png)


WITH DEVKIT 목록에 있는 파일 중 하나를 받아 설치하면 된다.<br>
나는 `Ruby+Devkit 3.4.5-1 (x64)`를 설치했다.<br>
설치가 끝나고 Finish를 누르면 아래와 같은 창이 뜬다.<br>

![2025-08-31-211435]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-211435.png)

1에서 3번 중 선택하라고 하는데, 3번을 선택하면 된다.<br>
그러면 Ruby 설치는 끝난다.<br>

* * *

## 2. jekyll 설치

![2025-08-31-211812]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-211812.png)

그 뒤 화면으로 돌아가 `Window + R` 을 누르고 `cmd`를 입력한 뒤 확인을 누른다.<br><br>
MAC OS의 경우 터미널 스포트라이트에 terminal을 입력하면 된다.<br>

![2025-08-31-212318]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-212318.png)

터미널 창이 뜨면 `gem install jekyll`를 입력해 설치한다.<br>

## 3. bundler 설치

jekyll 설치가 끝나면 bundler을 설치해야한다.<br>
방금과 똑같이 터미널에서 `gem install bundler`를 입력해 설치한다.<br>

## 4. 플러그인 설치

[https://mmistakes.github.io/minimal-mistakes/docs/installation/](https://mmistakes.github.io/minimal-mistakes/docs/installation/)<br>
minimal-mistakes의 installation 페이지를 보면 플러그인 설치가 필요하다.<br>

먼저 내 깃헙 블로그 파일들이 있는 경로로 이동한다.<br>
가장 쉬운 방법은 파일 탐색기에서 폴더로 이동한 뒤, 우측 마우스->터미널에서 열기를 누르면 된다.<br>

![2025-08-31-213422]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-213422.png)

루트 파일들이 있는 폴더에서 열어줘야 cd를 입력해서 이동할 필요가 없다.<br>

그리고 `bundle install`를 입력해서 설치한다.<br>

## 5. 터미널에서 실행

아까와 같은 github.io 폴더(루트 파일들이 있는 곳)에서 `bundle exec jekyll serve`를 입력하면 서버가 구동된다.<br>

![2025-08-31-214409]({{site.url}}/images/2025-08-31-blog-realtime/2025-08-31-214409.png)

잘 실행됐다면 사진과 같이 안내가 나온다.<br>
이제 `http://127.0.0.1:4000/`에 접속하면 내 블로그 페이지가 나오는데 <br>
VScode에서 수정한 뒤 `Ctrl + S`만 하면 수정된 게시글을 확인할 수 있다!<br>

단, _config.yml 파일을 수정했을 때는 서버를 껐다 켜야한다.<br>

종료는 사진에 나와있듯이 `Ctrl + C`를 누르면 가능하다.<br>

혹시 `cannot load such file -- webrick (LoadError)` 에러가 뜬다면<br>
`bundle add webrick`을 입력해 설치한 뒤 다시 실행해보자.<br>

## 마무리
이제 게시글 수정사항을 실시간으로 확인할 수 있다!<br>
하지만 최종적으로 내 블로그에 반영되는 것은 아니니, 원하는만큼 수정이 끝나면 꼭 커밋 푸시를 하자.<br>

## 참고 사이트
🔗[Minimal Mistakes Installation](https://mmistakes.github.io/minimal-mistakes/docs/installation/)<br>
🔗[jekyllrb Quickstart](https://jekyllrb.com/docs/)<br>
🔗[EP03. 업데이트 내역을 실시간 확인하기!! (로컬 개발환경 설정방법)](https://youtu.be/0TeHUqSAb6Q/)<br>