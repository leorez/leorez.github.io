---
layout: post
title: React Native로 간단버전의 To-Do List 앱을 만들어보자 1
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


## 프로젝트 초기화

프로젝트를 Todo라는 이름으로 만들고 일단 시뮬레이터에서 구동해보겠습니다.

터미널 명령창을 열고 다음과 같이 입력합니다.

{% highlight bash %}
react-native init Todo
cd Todo
react-native run-ios (or run-android)
{% endhighlight %}



<img class="screenshot center" src="/images/screenshot001.jpg">



시뮬레이터가 시작되면서 위와 같은 화면을 보게됩니다. react-native-cli가 설치되어있지 않으면 에러를 만나게 됩니다. 설치는 다음 링크를 참조하세요.

리엑트네이티브의 장점중하나는 상용 프로토타이핑툴을 사용하지 않아도 프로토타입을 쉽게 만들고 미리 실행해 볼 수 있다는 점입니다. 게다가 프로토타이핑된 결과물을 바로 개발에 사용할 수 있다는 커다란 이점이 있지요.

그래서 리엑트네이티브로 개발할때는 UI를 미리만들어 시험해 보고난뒤 실제 기능을 하나씩 구현하는 방법을 추천합니다.

이 튜토리얼에서도 같은 방식으로 진행해 나갑니다.

프로젝트를 만들기 위해서 우선 기능 정의가 필요할것 같습니다.

## 프로젝트 기능 정의

* 할일 목록보기 기능
* 할일 추가 기능
* 할일 삭제 기능
* 할일 완료 기능


일단 가장 간단하고 사용할수 있는 앱을 만들기위한 가장 기본적인 기능들만 정의 했습니다.

그럼 일단 완성된 모습을 보시죠.

우리의 첫번째 어플의 목표라고 할 수 있겠습니다.

위 그림을 참고로해서 UI/UX만을 구현해서 시험을 해보겠습니다.

## 프로토타이핑

이제 부터 우리가 만들 화면을 미리 만들어 보고 작동시켜 보겠습니다. 우선 작업을 편하게 하기 위해서 'Hot Reload'기능을 이용하겠습니다.

개발시 'Hot Reload'기능을 활성화 하면 매우 편리한데요. 네이티브 개발시에는 매번 새로 시작해야만 했던것을 소스가 저장되면 바로 화면에 반영이 되어 개발속도를 높일수 있는 매우 편리한 기능입니다.

그럼 기능을 활성화 하기 위해서 iOS에서는 'Cmd+D'를 입렵하고 안드로이드에서는 menu버튼을 누릅니다.

그럼 다음과 같은 메뉴가 나타납니다.

<img class="screenshot center" src="/images/screenshot002.jpg">

이중에서 'Enable Hot Reloading'을 선택하면 메뉴화면이 닫히고 화면이 리로딩되면서 기능이 활성화 됩니다. 앞으로는 소스를 저장할때마다 화면이 자동으로 갱신됩니다. 하지만 개발하다 보면 자동으로 갱신이 되지 않는 경우도 있습니다. 이런 경우에는 수동으로 'Cmd+R' 또는 'RR'을 입력해서 강제로 리로딩 하는 수 밖에는 없습니다.

그럼 먼저 리스트 화면을 만들어 보겠습니다.

### 리스트 화면 만들기

본인이 사용하기 편한 에디터를 이용해서 우리가 생성한 Todo 프로젝트 소스를 엽니다. 저는 마이크로소프트의 Visual Code를 사용했습니다. 

프로젝트파일 리스트를 보면 아래와 같이 보이게 됩니다.


<img class="screenshot center" src="/images/screenshot003.png">

'index.js'파일은 리엑트네이티브의 메인이라고 할 수 있습니다.

내용을 보면 아래와 같습니다.


{% highlight javascript linenos   %}
import { AppRegistry } from 'react-native';
import App from './App';

AppRegistry.registerComponent('Todo', () => App);

{% endhighlight %}

리엑트네이티브에서는 ES6문법을 사용합니다. ES6에 대한 설명은 이 강좌의 범위를 벗어나므로 생략하겠습니다.

{% highlight javascript %}
import App from './App';
{% endhighlight %}

이것은 App.js에 App클래스를 App이라는 이름으로 가져온다는 의미입니다.
**npm** 으로 설치한 모듈들은 상대경로 없이 가져오지만 우리가 만든 모듈들은 상대경로를 표시해줘야지만 가져올 수 있습니다.

