---
layout: post
title: "[일하다가 궁금해서 찾아본] user select 속성"
date:   2019-07-30 12:11:00 +0900
tags:
  - css
---

* css user-select란?

마크업을 한 후 스타일링을 하다가 보이는 user-select 속성!
모바일에 최적화된 팝업 플러그인의 css에 user-select가 일일히 지정되어있는걸 보고 찾아봤다.
```css
    .text{
        user-select: none;
    }
```

으로 처리하게 되면은 엘리먼트의 텍스트값이 드래그되지 않는다.
보통 모바일 웹앱에서 텍스트 선택되면 아무래도 네이티브 느낌이 떨어지니
이런 디테일한 부분도 잡아주는가보다!

```css
    .text{
        user-select: all;
    }
```
로 하게되면, 텍스트 선택시 클릭만으로도 드래그가 되는 현상!
그 외 프로퍼티 중 default, text는 기본값으로써 딱히 다른 설정없이도 엘리먼트의 텍스트가 드래그된다~
