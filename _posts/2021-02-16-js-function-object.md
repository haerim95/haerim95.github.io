---
title: built in Function 4 Object
date: 2021-02-16
categories: [javascript]
comments: true
---

# Function 오브젝트

## Function 오브젝트 프로퍼티 리스트

<table>
    <thead>
        <tr>
            <th>이름</th>
            <th>개요</th>
        </tr>
    </thead>
    <tbody style="text-align: center;">
        <tr>
            <td colspan="2" style="font-weight:bold; background-color:#eeeeee;">Function</td>
        </tr>
        <tr>
            <td>new Function()</td>
            <td>인스턴스 생성</td>
        </tr>
         <tr>
            <td>Function()</td>
            <td>인스턴스 생성</td>
        </tr>
        <tr>
            <td colspan="2" style="font-weight:bold; background-color:#eeeeee;">Function 프로퍼티</td>
        </tr>
        <tr>
            <td>lenght</td>
            <td>함수의 파라미터 수</td>
        </tr>
         <tr>
            <td colspan="2" style="font-weight:bold; background-color:#eeeeee;">Function.prototype</td>
        </tr>
        <tr>
            <td>constructor</td>
            <td>생성자</td>
        </tr>
         <tr>
            <td>call()</td>
            <td>함수 호출</td>
        </tr>
         <tr>
            <td>apply()</td>
            <td>함수 호출 : 배열을 파라미터로 사용</td>
        </tr>
         <tr>
            <td>toString()</td>
            <td>함수를 문자열로 반환</td>
        </tr>
         <tr>
            <td>bind()</td>
            <td>새로운 오브젝트를 생성하고 함수 실행</td>
        </tr>
    </tbody>
</table>

---

## new Function()

<table>
    <thead>
        <tr>
            <th>구분</th>
            <th>데이터(값)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="2">파라미터</td>
            <td>실행 가능한 JS 코드 opt</td>
        </tr>
       <tr>
            <td>파라미터 opt</td>
       </tr>
        <tr>
            <td>반환</td>
            <td>생성한 Function 인스턴스</td>
        </tr>
    </tbody>
</table>

* Function 인스턴스 생성  
* 파라미터에 문자열로 함수의 파라미터와 함수 코드 작성  
    var obj = new Function("book", "return book;");  
    obj("JS 책");  
    obj는 function 인스턴스이다. `book`에 파라미터 값인 "js책"이 들어간다. `return book`은 함수 코드이다.  
* 파라미터 수에 따라 인스턴스 생성 기준이 다름  
    - 파라미터 2개 이상 작성  
        마지막 파라미터에 함수에서 실행할 함수 코드를 작성한다.  
        이를 제외한 파라미터에 이름을 작성한다. 
        ```js
        var obj = new Function("one", "two", "return one + two;");
        console.log(obj(100, 200));
        // 값 : 300
        ```  
        파라미터를 `3개` 작성했으며 첫번째와 두번째 파라미터는 호출한 곳에서 넘여준 값을 매핑할 파라미터 이름을 작성한다.  
        세번째는 호출되었을 때 실행될 함수 코드이다.  
    - 파라미터 하나 작성  
        함수에서 실행할 함수 코드 작성  
        파라미터가 없을 때 사용  
        ```js
        var obj = new Function("return 1 + 2;");
        console.log(obj());
        // 값 : 3
        ```  
    - 파라미터를 작성하지 않을 때  
        함수 코드가 없는 Function 인스턴스가 생성된다.  

## Function()

* Function 인스턴스 생성  
* 처리 방법과 파라미터 작성이 new Function()과 같다.  
* 차이점은 단지 new 연산자를 사용하지 않는 것 뿐이다.

---

