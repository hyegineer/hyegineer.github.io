---
layout: post
title: "[Gitlab] you are not allowed to push code to protected branches on this project"
date:   2020-09-10 10:24:00 +0900
tags:
  - gitlab
---

gitlab 저장소의 권한 설정 문제로 일어나는 오류.
`clone`, `commit`, `pull`까지는 괜찮은데 서버로 올릴 때 문제

vs코드로 풀푸시를 할때 정상작동이 안돼고 'git로그를 참조하고 푸시하세요' 같은 alert경고창이 뜬다
혼자 사용할 경우는 상관이 없는데, 다른 사람의 경우는 권한이 developer나 guest기 때문에 문제가 발생할 수 있다.

해결방법을 2개의 블로그에서 참고했다.


[Try & Error](https://blueasa.tistory.com/2351)

해당 에러는 해당 push 하려는 branch 가 Protected로 설정 되어있기 때문에가 많습니다.
대부분 의 경우는 Master Branch 가 이런 경우가 많고 
아니면 다른 브랜치에 대한 Permission 을 주는 경우가 이에 해당되는데
사용중인 Project 에 들어가서 해당 Protected를 해제 하거나 권한을 설정 하면 됩니다.



[UX 공작소](https://uxgjs.tistory.com/169)

![큰 이미지](http://hyegineer.github.io/images/993E9B485E5F3B962D.png)

1. 해당 저장소의 설정메뉴 중 저장소를 선택합니다.
2. 페이지의 중간 쯤에 Protected Branches를 찾습니다.
3. 오른쪽 끝에 있는 펼치기[Expand]를 선택합니다.
4. 원하는 브런치를 선택합니다. 보통 master를 선택하면 맞을 거에요.
5. 서버에 merge를 할 수 있는 권한의 단계를 설정합니다.
6. 서버에 push를 할 수 있는 권한의 단계를 설정합니다. 이 권한을 낮춰주시면 됩니다. Protect 버튼을 클릭하면 바로 아래 권한 표시 된 리스트가 추가됩니다.
7. 일단 요기에 표시된 것이 실제 반영된 protected 리스트입니다. 이 리스트 우측에 있는 Unprotect 버튼을 클릭하면 해당 리스트가 삭제되고 잠김이 풀립니다.
8. 다른 것 안하고 7번 Unprotect 버튼을 눌러 리스트를 삭제해도 위의 문제를 해결할 수 있습니다.



이 포스팅을 참고하고 해결완료!
