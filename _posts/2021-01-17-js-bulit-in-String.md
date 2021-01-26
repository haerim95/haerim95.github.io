---
title: Built-in object 2 String 문자열
date: 2021-01-11
categories: [javascript]
comments: true
---

# String 오브젝트 🆒

* ABC 처럼 문자 처리를 위한 오브젝트  
* 문자처리를 위한 함수와 프로퍼티가 포함되어 있다.  
* 함수를 호출하여 문자 처리를 하게 된다. (프로퍼티 값을 구한다.)

## 1. 문자열 연결 방법

* 한 줄에서 연결하는 법
```js
var book = "12" + "AB" + "가나";
//결과 값 : 12AB가나
```
* 줄을 분리하여 연결  
    1. +로 문자열 연결  
    ```js
    var concat = 123 + "abc" +
                        "가나다";
    // 결과 값 : 123abc가나다
    ```
    2. 역슬래시(\) 문자열 연결
    ```js
    var concat = "abc \ 
                    가나다라";
    // 결과 값 : abc가나다라
    ```
    줄 끝에 역슬래시를 작성한다. (역슬래시 뒤에 다른 문자는 작성불가하다)


## 2. 프로퍼티 리스트

<table>
    <thead>
        <tr>
            <th>이름</th>
            <th>개요</th>
        </tr>
    </thead>
    <tbody style="text-align: center;">
        <tr>
            <td>new String()</td>
            <td>인스턴스 생성</td>
        </tr>
        <tr>
            <td colspan="2" style="font-weight:bold; background-color:#eeeeee;">String 함수</td>
        </tr>
        <tr>
            <td>String()</td>
            <td>문자열로 변환하여 반환</td>
        </tr>
        <tr>
            <td>fromCharCode()</td>
            <td>유니코드를 문자열로 변환하여 반환<br/><span style="color: #ffa500;">(사람이 읽을 수 있는 문자가 된다)</span></td>
        </tr>
        <tr>
            <td colspan="2" style="font-weight:bold; background-color:#eeeeee;">String 프로퍼티</td>
        </tr>
        <tr>
            <td>length</td>
            <td>문자열의 문자 수 반환</td>
        </tr>
        <tr>
            <td colspan="2" style="font-weight:bold; background-color:#eeeeee;">String.protoType</td>
        </tr>
        <tr>
            <td>constructor</td>
            <td>생성자</td>
        </tr>
        <tr>
            <td>valueOf()</td>
            <td>프리미티브 값 반환<br/><span style="color: #ffa500;">(인스턴스에 있는 프리미티브 값 반환)</span></td>
        </tr>
        <tr>
            <td>toString()</td>
            <td>문자열로 변환</td>
        </tr>
        <tr>
            <td>charAt()</td>
            <td>인덱스 번째 문자 반환</td>
        </tr>
        <tr>
            <td>indexOf()</td>
            <td>일치하는 문자열 중에서 가장 작은 인덱스 반환<br/><span style="color: #ffa500;">(왼쪽으로 오른쪽으로 가는데 가장 먼저 일치하는 문자의 index)</span></td>
        </tr>
        <tr>
            <td>lastIndexOf()</td>
            <td>일치하는 문자열 중에서 가장 큰 인덱스 반환 <br/><span style="color: #ffa500;">(가장 오른쪽에 위치하는 문자의 index)</span></td>
        </tr>
         <tr>
            <td colspan="2" style="font-weight:bold; background-color:#eeeeee;">String.protoType</td>
        </tr>
         <tr>
            <td>concat()</td>
            <td>문자열 연결</td>
        </tr>
         <tr>
            <td>toLowerCase()</td>
            <td>영문 소문자로 변환</td>
        </tr>
         <tr>
            <td>toUpperCase()</td>
            <td>영문 대문자로 변환</td>
        </tr>
         <tr>
            <td>trim()</td>
            <td>문자열 앞뒤의 화이트 스페이스 삭제<br/><span style="color: #ffa500;">(공백삭제)</span></td>
        </tr>
         <tr>
            <td>substring()</td>
            <td>시작에서 끝 직전까지 값 반환<br/><span style="color: #ffa500;">(바로 앞에까지의 값)</span></td>
        </tr>
         <tr>
            <td>substr()</td>
            <td>시작 위치부터 지정한 문자 수 반환</td>
        </tr>
         <tr>
            <td>slice()</td>
            <td>시작에서 끝 직전까지 값 반환. substring()과 차이 있음<br/><span style="color: #ffa500;">(추출하는 조건이 차이가 있다)</span></td>
        </tr>
         <tr>
            <td>match() <br/><span style="color : #447fcf; font-size: 12px;">정규표현식 사용가능</span> </td>
            <td>매치 결과 반환 <br/><span style="color: #ffa500;">(다수의 다양한 매치 가능)</span></td>
        </tr>
         <tr>
            <td>replace() <br/><span style="color : #447fcf; font-size: 12px;">정규표현식 사용가능</span> </td>
            <td>매치 결과를 지정한 값으로 대체</td>
        </tr>
         <tr>
            <td>search() <br/><span style="color : #447fcf; font-size: 12px;">정규표현식 사용가능</span> </td>
            <td>검색된 첫 번째 인덱스 반환</td>
        </tr>
         <tr>
            <td>split() <br/><span style="color : #447fcf; font-size: 12px;">정규표현식 사용가능</span> </td>
            <td>구분자로 분리하여 반환</td>
        </tr>
         <tr>
            <td>charCodeAt()</td>
            <td>인덱스 번째 문자를 유니코드로 반환</td>
        </tr>
         <tr>
            <td>localeCompare()</td>
            <td>값의 위치를 1(왼쪽),0(같음),-1(오른쪽)로 반환</td>
        </tr>
    </tbody>
</table>

---

## 3. 문자열로 변환

### String()

| 구분 | 데이터(값) |
| :---: | :---: |
| 파라미터  | 변환대상 opt |
| 반환 | 뱐환한 값 |

* 파라미터 값을 String 타입으로 변환하여 반환한다.
    - 값을 작성하지 않으면 빈문자열을 반환한다.

```js
var value = String(123);

console.log(value); // 값 : 123
console.log(typeof value); // 값 : string
console.log(typeof ("" + 123)) // 값 : string
```

- `("" + 123)` 으로도 String 타입이 되지만  
    `String(123)`형태가 더 가독성이 높다.

### new String()

| 구분 | 데이터(값) |
| :---: | :---: |
| 파라미터  | 값 opt |
| 반환 | 생성한 String 인스턴스 |

* String 인스턴스를 생성하여 반환한다.

```js
var obj = new String(123);
console.log(typeof obj); // 값 : object
```

* 파라미터 값을 String 타입으로 변환한다.  
    파라미터 값이 프리미티브 값이 된다.  

### valueOf()


| 구분 | 데이터(값) |
| :---: | :---: |
| data | String 인스턴스, 문자 |
| 파라미터  | 값 opt |
| 반환 | 생성한 String 인스턴스 |

* String 인스턴스의 프리미티브 값을 반환한다. 

```js
var obj = new String(123);
console.log(obj.valueOf()); //값 : 123
```
1. obj는 String 인스턴스이다.  
2. 파라미터 값 123이 String 인스턴스의 프리미티브 값으로 설정된다.  
3. obj에 프리미티브 값으로 설정된 값이 반환된다.

---

## 4. length 프로퍼티

* 문자 수를 반환한다. 

```js
var value = "ABC";
for(var k = 0; k < value.length; k++){
    console.log(value[k]);
};
// 실행결과 
// A
// B
// C
```
"ABC"를 문자 하나씩 분리하여 반복한다. 따라서 3번 반복한다.

* length 값이 반환되는 논리

`value = "ABC";` 에는 length 프로퍼티가 없는데 3이 출력된다. 왜 일까?  

```js
var obj = new String("ABC");
```

위 코드를 개발자 모드에서 실행시킨뒤 sources에 들어가 살펴보면  
오른쪽 local이 있다. 이 local에서 obj를 펼치면 length: 3이 있다. 둘은 같은 라인에 있다.   
이건 value 변수와 obj가 같다는 뜻이기도 하다.  
엔진이 value.length를 만나면 value가 String 타입 이므로  
내부에서 new String("ABC")를 하게 되며(인스턴스를 생성한다.)  
생성한 인스턴스의 length 값인 3을 반환하게 된다. 

> 위 예제로 풀이하자면!  
> 맨 처음 value에 대한 타입을 구한다.  
> 내부에서 new String 인스턴스를 만든다. 그리고 "ABC"가 프리미티브 값에 설정된다.  
> 이때 그 프리미티브 값을 보고 랭스를 만든다.


---

## 5. 화이트 스페이스 삭제

### trim()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 삭제 대상 |
| 파라미터  | 사용하지 않음 |
| 반환 | 삭제한 결과 |

* 문자열 앞뒤의 화이트 스페이스를 삭제한다.

```js
var value = "  abcd  ";
console.log(value.length); // 값 : 8

console.log(value.trim().length); // 값 : 4
```

그냥 value의 length는 공백을 포함하여 8,  
trim()을 사용하면 앞뒤의 공백이 사라지므로 4가 반환된다.

> `value.trim().length` 처럼 `.` 으로 이어진 걸 `메소드 체인(Method Chain)` 이라고 한다.

---

## 6. 함수호출 구조 (String에 toString이 필요한 이유)

### toString()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 문자열, string 인스턴스 |
| 파라미터  | 사용하지 않음 |
| 반환 | 변환한 값 |

* data 위치의 값을 String 타입으로 변환한다. 

_"123".toString();_

> string()은 이미 문자열인데 어째서 toString()이 필요할까?
> 의미가 없다?

[ toString() 함수가 필요한 이유 ]  

인스턴스를 만들때 toString이 인스턴스에 해당함

```js
var twoProto = instance.__proto__.__proto__;
```

```js
__proto__:
    toString();
    __proto__:
       toString(); 
```

위처럼 `__proto__` 안에 `__proto__`가 있는 구조이다.  

아래에 있는 것은 프로퍼티를 String으로 변환하는것, 위에 있는 것은 문자열을 String으로 변환하는 것  
내려가서 실행되는걸 방지하기 위해 toString()을 작성해준다.  
<br/>
그래서 대부분의 빌트인 오브젝트에 toString()과 valueOf()가 있는 것이다.  

### JS 함수 호출 구조

1. 데이터 타입으로 오브젝트를 결정한다.  
2. 오브젝트의 함수를 호출한다.

```js
var value = 123;
value.toString();
"123".toString();
```
value.toString()은 Number 오브젝트의 toString()을 호출한다.  
"123".toString()은 String 오브젝트의 toString()을 호출한다.

* toString(123);  
    123을 파라미터에 작성
    ```js
    var result = toString(123);
    console.log(result);
    ```
    1. Object 오브젝트의 toString()이 호출된다.  
    2. 123을 오브젝트로 간주하여 Object 형태를 문자열로 변환한다.  
    3. object Undefined 가 반환된다.  
    4. 값만 입력했는데 key:value 값이 들어오기 때문이다.

---

## 7. 인덱스로 문자열 정리

### cahrAt()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 반환 대상 |
| 파라미터  | 반환 기준 인덱스(index) |
| 반환 | 인덱스 번째 문자 |

* 인덱스의 문자를 반환한다.

    ```js
    var value = "sports";
    console.log(value.charAt(1)); // 함수를 호출하는 형태
    console.log(value[1]); //프로퍼티 이름으로 값을 구하는 형태
    // 값 : p, p
    ```
    ES5에선 `[1]` 형태로 사용할 수 있다.

* 문자열 길이보다 인덱스가 크면 빈문자열을 반환한다. 

    ```js
    var value = "sports";
    console.log(value.charAt(12));
    // 값 : ""
    ```
    `sports`의 전체 문자열 수는 6인데 파라미터의 인덱스가 전체 문자열보다 크므로  
    빈 문자열을 반환한다.

    <span class="color2"> 빈 문자열도 "값" 이다.</span>

* 일반적으로 존재하지 않으면 undefined를 반환한다.

    ```js
    var value = "sports";
    console.log(value[12]);
    // 값 : undefined
    ```
    12번째 인덱스가 없으므로 undefined를 반환한다.  
    프로퍼티 이름으로 가서 반환하기 때문에 위에 빈 문자열을 반환하는 것과는 차이가 있다.  

### indexOf()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 검색 대상 |
| 파라미터  | 검색한 문자열 |
| 반환 | 인덱스 번째 문자 |

