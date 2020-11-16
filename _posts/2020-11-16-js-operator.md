---
title: Javascript 연산자(Operator)
date: 2020-11-16
categories: [javascript]
comments: true
---

---

# 자바스크립트 연산자(Operator)

> **연산자의 사전적 의미?**  
> 규칙에 따라 계산하여 값을 구함

### 연산자 형태
* `+`, `-`, `*`, `/`, `%`
* `>`, `>=`, `<`, `<=`
* `==`, `!=`, `===`, `!==`
* `콤마(,)`, `typeof`, `delete`, `void`
* `instanceof`, `in`, `new` 등

# 자바스크립트 표현식(Expression)

### 표현식 형태
* 1 + 2
* var total = 1 + 2;
    1 + 2 는 표현식을 평가한다고 한다.  
    1 + 2 = 3 에서 `3`은 `평가 결과` 라고 한다.

자바스크립트는 `표현식의 연결`이다.

---

## 할당 연산자

1. 단일 할당 연산자
   * `=` 하나만 사용한다.
   * var result = 1 + 2;  
    왼쪽에서 오른쪽으로 계산한다. result 의 값은 3이 된다.

2. 복합 할당 연산자
   * `=` 앞에 연산자를 작성한다.
   * `+=`, `-=`, `*=`, `/=`, `%=`  
    `<<=`, `>>=`  
    `>>>=`, `&=`, `^=`, `|=`
   * 복합 할당 연산자는 `= 앞`을 먼저 연산한 후, 변수에 할당한다.
    
    ```javascript
    var point = 7;

    point += 3;
    // 7 + 3 = 10
    // 10을 포인트에 할당한다. 고로 point의 최종 값은 10이다.
    ```

---

## 산술 연산자

### + 연산자

1. 평가 결과를 더한다.
   ```js
   var value = 1 + 2 + 4;
   log(value);
    // 1 + 2 + 4
    //결과 값 : 7
   ```

2. 평가 결과를 `연결`한다.
   한 쪽이라도 숫자(number)가 아니면 연결한다.
   ```js
   var two = "2";
   var value = 1 + two;
   log(value);
   log(typeof value);

   // 12 (숫자 1과 문자 2가 연결되어 12)
   // String
   ```

```js
var value = 1 + 5 + "ABC";
log(value)

// 결과 값 : 6ABC
```

### 숫자로 변환

> 자바스크립트는 연산하기 전에 우선 숫자로 변환하려고 시도한다.

| 값 타입 | 변환 값 |
|:---|:---|
| Undifined | NaN |
| Null | +0 |
| Boolean | true : 1, false: 0 |
| Number | 변환 전 / 후 같음 |
| String | 값이 숫자이면 숫자로 연산  단, 더하기(+)는 연결 |


예제 1
```js
var value;
log(10 + value);

//결과 값 : NaN
```
>위의 코드를 보면 변수 value의 값은 undifined 이나 자바스크립트는 값을 숫자로 변환하는 것을 시도하기 때문에 `NaN` 으로 나온다.

예제2
```js
log(10+Null);
//결과 값 : 10
log(10 + true);
//결과 값 : 11
log(10 + false);
//결과 값 : 10
```
>Null은 0으로 변환  
>true는 1로 변환, false는 0으로 변환이다.

예제3
```js
log(10 + "123");
//결과 값 : 10123
log(123 - "23");
//결과 값 : 100
```
> `더하기(+)`는 값이 숫자라도 타입이 String이면 문자열로 연결한다.  
> 그러나 `-`, `*`, `/`는 숫자로 변환하여 연산한다.


### -(빼기) 연산자

* String 타입이지만 값이 숫자이면 Number 타입으로 변환하여 계산한다.

```js
log("125 - 2");
//결과 값 : 123
```
이처럼 `"125"` 는 `String` 타입이지만 값이 숫자이므로 `Number` 타입으로 변환하여 계산된다.

### *(곱하기) 연산자

* 빼기 연산자와 마찬가지로 숫자 값으로 변환할 수 있으면 변환한다.
* 양쪽의 평가가 하나라도 숫자가 아닐때 NaN을 반환한다.
    ```js
    log(10 * "20"); //결과 값 : 200
    log(10 * true); //결과 값 : 10
    log(10 * false); //결과 값 : 0
    log(10 * null); //결과 값 : 0
    log(10 * "A"); //결과 값 : NaN
    ```
* 소수 값이 생기는 경우 처리
    ```js
    log(2.3 * 3);
    //결과 값 : 6.8999999999999995
    ```
    2.3 * 3의 값은 6.9로 출력되지 않는다.  
    이는 정상이며 `IEEE 754 유동 소수점 처리` 때문이다.  

    이를 해결하기 위해선 실수를 정수로 변환하여 값을 구한 뒤  
    다시 정수를 실수로 변환하는 방법이다.
    ```js
    log(2.3 * 10 * 3 / 10);
    // 2.3 * 10 = 23
    // 23 * 3 = 69
    // 69 / 10 = 6.9
    // 결과 값 : 6.9
    ```

### / (나누기) 연산자

* NaN 반환
  * 양쪽의 평가결과가 하나라도 숫자가 아닐 때
  * 분모, 분자 모두 0일 때  
    분모가 0일 때 : `Infinity` 반환  
    분자가 0일 때 : `0` 반환
    ```js
    log(10 / 2); //결과 값 : 5
    log(10 / "2"); //결과 값 : 5
    log(10 / "A"); //결과 값 : NaN
    log(10 / 0); //결과 값 : Infinity
    log(0 / 10); //결과 값 : 0
    ```

### % (나머지) 연산자

* 왼쪽 표현식 평가 결과를 오른쪽 표현식 평가 결과로 나누어 나머지를 구한다.
```js
log(5 % 2.5); //결과 값 : 0
log(5 % 2.3); //결과 값 : 0.40000000000000036
```
소수 끝 36을 없애려면 실수를 정수로 변환하여 연산 후 다시 정수를 실수로 변환해야 한다.
```js
log((5 * 10 - (2 * 2.3 * 10)) / 10); //결과 값 : 0.4
```

---

## 단항 연산자

### 1. 단항 + 연산자

* 형태 : +value (+변수)

* 값을 `Number` 타임으로 변환시킨다.

```js
var value = "7";
log(typeof value); //결과 값 : String
log(typeof +value); //결과 값 : Number
```
이와 같이 타입을 Number 타입으로 변경시켜준다.  
좀더 가독성이 좋은 `Number()`도 같은 기능을 가진다.
```js
log(typeof Number(value)); // 결과 값 : Number
```

### 2. 단항 - 연산자

* 형태 : -value
* 값의 부호를 바꾼다.  
    `+` 👉 `-`  
    `-` 👉 `+`
* 값의 부호는 연산할 때만 변경된다. (원래 값은 변경 ❌)
  
```js
var value = 7;
log(-value); // 결과 값 : -7
log(8 + -7); // 결과 값 : 1
log(value); // 결과 값 : 7
```

---

## 후치 ++연산자

* 형태 value++
* 값을 자동으로 `+1 증가`시킨다.