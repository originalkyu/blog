---
title: "JavaScript Lecture2"
date: 2022-07-09T07:30:48+09:00
type: 
draft: false
---

## DOM
* HTML 문서의 프로그래밍 인터페이스
* 문서의 구조화된 표현을 제공
* 프로그래밍 언어가 문서 구조, 스타일, 내용 등을 변경할 수 있도록 함
* Core DOM, HTML DOM, XML DOM
* HTML DOM은 HTML 문서를 조작하고 접근하는 표준화된 방법
### Document 객체
* Document 객체는 웹 페이지를 의미
* 웹 페이지에 존재하는 HTML 요소에 접근할 때는 Document 객체부터 접근
### Document 메소드
* HTML 요소와 관련된 작업을 도와주는 다양한 메소드 제공
* HTML 요소의 선택과 생성
* HTML 이벤트 핸들러 추가
* HTML 객체의 선택

## Node 객체
### 노트와 노트 트리
* 노드는 HTML DOM에서 정보를 저장하는 계층적 단위이다
* 노드 트리는 노드들의 집합으로, 노드 간의 관계를 나타낸다
* 자바스크립트와 HTML DOM으로 노드 트리에 포함된 모든 노드에 접근할 수 있다
* 노드 트리의 모든 노드는 서로 계층적 관계를 맺는다
    * 부모노드, 형제노드
### 노드의 종류
* 문서 노드 : HTML 문서 전체를 나타낸다
* 요소 노드 : 모든 HTML 요소는 요소 노드로, 속성 노드를 가질 수 있는 유일한 노드이다
* 속성 노드 : HTML 요소의 모든 속성은 속성 노드. 요소 노드에 관한 정보를 가지지만, 해당 요소 노드의 자식 노드에는 포함되지 않는다.
* 텍스트 노드 : HTML 문서의 모든 텍스트는 텍스트 노드
* 주석 노드 : HTML 문서의 모든 주석은 주석 노드

## 이벤트(Event)
* 이벤트란 웹 브라우저가 알려주는 HTML 요소에 대한 사건의 발생이다. 
* 자바스크립트는 발생한 이벤트에 반응하여 특정 동작을 수행할 수 있다
### 이벤트 타입
* 폼, 키보드, 마우스, HTML DOM, Window 객체 등
### 이벤트 핸들러
* 이벤트가 발생했을 때 그 처리를 담당하는 함수
* 지정된 이벤트가 발생하면, 웹 브라우저는 그 요소에 등록된 이벤트 핸들러를 실행

---
<실습>
## DOM 요소의 선택
```JS
document.getElementsByTagName("div");  // 원하는 태그의 요소를 모두 선택
document.getElementById("banana");   // 아이디 선택
document.getElementsByClassName("vegetable");   // 해당 클래스에 속한 모든 요소 선택
document.getElementsByName("red");  // 해당 name 속성값을 가지는 요소를 모두 선택

document.querySelectorAll() // 해당 선택자로 선택되는 요소를 모두 선택
document.querySelector() // 해당 선택자로 선택되는 요소를 1개 선택
```
* document.getElementByTagName("div");
* document.getElementById("banana");
* document.getElementsByClassName("vegetable");
* document.getElementsByName("red");

## DOM 요소의 스타일 변경
```JS
var selectedId = document.getElementById("apple");
selectedId.style.color = "red"; 
```
* 선택한element.style.color = "red"

## DOM 요소의 내용 변경
```JS
var selectedId = document.getElementById("apple");
selectedId.innerHtml = "strawberry";
```
* 선택한Element.innerHtml = "abcd";

## 노드의 값(이름)에 접근해서 출력하기
```JS
var node1 = document.childNodes[2];
    // document의 자식 노드들 중 세 번째 노드를 node1에 할당
var node2 = node1.childeNodes[1];
    // node1의 자식 노드들 중 두 번째 노드를 node2에 할당
document.write(node1.nodeName);
    // node1의 이름을 출력
console.log(node2.childNodes);
    node2의 자식 변수를 모두 출력
```
* var node = document.childeNodes.childNodes[3];
* node.nodeName
* console.log(node);


## 노드의 값(값) 접근해서 변경하기
```JS
var node1 = document.getElementById("apple");
node1.firstChild.nodeValue = "banana";
    //node1의 첫번째 자식 노드의 값의 banana로
```
* 선택한노드.nodeValue = "abcd" // 선택한 노드의 값을 바꿀 수 있다
* 선택한노드.firstChild // 선택한노드의 첫번째 자식을 선택한다

## 노드의 값(타입) 접근 
```JS
// 1. 아이디가 apple인 요소의 첫번째 자식 노드를 선택하도록 코드를 작성하세요.
var apple_node = document.getElementById("apple").childNodes[0];

// 2. apple_node의 값을 변수에 할당하도록 코드를 작성하세요.
var apple_node_value = apple_node.nodeValue;

// 3. apple_node의 타입을 변수에 할당하도록 코드를 작성하세요.
var apple_node_type =  apple_node.nodeType;

// 4. apple_node의 값과 타입을 출력하도록 코드를 작성하세요.
document.write(apple_node_value);
document.write(apple_node_type);
```
* var apple_node_value = apple_node.nodeValue; // 선택한 노드의 nodeValue를 변수에 저장함

## 이벤트 핸들러 등록하기 1

<HTML에서 등록하기>

```HTML
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>자바스크립트 기초</title>
</head>
<body>

    <div name="text"  class="text" id="text">NULL</div>
    <button onclick="this.innerText = '성공입니다!'">클릭하세요!</button>
        <!-- HTML 태그에 이벤트 핸들러 등록하는 방법>-->
<script src="index.js"></script>
  
</body>
</html>
```
* HTML에서 이벤트를 등록할 수 있다
* onclik="this.innerText = '텍스트'" 를 이용해서 이벤트를 등록할 수 있다

<JS에서 등록하기>

```JS
// 자바스크립트 코드에서 등록
window.onload = fuction() 
{
    var text = document.getElementBId("text");
    text.innerHTML = "페이지가 열렸습니다";
}

```
* window.onload = function() {} 를 이용하면 HTML문서가 로드될 때 fucntion() 이 실행된다
* 노드.innerHTML 을 이용해서 요소의 내용을 바꿀 수 있다

## 이벤트 핸들러 등록하기 2
```JS
// step 1 요소 선택하기
var carrot_btn = document.getElementById("carrot"); 

// step 2 함수 만들기
function showText() {
    document.getElementById("text").innerHTML = "토끼가 나타났어요!!";
};

// step 3 이벤트 핸들러 등록하기
carrot_btn.addEventListener("click", showText);  
```
* 선택한요소.addEventListener("이벤트종류", 만든 함수 이름);
* 이벤트 종류
    * click : 마우스로 요소를 클릭
    * mouseover : 마우스를 요소 위에 올림
    * mousedown : 클릭 후 마우스를 떼지 않음
    * mouserup : 마우스 버튼을 떼는 순간, 드래그한 HTML 요소를 어딘가 놓을 때 사용할 수 있다
    * 이외에 아주 많다

## 이벤트 핸들러 등록하기 3
```JS
// id가 btn인 버튼을 클릭하면 id가 move인 상자의 크기가 변한다
function move() {
    var box = document.getElementById("move");
    box.style.width = "600px";
    box.style.height = "600px";
    box.style.left = "300px";
};

var btn = document.getElementById("btn");

btn.addEventListener("click", move);
```

## 이벤트 핸들러 등록하기 4
```JS
// Id가 one인 요소를 클릭하면 class에 on이 추가된다. 만약 이미 on이 있다면 사라지도록 한다
Tag1 = document.getElementById("one");

function handleOnclick() {
this.classList.toggle("on"); // 클래스 하나
}

divTag1.addEventListener("click", handleOnclick);
```
* this.classList.toggle("on"); // 이 요소의 class에 on이 없다면 추가, 있다면 삭제