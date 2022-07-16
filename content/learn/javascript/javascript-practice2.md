---
title: "Javascript Practice2"
date: 2022-07-09T11:15:02+09:00
type: 
draft: false
---


## Element를 서서히 사라지게 하기
```JS
// step1 id가 game인 element 가져오기
// step2 display 속성을 변경하여 요소가 사라지는 함수 만들기
function hide_game() 
{
    document.getElementById("game").style.display = "none";
}

// step3 id가 btn인 element를 클릭하면 만든 함수가 실행되는 이벤트를 등록
document.getElementById("btn").addEventListener("click", hide_game);
```

## FORM을 통한 입출력 문제
* <form> 태그를 이용해서 입력된 값에 따라 특정 값을 화면에 출력
```JS


// step1 <form> 태그의 값을 가져오는 함수 만들기
function getValue(e)
{
    // step1-1 필요한 element 가져오기
    var form = document.getElementById("form");
    var input = document.getElementById("input");
    var answer = document.getElementById("answer");

    // step1-2
    e.preventDefault();
        // 결과가 잠깐만 보이고 창이 새로 열리는 것을 방지함
    var val = input.value;
    if(val) {
        if(val >=50) {
            anser.textContent = "우산을 챙긴다.";
        }
        else {
            answer.textContent = "그냥 간다.";
        }
    }
    // step1-3
    form.reset(); 
        // 제출 시마다 텍스트 박스를 비워준다
}

// step2 이벤트 핸들러 등록하기
var form = document.getElementById("form");
form.addEventListener("submit", getValue(e));
```
=> 내가 생각한 답 : 오답
```JS
var form = document.getElementById('form');
var input = document.getElementById('input');
var answer = document.getElementById('answer');

form.addEventListener('submit', function(e) {
  e.preventDefault();


  var val = input.value;
  
  if(val) {
  
    if (val >= 50) {
      answer.textContent = '우산을 챙긴다.';
    }
    else {
      answer.textContent = '그냥 간다.';
    }
    
    form.reset();
  }
})
```

## DOM 요소 선택하기

## DOM 요소 렌더링

## DOM 사용자 등록하기

## 자동차 경주

## 쇼핑 리스트 만들기

## DOM Tree로 브라우저 형태 변형 - insertBefore()

## 스타벅스 메뉴 세기