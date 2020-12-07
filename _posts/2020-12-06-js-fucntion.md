---
title: Javascript 함수
date: 2020-11-16
categories: [javascript]
comments: true
---

## 함수(Function)

* function
* 특정 기능을 처리하는 자바스크립트 코드의 묶음이다.
```js
// 형태 1
function book(){
    var title = "js 책";
};
// 형태2
var point = function(one, two){
    var total = one + two;
    var bonus = total + 100;
}
```
--- 

## 함수의 구성요소

1. function 키워드
2. 함수 이름
3. 파라미터
    * 매개변수, 인자, 아규먼트로도 부른다.
    * 파라미터의 작성은 선택이다.
4. 함수 Body
    * 중괄호{} 안에 작성한 코드
    * 함수코드, 소스 텍스트로도 부른다.
    * 함수코드 작성은 선택이다.

---

## 함수의 이름 규칙

* 첫 문자
    * 영문자, $, 언더바(_) : 사용가눙
    * 숫자, &, *, @, + : 사용 불가
* 함수 이름 작명권장법
    * 함수 코드를 읽지 않더라도
    * 함수 이름과 파라미터로 기능을 알 수 있도록
    * 시맨틱(의미, 뜻)을 부여하여 작명한다.

