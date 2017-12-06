---
layout: post
title: React Native로 간단한 기능의 To-Do List 앱을 만들어보자 1
description: 우선 간단한것 부터 시작해 보자
tags: [sample post]
author: Leorez
image:
  title: /images/react-native-tutorial-cover.png
  background: triangular.png
---

<img src="/images/react-native-tutorial-cover.png">

* StyleSheet
* 프로젝트 아키텍쳐
* JSX
* ES6
* To-Do List 프로토타입 만들기
* iOS Simulator Developer menu
* 프로젝트 기능 정리


## 프로젝트 준비 초기화

프로젝트를 Todo라는 이름으로 만들고 일단 시뮬레이터에서 구동해보겠습니다.

터미널 명령창을 열고 다음과 같이 입력합니다.

{% highlight bash %}
react-native init Todo
cd Todo
react-native run-ios (or run-android)
{% endhighlight %}



<img class="screenshot center" src="/images/screenshot001.jpg">



시뮬레이터가 시작되면서 위와 같은 화면을 보게됩니다. react-native-cli가 설치되어있지 않으면 에러를 만나게 됩니다. 설치는 다음 링크를 참조하세요.

리엑트네이티브의 장점중하나는 프로토타입을 쉽게 만들고 미리 실행해 볼수 있다는 점입니다.


<img class="screenshot center" src="/images/screenshot002.jpg">