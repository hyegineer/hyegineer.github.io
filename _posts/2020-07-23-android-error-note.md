---
layout: post
title: "[Android] android studio build error - Unable to start the deamon process"
date:   2020-07-17 12:30:00 +0900
tags:
  - android
---

안드로이드 스튜디오로 앱을 빌드할 때 나타나는 오류현상

```
  FAILURE: Build failed with an exception.

  * What went wrong:
  Unable to start the deamon process.
  This problem might be caused by incorrect configuration of the daemon.
  For example, an unrecognized jvm option is used.
  Please refer to the User Manual chapter on the daemon at https://docs.gragle.org/6.0.1/userguide/gradle_daemon.html
  Process command line: C:\Program Files (x86)\Java\jdk1.8.0_211\bin\java.exe -XX:MaxPermSize=512m -XX:+HeapDumponOutOfMemoryError -Xmx2048m -Dfile.encoding=UTF-8 -Duser.country=KR……(이하생략)
  Pleae read the following process output to find out more:
  -----------------------
  Error occurred during initialization of VM
  Couldd not reserve enough space for 2097152KB object heap
  Java HotSpot(TM) Client VM warning: ignoring option MaxPermSize=512m; support was removed in 8.0

  * Try:
  Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.
```

메모리가 부족할 때 나타나는 에러현상
현재 컴터에 설치된 램용량을 비롯해 작동환경에 비해 버거운 용량이 설정되었기때문이라고 한다.
[출처: 임상노트 365](https://kerneler.tistory.com/13)

안드로이드스튜디오 > 프로젝트 > gradle script의 gradle.properties 파일

### 변경 전 
```
  ...
  
  # Default value: -Xmx10248m -XX:MaxPermSize=256m
  org.gradle.jvmargs=-`Xmx2048m` -XX:MaxPermSize=512m -XX:+HeapDumpOnOutOfMemoryError -Dfile.encoding=UTF-8

  ...
```

### 변경 후

```
  ...
  
  # Default value: -Xmx10248m -XX:MaxPermSize=256m
  org.gradle.jvmargs=-`Xmx512m` -XX:MaxPermSize=512m -XX:+HeapDumpOnOutOfMemoryError -Dfile.encoding=UTF-8

  ...
```

변경 전에는 Xmx2048m 로 되있었는데, Xmx512m 로 낮춰주니 정상적으로 실행이 되었음
jvm을 위한 가상메모리 할당을 현재 설정보다 낮춰준 후
`Refresh all Gradle projects` 수행 후 확인해야한다고 함

