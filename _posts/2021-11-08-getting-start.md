---
layout: post
title:  "getting started"
date:   2021-11-08 21:38:00 +0700
categories: [python]
---

## smooth communication

원활한 수업진행을 위한 프로그램 설치 및 설정

### 1. Chrome setting and remote desktop

크롬을 기본 브라우저로 설정하고 **크롬 원격 데스크톱**을 설치한다. 위 과정은 원활한 수업진행을 위해 공통된 브라우저를 사용하고 해결하기 어려운 경우 원격 데스크톱을 이용해 빠른 해결을 하기 위함이다.

### 2. Slack download and participation

Slack을 이용해 파일을 공유할 수 있고, 전하고자하는 내용을 채팅으로 대화하기 위함이다.

## Creating a blog using github

수업을 통해 배운 내용을 블로그에 작성함으로써 하루에 배운 내용 및 중요한 내용을 정리한다:

### 1. git Download

형상관리(버전관리)를 하기 위해서 git을 활용해서 버전관리를 한다.

### 2. Visual studio code Download

개발Tool로서 Visual studio code를 다운로드 한다.
웹기반의 에디터 프로그램으로 가볍고 강력(확장프로그램 다수 보유)하여 해당 개발Tool을 사용한다.

## Version management

cmd창을 이용해 로컬의 파일을 서버에 올리는 작업을 한다.

### 1. 기본 cmd 명령어 사용하기

#### 작업소스를 관리하는 폴더 만들기

작업소스를 관리하기 위한 폴더를 생성한다.
폴더위치 및 폴더명은 다음과 같다. **C:\apps\git_test**
위의 폴더에 apps 폴더 및 git_test 폴더를 생성하려면 cmd에서 실행해야하는 명령어는 아래와 같다.
```javascript
  cd /
  mkdir apps
  cd apps
  mkdir git_test && cd git_test
```

해당 폴더를 git 버전관리를 위한 폴더로 지정하려면 **git init** 을 cmd창에 실행하면 된다.

### 2. git hub 회원가입 및 로컬과 연결하기

github 홈페이지로 들어가서 회원가입을 한다.
회원가입을 한 후 new repository를 클릭해 repository의 이름을 설정한다.
repository명과 로컬의 작업폴더명을 동일하게 설정해두었다.
repository를 생성했다면 cmd 창에서 아래의 명령어를 실행한다.

```javascript
git remote add origin https://github.com/UserName/workplaceName.git
git branch -M main
git push -u origin main
```

위의 두줄은 딱 한번만 실행하는 코드지만 맨 아래의 명령어는 로컬에서 수정이 생겨서 
서버에 반영하고자 하는 경우에 계속 실행하는 명령어로서 자연스럽게 외우게 될 것이다.

### 3. 로컬에서 수정한 소스를 서버에 반영하는 방법

우리는 소스를 Visual studio code를 통해 생성 및 수정할 것이다.
생성 및 수정한 파일을 서버에 올리고자 한다면 다음과 같은 명령어를 cmd창에서 실행시켜주면 된다.

```javascript
git add .
git commit -m "수정한 내용"
git push -u origin main
```

**git add .**은 생성/수정/삭제된 소스에 한해서만 status에 올리겠다는 뜻이다.
**git commit -m "수정한 내용"** 은 commit하겠다는 뜻이다.
**git push -u origin main**은 main branch에 넣겠다는 뜻이다.(서버반영)

위의 내용을 통하여 우리는 버전관리를 하게 된다.
위 내용은 github 홈페이지에서 확인할 수 있다.