## ✅ **1. DOM이란?**

**DOM (Document Object Model)** 은 웹 문서를 **트리 구조로 표현한 객체 모델**이야. 
HTML 요소들을 **자바스크립트로 조작**할 수 있도록 해줘.

**📌 DOM의 핵심 개념:**
- 웹 브라우저가 **HTML을 읽고 트리 구조**로 변환한 것.
- 자바스크립트를 이용해 **HTML 요소를 추가, 수정, 삭제 가능**.
- 이벤트(클릭, 입력 등)를 감지하고 동적인 웹 페이지를 만들 수 있음.

---
## ✅ **2. DOM 기본 조작 (필수 메서드)**

### 🎯 **1) 요소 선택하기**
```javascript
const title = document.getElementById("title");  // ID로 선택
const buttons = document.getElementsByClassName("btn"); // 클래스 선택
const paragraphs = document.querySelectorAll("p"); // 모든 <p> 선택
```
📌 **DOM에서 특정 요소를 가져와야 조작 가능!**

---
### 🎯 **2) 요소 내용 변경하기**
```javascript
const title = document.getElementById("title");
title.textContent = "새로운 제목";  // 텍스트 변경
title.innerHTML = "<span style='color:red'>변경됨</span>"; // HTML 변경
```
📌 **서버에서 받은 데이터를 웹 페이지에 반영할 때 필수!**

---
### 🎯 **3) 요소 스타일 변경하기**
```javascript
const box = document.getElementById("box");
box.style.backgroundColor = "blue";  // 배경색 변경
box.style.display = "none";  // 요소 숨기기
```
📌 **백엔드에서 받은 응답에 따라 UI 변경할 때 유용!**

---
### 🎯 **4) 요소 추가 & 삭제**
```javascript
const newItem = document.createElement("div");  // 새로운 <div> 생성
newItem.textContent = "새로운 요소";
document.body.appendChild(newItem);  // 문서에 추가

const oldItem = document.getElementById("oldItem");
oldItem.remove();  // 요소 삭제
```
📌 **서버에서 받아온 데이터를 동적으로 추가할 때 필수!**

---
### 🎯 **5) 이벤트 추가 (버튼 클릭 등)**
```javascript
document.getElementById("btn").addEventListener("click", function() {
    alert("버튼 클릭됨!");
});
```
📌 **버튼 클릭 시 API 요청 보내거나, 유저 입력을 처리할 때 필요!**

---
## 🔥 **결론 (진짜 핵심 요약!)**
✔ **DOM = HTML을 트리 구조로 변환한 객체 모델**  
✔ **DOM 조작 = HTML 요소를 JS로 변경, 추가, 삭제**  
✔ **DOM을 알아야 폼 데이터 읽기, 서버 응답 반영 가능**  
