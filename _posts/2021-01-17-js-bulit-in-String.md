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

<table style="text-align:center;">
    <thead>
        <tr>
            <th>구분</th>
            <th>데이터(값)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data</td>
            <td>검색 대상</td>
        </tr>
        <tr>
            <td rowspan="2">파라미터</td>
            <td >검색한 문자열</td>
        </tr>
        <tr>
            <td>검색 시작 위치, 디폴트 : 0</td>
        </tr>
        <tr>
            <td>반환</td>
            <td>인덱스</td>
        </tr>
    </tbody>
</table>

* data 위치의 문자열에서 파라미터의 문자와 같은 첫 번째 인덱스를 반환한다.
* 검색기준은 3가지가 있다.

#### 1. 왼쪽에서 오른쪽으로  

```js
var value = "123123";
console.log(value.indexOf(2)); // 값 : 1
console.log(value.indexOf(23)); // 값 : 1
```
    
    123123에서 `2` 는 두개이지만 처음 인덱스를 반환하므로 1이다.  
    값을 구하게 되면 더 이상 값을 구하지 않고 끝난다.  
    23에선 23이 존재하며 23중 처음인 2가 검색된 인덱스를 반환한다.

#### 2. 두 번째 파라미터를 작성하면 그 작성한 인덱스번째부터 검색한다. 

```js
var value = "123123";
console.log(value.indexOf(2,3)); //값 : 4
```
index(2,3) 은 3번 인덱스부터 2를 찾아 검색하는 것이다.  
3번째 인덱스부터 2를 찾아 2의 인덱스를 찾으니 값은 4가 된다.

#### 3. 같은 문자가 없으면 -1 을 반환한다. <span class="color2">(자주 쓰이는 방법!)<span>

```js
var value = "123123";
console.log(value.indexOf(15)); //값 : -1
```

> indexOf를 사용할때 자주 사용한다.  존재 여부를 체크하기 때문

```js
var value = "123123";
console.log(value.indexOf(2, -1)); //값 : 1
console.log(value.indexOf(2, 9)); //값 : -1
console.log(value.indexOf(2, "A")); //값 : 1
```
예제 1. 두 번째 파라미터 값이 0보다 작으면 처음부터 검색하므로 1이 나온다.  
예제 2. 두 번째 파라미터 값이 length 보다 `크면` -1 을 반환한다.  
예제 3. 두 번째 파라미터가 NaN이면 처음부터 검색한다.

> 조건들은 전부 안 외워도 된다. index 번째의 값을 반환한다는 것, 존재하지 않으면 -1을 반환한다는 것. 이것만 기억하자

### lastIndexOf()

<table style="text-align:center;">
    <thead>
        <tr>
            <th>구분</th>
            <th>데이터(값)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data</td>
            <td>검색 대상</td>
        </tr>
        <tr>
            <td rowspan="2">파라미터</td>
            <td >검색한 문자열</td>
        </tr>
        <tr>
            <td>검색 시작 위치, 디폴트 : 0</td>
        </tr>
        <tr>
            <td>반환</td>
            <td>인덱스</td>
        </tr>
    </tbody>
</table>

* data 위치의 문자열에서 파라미터의 문자와 같은 인덱스를 반환한다.  
    (단, 뒤에서 앞으로 검색한다.)

    ```js
    var value = "123123";
    console.log(value.lastIndexOf(2)); //값 : 4

    ```
    마지막 인덱스를 반환하므로 4를 반환한다. 

* 검색기준은 2가지 이다.

#### 1. 두 번째 파라미터를 작성하면 작성한 인덱스부터 검색

```js
var value = "1231231";
console.log(value.lastIndexOf(1, 4)); //값 : 3
console.log(value.lastIndexOf(2, -1)); // 값 : -1
```
예제 1)  
<span class="color2">인덱스는 왼쪽에서 오른쪽부터 시작한다.</span> 그러나 첫번째 파라미터를 찾을땐 역순이다.  
"1231`2`31" 4번째 인덱스 2에서 오른쪽에서 왼쪽으로 이동해 "123`1`231" 1을 찾음. 고로 3이 반환된다.  
예제 2) 두 번째 파라미터가 `0보다 작으면 -1을 반환`한다.

---

## 8. 문자열 연결, 대소문자 변환

### concat()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 연결 시작 값, String 인스턴스 |
| 파라미터  | 연결 대상 opt, 다수 작성 가능 |
| 반환 | 연결한 결과 |

* data 위치의 값에 파라미터 값을 작성 순서로 연결하여 문자열로 반환한다.  

```js
var result = "sports".concat("축구", 11);
console.log(result); // 값 : sports축구11

var obj = new String(123);
console.log(obj.concat("ABC")); // 값 : 123ABC
```
 String 인스턴스를 작성하면 프리미티브 값을 연결한다.

### toLowerCase()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 변환 대상 |
| 파라미터  | 사용하지 않음 |
| 반환 | 변환 결과 |

* 영문 대문자를 소문자로 변환한다.

### toUpperCase()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 변환 대상 |
| 파라미터  | 사용하지 않음 |
| 반환 | 변환 결과 |

* 영문 소문자를 대문자로 변환한다.

```js
console.log("CODE".toLowerCase()); // 값 :code
console.log("code".toUpperCase()); // 값 : CODE
```

---

## 문자열 추출 (외울 필요 없다 그냥 알아두면 좋음)

### subString()


<table style="text-align:center;">
    <thead>
        <tr>
            <th>구분</th>
            <th>데이터(값)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data</td>
            <td>반환 대상</td>
        </tr>
        <tr>
            <td rowspan="2">파라미터</td>
            <td >시작 인덱스</td>
        </tr>
        <tr>
            <td>끝 인덱스</td>
        </tr>
        <tr>
            <td>반환</td>
            <td>결과</td>
        </tr>
    </tbody>
</table>

* 파라미터의 `시작 인덱스`부터 `끝 인덱스 직전`까지 반환한다.

```js
var value = "01234567";
console.log(value.subString(2, 5)); // 값 234
```
2번 인덱스부터 5번 인덱스 직전(4번 인덱스)까지 반환한다.  

* 두번째 파라미터를 작성하지 않으면(끝 인덱스를 작성하지 않으면) 반환 대상의 끝까지 반환한다.  

* 파라미터를 모두 작성하지 않으면 전체가 반환된다.  

* 다양한 추출 조건을 작성할 수 있다.  
    1. 두번째 파라미터 값(끝 인덱스)이 전체 length 보다 크면 전체 문자열 Length를 사용한다.  
        따라서 시작 인덱스부터 끝까지 반환한다.  
    2. 파라미터 값이 음수이면 0으로 간주한다.  
    3. 첫 번째 파라미터 값(시작 인덱스 값)이 두번째(끝 인덱스 값)보다 크면 파라미터의 값을 뒤바꿔서 처리한다.  
    4. NaN은 0으로 간주한다.


### substr()

<table style="text-align:center;">
    <thead>
        <tr>
            <th>구분</th>
            <th>데이터(값)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data</td>
            <td>반환 대상</td>
        </tr>
        <tr>
            <td rowspan="2">파라미터</td>
            <td >시작 인덱스</td>
        </tr>
        <tr>
            <td>반환할 문자 수</td>
        </tr>
        <tr>
            <td>반환</td>
            <td>결과</td>
        </tr>
    </tbody>
</table>

* 파라미터의 시작 인덱스부터 지정한 문자 수를 반환한다.  

```js
var value = "01234567";
console.log(value.substr(0, 3)); 값 : 012
```
0번 인덱스부터 문자 3개를 반환한다.  

* 첫 번째 파라미터 값이 음수이면 length에서 파라미터 값을 더해 시작 인덱스로 사용한다.  

```js
var value = "01234567";
console.log(value.substr(-3, 3));
// 값 : 567
```
첫 번째 파라미터 값이 -3이므로 value의 length 값인 8을 더해 첫 번째 파라미터를 5로 만든다.  
5번째 인덱스부터 3개의 문자를 반환하므로 567이 나온다.  

* 두 번째 파라미터를 작성하지 않으면 양수 무한대로 간주한다.  
    양수 무한대는 최대 값이다. 고로 첫 번째 파라미터의 인덱스 값 부터 전체를 반환한다.  
    첫 번째 파라미터를 작성하지 않으면 0으로 간주하여 아예 전체가 반환된다.

### slice()

<table style="text-align:center;">
    <thead>
        <tr>
            <th>구분</th>
            <th>데이터(값)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data</td>
            <td>반환 대상</td>
        </tr>
        <tr>
            <td rowspan="2">파라미터</td>
            <td >시작 인덱스</td>
        </tr>
        <tr>
            <td>끝 인덱스</td>
        </tr>
        <tr>
            <td>반환</td>
            <td>결과</td>
        </tr>
    </tbody>
</table>

* 파라미터의 시작 인덱스부터 끝 인덱스 직전까지 반환한다.  
* 첫 번째 파라미터 값을 작성하지 않거나 NaN이면 0으로 간주한다.  
* `false`, `undefined`, `null`, `빈 문자열` 은 0으로 간주한다.
* 두번째 파라미터를 작성하지 않으면 lenght를 사용한다.
* 값이 음수이면 lenght에 더해 사용한다.

---

## 정규 표현식을 사용할 수 있는 함수

### match()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 매치 대상 |
| 파라미터  | 정규표현식, 문자열 |
| 반환 | [ 매치결과 ] |

* 매치 결과를 `배열`로 반환한다.
    매치 대상에 정규 표현식의 패턴을 적용하여 매치하고 결과를 반환한다.

    ```js
    var value = "Sports";
    console.log(value.match(/s/)); // 값 : [s]
    console.log(value.natch("spo")); // 값 : null
    ```
    match에서 `/s/`는 정규표현식이다.  
    한개가 있든 몇개가 있든 배열로 반환하기 때문에 [ s ] 가 반환된 것이다.  
    "spo"는 소문자 s를 파라미터에 작성했기 때문에(value의 값은 대문자 s로 입력되어 있다.) null이 반환된다.

> 정규 표현식이란? 🤔
>> 문자열을 패턴으로 매치한다.  
>> 패턴(pattern) 형태 : ^,$,*,+ 등


### replace()

<table style="text-align:center;">
    <thead>
        <tr>
            <th>구분</th>
            <th>데이터(값)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data</td>
            <td>치환 대상</td>
        </tr>
        <tr>
            <td rowspan="2">파라미터</td>
            <td >정규 표현식, 문자열</td>
        </tr>
        <tr>
            <td>대체할 값, 함수</td>
        </tr>
        <tr>
            <td>반환</td>
            <td>치환 결과</td>
        </tr>
    </tbody>
</table>

* 매치 결과를 파라미터에 작성한 값으로 대체하여 반환한다.  
* 두번째 파라미터에 함수를 작성하면 먼저 함수를 실행하고 함수에서 반환된 값으로 두 번째 파라미터를 대체한다.

```js
var value = "abcabc";
console.log(value.replace("a", "바꿈")); 
// 값 : 바꿈bcabc
console.log(value.replace(/a/, "바꿈"));
// 값 : 바꿈bcabc

function change(){
    return "함수";
};
console.log(value.replace(/a/, change()));
//값 : 함수bcabc
```
1. /a/는 처음 하나만 바꾸므로 뒤에 있는 a는 변경되지 않는다.  
2. 함수로 불러오면 함수를 먼저 실행하고 반환된 값으로 바꾼다. 

### search()

| 구분 | 데이터(값) |
| :---: | :---: |
| data | 검색 대상 |
| 파라미터  | 정규표현식, 문자열 |
| 반환 | 매치된 인덱스 |

* 검색된 첫번째 인덱스를 반환한다.  
* 매치되지 않으면 `-1` 을 반환한다.  

```js
var value = "cbacba";
console.log(value.search(/a/)); // 값 : 2
console.log(value.search("K")); // 값 : -1
```
두번째 결과는 k가 없으므로 매치되지 않는다. 그러므로 -1을 반환한다.


### split()

<table style="text-align:center;">
    <thead>
        <tr>
            <th>구분</th>
            <th>데이터(값)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data</td>
            <td>분리 대상</td>
        </tr>
        <tr>
            <td rowspan="2">파라미터</td>
            <td >분리자(separator) : 정규 표현식, 문자열</td>
        </tr>
        <tr>
            <td>반환 수</td>
        </tr>
        <tr>
            <td>반환</td>
            <td>결과</td>
        </tr>
    </tbody>
</table>

* 분리 대상을 분리자로 분리하여 `배열`로 반환한다.

```js
console.log("12_34_56".split("_"));
// 값 : [12, 34, 56]
```
split 파라미터에 넣은 '_' 을 분리자로 사용하여 분리했다.  
분리자는 반환되지 않는다.

* 분리자에 빈 문자열을 작성하면 문자를 하나씩 분리하여 반환한다.
```js
var value = "123"
console.log(value.split("")); // 값 : [1,2,3]
```
* 분리자를 아예 작성하지 않으면 분리 대상 전체를 하나의 배열로 반환한다.
```js
console.log("123".split()); //값 : [123]
```

* 두 번째 파라미터에 반환 수를 작성할 경우 그 수만큼 반환된다.
```js
var value = "12_34_56_78";
console.log(value.split("_", 3));
// 값 : [12, 34, 56]
value = "123";
console.log(value.split("A"));
// 값 : [123]
```
분리자가 대상에 없으면 분리 대상 전체를 하나의 배열로 반환한다.

---

## unicode 관련 함수