---
title: Built-in object 2 Object
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

