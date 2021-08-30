---
title: State2
date: 2021-08-30
categories: [react]
comments: true
---

---

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
