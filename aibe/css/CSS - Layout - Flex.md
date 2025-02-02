### **Flexbox의 핵심 개념**

Flexbox는 **"부모-자식" 관계**로 동작합니다.

- **부모(컨테이너)**: `display: flex`를 적용하면 자식 요소들이 유연하게 배치됩니다.
- **자식(아이템)**: 컨테이너 내에서 크기와 위치를 조절합니다.

---

### **1. 반드시 기억할 부모(컨테이너) 속성**

#### **(1) 방향 설정: `flex-direction`**

- 주축(main axis)을 결정합니다.
  ```css
  .container {
    flex-direction: row; /* 기본값 (가로) */
    flex-direction: column; /* 세로 */
  }
  ```

#### **(2) 정렬: `justify-content` & `align-items`**

- `justify-content`: **주축** 기준 정렬 (가로/세로)
- `align-items`: **교차축** 기준 정렬 (세로/가로)
  ```css
  .container {
    justify-content: center; /* 주축 중앙 정렬 */
    align-items: flex-start; /* 교차축 시작점 정렬 */
  }
  ```

#### **(3) 줄바꿈: `flex-wrap`**

- 아이템이 한 줄에 안 담길 때 **줄바꿈** 여부
  ```css
  .container {
    flex-wrap: wrap; /* 여러 줄로 배치 */
  }
  ```

---

### **2. 자식(아이템) 속성**

#### **(1) 비율 조정: `flex-grow`**

- 남는 공간을 아이템이 **차지하는 비율**
  ```css
  .item {
    flex-grow: 1; /* 모든 아이템이 균등한 크기 */
  }
  ```

#### **(2) 순서 변경: `order`**

- 아이템의 **배치 순서**를 숫자로 지정 (작은 수가 먼저)
  ```css
  .item2 {
    order: -1; /* .item2가 맨 앞으로 이동 */
  }
  ```

---

### **예제 1: 간단한 네비게이션 바**

```html
<nav class="navbar">
  <div class="nav-item">Home</div>
  <div class="nav-item">About</div>
  <div class="nav-item">Contact</div>
</nav>
```

```css
.navbar {
  display: flex;
  justify-content: space-between; /* 양쪽 끝 정렬 */
  padding: 1rem;
  background: #333;
  color: white;
}

.nav-item {
  padding: 0.5rem 1rem;
}
```

---

### **예제 2: 카드 레이아웃 (반응형)**

```html
<div class="card-container">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
</div>
```

```css
.card-container {
  display: flex;
  flex-wrap: wrap; /* 화면 줄이면 줄바꿈 */
  gap: 1rem; /* 아이템 사이 간격 */
}

.card {
  flex: 1; /* 남는 공간 균등 분배 */
  min-width: 200px; /* 최소 너비 (반응형) */
  padding: 2rem;
  background: #f0f0f0;
}
```

---

### **Flexbox의 본질: 축(axis) 중심**

- **메인축(main axis)**: `flex-direction`으로 방향 설정 (가로 `row` / 세로 `column` / 역방향 `row-reverse`, `column-reverse`)
- **교차축(cross axis)**: 메인축과 수직인 축

---

### **정렬의 핵심 3가지**

| 속성              | 역할                      | 예시 값                   |
| ----------------- | ------------------------- | ------------------------- |
| `justify-content` | **메인축** 정렬           | `center`, `space-between` |
| `align-items`     | **교차축** 정렬 (단일 줄) | `center`, `flex-start`    |
| `align-content`   | **교차축** 정렬 (여러 줄) | `stretch`, `space-around` |

---

### **반드시 기억해야 할 것**

1. **컨테이너에 `display: flex` 필수**  
   → 자식(아이템)은 자동으로 Flex 아이템이 됨
2. **기본값** - `flex-direction: row` (가로) - `justify-content: flex-start` (메인축 시작점) - `align-items: stretch` (교차축 꽉 채움) - `flex-shrink: 1` (아이템이 줄어들 수 있음) ← "쉬링크" 맞아요!

   > **`flex-shrink`**
   >
   > - 기본값이 `1`이므로 아이템이 컨테이너보다 크면 **줄어듭니다**.
   > - `flex-shrink: 0`으로 설정하면 줄어들지 않음 (예: 고정 사이드바)

3. **`gap`**: 아이템 간 간격 (예: `gap: 10px`)

#### 예제로 이해하기

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

```css title:'가로 중앙 정렬 + 세로 중앙 정렬'
.container {
  display: flex;
  justify-content: center; /* 메인축(가로) 중앙 */
  align-items: center; /* 교차축(세로) 중앙 */
  height: 300px; /* 세로 높이 필수! */
  border: 2px solid #333;
}

.item {
  width: 50px;
  height: 50px;
  background: tomato;
}
```

```css title:'아이템 간격 + 줄바꿈'
.container {
  display: flex;
  flex-wrap: wrap; /* 여러 줄 허용 */
  gap: 10px; /* 아이템 간 간격 */
}
```

---

### **💡 백엔드 개발자에게 중요한 이유**

- **협업**: 프론트엔드 팀의 레이아웃 방식을 이해하면 API 연동 시 구조 파악이 쉬워집니다.
- **간단한 수정**: 관리자 페이지나 기본 UI를 직접 조정할 때 유용합니다.
- **디버깅**: 프론트엔드 이슈를 더 정확히 파악할 수 있습니다.

---

### **주의사항**

- `flex`는 IE11에서 부분 지원되며, `gap` 속성은 최신 브라우저에서만 작동합니다.
- 복잡한 레이아웃은 `Grid`를 함께 사용하는 것이 효율적입니다.

Flexbox는 연습만이 답! [Flexbox Froggy](https://flexboxfroggy.com/) 게임으로 재밌게 익혀보세요 😊

---

> [!note] >[[CSS - Container vs. Item]]

> **이미지 정렬**:
>
> - 이미지는 기본적으로 `inline` 요소지만, Flex 컨테이너 안에서는 **Flex 아이템**으로 취급됩니다.
> - 따라서 `text-align` 대신 `justify-content`, `align-items`로 정렬해야 합니다.

> **세로축 정렬 어려움?**  
> → Flex에서는 `align-items: center`로 **세로 중앙 정렬이 초간단**해집니다!
