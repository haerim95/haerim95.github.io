---
title: 이벤트 핸들링
date: 2021-08-28
categories: [react]
comments: true
---

---

> Event?

사용자가 웹 브라우저에서 DOM 요소들과 상호 작용하는 것.

## 이벤트를 사용할 때 주의사항 🚨🚨🚨

1. **이벤트 이름은 카멜(Camel) 표기법으로 작성한다.**

   ex) onClick, onChange

<br/>

2. **함수형태의 값을 전달한다.**

   리액트에선 이벤트를 설정할 때, 함수 형태의 객체를 전달한다. 화살표 함수로 바로 전달해도 되고, render() 외부에서 함수를 작성하여 불러와 전달해주어도 된다.

<br/>

3. **DOM 요소에만 이벤트를 설정할 수 있다.**

   컴퍼넌트에는 이벤트를 자체적으로 설정할 수 없다.

   ```jsx
   <MyComponent onClick={doSomething} />
   ```

   이렇게 컴퍼넌트에 onClick 이벤트를 보내주어도 MyComponent 를 클릭할 때마다

   dosomtiong 함수를 실행시키는 것이 아니라, 이름이 onClick인 props를 MyComponent에 전달을 해줄 뿐이다...

   전달받은 props를 컴포넌트 내부의 DOM 이벤트로 설정할 수는 있다.

   ```jsx
   <div onClick={this.props.onClick}></div>
   ```

   <br/>

   ***

   # 예제로 알아보자

---

위의 class 형 컴포넌트에서 작업했던 내용을 함수형 컴포넌트로 똑같이 구현이 가능하다.

## e.target.name을 활용하지 않은 경우

```jsx
import React, { useState } from 'react';

const EventPratice2 = () => {
  // state 설정
  const [username, setUsername] = useState('');
  const [message, setMessage] = useState('');

  // onChange 이벤트 설정
  const onChageUsrname = (e) => setUsername(e.target.value);
  const onChangeMessage = (e) => setMessage(e.target.value);

  const onClick = () => {
    alert(username + ':' + message);
    setUsername('');
    setMessage('');
  };

  const onKeyPress = (e) => {
    if (e.key === 'Enter') {
      onClick();
    }
  };

  return (
    <div>
      <h1>이벤트 핸들러 연습</h1>
      <input
        type='text'
        name='username'
        placeholder='사용자 명'
        value={username}
        onChange={onChageUsrname}
      />

      <input
        type='text'
        name='message'
        placeholder='할 말이 있나요?'
        value={message}
        onChange={onChangeMessage}
        onKeyPress={onKeyPress}
      />
      <button onClick={onClick}>메세지를 보내세요</button>
    </div>
  );
};

export default EventPratice2;
```

다음과 같이 onChange 관련 함수를 두개 만들어서 사용했다.

위와 같은 코드도 나쁘진 않지만, input의 갯수가 많아지면 가독성이 떨어지고 관리도 힘들다.

그럴 땐 e.target.name 을 활용하는게 훨 낫다.

## e.target.name을 활용한 경우. && useState 객체로 변경한 경우

```jsx
import React, { useState } from 'react';

const EventPratice2 = () => {
  // state 설정
  const [form, setForm] = useState({
    username: '',
    messgae: '',
  });

  const { username, message } = form;

  const onChange = (e) => {
    const nextForm = {
      ...form, // 기존의 form 내용을 이 자리에 복사한다.
      [e.target.name]: e.target.value, // 원하는 값을 덮어 씌운다.
    };
    setForm(nextForm);
  };

  const onClick = () => {
    alert(username + ':' + message);
    setForm({
      username: '',
      messgae: '',
    });
  };

  const onKeyPress = (e) => {
    if (e.key === 'Enter') {
      onClick();
    }
  };

  return (
    <div>
      <h1>이벤트 핸들러 연습</h1>
      <input
        type='text'
        name='username'
        placeholder='사용자 명'
        value={username}
        onChange={onChange}
      />

      <input
        type='text'
        name='message'
        placeholder='할 말이 있나요?'
        value={message}
        onChange={onChange}
        onKeyPress={onKeyPress}
      />
      <button onClick={onClick}>메세지를 보내세요</button>
    </div>
  );
};

export default EventPratice2;
```

---

## 정리

리액트에서 이벤트를 다루는 것은 제이쿼리나 순수 자바스크립트를 사용한 웹 애플리케이션에서 이벤트를 다루는 것과 유사하다. 리액트의 장점은 자바스크립트에 익숙하다면 쉽게 활용이 가능하다는 것이다.

그리고 클래스형 컴포넌트로 할 수 있는 대부분의 작업은 함수형 컴포넌트에서도 작업이 가능하다.

해당 예제에선 함수형 컴퍼넌트에선 useState 객체를 사용하는 방법을 이용하였는데,

이는 useReducer와 커스텀 Hooks 와 함께 사용하면 훨씬 편하게 할 수 있다.
