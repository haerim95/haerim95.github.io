---
title: npm과 yarn 그리고 brew
date: 2020-08-11
categories: dev
comments: true
---

---
# 패키지 관리자 툴 ⚙

패키지 관리자 툴이란?  
JavaScript에서 모듈을 설치할 수 있는 패키지 툴이다.  
pakage는 모듈이라고도 불리는데 프로그램보다는 조금 작은 단위이다.


node.js 에서 자주 사용하는 `NPM` 과 페이스북에서 개발한 `yarn`  그리고 맥OS에서 사용하는 `brew` 에 대해 알아보자.

---

## 1. NPM


![npm](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJcAAAA7CAMAAABBn+jeAAAAJFBMVEX////LODfJKCfot7bgmJfOSUnFAADuy8v14eHGEA7kqKfXdXRcp15cAAAA+0lEQVRoge3Z4Q7CIAwEYCiMse3939cYwSUlpaCSkXn3y7Bb/WaiJmDsnDFXA4TA1Re4+jK9i9SMaIq3Zhd5p4UGNHk8cddqtITe5hbVJs9auNwAl97kcXDBBVfFdX7XNVfRFF2Rv3ovNLhs2J4JXnVRau6q61U8mzEvZFiDa0kXdFceobuIvVncUhMuuOCCCy644Pp3F83pOlIca17tKgIXXHDd01XMyC7+a/nN/hd3Ge4q9r/swmP5FfkJpFubZ9qi0b/vK/4//jRw9QWuvkzr6j6KqLg+ON+QYnxzxFOMzDraZ6nhz15JkD6VvL7rM0Yk2Hrggguum7oeyc0jXd/03kcAAAAASUVORK5CYII= "npm logo")  





#### npm 이란?

npm은 Node Package Manager의 약자이다. 말 그대로 node.js로 만들어진 pakage(Module)를 설치 및 관리해주는 CLI 기반의 툴이다.  
npm 명령어를 통해 개발자는 패키지 또는 모듈을 프로젝트에 설치할 수 있다.


#### npm 웹 사이트

> [npm 사이트 바로 가기](https://npmjs.org){:target="_blank"}

npm 홈페이지에선 원하는 패키지를 검색할 수 있다.

#### npm 사용법

1. node.js 설치

2. npm 시작

```
    > npm init
```

3. 패키지 설치

```
    > npm install [pakage name]
```
여기서 [pakage name]은 원하는 패키지 파일을 찾아서 설치를 한다. (괄호는 x)

4. localhost 호출하기

```
    > npm run serve
```
npm을 이용해 사이트를 만들때 로컬 호스트를 호출하는 방법이다.  

---

## 2. yarn

![yarn](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRWseHnrqbiy8Y2gX_t__UCfgKjFssaSJCPMQ&usqp=CAU "yarn")  



#### yarn 이란?

npm과 마찬가지로 javaScript 패키지 매니저이다.  
npm보다 뒤늦게 만들어졌으며 npm의 단점을 보완하기 위해 facebook에서 개발했다.

#### yarn 웹사이트

> [yarn 사이트 바로 가기](https://yarnpkg.com/){:target="_blank"}

#### yarn 사용법

1. node.js 설치

2. yarn 설치

설치 방법은 여러가지이다. 가장 쉽게 설치할 수 있는 방법은 `npm`을 통해 설치하는 것이다!  

```
    > npm install --global yarn
```
> 🤔 왜 `npm`을 통해 설치?  
> yarn은 조금 개선된 버전의 npm이다. 따라서 npm으로 설치가 가능하니
> npm이 설치되어 있다면 npm을 이용해 설치하는 것이 간단하다.

두 번째는 yarn 홈페이지에 나와있는 `chocolatey` 나 `scoop`을 이용해 설치하는 것이다.

```
    $ choco install yarn
```
```
    @scoop install yarn
```

마지막으로 소개할 `brew (맥OS 패키지 매니저)`를 이용하여 설치할 수 도 있다. 
```
    $ brew install yarn
```
버전 관리 툴을 사용해야 한다면 node.js를 제외하고 설치도 가능하다.
```
    $ brew install yarn --without-node
```

3. yarn 실행하기

프로그램 초기화 (package.json을 생성한다.)
```
    yarn init
```

pacjage.json 의존성 모듈 설치
```
    yarn install
```
또는
```
    yarn
```

의존성 모듈을 설치하려면
```
    $yarn add [pakage]
    $yarn add [pakage]@[version]
    $yarn add [pakage]@[tag]
```

의존성 모듈을 제거하려면
```
    yarn remove [pakage]
```

4. locallhost 호출

```
    yarn start
```

---

## 3. Homebrew(홈브류)

![homebrew](https://miro.medium.com/max/256/1*CBCWQowzYqU83B0capCTQA.png "홈브류")  



1. homebrew (홈브류)란?

맥OS용 패키지 관리자 이다.  
리눅스 등의 패키지 관리자와 사용법이 비슷해서 쉽게 사용이 가능하다는 장점이 있다.  
기본적으로 맥OS용 패키지 관리자이지만 리눅스나 윈도우의 WSL도 지원하고 있다.

편리하게 사용할 수 있지만 커뮤니티 기반으로 운영이 되기 때문에 안정성이 보장되지 않다.

> 🤔 홈브류 를 사용하는 이유?
>> 맥에서 원하지 않는 프로그램들이 나도 모르게 설치되거나 재설치, 업데이트, 삭제할 때 기존의 데이터가 남아있는 경우가 많다.
>> Homebrew를 이용하면 이러한 문제 없이 깔끔하게 프로그램을 설치, 삭제, 업데이트 할 수 있다.



2. 웹사이트

> [homebrew 사이트 바로가기](https://brew.sh/)


3. homebrew 설치하기

첫 째로 터미널을 실행한 뒤 `homebrew` 웹사이트로 들어가 설치 코드를 복사한다.
둘 째로 터미널에 복사한 코드를 붙여넣기 한다.
셋 째로 설치 중간에 password를 입력하라 하는데, 여기선 자신의 맥북 비밀번호를 입력하면 된다.

```
    $brew --version
```
위의 명령어를 실행하여 버전이 뜨면 `homebrew` 설치 완료

> 🤔 만약 GUI 기반의 어플리케이션을 설피하고 싶다면?
> cask 패키지를 설치!

```
    brew install cask
```

위와 같이 cask를 설치하면 safari, chrome 같이 그래픽을 통해 작업하는 프로그램을 설치할 수 있게 된다.


4. homebrew 실행하기

먼저 새롭게 진행된 업데이트가 있는지 확인해보기

```
    brew update
```
새로운 업데이트가 있다면 자동으로 설치된다.

내가 설치하고 싶은 프로그램을 `Homebrew`를 통해 설치할 수 있는지 확인하는 법

```
    brew search [프로그램 명]
```

`Homebrew`를 통해 프로그램 설치가 가능한지 확인해봐야 한다. (만약에 없으면 Appstore를 통해 설치해야한다.)

설치가 가능하다면 cask를 통해 설치 프로그램명을 확인 한다.

```
    brew cask install [프로그램명]
```

`[프로그램명] was successfully installed!`

위와 같은 문장이 뜨면 정상적으로 설치가 완료된 것이다.


---

## 🤔 어떤 패키지 매니저를 사용하는게 좋을까?

> `yarn`은 `npm`을 기반으로 `npm`의 단점을 보완하고자 나온 패키지 매니저이다.
> 속도와 보완을 개선한 것이 `yarn`이지만 요즘 `npm`의 속도도 별반 다르지 않아 차이가 없다 한다.
> `yarn`과 `npm`의 명령어는 기본적으로 동일하거나 비슷하다.
> 따라서 그냥 자기가 쓰기에 편한 / 익숙한 패키지 매니저를 사용하는게 좋을 것 같다. (모두 쓸 줄 알면 더 좋다)

난 업무용 컴퓨터에선 npm을, 개인 공부용 컴퓨터에선 brew와 yarn을 사용할 예정이다.