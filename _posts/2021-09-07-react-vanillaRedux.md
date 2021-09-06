---
title: vanilla JS 에서 리덕스 사용해보기
date: 2021-09-07
categories: [react]
comments: true
---

---

### 리액트 없이 리덕스 사용하기, 이게 무슨 소리인가 싶을 것이다.

리덕스는 리액트에 종속되는 라이브러리가 아니다.

물론, 탄생한 이유는 리액트에서 사용하기 위해서 이지만 실제로 `다른 UI 라이브러리, 프레임워크와 함께 사용할 수 있다.` (앵귤러리덕스, 엠버리덕스) vue에서도 사용할 수 있지만, 여기선 리덕스와 비슷한 vuex 를 자주 사용한다. 그리고 리덕스는 바닐라 자바스크립트와 함께 사용할 수도 있다.

## 이번엔 바닐라 자바스크립트 환경에서 리덕스르 사용하여 기능과 원리를 이해해보자.

## Paecel 로 프로젝트 만들기

프로젝트 구성을 위해 `parcel` 이라는 도구를 사용한다. 이걸 사용하면 쉽고 빠르게 웹 애플리케이션을 구성할 수 있다.

우선 parcel-bundler를 글로벌로 설치해주자.

```jsx
yarn global add parcel-bundler
```

프로젝트 파일을 생성하고, package.json 파일을 생성하자.

```jsx
// 파일 생성
mkdir 프로젝트명

// 해당 프로젝트 이동후
// package.json 파일 생성
yarn init -y
```

index.html 과 index.js 파일을 생성하자.

```html
<html>
  <body>
    <div>바닐라 자바스크립트</div>
    <script src="./index.js"></script>
  </body>
</html>
```

```jsx
console.log('hello parcel');
```

이제 실행시키기 위해 터미널에 다음과 같이 입력해준다.

```jsx
parcel index.html
```

그럼 개발 서버의 주소가 나온다.

![스크린샷 2021-09-06 오전 4.53.02.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd5b15a5-8024-4393-9b4b-dc4b040e3703/스크린샷_2021-09-06_오전_4.53.02.png)

정상 출력되었다면 서버를 끄고 리덕스 모듈도 설치해주자.

```jsx
yarn add redux
```

---

## 간단한 UI 구성하기

간단한 스타일 파일을 하나 작성해보자.

```css
.toggle {
  border: 2px solid #000;
  width: 64px;
  height: 64px;
  border-radius: 50%;
  box-sizing: border-box;
}

.toggle .active {
  background: yellow;
}
```

html 파일도 수정하자.

```html
<html>
  <head>
    <link rel="stylesheet" href="./index.css" />
  </head>
  <body>
    <div class="toggle"></div>
    <hr />
    <h1>0</h1>
    <button id="increase">+1</button>
    <button id="decrease">-1</button>
    <script src="./index.js"></script>
  </body>
</html>
```

![스크린샷 2021-09-06 오전 4.59.15.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2601bb8b-aac6-40cf-b981-1846ea6d64ec/스크린샷_2021-09-06_오전_4.59.15.png)

간단한 ui 끝~

---

## DOM 레퍼런스 만들기

이번엔 UI를 관리할 때 별도의 라이브러리를 사용하지 않기 때문에 DOM을 직접 수정해줘야한다.

자바스크립트 파일 상단에 수정할 DOM 노드를 가리키는 값을 미리 선언해주자.

```jsx
const divToggle = document.querySelector('.toggle');
const counter = document.querySelector('h1');
const btnIncrease = document.querySelector('#increase');
const btnDecrease = document.querySelector('#decrease');
```

---

## 액션 타입과 액션 생성 함수 정의

먼저, 액션 이름을 정의해주자. 액션 이름은 `문자열` 형태로 주로 `대문자` 로 작성한다.

액션 이름은 `고유` 해야한다. 이름이 중복되면 의도하지 않은 결과가 발생할 수도 있다.

```jsx
const TOGGLE_SWITCH = 'TOGGLE_SWITCH';
const INCREASE = 'INCREASE';
const DECREASE = 'DECREASE';
```

다음으로 이 액션 이름을 사용하여 액션 객체를 만드는 `액션 생성 함수` 를 작성해주자.

```jsx
const toggleSwitch = () => ({ type: TOGGLE_SWITCH });
const increase = (difference) => ({ type: INCREASE, difference });
const decrease = () => ({ type: DECREASE });
```

액션 함수엔 항상 `type` 이 명시되어 있어야 하며, 추후 상태를 업데이트할 때 참고하고 싶은 값은 내 맘대로 넣으면 된다.

---

## 초깃값 설정

이제 이 프로젝트에서 사용할 초깃값을 정의해주자. 초깃값의 형태는 자유이다.

숫자일수도, 객체일수도, 문자열일 수도 있다. 이 프로젝트에선 객체 형태로 정의해준다.

```jsx
const divToggle = document.querySelector('.toggle');
const counter = document.querySelector('h1');
const btnIncrease = document.querySelector('#increase');
const btnDecrease = document.querySelector('#decrease');

const TOGGLE_SWITCH = 'TOGGLE_SWITCH';
const INCREASE = 'INCREASE';
const DECREASE = 'DECREASE';

const toggleSwitch = () => ({ type: TOGGLE_SWITCH });
const increase = (difference) => ({ type: INCREASE, difference });
const decrease = () => ({ type: DECREASE });

// 초깃값 설정
const initialState = {
  toggle: false,
  counter: 0,
};
```

---

## 리듀서 함수 정의

리듀서는 변화를 일으키는 함수이다. 함수의 파라미터로는 `state` 와 `action` 값을 받아 온다.

```jsx
function reducer(state = initialState, action) {
  // action.type 에 따라 다른 작업을 처리함
  switch (action.type) {
    case TOGGLE_SWITCH:
      return {
        ...state, // 불변성 유지
        toggle: !state.toggle, // state.toggle의 값 반전
      };
    case INCREASE:
      return {
        ...state,
        counter: state.counter + action.difference,
      };
    case DECREASE:
      return {
        ...state,
        counter: state.counter - 1,
      };
    default:
      return state;
  }
}
```

리듀서 함수가 처음 호출될 때는 state 값이 `undefined` 이다. 해당 값이 undefined 로 주어졌을 때는 initialState를 기본 값으로 설정하기 위해 함수의 파라미터 쪽에 기본 값으로 설정되어 있다.

리듀서에서는 상태의 불변성을 유지하면서 데이터에 변화를 일으켜 주어야 한다.

이 작업을 할 땐 `spread 연선자(...)` 를 사용하면 편리하다. 단, 객체의 구조가 복잡해지면 spread 연산자로 불변성을 지켜주는 것이 번거롭고 가독성도 나빠지기 때문에 `리덕스의 상태`는 `최대한 깊지 않은 구조`로 진행하는 것이 좋다.

해당 구조가 복잡해지거나 배열도 함께 다루는 경우, `immer` 라이브러리를 사용하면 좀더 쉽게 리듀서를 작성할 수 있다.

---

## 스토어 만들기

이제 스토어를 만들어보자. 스토어를 만들 때는 `createStore` 함수를 사용한다.

이 함수를 사용하려면 코드 상단에 `import` 구문을 넣어 리덕스에서 해당 함수를 불러와야 하고, 함수의 파라미터에는 리듀서 함수를 넣어주어야 한다.

```jsx
import { createStore } from 'redux';

// 생략...

const store = createStore(reducer);
```

이제 스토어 내장 함수들을 사용해보자.

---

## reducer 함수 만들기

render 라는 함수를 작성해 보자. 이제부터 만들 render 함수는 상태가 업데이트될 때마다 호출되며, 리액트의 render 함수와는 다르게 이미 html 을 사용하여 만들어진 UI의 속성을 상태에 따라 변경해준다.

```jsx
// 생략...

const store = createStore(reducer);

const render = () => {
  const state = store.getState(); // 현재 상태를 불러온다.
  // 토글 처리
  if (state.toggle) {
    divToggle.classList.add('avtive');
  } else {
    divToggle.classList.remove('active');
  }

  // 카운터 처리
  counter.innerText = state.counter;
};

render();
```

---

## 구독하기

이제 스토어의 상태가 변경될 때마다 render 함수가 호출되도록 해줄 것이다.

이작업은 스토어의 내장 함수 `subscribe` 을 사용하여 수행할 수 있다.

`subscribe` 함수의 파라미터로는 `함수 형태의 값` 을 전달해준다. 이렇게 전달된 함수는 추구 액션이 발생하여 상태가 업데이트될 때마다 호출된다.

```jsx
const listener = () => {
  console.log('상태가 업데이트 됐어요');
};
const unsubscribe = store.subscribe(listener);

unsubscribe(); // 추후 구독을 비활성할 때 함수를 호출
```

이번에는 `subscribe` 함수를 직접 사용하지만, 나중에 프로젝트에 리덕스를 사용할 때는 이 함수를 직접 사용하는 일은 없을 것이다. 왜냐면 컴포넌트에서 리덕스 상태를 조회하는 과정에서 `react-redux` 라는 라이브러리가 이 작업을 대신해 주기 때문이다.

이제 상태가 업데이트될 때마다 render 함수를 호출하도록 코드를 작성해 보자.

```jsx
// ,,, 생략
render();

store.subscribe(render);
```

---

## 액션 발생시키기

액션을 발생시키는 것을 `dispatch(디스패치)` 라고 한다. 디스패치를 할 때는 스토어의 내장함수 `dispatch` 를 사용한다. 파라미터는 액션 객체를 넣어주면 된다.

다음과 같이 각 DOM 요소에 클릭 이벤트를 설정해주자. 이벤트 함수 내부에서는 dispatch 함수를 사용하여 액션을 스토어에 전달해준다.

```jsx
divToggle.onclick = () => {
  store.dispatch(toggleSwitch());
};

btnIncrease.onclick = () => {
  store.dispatch(increase(1));
};

btnDecrease.onclick = () => {
  store.dispatch(decrease());
};
```

이제 클릭할때마다 숫자가 올라가거나 내려가고, 동그라미의 상태가 변화된다.

![스크린샷 2021-09-07 오전 2.37.36.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d4445641-f4c7-4bee-bc70-71bafe33fd63/스크린샷_2021-09-07_오전_2.37.36.png)
