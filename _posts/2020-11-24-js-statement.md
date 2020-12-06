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

---

## for()

* 형태 : for (초기값 opt; 비교 opt; 증감 opt)
    (괄호 안은 옵션이기 때문에 안 써도 무방하다.)
* 2번째에 있는 `비교 효현식`이 `true`일 동안 반복 실행한다.
```js
    for(var k = 0; k < 2; k++){
        log(k);
    }
    // 결과 값 : 0
    // 1
```
[해설]
1. var k = 0;
    초기값을 할당한다. 처음 한 번만 실행된다.
2. k < 2;
    비교 결과가 `true`이면 for()블록 코드를 실행한다.
3. 처음은 k가 0 이므로 `true`가 되어 블록에 console을 실행한다.
4. k++ 로 넘어가서 k 변수값을 1 증가시킨다.
5. 다시 2번부터 실행된다. k가 2가 되면 `false`가 되어 실행 종료된다.

### for() 옵션(opt)

* for (초기값 opt; 비교 opt; 증감 opt)
* opt는 생략 가능하다.
    * 증감 생략
    ```js
    for(var k = 0; k < 3;){
        log(k);
        k++
    }
    //결과 값 : 0, 1, 2
    ```
    증감식 옵션이 아닌 블록에서 변수 값을 증가 시켰다.

    * 초기값과 증감 생략
    ```js
        var k = 0;
        for(; k < 3){
            log(k);
            k++
        }
        // 결과 값 : 0,1,2
    ```
    1. 초기값은 작성하지 않아도 옵션에 ;를 적어줘야 한다.
    2. for문 앞에 변수 할당
    3. 증감식은 블록에서 실행

    * 비교와 증감 생략
    ```js
        for(var k = 0; ;){
            log(k);
            k++;
            if(k < 2){
                break;
            };
        };
    ```
    옵션을 생략하더라고 ;는 작성해야한다.  
    프로그램 코드는 심플한게 최고이기 때문에 이런 코드 방식은 지양하자.

    * 모두 생략
    ```js
    var k = 0;
    for(;;){
        log(k);
        if(k<2){
            break;;
        };
        k++;
    }
    ```
    이렇게 모두 생략해서 작성해도 되지만,  
    이런방식은 지양하자.

### for() coding test
> 조건  
> 1~50까지 수에서 짝수를 정렬하고 짝수끼리의 합을 구하라  
> 1~50까지 수에서 홀수를 정렬하고 홀수끼리의 합을 구하라

```html
<p id="even"></p>
<p id="odd"></p>

```

```js
//짝수
var even = 0;
for(var i = 1; i <= 50; i++){
  if(i % 2 === 0){
    even += i;

    document.write(i + '<br/>'); // 짝수 리스트 출력
    document.getElementById('even').innerHTML = even; //짝수의 합 출력
  }
};

//홀수
var odd = 0;
for(i = 1; i <= 50; i++){
  if(i % 2 != 0){
    odd += i;
   document.write(i + '<br/>'); // 홀수 리스트 출력
   document.getElementById('odd').innerHTML = odd; // 홀수의 합 출력
  }
}

```

## break;

* 형태 : break;
        break 식별자;
* 반복문을 종료시킬 때 사용한다.
```js
var k = 0, m = 0;
while(k < 3){
    m++;
    if(m === 2){
        break;
    };
    log(m)
};
//실행결과 : 1
```
변수 m이 1씩 증가하여 if문 조건에 맞는 2가 되었을때 break 문이 사용되며 반복이 중지된다.  
이때 k의 값이 3보다 작아도 `break`가 실행됐기 때문에 더 반복하지 않고 끝난다.

* `for`, `for~in`, `while`, `do~while`, `swich` 에서 사용된다.

---

## continue

* 형태 : continue;
        continue 식별자;
* 반복문의 처음으로 분기된다.

```js
for(var k = 0; k < 5; k++){
    if(k === 2 || k === 3){
        continue;
    };
    log(k);
}
// 실행 값 : 0, 1, 4
```
1. k가 2 또는 3이면 continue문을 실행한다.
2. continue가 실행되면 consol.log(k)를 실행하지 않고 바로 k++로 간다.

* `for`, `for~in`, `while`, `do~while`에서 사용된다.

---

## swich

* 형태 : 
    ```js
    swich(표현식){
        case 표현식 : 문장 리스트 opt
        default : 문장 리스트 opt
    };
    ```
* switch 표현식의 평가 값과 일치하는 case문을 수행한다.
```js
var exp = 1;
switch(exp){
    case 1:
    log(100);
    case 2:
    logo(200);
};

// 실행 값 : 100, 200
```
`switch`의 평가값은 exp로 1이다. 그러므로 case 1을 수행하여 100이 나온다.  
주의할 점은 case1 아래의 모든 문장도 수행된다는 점이다.  
이를 방지하려면 `break`를 작성해야한다.

* 일치하는 case가 없을 땐 `default` 실행
```js
var exp = 7, value;
switch(exp){
    case 1:
        value = 100;
    default:
        value = 700;
    case 2:
        value = 200;
};
//결과 값 : 200
log(value);
```
`switch`의 값이 7이므로 일치하는 `case`가 없기 때문에  
`default` 값을 실행한다. `default` 뒤에 이어진 `case2`도 이어 실행되기 때문에 값은 200이 된다.
* OR(||) 형태
```js
var exp = 3;
switch(exp){
    case 2:
    case 3:
        log(100);
};
//실행 값 : 100
```
exp 값이 2 또는 3이면 `case` 가 실행된다.

---

## try-catch

* 형태 :
    try 블록 catch(식별자) 블록  
    try 블록 finally 블록  
    try 블록 catch(식별자) 블록 finally 블록
* `try`문에서 예외 발생을 인식한다.
* 예외가 발생하면 `catch` 블록을 실행한다.
```js
var value;
try{
    value = ball;
}catch(error){
    log("catch 실행");
};
// 실행 값 : catch 실행
```
에러가 발생할 가능성이 있으면 반드시 try-catch를 사용해야 한다.
try 블록에서 ball 변수가 존재하지 않으므로 에러가 발생한다.  
에러가 발생하면 catch(error) 블록을 실행한다.

* `finally` 블록은 예외 발생과 관계없이 실행된다.
```js
var sports;
try{
    sports = ball;
    }catch(error){
        log("catch 실행");
    }finally{
        log("finally 실행");
    };
    //실행 값 : catch 실행, finally 실행
```
에러가 발생해 `catch` 블록을 실행한 후에 `finally` 블록을  실행한다.
만약 에러가 나지 않아도 `finally` 블록은 실행된다.

---

## throw

* 형태 : `throw` 표현식;
* 명시적으로 예외를 발생시킨다.
* 예외가 발생하면 catch를 실행한다.
```js
try{
    throw "오류 발생시킴";
    var sports = "스포츠";
}catch(error){
    log(error);
    log(sports);
}
// 실행 값 : 오류 발생시킴, undefined
```
`throw` 표현식에 문자열을 작성했다.  
`throw`를 만나면 에러가 발생하고 catch 블록이 실행된다.
이때, throw 아래의 코드는 몇 줄이 있든 실행되지 않는다.  
따라서 sports 변수의 값이 `undefined`가 된것이다.

```js
try{
    throw{
        msg: "예외 발생시킴",
        bigo: "임의의 이름 사용"
    };
}catch(error){
    log(error.msg);
    log(error.bigo);
};
// 실행 값 : 예외 발생시킴, 임의의 이름 사용
```

```js
try{
    throw new Error("예외 발생시킴");
}catch(error){
    log(error.message);
};
// 실행 값 : 예외 발생시킴
```
new 연산자는 새로운 object를 만드는 것이다. 

---

## strict 모드

* 형태 : "use strict"
* 엄격하게 JS문법 사용의 선언이다.
* 작성한 위치부터 적용된다.
* ES5부터 지원된다.
```js
"use strict";
try{
    book = "var를 선언하지 않음";
    log(book);
}catch(error){
    log(error.message);
}
// 결과 : book is not defined
```