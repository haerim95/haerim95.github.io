---
title: ref-Dom
date: 2021-09-03
categories: [react]
comments: true
---

---

일반 HTML에서 id를 이용하여 DOM에 이름을 다는 것처럼 (`<div id="imId"></div>`) 리액트 프로젝트 내부에서 DOM에 이름을 다는 방법이 있다. 바로 `ref` 이다.

→ 물론 리액트 컴포넌트 안에서도 id 값을 사용할 수 있지만, 권장하지는 않는다.

`id는 유일`해야 하는데 컴포넌트를 재사용하다보면 여러개의 id가 생기는 일이 발생한다.

---

# 🕵️‍♀️ ref(reference)의 모든것...

### ref는 어떤 상황에 사용하는가?

**DOM을 직접적으로 건드려야 할 때** 사용한다.

`state` 로 해결이 가능한 부분도 있지만, 가끔 `state` 로만으로는 해결할 수 없는 기능도 잇다. 어떨때일까?

다음과 같을 때 사용한다.

- 특정 input에 focus 주기
- 스크롤 박스 조작
- Canvas 요소에 그림 그리기 등

그런데, `state` 만으로도 해결이 가능한 부분이 있다고 했다. 밑에 예제 코드가 바로 그런 예이다.

해당 예제 코드는 [class 형 컴포넌트] 로 작성되었다.

- click시 input 창 결과 값 다르게 해주기

  ```jsx
  import React, { Component } from 'react';
  import './ValidationSample.css';

  class ValidationSample extends Component {

    state = {
      password: '',
      clicked: false,
      validated: false
    }

    handleChange = (e) => { // input에 값 입력시 password 값 업데이트
      this.setState({
        password: e.target.value
      });
    }

    handleButtonClick = () => { // 버튼 클릭시
      this.setState({
        clicked: true, // cliked는 참이 되고
        validated: this.state.password === '0000' // validated 값을 검증 결과로 설정
      })
    }

    render() {
      return (
        <div>
          <input
            type="password"
            value={this.state.password}
            onChange={this.handleChange}
  					{/* 검증 결과에 따라 sucess 혹은 failure 값 설정 */}
            className={this.state.clicked ? (this.state.validated ? 'success' : 'failure') : ''}
          />
          <button onClick={this.handleButtonClick}>검증하기</button>
        </div>
      );
    }
  }

  export default ValidationSample;
  ```

  ```css
  .success {
    background-color: lightgreen;
  }
  .failure {
    background-color: lightcoral;
  }
  ```

---

state 를 이용한 제어를 해보았으니 이제 ref 를 이용하여 제어를 해보자.

## ref 사용

ref를 사용하는 방법은 `두 가지` 이다.

### 1. 콜백 함수를 통한 ref 설정

ref를 만드는 가장 기존벅은 방법은 `콜백 함수` 를 사용하는 것이다. ref를 달고자 하는 요소에 ref라는 콜백 함수를 props로 전달해주면 된다. 이 콜백 함수는 ref의 값을 `파라미터` 로 전달받는다. 그리고 함수 내부에서 파라미터로 받은 ref를 컴포넌트의 멤버 변수로 설정해 준다.

```jsx
<input
  ref={(ref) => {
    this.input = ref;
  }}
/>
```

다음과 같이 사용하면 된다.

`this.input` 은 input 요소의 DOM 을 가리킨다. ref의 이름은 자유롭게 지어주면 된다.

`this.input` 이 아닌 `this.pizza` 로 해주어도 된다.

### 2. createRef를 통한 ref 설정

이 방법은 리액트에 내장되어 있는 `createRef` 라는 함수를 사용하는 것이다.

이를 사용하면 더 적은 코드로 쉽게 사용이 가능하다.

```jsx
import React, { Component } from 'react';

class RefSample extends Component {
  // 변수로 React.createRef() 담아주기
  input = React.createRef();

  handleFocus = () => {
    this.input.current.focus();
  };

  render() {
    return (
      <div>
        {/* 해당 변수를 ref를 달고자하는 요소에 ref props로 넣어줌 */}
        <input ref={this.input} />
      </div>
    );
  }
}

export default RefSample;
```

이렇게 설정한 뒤, 나중에 ref를 설정해준 DOM에 접근하려면 `this.input.current`를 조회하면 된다.

콜백함수와 다른 점, 눈치챘지? 저렇게 뒷부분에 `.current` 를 넣어 주어야 한다는 점이다.

---

# Component에 ref 달기

> 리액트에서는 컴포넌트에서도 ref를 달 수 있다.
> 이 방법은 주로 컴포넌트 내부에 있는 DOM 을 컴포넌트 외부에서 사용할 때 사용한다. 컴포넌트에서 ref를 다는 방법과 DOM에서 ref를 다는 방법은 동일하다.

### 사용법

```jsx
<MyComponent ref={(ref) => {this.myComponent=ref} />
```

이렇게하면 MyComponent 내부의 메서드 및 멤버 변수에도 접근할 수 있다.

즉, 내부의 ref에도 접근이 가능하다. (ex. myComponent.handleClick, myComponent.input 등..)

예제를 사용하며 더 알아보자.

스크롤 박스가 있는 컴포넌트를 하나 만들고

스크롤바를 아래(최하단)로 내리는 작업을 부모 컴포넌트에서 실행해보자.

```jsx
import React, { Component } from 'react';

class ScrollBox extends Component {
  render() {
    const style = {
      border: '1px solid black',
      height: '300px',
      width: '300px',
      overflow: 'auto',
      position: 'relative',
    };

    const innerStyle = {
      width: '100%',
      height: '650px',
      background: 'linear-gradient(white, black)',
    };

    return (
      <div
        style={style}
        ref={(ref) => {
          this.box = ref;
        }}
      >
        <div style={innerStyle} />
      </div>
    );
  }
}

export default ScrollBox;
```

우선, 스크롤 박스 컴포넌트를 만들어주었다.

이제 잘 나오는지 확인해보자.

```jsx
import React, { Component } from 'react';

import ScrollBox from './ScrollBox';

class App extends Component {
  render() {
    return (
      <>
        <ScrollBox />
      </>
    );
  }
}

export default App;
```

그럼 스크롤 박스가 잘 나올 것이다.

```jsx
import React, { Component } from 'react';

class ScrollBox extends Component {
  // 스크롤바 아래쪽으로 내리는 메서드
  scrollToBottom = () => {
    // scrollHeight : 스크롤이 있는 박스 안의 div 높이 (650)
    // clientHeight : 스크롤이 있는 박스의 높이 (300)
    const { scrollHeight, clientHeight } = this.box;
    this.box.scrollTop = scrollHeight - clientHeight;
    // scrollTop : 세로 스크롤 바 위치 (0~350)
  };

  render() {
    // 생략....
  }
}

export default ScrollBox;
```

이 메서드는 부모 컴퍼넌트인 App 컴퍼넌트에서 ref를 이용하여 사용할 수 있다.

```jsx
import React, { Component } from 'react';

import ScrollBox from './ScrollBox';

class App extends Component {
  render() {
    return (
      <>
        <ScrollBox ref={(ref) => (this.ScrollBox = ref)} />

        {/* 화살표 함수를 이용해 내부에서 메서드 실행 */}
        <button onClick={() => this.ScrollBox.scrollToBottom()}>
          맨 밑으로
        </button>
      </>
    );
  }
}

export default App;
```

버튼을 누르면 ScrollBox 컴퍼넌트의 ref를 타고 이 컴퍼넌트 안에 생성해준 scrollToBottom 을 실행하게끔 했다.

여기서 주의할 점은, 컴포넌트가 처음 렌더링 될때는 `this.scrollBox` 의 값이 `undefined` 라는 점이다.

그래서 문법상으로는 onClick={ this.scrollBox.scrollBottom } 형식으로 써도 틀리지는 않지만, 이 과정에서 값을 읽어올때 `undefined` 이기 때문에 오류가 발생한다.

그래서 화살표 함수 문법으로 새로운 함수를 만들고, 그 내부에서 `this.scrollToBottom` 메서드를 실행하면 이미 한 번 렌더링을 해서 this.scrollBox를 설정했기 때문에, 버튼을 누를때 `this.ScrollBox.scrollToBottom` 의 값을 읽어올 수 있는 것이다.

버튼을 누르면 정상적으로 최하단으로 이동이 가능할 것이다.

---

# 정리 📝

우선, ref는 컴포넌트 내부에서 DOM에 직접 접근해야 할 때에 사용한다.

사용하기 전에 ref를 사용하지 않고 기능 구현이 가능한지 고려하고 활용하는 것이 좋다.

여기서 **조심할 점**은 서로 다른 컴포넌트 끼리 교류를 할 때 ref를 사용하지 말아야하는 점이다.

물론, 구현은 가능하다. 그렇지만 컴포넌트1에 ref를 달고 그 ref를 다른 컴포넌트2로 이동시키고, 컴포넌트 1에서 전달받은 컴포넌트 메서드를 실행하게 된다면 이는 어긋난 리액트 설계이다.

위처럼 코딩을하면 앱 규모가 커질수록 스파게티 코드가 될 가능성이 높아진다. 컴포넌트 끼리 데이터 교류는 무조건 부모 ↔ 자식 흐름으로 교류하는 것이 맞다.

이는 나중에 리덕스 혹은 context API 를 이용해 효육적인 교류가 가능해진다 🙂

함수형 컴포넌트에선 `useRef` 라는 Hook 을 이용한다.
