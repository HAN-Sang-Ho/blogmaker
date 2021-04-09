---
layout: post
current: post
cover:  assets/built/images/jekyll-logo.png
navigation: True
title: Jekyll - 나의 블로그를 수정해보자 & Publishing
date: 2020-03-07 20:20:00
tags: [jekyll]
class: post-template
subclass: 'post tag-python'
author: Hono
---



<i class="fa fa-list-alt"></i>저번 포스팅에서는  여러가지 환경 구축과 블로그를 내장 웹서버를 통해 블로그를 내화면에 띄우는데 까지 해봤다.

------

<i class="fa fa-tag"></i>이번 포스팅은 블로그를 내가 원하는 모양 수정하는 법과 **GitHub Page**에 내 블로그를 개설하는 방법에 대해서 다루도록 하겠다.

여기서 먼저 **GitHub Page**가 뭔지 알고 가도록 하자.  <i class="fa fa-thumb-tack"></i> **GitHub는 중요해...**

<img src="https://user-images.githubusercontent.com/79001968/110790844-de494500-82b4-11eb-9504-10493a923fe1.png" alt="GitHub-logo" style="zoom: 50%;" />



**GitHub**란 쉽게 설명하자면 개발자들이 사용하는 홈페이지인데 여기 여러 가지 기능들이 있다. 우리는 그중 우리 블로그 페이지를 만들어주는 기능과 수정을 용이하게 하려는 기능을 사용하려 한다.

그러면 한 가지 의문이 들것이다. 페이지가 만들어졌는데 굳이 왜 **GitHub Page**를 이용하는 거지? 

 그 이유는 간단하다. 정말 나만 보기 위해 그리고 다른 컴퓨터가 아닌 내컴퓨터에서만 확인하려면 내장 웹서버를 이용해도 된다. 
 하지만 우리는 내가 아닌 그리고 내컴퓨터에서만 확인하는 게 아니라 **URL** 주소만 있다면 언제 어디서든 그 누구라도 24시간 페이지에 접속이 가능한 웹사이트를 만들고 싶을 거다. 즉, 쉽게 말해 우리 대신 페이지를 24시간 동안 활성화되고 접근할 수 있도록 **GitHub**에서 관리해주는 것이다.

물론 다른 사이트들도 많지만, 그중 개발자들이 **GitHub**를 가장 선호하는 이유는 무료! 두 번째 이 외에도 개발에 필요한 많은 기능이 있기 때문이다.
이 기능들은 앞으로 차차 알아가고 이번 포스팅은  Page를 개설하는 곳에 포커스를 두도록 하자. 

------

<i class="fa fa-tag"></i>첫번째 포스팅에서도 언급했지만, 네이버 블로그나 다음 티스토리 같은 경우는 수정하기는 쉬워도 자기 마음대로 기능을 추가하고 배치하는 것에 대한 한계가 있다.

**Jasper2** 를 이용한 블로그는 자신이 원하도록 수정을 할 수 있는데... 이게... 생각보다 많이 어렵다... 차근차근히 해보도록 하자...

우선 압축 해제한 폴더 **C:/blogmaker** 이 폴더가 **Jekyll Source Folder**가 된다.
폴더 안의 **_post**라는 파일이 우리가 글을 직접 작성하는 곳이다. (내장 웹서버)

이 폴더에 글을 **markdown** 형식으로 작성을 하고, **bundle exec Jekyll serve** 명령을 이용하여  **build** 시키면 저장된 글에 컴파일이 진행되고 결과물이 **destination** 폴더에 생성된다.

이후에 **GitHub Page**에 올려 실제 사용하는 블로그가 이 **destination** 폴더 안에 있는 내용이다. 따라서 **Git**을 이용하여 변환된 결과물(destination 폴더 안의 내용)을 **GitHub Page**와 연동되는 **GitHub Repository**에 **push** 해 주어야 한다.

처음에 이 내용이 어려울 수도 있는데...  쉽게 설명하자면 수학 문제를 풀 때 연습장에다가 문제를 풀다가 정답이 확실해지면 시험지에 풀이와 답을 적듯이 우리도 내장 웹서버에서 파일들을 이것저것 수정하고 추가하다가 수정할 내용이 확정이 되었을 때 최종적으로 **GitHub**에 올리는 것이다. (이 과정을 commit하고  push준다 라고 생각하면 될 것 같다.)  

그리고 이때 사용하는 **IDE**는 **WebStorm**을 이용하도록 하겠다.

------

**C:/blogmaker **폴더안에서 **_config.yml**을 찾아 해당내용을 자신에 맞게 수정해서 사용해야 한다.

<script src="https://gist.github.com/HAN-Sang-Ho/abb5761cdd32b71ab17e25627a9a9e07.js"></script>

_config.yml 을 들어가보면 이렇게 긴 코드들이 뜰것이다.

대부분 주석처리가 되어 있기 때문에 정보를 수정하는데 큰 어려움이 없을 것이다.

(위에있는 코드를 그대로 사용하면 안됨. 본인의 정보에 맞게 수정) 

------






