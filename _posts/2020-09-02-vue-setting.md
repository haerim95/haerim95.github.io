---
title: vue 세팅해보자!
date: 2020-09-02
categories: [vue]
comments: true
---

---

# vue.js 를 시작하며...  

앞으로 vue.js 카테고리에 추가될 글들은 책 <br/>
`커피한잔 마시며 끝내는 Vue.js`를 정리하며 작성될 예정입니다. 🤸‍♀️🤸‍♀️🤸‍♀️  
책을 기반으로 포스팅을 하지만 추가적인 의문점이나 구글링을 통한 내용도 작성될 것입니다.

---
# vue 시작하기 🚀

## 1. node.js 설치 (설치가 되어 있다면 pass)

> vue.js 를 설치하기 위해선 node.js가 설치되어 있어야 한다.  
> [node.js 설치하기](https://nodejs.org/en/)
>> current 버전은 지양하도록 한다. 최신 버전이기 때문에 호환성 문제가 있기 때문이다.
>> 편의에 따라 yarn을 설치하셔도 좋습니다!

Node.js 설치 확인 방법
<div class="iterm">
   <span>$ node -v </span>  <br/>
   <span>$ npm -v  </span>
</div>  <br/>

위의 코드를 터미널, cmd 등에 입력 했을 때 버전이 뜨면 설치가 완료됐다는 뜻이다.
💡 npm은 node.js를 설치하면 함께 설치되므로 별도로 설치하지 않아도 된다. 

<br/>
<br/>

## 2. Vue CLI

> CLI란 Command Line Interface의 약자다.
> 텍스트 터미널을 통한 사용자와 컴퓨터의 상호 작용 방식을 말한다.
>> cli 2.x.x / cli 3.x.x or 4.x.x 를 유의하자
>>> 나는 책에 소개된대로 2.x.x 버전을 이용하겠다.

vue cli 설치를 위해 터미널 or cmd에 아래와 같은 명령어를 입력해 준다.

#### 2.x 버전 설치

<div class="iterm">
    <span class="notes">/* 해당 디렉토리 안에서만 설치 */</span>
    <span>$npm install vue-cli</span> 
    <span class="notes">/* 전역 설치 */ </span>
    <span>$npm install vue-cli -g</span>
</div>

#### 3.x 버전 설치

<div class="iterm">
    <span class="notes">/* 해당 디렉토리 안에서만 설치 */</span>
    <span>$npm @vue/cli-service</span> 
    <span class="notes">/* 전역 설치 */ </span>
    <span>$ npm i -g @vue/cli</span>
</div>

### 여기서 잠깐!! 👀
<div class="notice">
    <span class="color1">Vue CLI 3.x 버전</span>과 (현재는 기본으로 깔면 4.x이다) <span class="color1">Vue CLI 2.X</span> 버전은 프로젝트를 생성할때 기본적으로 생성되는 디렉토리 구성이 다릅니다. 
</div>

| Vue CLI 2.x | Vue CLI 3.x |
| :---: | :---: |
| 개발자가 직접 파일을 세팅할 수 있다 | 옵션 지정을 안하면 간단하게 시작 할 수 있다 |

### 3.x 버전을 미리 깔았는데...2.x 버전으로 바꾸고 싶다면? 🤔
<div class="iterm">
    <span> $ npm install @vue/cli-init -g </span>
    <span class="notes">/* init으로 초기화 후 2.x 버전을 까는 명령어를 입력한다. */</span>
    <span>npm install -g vue-cli</span>
</div>

vue 버전 확인은 이렇게 한다.
<div class="iterm">
    <span> $ vue --version </span>
</div>
<br/>

버전을 확인 했으면 이제 프로젝트를 생성해보자!

나는 책을 따라 2.x 버전을 이용할 것이다. 📖

##### 반대로 낮은 버전에서 높은 버전으로 올린다면?

<div class="iterm">
    <span>npm r -g vue-cli </span>
    <span>npm install -g @vue/cli</span>
</div>

## 2. Vue 프로젝트 생성

vue CLI 를 이용해 프로젝트를 초기화하는 기본 명령어는 아래와 같다.
<div class="iterm">
    <span> $vue init template-name project-name </span>
</div>

vue CLI 3.x 버전 이상은 아래와 같이 생성합니다.
<div class="iterm">
    <span> vue create [project name] </span>
</div>

`template-name` 이 위치한 곳엔 template-name을, `project-name` 이 위치한 곳엔 프로젝트 이름을 넣으면 완성 <br/>


#### 그런데...template-name이 뭐야? 🤔

위의 2.x 버전 코드를 보면 `project-name`은 내 프로젝트 디렉토리의 이름을 입력하라는거구나! 하고 생각할 수가 있다.  
그런데 `template-name` 은?

<br/>

> template-name은 Vue CLI에서 정의하는 옵션 `6개` 중 하나를 입력해야 한다.


| option-name | description |
  |:---|:---|
| webpack | browserify와 vueify를 이용하는 간단한 옵션 <br/>  liter와 단위 테스팅 도구를 사용할 수 있다.|
| webpack-simple |  webpack 빌드 도구, vue-loader를 이용하는 풀옵션 <br/>  작은 애플리케이션을 만드는데 용이|
| browserify | browserify와 vueify를 이용하는 간단한 옵션 <br/>  liter와 단위 테스팅 도구를 사용할 수 있다.|
| browserify-simple | browserify와 vueify를 이용하는 간단한 옵션 <br/>  작은 애플리케이션을 만드는데 용이|
|  pwa-webpack | pwa 기반의 애플리케이션을 만들때 용이|
| simple | 하나의 HTML 파일 안에서 Vue 컴포넌트로 개발하기에 용이|

#### 책에는 이렇게 나와있지만... 
#### 그래서 템플릿 네임은 왜 적어주는거고, 웹팩이 뭔데? 🤔

vue setting을 하면서 `에러`가 뜨면 열에 여덟은 `웹팩 관련`이었다!  
그래서 웹팩에 관련해서 짧막하게 알아보았다.

##### 웹팩?

<p class="message">webpack : 파일 간의 연관 관계를 파악하여 하나의 자바스크립트 파일로 변환해 주는 변환 도구 </p>

웹팩은 애플리케이션 동작과 관련된 여러개의 파일(HTML, CSS, Javascript...) 들을 `하나의 js 파일`로 변환 시켜준다.  <br/>
내가 애플리케이션을 만들때 10개의 html 파일, 3개의 css 파일 등등을 만들어 사용했다면 <br/>
웹팩이 이것을 합쳐 하나의 js 파일로 만들어주고 애플리케이션을 구동할땐 이 하나의 js 파일만 로딩하면 되도록 한다. <br/>


웹팩에 대한 건 다른 포스팅에서 자세히 알아보도록 하겠다. 👩‍🎓

