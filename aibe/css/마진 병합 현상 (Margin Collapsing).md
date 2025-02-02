마진 병합은 **인접한 블록 요소의 수직 마진이 겹칠 때 발생**하는 CSS 동작

---

### **마진 병합의 주요 특징**

- **==수직 마진만 병합==**된다.  
   (수평 마진은 병합되지 않음.)
- 병합된 마진은 **더 큰 값**을 사용한다.  
   (예: `20px`과 `10px` → 최종 마진은 `20px`.)
- **다음과 같은 경우에 발생:**
  1. **형제 요소 간 마진 병합**:  
     인접한 블록 요소들의 아래/위 마진이 겹칠 때.
  2. **부모와 자식 간 마진 병합**:  
     부모 요소의 위쪽 마진과 첫 번째 자식 요소의 위쪽 마진이 겹칠 때.
  3. **빈 블록 요소**:  
     내용이 없는 요소의 상하 마진이 병합될 수 있음.

---

### **예제**

#### 형제 요소 간 병합

```html
<div class="box1"></div>
<div class="box2"></div>
```

```css
.box1 {
  height: 50px;
  margin-bottom: 20px;
  background: lightblue;
}

.box2 {
  height: 50px;
  margin-top: 30px;
  background: lightgreen;
}
```

- 두 박스의 **수직 마진(20px, 30px)** → 병합되어 **최종 마진은 30px**.

#### 부모와 자식 간 병합

```html
<div class="parent">
  <div class="child"></div>
</div>
```

```css
.parent {
  margin-top: 20px;
  background: lightgray;
}

.child {
  margin-top: 30px;
  background: lightcoral;
}
```

- 부모의 위쪽 마진과 자식의 위쪽 마진이 병합 → **최종 마진은 30px**.

---

### **마진 병합 방지 방법**

1. **`overflow` 속성 사용**: 부모 요소에 `overflow: hidden;` 또는 `auto;` 추가.
2. **`padding` 추가**: 부모 요소에 상단/하단 `padding` 추가.
3. **`border` 추가**: 부모 요소에 상단/하단 `border`를 추가.
4. **BFC(Block Formatting Context) 생성**:  
   `display: flow-root;` 또는 `position: absolute;` 등으로 BFC를 활성화.

---

- 마진 병합은 블록 요소 간의 **불필요한 간격 조정 문제**를 방지하기 위해 설계된 CSS 동작.
- **`overflow: hidden;`** 같은 간단한 방법으로 대부분 해결 가능.
- 병합을 이해하고 필요에 따라 제어하면 레이아웃 디버깅이 훨씬 수월해짐!

> `<div>`로 외부를 감싸서 margin대신 padding으로 간격 조절하는 것도 하나의 방법
