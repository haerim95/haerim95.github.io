---
title: Built-in object 3 Object
date: 2021-01-31
categories: [javascript]
comments: true
---

# Object

---

## 1. 자바스크립트의 오브젝트

* 오브젝트 구분  
1. 빌트인 오브젝트(Built-in Object)  
2. 네이티브 오브젝트(Native Object)  
3. 호스트 오브젝트(Host Object)

### 빌트인 오브젝트
* 사전에 만들어 놓은 오브젝트이다.  
* 예로는 앞서 포스팅한 Number 오브젝트와 String 오브젝트 등 11개의 오브젝트가 있다.

### 네이티브 오브젝트
* JS 스펙에서 정의한 오브젝트이다.  
* 빌트인 오브젝트도 네이티브 오브젝트에 포함된다.  
* JS를 실행할때 만드는 코드이다.  

### 호스트 오브젝트

* 빌트인, 네이티브 오브젝트를 제외한 오브젝트이다.(즉, 네이티브 오브젝트가 아니면 전부 호스트 오브젝트이다)  
    예) window, DOM 오브젝트
    ```js
    var node = document.querySelector("div");
    console.log(node.nodeName); //값 : DIV
    ```
    DOM 함수 : querySelector()  
    DOM에서 제공하는 오브젝트를 `호스트 오브젝트`라고 한다.  
    마치 JS 함수처럼 DOM 함수를 사용한다.

> 빌트인 오브젝트는 네이티브 오브젝트에 포한된다고 봐야하기 때문에 자바스크립트의 오브젝트는 `네이티브`와 `호스트` 두가지라고 보면 된다.

* JS는 호스트 환경에서 브라우저의 모든 요소 기술을 연결하고 융합하며 이를 제어한다.  


---

## 2. 빌트인 Object 프로퍼티 리스트

<table>
    <thead>
        <tr>
            <th>이름</th>
            <th>개요</th>
        </tr>
    </thead>
    <tbody style="text-align: center;">
        <tr>
            <td>new Object()</td>
            <td>파라미터 데이터 타입의 인스턴스를 생성</td>
        </tr>
         <tr>
            <td>Object()</td>
            <td>Object 인스턴스 생성</td>
        </tr>
        <tr>
            <td colspan="2" style="font-weight:bold; background-color:#eeeeee;">Object.prototype</td>
        </tr>
        <tr>
            <td>constructor</td>
            <td>생성자</td>
        </tr>
        <tr>
            <td>valueOf()</td>
            <td>프리미티브 값 반환</td>
        </tr>
         <tr>
            <td>hasOwnProperty()</td>
            <td>프로퍼티 소유 여부 반환</td>
        </tr>
         <tr>
            <td>propertyIsEnumerable()</td>
            <td>프로퍼티 열거 여부 반환</td>
        </tr>
         <tr>
            <td>isPrototypeOf()</td>
            <td>prototype의 존재 여부 반환</td>
        </tr>
         <tr>
            <td>toString()</td>
            <td>문자열로 반환</td>
        </tr>
         <tr>
            <td>toLocaleString()</td>
            <td>지역화 문자열로 변환</td>
        </tr>
    </tbody>
</table>

밑에서 6개의 함수는 빌트인 오브젝트로 인스턴스를 만드는 오브젝트에 포함된다.  (__ proto __)

---

## 3. 빌트인 오브젝트 구조

* 오브젝트 이름 (Object, String, Number...)  
* 오브젝트.prototype  
    - 인스턴스 생성 가능 여부 기준  
    - 프로퍼티를 연결하는 오브젝트  
prototype이 없으면 인스턴스를 만들 수 없다. (프로퍼티를 연결할 수 없다)   
* 오브잭트.prototype.constructor  
    - 오브젝트의 생성자  
* 오브젝트.prototype.method  
    - 메소드 이름과 함수 작성  

---

## 4. 함수와 메소드 연결

* 함수  
    -오브젝트에 연결  
    -Object.create()  

* 메소드
    -오브젝트의 prototype에 연결  
    -Object.prototype.toString()  
    이때 < toString > 함수가 메소드가 된다.  

### 함수, 메소드 호출

* 함수 호출 방법  
    -Object.create();  
    ```js
    console.log(Object.create);
    // 값 : function create(){[native code]}
    console.log(Object.prototype.create);
    // 값 : undefined
    ```
    1. Object에 create가 존재하므로 함수를 출력한다.  
    2. Object.prototype에 create가 존재하지 않으므로 undefined가 출력된다.  

* 메소드 호출 방법
    -Object.prototype.toString();  
    -또는 인스턴스를 생성하여 호출한다.  
    ```js
    console.log(Object.protoType.toString());
    // 값 : function toString(){[native code]}

    var obj = {};
    log(obj.toString);
    // 값 : function toString(){[native code]}
    ```
    1. Object.prototype에 toString이 존재하므로 함수를 출력한다.  
    2. 인스턴스를 사용하여 메소드를 호출할 때는 prototype을 작성하지 않는다.  
        prototype에 연결된 메소드로 인스턴스를 생성하기 때문이다.  
        즉, toString 함수는 방법이 두가지 이다.  

* 함수와 메소드를 구분해야 하는 이유  
    -JS 코드 작성 방법이 다르다.
    -함수는 파라미터에 값을 작성하고 메소드는 메소드 앞에 값을 작성한다.  
    ```js
    console.log(String.fromCharCode(49, 65);
    //값 : 1A
    ```
    함수 앞에 배열로 값을 작성하면 Array 오브젝트의 함수가 호출되므로  
    String 오브젝트의 함수를 호출하면서 파라미터에 값을 작성해야한다.  

> prototype이 연결되어 있으면 medhod이고  
> 연결되어 있지 않으면 함수이다.

---

## 프로퍼티 처리 메소드

### hasOwnProperty()

| 구분 | 데이터(값) |
| :---: | :---: |
| object  | 기준 인스턴스 |
| 파라미터 | 프로퍼티 이름 |
| 반환 | true, false |

* 인스턴스에 파라미터 이름이 존재하면 `true` 반환, 존재하지 않으면 `false` 반환

```js
var obj = {value: 123};
var own = obj.hasOwnProperty("value");
console.log(own);
//값 : true
```
<p style="text-align: center; background-color: #eeeeee;">[프로퍼티 존재 여부 코드]</p>

1. obj 인스턴스에 value 프로퍼티가 존재하며 (name="value")
2. obj를 만들면서 직접 작성했으로 true를 반환한다.  
```js
var obj = {value: undefined};
var own = obj.hasOwnProperty("value");
console.log(own); //값 : true
```
<p style="text-align: center; background-color: #eeeeee;">[값은 체크하지 않음]</p>

1. undefined가 값이지만 false로 인식된다.  
2. 하지만 값은 체크하지 않고 `존재 여부만 체크` 하므로 true가 반환된다.

* 자신이 만든 것이 아니라 상속받은 프로퍼티이면 false를 반환한다.  

```js
var obj = {};
var own = obj.hasOwnProperty("hasOwnProperty"); //괄호 안 hasOwnProperty는 프로퍼티 이름이면서 메소드이다.
console.log(own); //값 false
```
0. obj 에 아무런 값도 할당하지 않았으므로  
1. hasOwnProperty()는 자신이 만든 것이 아니라 빌트인 Object 오브젝트에 있는 것이다.  
    자신이 만든 것은 위에 있는 프로퍼티 존재여부 코드에 있는 것이다.  
2. {}를 실행하면 빌트인 Object의 prototype에 연결된 메소드를 사용하여  
3. Object 인스턴스를 만드므로 자신이 만든 것이 아니다.  


### propertyIsEnumerable()

| 구분 | 데이터(값) |
| :---: | :---: |
| object  | 인스턴스, 오브젝트 |
| 파라미터 | 프로퍼티 이름 |
| 반환 | true, false |

* 오브젝트에서 프로퍼티를 열거 할 수 있으면 `true`를 반환한다.  
```js
var obj = {sports: "축구"};
console.log(obj.propertyIsEnumerable("sports"));
//값 : true
```  
1. {sports: "축구"} 형태로 생성한 인스턴스는 obj의 프로퍼티를 열거할 수 있다.(for in 문 사용)  

* 오브젝트에서 프로퍼티를 열거할 수 없으면 `false`를 반환한다.

```js
var obj = {sports: "축구"};
Object.defineProperty(obj, "sports", {
    enumerable : false //열거할 수 없는 상태로 설정함
});
console.log(obj.propertyIsEnumerable("sports"));

for(var name in obj){
    console.log(name);
}
// 값 : false
```
1. {enumerable: false}로 열거 불가 설정  
2. for-in 문에서 프로퍼티가 열거되지 않는다  

---

## Object와 prototype, 빌트인 Object 특징

### 빌트인 Object의 특징

* 인스턴스를 만들 수 있는 모든 빌트인 오브잭트의 `__proto__`에 Object.prototype의 6개 메소드가 설정된다.  
    number, string 등등 의 인스턴스의 `__proto__`에도 설정된다는 말이다.  

* 따라서 빌트인 오브젝트로 만든 인스턴스에도 설정된다.  

### isPrototypeOf()

| 구분 | 데이터(값) |
| :---: | :---: |
| object  | 검색할 오브젝트.prototype |
| 파라미터 | 검색 대상 오브젝트 |
| 반환 | true, false |

* 파라미터에 작성한 오브젝트에서 object 위치에 작성한 prototype이 존재하면 true를 반환하고 존재하지 않으면 false를 반환한다.  

```js
var numObj = new Number(123);
console.log(Object.prototype.isPrototypeOf(numObj));
//값 : true
```  
1. Object.prototype처럼 오브젝트의 prototype을 작성한다.  
2. numObj에 Object.prototype의 존재를 체크한다.  
3. prototype이 존재하므로 true를 반환한다.  
    > `깊은 풀이 `  
    > 앞서 모든 빌트인 오브젝트엔 Object.prototype의 6개의 메소드가 들어있다 했다. 
    > new Number를 선언하여 number 인스턴스를 불러왔고 number 인스턴스 안에 `__proto__`가 있고 
    > 그 안에 또 `__proto__` 안에 Object.prototype의 6개의 메소드가 들어있으므로  
    > object.prototype이 존재하는 것이다.

### toString()

| 구분 | 데이터(값) |
| :---: | :---: |
| object  | Object 인스턴스 |
| 파라미터 | 사용불가 |
| 반환 | 변환한 값 |

* 인스턴스 타입을 문자열로 표시한다.  
```js
var point = {book: "책"};
console.log(point.toString());
// 값 : [object Object]

var obj = new Number(123);
console.log(Object.prototype.toString.call(obj));
// 값 : [object Number]
```  
1. toString() 앞에 Object 인스턴스를 작성했으며  
2. toString()을 실행하면 결과 값처럼 [object Object]를 표시한다.  
3. 앞의 소문자 object는 인스턴스를 나타내고 뒤의 대문자 Object는 빌트인 Object를 나타낸다.  

* 오브젝트에 toString()이 있으면 toString()이 호출되고  
    없으면 Object의 toString()이 호출된다.  

### toLocaleString()

| 구분 | 데이터(값) |
| :---: | :---: |
| data  | 변환 대상 |
| 파라미터 | 사용하지 않음 |
| 반환 | 변환한 값 |

* 지역화 문자 변환 메소드 대체 호출  
    Array, Number, Date 오브젝트의 toLocaleString()메소드가 먼저 호출된다.  
```js
console.log(1234.56.toLocaleString());
console.log("4567.89".toLocaleString());
// 값 : 1,234.56
// 값 : 4567.89
```  
1. 1234.56에 콤마(,)를 삽입하여 1,234.56으로 출력  
2. 이때에는 Number.prototype.toLocaleString()메소드가 호출된다.  
3. "4567.89"는 String 타입이며  
4. String.prototype.toLocaleString()이 없으므로  
5. Object,prototype.toLocaleString() 메소드가 호출된다.  
6. Object의 toLocaleString()이 없으면 애로거 발생한다. 즉, 에러 발생을 방지하기 위한 것이다.