- `float`는 **요소를 컨테이너 안에서 왼쪽(`left`) 또는 오른쪽(`right`)으로 배치**하고, 다른 콘텐츠가 이를 둘러싸도록 만드는 속성
- 주로 이미지나 텍스트를 정렬할 때 사용

---

### **핵심 개념**

- **역할**: - 원래는 텍스트와 이미지를 나란히 배치하기 위한 용도로 설계.
  - 하지만 레이아웃 설계에도 많이 활용됨 (예: 2-컬럼 레이아웃).
- **값**: - `none`(기본값): 플로트 비활성화.
  - `left`: 요소를 왼쪽으로 플로트.
  - `right`: 요소를 오른쪽으로 플로트.
- **컨텐츠 흐름 영향**: - 플로트된 요소는 **일반 문서 흐름에서 제거**되어 다음 요소가 이를 따라 흐름.

---

### **문제점**

1. **부모 요소의 높이 상실**:
   - 플로트된 자식 요소는 부모 요소의 높이에 포함되지 않음.
2. **레이아웃 꼬임 발생 가능**:
   - 요소가 의도치 않게 겹치거나 비정상적으로 배치될 수 있음.

---

### **해결 방법**

- **`clearfix`를 사용해 부모 요소 높이 복구**:
  ```css
  .clearfix::after {
    content: "";
    display: table;
    clear: both;
  }
  ```
  ```html
  <div class="clearfix">
    <div style="float: left;">왼쪽 콘텐츠</div>
    <div style="float: right;">오른쪽 콘텐츠</div>
  </div>
  ```
- **BFC(Block Formatting Context) 활용**:  
   `overflow: hidden;`을 사용해 플로트 문제를 해결.

---

### **예제**

```html
<div class="container">
  <div class="box" style="float: left; width: 50%; background: lightblue;">
    왼쪽 박스
  </div>
  <div class="box" style="float: right; width: 50%; background: lightgreen;">
    오른쪽 박스
  </div>
</div>
```

---

### **현대적 대안**

- **플렉스박스(Flexbox)**: 플로트보다 간단하고 강력한 레이아웃 방식.
- **CSS 그리드(Grid)**: 정교한 레이아웃 설계에 적합.

---

- `float`는 과거 레이아웃의 핵심이었지만 **현재는 Flexbox와 Grid가 대세**.
- 플로트는 여전히 **텍스트와 이미지 정렬** 같은 간단한 작업에 유용.
- 레거시 코드를 유지하거나 디버깅할 때 `float`의 동작을 이해하는 것이 중요!

> `float`는 특정 상황에서만 사용됨
>
> - 특정 이미지/요소를 글자로 감싸야할 경우
> - 이질적인 플로우 설명할 때
