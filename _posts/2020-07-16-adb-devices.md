---
layout: post
title: "[android] 프로젝트에서 디바이스 연결여부 체크하기"
date:   2020-07-16 12:56:00 +0900
tags:
  - android
---

안드로이드 디버깅을 위한 환경설정
프로젝트 디렉토리에서 `adb devices` 명령어를 치면 디바이스 연결여부가 나온다.
```
  $ adb devices
  * daemon not running; starting now at tcp:5037
  * daemon started successfully
  List of devices attached
  ~(디바이스넘버)        device
```

```
  $ adb devices
  List of devices attached  
  0715f7e8d1aa2b34        device
```


##### 출처
[Android 디버그 브리지(adb)](https://developer.android.com/studio/command-line/adb?hl=ko)

[윈도우 환경에 ADB 설치하기](https://4urdev.tistory.com/77)

[QA 끝! ADB 설치부터 사용까지](http://labs.brandi.co.kr/2018/08/10/kimcy.html)
