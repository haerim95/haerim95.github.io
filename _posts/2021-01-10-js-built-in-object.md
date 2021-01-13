---
title: Built-in object
date: 2021-01-11
categories: [javascript]
comments: true
---

# Built-in object 목록

---

## Number 오브젝트

숫자 처리를 위한 오브젝트이다.  
즉, Number object엔 숫자 처리를 위한 함수와 프로퍼티가 포함되어있다.  
함수를 호출하여 숫자를 처리하고 프로퍼티 키로 값을 구한다.  

### 프로퍼티 리스트

<table>
    <thead>
        <tr>
            <th>이름</th>
            <th>개요</th>
        </tr>
    </thead>
    <tbody style="text-align:center;">
        <tr>
            <td>new Number()</td>
            <td>인스턴트 생성</td>
        </tr>
        <tr>
            <td colspan="2" style="font-weight:bold;">Number 함수</td>
        </tr>
        <tr>
            <td>Number()</td>
            <td>숫자 값으로 변환하여 반환</td>
        </tr>
        <tr>
            <td colspan="2" style="font-weight:bold;">Number.propeotype</td>
        </tr>
        <tr>
            <td>constructor</td>
            <td>생성자</td>
        </tr>
        <tr>
            <td>toString()</td>
            <td>숫자값을 문자열로 변환</td>
        </tr>
        <tr>
            <td>toLocaleString()</td>
            <td>숫자값을 지역화 문자로 변환</td>
        </tr>
        <tr>
            <td>valueOf()</td>
            <td>프리미티브 값 변환</td>
        </tr>
        <tr>
            <td>toExponential()</td>
            <td>지수 표기로 변환</td>
        </tr>
        <tr>
            <td>toFixed()</td>
            <td>고정 소숫점 표기로 변환</td>
        </tr>
        <tr>
            <td>toPrecision()</td>
            <td>고정 소숫점 또는 지수표기로 변환</td>
        </tr>
    </tbody>
</table>

> 목적(개요)을 이루기 위해 수단(이름)을 사용한다.

### 1. Number()

| 구분 | 데이터(값) |
|:---|:---|
| 파라미터 | 변환할 값 opt |
| 반환 | 변환한 값 |

1. 파라미터 값을 `Number` 타입으로 변환  
    1-1 ) 파라미터 값은 필수가 아니다.(입력 안해도 됨)
2. 파라미터 값이 `String` 타입이라도 값이 숫자라면 변환이 가능하다.
```js
log(Number("123") + 500);
log(Number("abs"));
// 결과 값 : 623, NaN
```
3. 숫자로 변환할 수 있으면 변환한다.  
```js
log(Number(0x14)); //16진수를 10진수로 변환
// 0x는 16진수를 뜻한다. 그리고 1에 16을 곱한 뒤 4를 더한다. 고로 값을 20이다.
log(Number(true)); // true는 1, false는 0
log(Number(null)); // null은 0으로 변환
log(Number(undefined)); // undefined는 NaN으로 변환
// 결과 값 : 20, 1, 0, NaN
```
4. 파라미터 값을 작성하지 않으면 0을 반환한다.

### 2. Number 상수

| 상수 이름 | 값 |
|:--- |:--- |
| Number.MAX_VALUE | 1.7976931348623157 * 10(308승) |
| Number.MIN_VALUE | 5 * 10(-324승) |
| Number.NaN | Not-a-Number |
| Number.POSITIVE_INFINITY | infinity |
| Number.NEGATIVE_INFINITY | -infinity |

1. 상수는 값을 변경하거나 삭제할 수 없다.
2. 영문 대문자 사용이 관례이다.
3. Number.MAX_VALUE 형태로 값을 사용한다.

### 3. new 연산자

> `new 연산자`는 Number object는 아니지만 Number 인스턴스 생성과 연계가 되므로 알아보도록 하자.

| 구분 | 데이터(값) |
|:--- |:--- |
| constructor | 생성자 |
| 파라미터 | 값 opt |
| 반환 | 생성한 인스턴스 |

1. 오브젝트로 인스턴스를 생성하여 반환한다.
    * 원본을 복사하는 개념이다.
    * new  연산자를 사용하면 인스턴스
    ```js
    var obj = new Number();
    log(typeof obj);
    //결과 값 : object
    ```
    빌트인 Number 오브젝트로 인스턴스를 생성하여 반환한다.  
    복사를 하는 게 `new 연산자` 복사한 복사본이 `인스턴스`이다.  
    이렇게 생성한 인스턴스를 할당하고 호출되는 함수를 `생성자 함수`라고 부른다.  
    생성한 인스턴스 타입은 object다.

    > 소문자 object와 대문자 Object의 차이점을 기억하자.
    * 코딩 관례로 첫 문자를 대문자로 작성한다.

2. 인스턴스 생성 목적
    * 인스턴스마다 값을 갖기 위해서이다.

    ```js
    var oneObj = new Number("123");
    log(oneObj.valueOf());

    var twoObj = new Number("456");
    log(twoObj.valueOf());
    // 실행 값 : 123, 456
    ```

    두 코드가 가지고 있는 다른 점은 `파라미터 값` 뿐이다.  
    다른 값을 저장하기 위해 인스턴스를 만들어서 저장하는 것이다.  
    (값이 다른 경우를 위해 인스턴스를 생성한다.)

### 4. new Number()

| 구분 | 데이터(값) |
| :---: | :---:  |
| 파라미터 | 값 option |
| 반환 | 생성한 Number 인스턴스 | 

* 빌트인 Number object로 새로운 Number 인스턴스 생성
    ```js
    var obj = new Number("123");
    log(obj.valueOf());
    // 실행 값 : 123
    ```
    빌트인 Number 오브젝트로 인스턴스를 생성하여 반환한다.  
    파라미터 값이 문자열이면 숫자로 변환한다.  
    생성한 인스턴스에 파라미터 값을 설정한다.

* 인스턴트 형태  
    인스턴스를 생성시 프로퍼티들이 단 하나도 오지 않는다.
    단 하나 가져오는 것이 있는데 바로 `prototype`이다.
    인스턴스를 만드는 기준은 프로토타입을 기준으로 해서 프로토타입에 연결되어 있는 것만 설정된다.  

    디버그로 찍어보면 `prototype`은 `__proto__` 로 나와있다.  

    > 인스턴스를 만드는 기준은 프로토 타입이다.  
    > > 프로토타입에 연결되어 있는 함수들을 복사해주는 것, 즉 다른 것들은 가려서 복사해주는 거다

### 5. 프리미티브 값

* Primitive Value
    * 언어에 있어 가장 낮은 단계의 값  
    * `var book = "책";`  
        책은 더이상 분해나 전개가 불가하다.
* Primitive type
    * `Number`, `String`, `Boolean` : 인스턴스 생성 가능  
    * `Null`, `Ùndefined` : 인스턴스 생성 불가  
    * `Object`는 프리미티브 값을 제공하지 않는다.

    `[[PrimitiveValue]]` : value
    `[[]]`는 자바스크립트 엔진이 만들었다는 것이다.  
    즉, 프리미티브 값은 자바스크립트 엔진이 만든 것이다.  

* var obj = new Number(123);  
    인스턴스를 생성하면 파라미터 값을 인스턴스의 프리미티브 값으로 설정한다.  
* 프리미티브 값을 갖는 오브젝트  
    `Boolean`, `Date`, `Number`, `String`
    ```js
        var obj = new Number(123);
        log(obj + 200);
        // 실행 값 : 323
    ```
    프리미티브 값을 갖기 때문에 obj엔 123 값이 설정되기 때문에 값을 더할 수 있는 것이다.

* valueOf() 함수

    | 구분 | 데이터(값) |
    | :---: | :---: |
    | data | Number 인스턴스, 숫자 |
    | 파라미터 | 사용하지 않음 |
    | 반환 | 프리미티브 값 |

    > Number 인스턴스의 프리미티브 값 반환  

    ```js
    var obj = new Number("123");
    log(obj.valueOf());
    // 실행 값 : 123
    ```
    
    위와 같이 인스턴스 obj의 프리미티브 값 123을 반환한다.

---

