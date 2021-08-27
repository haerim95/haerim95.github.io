---
title: State
date: 2021-02-16
categories: [react]
comments: true
---

---

> State 란?

`component 내부에서 변경할 수 있는 값` 을 의미한다. 부모 컴포넌트는 자식 컴포넌트에게 `props` 를 전달해 주지만, 자식 컴포넌트는 부모에게 받은 `props` 를 `읽기 전용` 으로 밖에 사용하지 못한다. 즉, 수정을 하지 못한다는 뜻이다.

`props` 를 변경해주려면 부모 컴포넌트에서 변경을 해주어야 하는데, 그러면 너무 번거로우니 `state` 를 통해 직접 변경을 하는 것이다. 내부에서 선언하여 값을 변경할 수 있다.

`state` 는 두 가지 종류가 있다. 하나는 `클래스형 컴포넌트 state` 나머지 하나는 `함수형 컴포넌트 state` 이다.

---

## 클래스형 컴포넌트 State

```jsx
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      number: 0,
    };
  }

  render() {
    const { number } = this.state;
    return (
      <div>
        <h1>{number}</h1>
        <button
          onClick={() => {
            this.setState({ number: number + 1 });
          }}
        >
          +1
        </button>
      </div>
    );
  }
}

export default Counter;
```

### 1. constructor 메서드

```jsx
constructor(props){
	super(props);
}
```

생성자 메서드이다. 클래스형 컴포넌트에선 반드시 먼저 `super(props)` 를 호출해주어야 한다. 이 함수가 호출되어야 현재 클래스형 컴포넌트가 상속받고 있는 `react의 Component 클래스` 가 지닌 생성자 함수를 호출해준다. (리액트 안 내장 함수)

`super()` 메소드를 호출해주어서 부모클래스에 `props` 를 전달해주어야 하기 때문이다.

### 2. State 초기값 설정

```jsx
this.state = {
  number: 0,
};
```

`this.state` 값에 초기값을 생성해준다. state는 `객체형` 이여야 한다.

### 3. render 함수 코드

```jsx
render(){
	const { number } = this.state;
	return(
		<div>
			<h1>{number}</h1>
			<button onClick={()=>{
          this.setState({ number: number + 1 })
        }}>+1</button>
		</div>
	)
}
```

3-1. state를 조회할때는 this.state로 조회한다.

3-2. `setState` :

state에 있는 값을 변경하기 위해선 `this.setState` 를 무조건 거쳐야한다. 이 함수가 호출되면 컴포넌트는 리렌더링 된다. `setState` 는 객체로 전달되는 값만 업데이트 해준다.

3-3. 리액트 이벤트 시스템 (onClick Event) 는 버튼이 클릭 될 때 호출할 함수를 설정해준다.

---

# State 객체 사본 (state 사용시 주의사항)

> state의 값을 바꾸어야할 때는 `setState` 혹은 `useState` 를 통해 전달받은 `새터함수` 를 사용

### 🤔 배열이나 객체를 업데이트 하는 경우는??

이 경우는 배열이나 객체의 `사본` 을 만들고, `사본` 을 `업데이트` 한 후, 그 `사본`의 상태를 `setState` 혹은 `새터함수` 를 통해 업데이트한다.

```jsx
// 객체 다루기
const object = { a: 1, b: 2, c: 3 };
const nextObject = { ...object, b: 2 };

// 배열 다루기
const array = [
  { id: 1, value: true },
  { id: 2, value: true },
  { id: 3, value: false },
];
let nextArray = array.concat({ id: 4 }); // 항목 추가
nextArray.filter((item) => item.id !== 2); // 아이디가 2인 항목 제거
nextArray.map((item) => (item.id === 1 ? { ...item, value: false } : item));
```

객체에 대한 `사본` 을 만들 때에는 `spread 연산자` 라고 불리는 `...` 을 사용하여 처리한다.

배열에 대한 `사본` 을 만들 때에는 `배열의 내장함수` 를 활용한다.

(배열의 내장 함수 : `forEach`, `map` , `filter`, `reduce`, `splice`, `slice`, `shift`, `pop`, `unshift`, `push`, `indexOf`, `findIndex`, `find`, `join` )

---

## 정리 📝

`props` 와 `state` 는 둘 다 컴포넌트에서 사용하거나 렌더링할 데이터를 담고 있어서 비슷해 보일 수 있지만, 역할이 다르다.

`props` : 부모 컴퍼넌트가 설정.

`state` : 컴퍼넌트 자체적으로 지닌 값.

`props`는 자식 컴퍼넌트 내부에서 값을 스스로 업데이트 하지 못하지만, `state`는 내부에서 값을 업데이트 할 수 있다.

`props` 를 사용한다고 해서 값이 무조건 고정적이지는 않다.

부모 컴퍼넌트의 `state` 를 자식 컴포넌트의 `props` 로 전달하고, 자식 컴포넌트에서 특정 이벤트가 발생할 때, 부모 컴퍼넌트의 메서드를 호출하면 `prop` 도 유동적으로 사용이 가능하다.

<div class="imgWrap">
    <figure>
        <img src="/assets/img/post/react/stateExample.png">
    </figure>
</div>
