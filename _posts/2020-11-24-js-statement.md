---
title: Javascript 문장(Statement)
date: 2020-11-24
categories: [javascript]
comments: true
---

---

# Javascript 문장

## 1. if

* 형태
    if(표현식) 문장1
    if(표현식) 문장1 else 문장2
* 조건에 따른 처리
    1. 표현식 평가
    2. 평가 결과 `true` / `false` 로 변환
    3. `true`면 문장 1 실행
    4. `false`면 문장 2 실행
    ```js
    var a = 1, b = 1;
    if(a === b){ //문장 1
        log("블록사용");
    }
    // 결과 값 : 불록사용
    ```
    ```js
    var a = 1, b = 2;
    if(a === b){
        //문장 1
        log("블록사용, true");
    }else{
        //문장 2
        log("블록사용, false");
    }
    //결과 값 : 블록사용, false
    ```

---

## 2. debugger

* 브라우저 개발자 도구 창이 열려있을 때만 멈춘다.
* ES5부터 지원한다.
* break point를 주의 깊게 보자. 해당 버그로 이동시켜준다.
    
---

## 3. While

* 형태 : while(표현식)
* 표현식의 평가결과가 `false`가 될 때까지 문장을 반복하여 실행한다.
* 반복이 종료되는 조건이 필요하다.

```js
var k = 1;
while(k < 3){
    log(k);
    k++; 
}; 
//결과 값 : 1
//        2
```
> k는 1이므로 평가결과가 true로 log에 1이 입력된다.  
> 그 후 k++로 인해 k+1 이 되고 k는 2가 된다.  
> k는 2 이므로 평가결과가 true가 되어 logdp 2가 입력된다.  
> 반복해서 k가 3이 되면 평가결과가 false가 되므로 문장이 종료된다.

---

## 4. do ~ while

* 형태 : do 문장 while(표현식)
* 처리 방법은 `while`문과 같다. <span class="color2">단, do 문을 먼저 실행한다.</span>

```js
var k = 0;
do{
    log("do :", k);
    k++;
}while(k < 3){
    log("while :", k);
};
// 결과 값
// do: 0
// do : 1
// do : 2
// while: 3
```
> 제일 먼저 `do`문을 실행한다. do: 0이 출력된다.  
> `while` 문의 표햔식을 평가한다. `true`일시 `do`문을 실행한다. -> 반복  
> `false`일시 `while`문의 블록을 실행한다.