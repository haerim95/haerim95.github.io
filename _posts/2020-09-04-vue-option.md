---
title: "vue CLI로 생성된 환경을 알아보자"
date: 2020-09-04
categories: [Vue]
---

---

# vue CLI 프로젝트 생성 후 환경 

> Vue 환경 세팅을 마쳤다면 자동으로 생성된 파일과 폴더를 볼 수 있을 것이다.
> 이 자동으로 생성된 파일들에 대해 알아보자! 👀

Vue Project를 성공적으로 생성했다면 이와 같은 구조의 파일, 디렉토리를 볼 수 있을 것이다.

<div class="imgWrap">
    <img src="./../public/img/rootImg.png">
    <span>파일 앞에 마침표(.)가 붙은 파일들은 Linux / Unix 기반의 운영체제에서 숨김 파일을 의미하므로 보이지 않을 수도 있다.  
    하지만 IDE로 해당 프로젝트를 불러오면 모두 노출된다.
    </span>
</div>

#### 자, 이제 파일 구조를 살펴보자.

`* 순서는 위에 이미지 목록에 있는 순서이다.`

### 1. 📁 build

<p class="message">이 디렉토리에는 Vue 프로젝트를 브러우저에서 실행할 수 있게끔 빌드하기 위해 작성된 파일들이 위치한다.</p>

### 2. 📁 config

<p class="message">
    config 디렉토리엔 설정에 필요한 여러 가지 상수들이 선언되어 있다. <br/>
    크게 나누면 <span class="color2">dev 속성</span>과 <span class="color2">build 속성</span>이 있다.
</p>

| dev 속성 | bulid 속성 |
| :---: | :---: |
| 개발환경에서 사용하는 상수 | 개발완료 후 애플리케이션을 빌드할때 사용하는 상수 |

### 3. 📁 node_modules / 📄 package.json

<p class="message">
    node_modules에는 사용자가 npm을 통해 설치한 패키지들이 위치하고 있다. <br/>
    설치한 패키지들은 pakage.json 이라는 파일을 통해 관리하게 되는데, vue CLI는 필요한 패키지들을 초기 설정시 설치해주기 때문에 따로 원하는 패키지가 없다면 새롭게 설치할 필요가 없다.
</p>

### 4. 📁 src 

<p class="message">
    src 에는 애플리케이션의 소스가 위치하게 된다. <br/>
    애플리케이션이 동작하는데 필요한 대부분의 소스는 이 디렉토리 안에 존재한다.<br/>
    <span class="color2">main.js</span>, <span class="color3">App.vue</span>, <span class="color4">assets</span>, <span class="color4">router</span>, <span class="color4">component</span>
    기본적으로 세팅되는 5가지의 파일이다.
</p>

### 4-1. 📁 assets

<p class="message">
    애플리케이션에서 사용되는 정적 리소스들이 위치한다. 뒤에 설명할 static 디렉토리(5번)와 다른점이 있다면 이 디렉토리에 위치하는 리소스들은 빌드 시 Webpack이 처리하게 된다. <br/>
    프로젝트 진행시 정적 리소스를 static에 위치할 것인지 assets에 위치할 것인지에 대한 판단이 필요하다.
</p>

### 4-2 📁 component

<p class="message">
    Vue 컴포넌트들이 위치하게 된다. 
</p>

> component?
>> 하나의 독립적인 기능을 가지고 있는 단위 모듈.

### 4-3 📁 router

<p class="message">
    Vue의 공식 라이브러리인 Vue Router의 코드가 위치하게 된다. <br/>
    사용자가 접속한 url에 어떤 컴포넌트를 랜더해야 하는지 정해주는 라이브러리다. <br/>
    index.js에서 Router 객체를 추출하는 모듈 형태로 되어있다.
</p>

vue router는 거의 모든 vue 프로젝트에 사용되는 만큼 공식문서를 꼭 읽어보자

[vue.router]("https://router.vuejs.org/kr/")

### 4-4 📄 App.vue

<p class="message">
    Vue 애플리케이션의 루트 컴포넌트다. <br/>
    vue 애플리케이션의 컴포넌트들은 App 컴포넌트를 중심으로 트리 형태의 구조를 가지게 된다.
</p>

### 4-5. 📄 main.js

<p class="message">
    Webpack이 빌드를 시작할때 가장 처음 불러오는 진입 지점이다. <br/>
    즉, 우리가 작성한 애플리케이션은 이 파일을 실행함으로써 시작된다. 해당 파일에선 App.vue 파일을 불러와서 Vue 객체를 생성하고 #app 엘리먼트에 바인딩하는 코드거 작성되어 있다.
</p>

### 5. 📁 static

<p class="message">
     static 에는 이미지, 폰트같은 정적(static) 리소스들이 위치하게 된다. <br/>
     이 디렉토리 내부에 위치한 파일들은 Webpack을 거치지 않는다. 거치지 않고 이 안에 있는 파일들을 그대로 복사하여 빌드 결과문 디렉토리인 dist📁 로 옮길 것이다. <br/>
     처음 프로젝트를 세팅하면 이 안에 .gitkeep📄 이라는 파일 하나만 존재한다. 깃은 비어있는 디렉토리를 추적하지 않기 때문에 추적하게 하기 위해 생성해둔 것이다.
</p>


### 6. 📁 test

<p class="message">
    test 에는 e2e 테스트(end to end Test)에 관한 코드와 단위 테스트(Unit Test)에 대한 코드들이 위치하고 있다.
</p>

<div class="iterm">
    <span class="notes"># 단위 테스트 명령어 실행</span>
    <span>npm run unit</span>
    <span class="notes"># e2e 테스트 명령어 실행</span>
    <span>npm run e2e</span>
    <span class="notes"># 통합 테스트 명령어 실행</span>
    <span>npm run test</span>
</div>

> e2e 테스트란? 🤔
>> 전체 시스템이 제대로 작동하는지 확인하기 위한 테스트.
>> 최대한 실제 사용자 관점에서 테스트를 수행하기 때문에 수행 속도가 느릴 수 있다. 그래서 단위 테스트와 같이 자동화되는 테스트와 함께 구성된다.

> 단위 테스트란? 🤔
>> 전체 시스템이 아닌 개별적으로 작성된 작은 규모의 코드 뭉치들이 제대로 작동하는지 검사한다.
>> vue의 경우 보통 컴퍼넌트들의 기능을 테스트한다. 

### 7. 📄 .babelrc

<p class="message">
    ES6를 지원하지 않는 웹 브라우저를 위해 ES6 문법을 ES5 문법으로 트랜스파일링(Transpiling) 하는 작업이 필요하다. 이는 주로 바벨(babel) 이라는 도구를 사용해주는데 .babelrc 파일에 바벨에 대한 세팅이 정의되어 있다. 
</p>

### 8. 📄 .editorconfig

<p class="message">
    .editorconfig는 코드에 영향을 미치는게 아니라 여러가지 IDE에서 통일된 코딩 스타일을 유지할 수 있게 도와주는 파일이다. 파일의 인코딩 형식 등에 대한 설정이 정의되어 있다. IDE에 따라 프로그램 내에 플러그인이 기본적으로 내장되어 있는 경우도 있지만 그렇지 않은 경우도 있기때문에 별도의 플러그인을 설치해줘야 하는 경우도 있다.
</p>

### 9. 📄 .eslintignore

<p class="message">
    이 파일 내부에 선언되어 있는 경로에 위치한 파일들은 린터(Linter)가 검사를 진행하지 않는다.
</p>

> Linter?
>> 정적 타입 분석도구이다. 

### 10. 📄 .eslintrc.js

<p class="message">
    앞서 말했듯이 linter란 코딩 컨벤션(coding convention)과 관련된 에러를 체크해주는 작은 프로그램이다. 이런 코딩 컨벤션에 대한 설정 파일이 들어있다. 물론, 코딩 컨벤션을 지키지 않았다면 빌드는 실패한다. 
</p>

### 11. 📄 .gitignore

<p class="message">
    이 파일에 선언된 경로에 위치한 파일들은 깃에서 따로 형상 관리를 하지 않는다. (깃을 사용하지 않는 프로젝트라면 무시해도 좋다)
</p>

### 12. 📄 .postcssrc.js

<p class="message">
    자바스크립트를 이용하여 css를 변환하는 툴이다. 그렇지만 sass와 less같은 css 메타언어와는 다르다. postCSSsms 는 언어가 아닌 개발 도구이며, 어떤 플러그인을 쓰냐에 따라 수행하는 역할이 달라진다. 
</p>

### 13. 📄 index.html

<p class="message">
    사용자가 웹페이지에 접속했을 때 다운로드하게 되는 HTML 템플릿이다. <br/>
    기본적인 vue 애플리케이션은 Webpack이 번들린된 파일을 index.html에 삽입하고 클라이언트에서 랜더링을 수행하는 방식으로 작동한다. <br/>
    외부 스크립트를 CDN을 통해 호출해야 하거나 문서의 타이틀을 수정하는 등, HTML에 작성해야 하는 코드가 있다면 이 파일에 작성하면 된다.
</p>

