---
layout: post
title: "[Git] Git 기본 개념 (2)"
date:   2021-11-02 17:15:00 +0900
tags:
  - Git
---

# Git commit history

## 1. 커밋 히스토리 살펴보기

```jsx
git log
git log --pretty=oneline
git show {{ commit hash 4자리 }}
git show # 제일 최신 커밋 내역 보여줌
```

### git aliasing하기 (별명 짓기)

```jsx
git config alias.앨리어스할 별명 'log --pretty=oneline'
```

1. 이 경우 해당 폴더에서만 (.git이 만들어진 디렉토리) 앨리어싱이 적용되게 됌.
    
    해당 디렉토리 경로에서 `cat .git/config`을 통해 alias를 비롯한 다른 설정들을 확인할 수 있음 
    
2. 글로벌로 사용하기 위해선 `—global` 옵션 사용. 전역적으로 사용하게 됌.
    
    이 경우는 `cat ~/.gitconfig` 로 확인할 수 있음
    
3. 현재 사용자 뿐만 아니라 모든 사용자의 모든 git파일에 적용시키는건 `—system` 옵션 사용.
    
    이 경우는 `cat /etc/gitconfig` 으로 확인
    

## 2. m옵션 없이 커밋메세지 상세히 남기는 방법

```bash
git commit
# i (insert) 누른 후 메세지 삽입, 상세설명 적을 시 한줄 띄우고 작성
# 다 작성했으면 esc 누르고
# :wq 작성 후 나간다.

# 제목 + 상세설명이 함께 남겨지는 커밋 완성!
```

## 3. 최신 커밋 수정하는 방법

```bash
git commit --amend
# --amend 옵션을 적어주면, git commit 했을 떄의 화면이 나옴
# 메세지 수정 후 esc 누르고
# :wq 작성 후 나간다

# 잘 수정됐는지 보려면 git show or git log --pretty=oneline
```

## 4. 커밋 생성과 커밋 메세지 작성 가이드라인

### 커밋메세지 작성 가이드라인

1. 커밋 메시지의 제목과 상세 설명 사이에는 한 줄을 비워두세요.
2. 커밋 메시지의 제목 뒤에 온점(.)을 붙이지 마세요.
3. 커밋 메세지의 제목 첫번째 알파벳은 대문자로 작성
4. 커밋 메세지의 제목은 명령조로 작성
5. 커밋의 상세내용은 되도록 친절히

### 커밋할 때 가이드라인

1. 하나의 커밋에는 하나의 수정사항, 하나의 이슈를 해결한 내용만 남길것
    
    다양하게 수정을 하고나서 하나의 커밋으로 남기는건 추적이 쉽지않음 (커밋간의 독립성이 사라져서 프로젝트의 이력을 파악하는게 어려워짐)
    
2. 현재 프로젝트 디렉토리 상태가 에러가 발생하지 않는 상태인 경우에만 커밋할 것.
    
    항상 문제 없이 실행되는 상태여야하고, 과거의 커밋이라도 과거 커밋을 시작점으로 다른 방향의 별도 프로젝트를 시작해야할 수도 있고, 아예 그 커밋으로 리셋해야할 때도 있음
    

가이드라인은 사내규칙따라 다를 수 있음. 하지만 **나중에 다시 봤을 때 이해하는데 어려움이 없도록**

**다른 동료 개발자와 협업하는 데 방해가 되지 않도록** 작성하는 것이 중요

## 5. 두 커밋 간의 차이 보기

```bash
git diff 이전커밋아이디 이후커밋아이디
```

## 6. 커밋 되돌아가기

### HEAD 개념

HEAD ? 어떤 커밋 하나를 가르키는데, 가장 최근에 한 커밋이라 볼 수 있음.
HEAD가 가르키는 커밋에 따라 working directory 구성

헤드가 과거의 커밋을 가리키게 할 수 있다. 특정시점 이후의 작업들을 리셋하고 돌아가고 싶을 때 쓰는 커맨드가 git reset

```bash
git reset --hard 커밋아이디

# 원상태 복구하고 싶으면?
git reflot # 이전 commit 내역과 id 확인 후 다시 git reset 설정
```

### git reset 시 hard, soft, mixed 옵션

![http://hyegineer.github.io/images/gitreset.PNG](http://hyegineer.github.io/images/gitreset.PNG)
![http://hyegineer.github.io/images/mixedhardetc.PNG](http://hyegineer.github.io/images/mixedhardetc.PNG)

### hard 옵션

- 별로 권장하진 않음, hard옵션으로 reset을 하면 working directory에서 했던 내용이 다 사라지고 복구를 할 수 없어서.
- commit 이후로 했던 내용들이 전부 사라져도 상관없을 때만 사용

![http://hyegineer.github.io/images/harddesc.PNG](http://hyegineer.github.io/images/harddesc.PNG)

### mixed 옵션

![http://hyegineer.github.io/images/mixeddesc.PNG](http://hyegineer.github.io/images/mixeddesc.PNG)