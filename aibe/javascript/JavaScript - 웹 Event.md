
## ✅ **1. 태그에 직접 이벤트 추가 (인라인 이벤트)**
HTML 태그의 속성으로 이벤트를 추가하는 방법이야.
### **📌 예제: 인라인 이벤트**
```html
<button onclick="alert('버튼 클릭됨!')">클릭</button>
```
✔ HTML 태그 안에서 직접 `onclick` 속성을 사용해서 이벤트를 추가할 수 있음.  
✔ 하지만 이 방법은 **비추천!** (아래에서 이유 설명)

---
## ❌ **2. 인라인 이벤트가 비추천되는 이유**
### **🎯 1) 유지보수 어려움**
✔ HTML과 JavaScript 코드가 섞여서 **코드가 지저분**해지고 관리가 어려워져.  
✔ 여러 개의 이벤트를 추가하기 어렵고, 수정할 때 **HTML을 직접 고쳐야 함**.  
✔ 규모가 커지면 유지보수하기 힘들어짐.

```html
<!-- ❌ 인라인 이벤트 사용 -->
<button onclick="doSomething()">클릭</button>
```

```javascript
function doSomething() {
    alert("이벤트 실행!");
}
```

❌ 버튼이 많아지면 HTML에서 `onclick="doSomething()"`을 일일이 수정해야 함.

---
### **🎯 2) 여러 개의 이벤트 핸들러를 추가하기 어려움**

✔ `addEventListener()`를 쓰면 하나의 요소에 여러 개의 이벤트를 추가할 수 있지만,  
✔ 인라인 이벤트는 **새로운 이벤트를 추가하면 기존 이벤트가 덮어쓰기 됨**.

```html
<button onclick="firstFunction(); secondFunction();">클릭</button>
```
❌ 이런 식으로 여러 개의 함수를 실행하려면 **수동으로 다 써야 해서 불편**함.

---

### **🎯 3) `this`가 예상과 다를 수 있음**

✔ 인라인 이벤트에서 `this`는 **문자열로 실행**되기 때문에 예상과 다르게 동작할 수 있어.

```html
<button onclick="console.log(this)">클릭</button>
```
🚨 `this`가 `<button>` 요소가 아닌 **전역 객체 (`window`)를 가리킬 수도 있음**.

---

### **🎯 4) 보안 문제 (XSS 공격 위험)**

✔ 인라인 이벤트는 **보안적으로 취약**해서 XSS(크로스 사이트 스크립팅) 공격의 대상이 될 수 있어.  
✔ 공격자가 악성 스크립트를 HTML 태그 안에 삽입할 수 있음.

```html
<input type="text" value="<script>alert('해킹!')</script>">
```
🚨 이런 식으로 악성 스크립트가 삽입되면 보안 문제가 발생할 수 있음.

---

## ✅ **3. 권장하는 방법 (addEventListener 사용)**

✔ **JavaScript 코드와 HTML을 분리**해서 유지보수가 쉬움.  
✔ **여러 개의 이벤트를 추가할 수 있음.**  
✔ **보안적으로 더 안전함.**

```html
<button id="myButton">클릭</button>
```

```javascript
const button = document.getElementById("myButton");

button.addEventListener("click", function() {
    alert("버튼이 클릭됨!");
});
```

🚀 **HTML은 깔끔하게 유지하고, JS에서 이벤트를 추가하는 것이 최선!**

---
## 🔥 **결론: 인라인 이벤트는 비추천!**

✔ **HTML과 JavaScript가 섞이면 유지보수가 어렵다.**  
✔ **여러 개의 이벤트 핸들러를 추가할 수 없다.**  
✔ **this가 예상과 다르게 동작할 수 있다.**  
✔ **보안 문제(XSS 공격 위험)가 생길 수 있다.**  
✔ **`addEventListener()`를 사용하면 더 깔끔하고 유지보수하기 쉽다!**

---

# 이벤트 리스너
이벤트 리스너는 **사용자의 행동(클릭, 입력 등)을 감지하고 특정 동작을 실행**할 때 필수적이야.
## ✅ **1. 이벤트 리스너 사용 방법**
이벤트 리스너는 `addEventListener()` 메서드를 사용해서 추가해.
### **📌 기본 문법**
```javascript
element.addEventListener("이벤트이름", 실행할함수);
```

### **📌 예제: 버튼 클릭 이벤트**
```javascript
const button = document.getElementById("myButton");

button.addEventListener("click", function() {
    alert("버튼이 클릭됨!");
});
```
✔ **"click"** 이벤트가 발생하면 `function()` 내부의 코드가 실행돼.  
✔ 여러 개의 이벤트를 같은 요소에 **중복 등록 가능**.

---

## ✅ **2. 이벤트 리스너 사용 시 주의사항**

### **🎯 1) `onclick` 사용 대신 `addEventListener()` 사용하기**
```javascript
button.onclick = function() { alert("클릭!"); };
```

✔ `onclick`은 한 개의 이벤트 핸들러만 설정 가능 → **새 핸들러가 오면 덮어쓰기됨!**  
✔ `addEventListener()`는 **여러 개의 핸들러를 추가할 수 있음**.
```javascript
button.addEventListener("click", function() { alert("첫 번째!"); });
button.addEventListener("click", function() { alert("두 번째!"); });
```
✅ **출력:** "첫 번째!", "두 번째!" (둘 다 실행됨)

---

### **🎯 2) 이벤트 리스너 해제 (`removeEventListener`)**
이벤트 리스너를 제거할 때는 **함수를 변수로 저장한 후 제거**해야 해.
```javascript
function handleClick() {
    alert("클릭됨!");
}

button.addEventListener("click", handleClick);
button.removeEventListener("click", handleClick); // 리스너 제거
```

❌ **익명 함수는 제거 불가능!**
```javascript
button.addEventListener("click", function() { alert("클릭!"); });
button.removeEventListener("click", function() { alert("클릭!"); }); // 제거 안됨!
```

---

### **🎯 3) `this` 키워드 주의**

이벤트 리스너 안에서 `this`는 **이벤트가 발생한 요소를 가리킴**.
```javascript
button.addEventListener("click", function() {
    console.log(this); // 클릭된 버튼 요소를 가리킴
});
```

❌ 하지만 **화살표 함수 사용 시 `this`가 `window`를 가리킴**
```javascript
button.addEventListener("click", () => {
    console.log(this); // `window` 객체를 가리킴
});
```

---

## ✅ **3. 이벤트의 기본 동작 방지**
어떤 요소들은 기본적으로 특정 동작을 수행해.  
예를 들면:
- `<a>` 태그 → 클릭 시 페이지 이동
- `<form>` 태그 → 제출 시 페이지 새로고침
- `<input type="checkbox">` → 체크박스 선택/해제

이런 **기본 동작을 막고 싶을 때 `event.preventDefault()`를 사용**해.

### **📌 예제: 링크의 기본 이동 막기**
```javascript
const link = document.getElementById("myLink");

link.addEventListener("click", function(event) {
    event.preventDefault(); // 기본 이동 방지
    alert("링크 클릭했지만 이동 안 함!");
});
```

---

### **📌 예제: 폼 제출 방지**
```javascript
const form = document.getElementById("myForm");

form.addEventListener("submit", function(event) {
    event.preventDefault(); // 새로고침 방지
    alert("폼이 제출되지 않음!");
});
```

---
## 🔥 **정리 (핵심 요약!)**
✔ `addEventListener("이벤트명", 함수)` → 이벤트 감지 및 실행  
✔ `removeEventListener("이벤트명", 함수)` → 이벤트 제거 가능  
✔ **익명 함수는 제거 불가능** (`function`을 변수로 저장해야 함)  
✔ `event.preventDefault()` → **기본 동작(페이지 이동, 새로고침 등) 방지**  
✔ `this`는 일반 함수에서는 이벤트 발생 요소, **화살표 함수에서는 `window`**

