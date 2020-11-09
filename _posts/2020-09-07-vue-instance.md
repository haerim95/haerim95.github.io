---
title: vue 인스턴스
date: 2020-09-07
categories: [vue]
comments: true
---

---
# Vue 인스턴스

vue 애플리케이션은 Vue 함수를 사용하여 새로운 Vue 인스턴스를 만드는 것부터 시작한다.

```vue
    import Vue from 'vue'
    import App from './App.vue'

    new Vue({
        el: '#app',
        component: { App },
        template: '<App/>'
    });
```

vue 애플리케이션의 루트는 위와 같은 Vue 인스턴스로 구성된다.  
이 루트를 기반으로 component들이 트리 형태로 위치한다.

<div style="text-align: center; margin-bottom:1em;">
    <img src="./../public/img/componentEx.png">
    <span style="display: inline-block; width: 100%; color: #999; font-size: .8em;">[그림] component 구조 도식화</span>
</div>

> component란? 🤔
>> 하나의 블록 안에 다른 블록들이 들어가 있는 부모-자식 구조다.
>> 컴포넌트는 트리 구조를 형성한다.
>> Vue 컴포넌트는 Vue 인스턴스를 가질 수 있다. 그러므로 인스턴스가 제공해주는 `모든 기능`을 전부 가지고 있다.


# Vue 인스턴스 옵션

Vue 인스턴스 및 Vue 인스턴스가 확장된 컴포넌트에서 사용할 수 있는 데이터 기능 및 옵션

## 1. data 속성

```vue
    // 뷰 인스턴스
    const data = { a : 1};
    new Vue({
        data : data
    })

    //뷰 컨포넌트
    const myComponent = Vue.extend({
        name : 'MyComponent',
        data(){
            return { a : 1 };
        }
    })
```
<div style="text-align: center; color: #999; font-size: .8em; margin-bottom: 1em;">
    <span>[코드] data 속성 선언법</span>
</div>

<p class="message">
    data 속성은 <span class="color2">반응형 모델</span>을 선언할때 사용한다. <br/>
    반응형 모델이란, 어떤 액션으로 인해 값이 변경되었을 때 javascript, 사용자 view 에서 보이는 값도 연동되어 변경되는 것을 의미한다. <br/>
    인스턴스가 생성된 후 <span class="color3">this.$data</span>로 접근할 수 있다.
</p>

vue 인스턴스는 데이터 객체 내부의 값을 프록싱(Proxying) 하므로 `this.$data` 와 `this.a` 는 같은 값이다.

> 프록시, 프록싱? 🤔 
>> 프락시 서버는 사용자가 요청을 보내고자 했던 서버로 대신 요청을 보내주는 역할을 한다. 접근하고자 하는 대상에 직접 접근하지 않더라도 프록시 구현체가 대상에 접근함으로써 접근 과정의 일부를 대신 처리해준다.
>> 위에 설명한 `this.a(Vue 인스턴스)`에 접근함으로써 `this.$data.a`에 담겨있는 값에 접근할 수 있으므로 `this.$data` 내부의 값에 `this`가 대신 접근해준다 볼 수 있다.
>> 즉 `this.$data`의 값을 `this`가 프록싱 해주고 있는 거다.

data 속성 선언 코드를 보면 Vue 인스턴스에서와 Vue 컴포넌트에서의 문법이 다른 것을 알 수 있다.  

🔥 data 속성은 반드시 <b>Object</b> 지료형을 반환하는 함수로 선언되어야 한다. <br/>
javascript Object 자료형은 메모리에 저장된 값을 직접 가져오는 호출이 아닌 메모리에 저장된 주소 값을 가져오는 `참조에 의한 호출`이다. <br/>
따라서 data 속성을 일반 객체로 선언한다면 같은 주소를 참조하는 데이터들을 컴포넌트들이 공유하게 된다.

<p class="color2"><b>여러개의 컴포넌트 인스턴스들이 같은 객체를 참조해서 상태가 공유되는 것을 회피하기 위해 객체를 return 하는 함수를 써야하는 것이다.</b></p>

> 값에 의한 호출, 참조에 의한 호출 💡
>> 프로그래밍 언어에서 사용되는 호출 방식들이다. 
>> 어떤 함수에 값이 인자로 주어지거나 변수 어떤 값을 변수에 할당할 때 어떤 방식으로 호출되어 할당하느냐를 의미한다.
>>> 이부분은 C언어 이기때문에 나중에 따로 포스팅을 하겠다. 궁금하다면 [호출 바로가기]("https://programist.tistory.com/entry/C-%EC%96%B8%EC%96%B4-Call-by-Value%EA%B0%92%EC%97%90-%EC%9D%98%ED%95%9C-%ED%98%B8%EC%B6%9C-Call-by-Reference%EC%B0%B8%EC%A1%B0%EC%97%90-%EC%9D%98%ED%95%9C-%ED%98%B8%EC%B6%9C%EC%9D%98-%EC%9D%B4%ED%95%B4") 에서 글을 읽어보자

---

## 2. Props 속성

```vue
    // String 배열
    Vue.component('MyComponent', {
        // 단순한 구문으로 표현하기
        props: ['size', 'myMessage']
    });

    //객체타입 지정
    Vue.component('MyComponent2', {
        props: {
            //타입만 체크할 경우
            height: Number,
            //타입 체크와 유효성 검사, 기본값 등을 추가로 지정할 경우
            width: {
                type: Numberm,
                required: true,
                default: 1,
                validator(value){
                    return value > 0
                }
            }
        }
    })

```

```vue
    <my-component :width="3" :height="3"></mycomponent>
```
<div style="text-align: center; color: #999; font-size: .8em; margin-bottom: 1em;">
    <span>[코드1] props 속성 선언법</span>
</div>

<p class="message">
    props 속성은 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하기 위해 사용된다. <br/>
    원래 모든 컴포넌트 인스턴스에는 각자의 자체 격리된 범위(scope)가 있기때문에 하위 컴포넌트의 템플릿에서는 상위 데이터를 직접 참조할 수 없다. 그래서 props를 사용하여 하위 컴포넌트로 데이터를 전달하는 것이다.
</p>

> 스코프(Scope)? 🤔
>> 변수에 접근할 수 있는 범위
>> 스코프 종류에 따라 변수, 함수, 코드 등의 유효 범위가 달라질 수 있다. 관련 포스팅은 따로 할 예정이다.

그렇지만 상단의 [코드1] 은 동적(반응형) 바인딩이 아니라 상위 컴포넌트의 데이터가 변해도 하위 컴포넌트에는 반영되지 않는다. 만약 하위 컴포넌트 내부에서 props 데이터를 다뤄야 하는 경우 `data` 속성 내에서 해당 `prop`을 `this`로 접근하여 참조하도록 다시 선언하여 사용하거나 `emit`을 통해 부모 컴포넌트의 데이터를 변경해줘야 한다. (emit에 대해선 추후에 포스팅할 예정이다.)

```vue
Vue.component('MyComponent2', {
    props: {
        height : Number,
    },
    data(){
        return{
            dataHeight: this.height
        }
    }
})
```
<div style="text-align: center; color: #999; font-size: .8em; margin-bottom: 1em;">
    <span>[코드2] props 속성 동적(반응형) 사용법</span>
</div>

## 3. computed 속성

<p class="message">
    computed는 계산된 데이터다. template 안에 표현식을 넣는 방법도 있지만, 복잡한 연산을 template 안에서 하다보면 유지보수하기 어려워진다. 복잡한 로직이라면 complate 속성을 사용하는게 좋다.
</p>

```vue
    // template 안에 표현식 사용
    <div id="example">
        {{ message.split('').reverse().join('') }}
    </div>
```
<div style="text-align: center; color: #999; font-size: .8em; margin-bottom: 1em;">
    <span>[코드1] 템플릿 내부 표현식</span>
</div>

```vue
    // computed 사용
    <div id="example">
        <p>원본 메세지 : "{{ message }}"</p>
        <p>역순 변환 메세지 : "{{ reversedMessage }}"</p>
    </div>

    var vm = new Vue({
        el: '#example',
        data: {
            message: '안녕하세요'
        },
        computed: {
            //계산된 getter
            reversedMessage: function(){
                // this는 vm 인스턴스를 가리킵니다.
                return this.massage.split('').reverse().join('')
            }
        }
    })
```
<div style="text-align: center; color: #999; font-size: .8em; margin-bottom: 1em;">
    <span>[코드2] computed 사용 표현식</span>
</div>


> 예제 결과
>>  원본 메세지 : 안녕하세요  
>> 역순 변환 메세지 : 요세하녕안

위의 코드에서 `data` 속성인 `message`의 값을 변경한다면 `computed` 속성인 `reversedMessage`의 값도 변경된 `message` 값으로 함께 변경된다. 즉, `computed`는 `data` 값에 의존적이다.  

computed의 장점은 종속 대상을 따라 저장(캐싱)된다는 것이다. 즉 위 코드에서 `message` 값이 변경되지 않는 한 `reversedMessage`를 여러번 요청해도 다시 계산하지 않고 이미 계산되어 있던 결과(저장된 값)를 즉시 반환한다.  

즉, 쓸데없이 실행되지 않기 때문에 속도가 빨라진다.  또한 자신과 관련이 없다면 재실행 되지 않는다는 것이다.


## 4. method 속성

<p class="message">
    기본적으로 computed와 하는 일이 동일하다. 그러나 method는 template에서 호출시 ()를 적어주어야 한다.
</p>

```vue

<p id="example">뒤집힌 메세지 : "{{ reverseMessage() }}" </p>

 var vm = new Vue({
        el: '#example',
        data: {
            message: '안녕하세요'
        },
      method : {
          reverseMessage: function(){
              return this.message.split('').reverse().join()
          }
      }
    })

```

method는 computed와 하는 일이 기본적으로 같지만, computed와 다르게 method는 캐싱이라는 개념이 없기 때문에 매번 다시 렌더링된다.


> method 🥊 VS 🥊 computed 
>> 둘은 vue 안에서 함수를 정의하고, 데이터가 변동됨에 따라 안에 있는 함수를 재호출한다.  
>> 둘의 차이점은 데이터가 변됭되는 것과 변동되지 않는 것에 있다.  
>> 만약 데이터가 자주 변동된다면 method, 그렇지 않다면 계속 캐시를 저장하는 computed를 사용하는 게 좋다.


## 5. watch 속성

<p class="message">
    watch 속성은 데이터 변화를 감지하여 자동으로 특정 로직을 수행한다. <br/>
    computed와 유사하지만 computed는 내장 api를 사용하는 간단한 연산정도에 적합하고 <br/> 
    watch는 데이터 호출과 같이 시간이 상대적으로 많이 소모되는 비동기 처리에 적합하다.
</p>

```vue

<div id="app">
  <input type="text" v-model="message">
  {{message}}
</div>

var vm = new Vue({
  el: '#app',
  data: {
    message: '메세지!'
  },
  watch:{
    message: function(data){
      console.log('데이터가 갱신되었습니다. :' , data )
    }
  }
})

```
<div style="text-align: center; color: #999; font-size: .8em; margin-bottom: 1em;">
    <span>[코드2] watch 사용 표현식</span>
</div>

watch는 감시할 데이터를 지정하고, 그 데이터가 변경되면 이런 함수를 실행하라는 방식으로 `명령형 프로그래밍` 방식이다.  


> watch 🥊 VS 🥊 computed  
>> watch는 캐싱되지 않고 변수가 Obhect라도 deep 옵션을 통해 내부를 깊게 감시할 수 있다. 따라서 그 값을 사용하여 API 통신을 수행해 모델을 서버로부터 다시 받아와야 한다든가 하는 특정한 로직을 수행할 때 적합하다.  
>> 반면 computed는 한번 저장된 값은 캐싱되므로 어떤 변수들을 사용해 계산하기에 적합하다.



