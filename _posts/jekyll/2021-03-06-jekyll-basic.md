---
layout: post
current: post
cover:  assets/built/images/jekyll-logo.png
navigation: True
title: Jekyll - 나의 블로그를 만들어보자
date: 2020-03-07 20:20:00
tags: [jekyll]
class: post-template
subclass: 'post tag-python'
author: Hono
---
<i class="fa fa-list-alt"></i> **Jekyll**과 **Github**를 이용해서 자신만의 블로그를 만들어보자.

<i class="fa fa-cog"></i>  우선 개발환경으로는 **Ruby**를 사용할 것이고 에디터는  Window 10으로 작업

네이버 블로그나 다음의 티스토리 같은 블로그를 사용하지 않는 이유는 버튼 몇 개만 누르면 바로바로 완성된 블로그를 만들어 주겠지만 커스텀마이징이 많이 제한된다는 점과 코드들을 올렸을 때 가독성이 떨어지기 때문이다.   
(그리고... 나름 개발자를 꿈꾸는데 블로그 하나 정도는 만들어야 하지 않겠나,,,? 하하...)

<img src="https://user-images.githubusercontent.com/79001968/110789186-ee602500-82b2-11eb-9385-79101cfb964a.png" alt="jekyll-logo" style="zoom: 50%;" />



<img src="https://user-images.githubusercontent.com/79001968/110790844-de494500-82b4-11eb-9504-10493a923fe1.png" alt="GitHub-logo" style="zoom: 50%;" />



<img src="https://user-images.githubusercontent.com/79001968/110790606-94605f00-82b4-11eb-9aa0-7263869deb16.png" alt="Ruby logo" style="zoom: 80%;" />

<i class="fa fa-tag"></i>
**Jekyll**은 간단하게 말해서 테마 **Github는** 저장소 **Ruby는** 개발언어(툴)이라고 생각하면 편하다. (자세하게는 뒤에 가서)

우리는 **Jekyll**의 테마 중 **Ghost**라는 테마를 사용할 것이다.

Window 환경에서 주의해야 할 점이 있다. 컴퓨터 계정의 ID가 한글로 되어 있는 경우 여러 문제가 발생하니 Window 계정 ID를 한글 계정으로 바꾸자.

-*여기서 Tip을 하나  주자면 원래 **(설정 - 계정 - 사용자 정보)** 이런 식으로 컴퓨터 자체에서 바꿨는데 최근에 Window 10을 업데이트했고 Microsoft에 계정을 사용 중이라면 Microsoft 홈페이지에서 내 정보 변경을 통해 바꿔야 할 가능성이 높다.*

------

<i class="fa fa-tag"></i>자 그럼 이제 시작해야 할 일은 **Ruby**를 설치해야 한다.

**Ruby**는 [Ruby-download](https://rubyinstaller.org/downloads/) 이곳에서 다운받으면 된다. 내가 이 페이지에서 사용할 버전은 **2.6.6-2** 이다.  (*다른 버전으로 사용 시 오류 가능성*)

**Ruby**를 다운받았다면 이제 **bundler**를 설치하자.

**bundler**는 Ruby application 개발을 위한 일관된 환경을 제공한다. 단편적 기능 중 하나인 gem의 dependency를 관리하는 것이다.
쉬운 이해를 위해 말하자면,  Ruby에다가 bunlder를 설치해서 bundler로 Jekyll을 실행해서 Jekyll이 블로그를 만드는 것이다.

bundler를 설치하려면 **gem install bundler** 을 터미널에 입력하면 된다.

------

<i class="fa fa-tag"></i>bundler를 설치하였다면 이제 Theme를 설치하자. [Jekylltheme-Jasper2]( http://jekyllthemes.org/themes/jasper2/)
경로를 통하여 압축 폴더를 다운받은 뒤 저장하자.

여기서 주의해야 할 점 폴더 내에 공백이 포함되어 있으면 나중에 css빌드할 때 문제가 발생하니 *C:/blogmaker* 처럼 폴더는 소문자로 공백없이 생성하자.

이 폴더에 있는 파일들이 앞으로 우리가 블로그 만들고 수정하는 곳이다.

cmd 를 실행해서 해당폴더 (C:/blogmaker)에서 실행해 필요한 gem을 설치하자.

1. bundle install 명령 실행

2. bundle exec jekyll serve 명령 실행 (내장 웹서버 실행 명령어)
 이 후 아마 에러가 발생할 것이다.
 실행을 Ctrl + c를 눌러서 일괄 작업을 멈추고
3. gem 'wdm', '>= 0.1.0' 을 Gemfile 파일에 입력하면 된다.

<img src="https://user-images.githubusercontent.com/79001968/110805362-5b2feb00-82c4-11eb-9bd2-73e10a3110f4.png" alt="gemfile" style="zoom:67%;" />

다운이 다 마치고 다시 2번 명령을 실행하면 

<img src="https://user-images.githubusercontent.com/79001968/110806143-1d7f9200-82c5-11eb-8eb0-8b30b5ecabe5.png" alt="browser-view" style="zoom:67%;" />

이러한 내장 웹서버가 실행되는 것을 볼 수 있다. 그러면 자신만의 페이지가 생성된 것이다.

우선 페이지를 만들었으니 반은 성공이다. 다음 포스팅부터는 어떻게 자신에게 맞게 수정을 하고 서버를 구축하는지 알아보도록 하자.

------

##### <i class="fa fa-pencil"></i>

혹시 누군가가 나의 Blog를 보고 코딩을 배운다. 혹은 블로그를 만든다라고 해서 이 글을 본다면...

이 글을 봤을 때 50% 이상이 이해가 안 되거나 오류가 나거나 또는 단어 자체가 생소해서 등등의 많은 힘듦이 있을 거다.

나도 그랬다. 비전공자이고 그렇다고 학원이나 부트캠프에서 배우지 않아서 정말 아무것도 모르는 상태에서 시작했다. 모르는 것이 나오면 계속 유튜브 찾아보고, 구글링하고, 책을 읽었다. 그러다 보니 하나씩 알아듣는 내용이 생기고 재미가 붙기 시작했으니 포기하지 말고 힘내기를 바란다.

이 포스팅 내용 또한 나도 유튜브와 블로그에 포스팅한 내용을 공부하고 복습하려고 내가 다시  봤을때  조금 더 쉽게 수정한 내용이다.