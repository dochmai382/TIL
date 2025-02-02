### **CSS Position의 핵심 개념**

#### **position 속성 값**

##### static(기본값):

- 요소를 **문서 흐름(normal flow)** 에 따라 배치.
- `top`, `left` 등 위치 속성이 적용되지 않음.
  > - 명시적으로 `position: static`을 쓰는 경우는 다른 위치 속성을 초기화할 때

##### relative:

- 요소를 원래 위치를 기준으로 **상대적**으로 배치.
- 다른 요소의 위치에 영향을 주지 않음.
  > - **새로운 기준**이 됨 → 자식 요소의 `absolute` 위치 기준으로 사용 가능.

##### absolute:

- 요소를 **가장 가까운 positioned 부모 요소**(`relative`, `absolute`, `fixed` 등) 기준으로 배치
- 문서 흐름에서 제거됨
  > - **static이 아닌 가장 가까운 부모** 기준으로 배치
  > - 기준이 없으면 **뷰포트(초기 컨테이닝 블록)**를 기준으로 함
  >   - `body`가 `position:static`인 경우
  >   - 보통 `html`요소
  > - 기준이 되는 부모 요소 안에서 스크롤시 함께 움직임

##### fixed :

- 요소를 **뷰포트(화면) 기준**으로 고정
- 스크롤 시에도 같은 위치에 머뭄 (= 영향을 받지 않음)

##### sticky:

- `relative`와 `fixed`를 혼합
- 특정 스크롤 위치에 도달하면 고정됨

#### **요약 표**

| 속성       | 기준점                      | 문서 흐름 | 스크롤 영향            |
| ---------- | --------------------------- | --------- | ---------------------- |
| `static`   | X (기본 흐름)               | 유지      | 영향받음               |
| `relative` | 자신의 원래 위치            | 유지      | 영향받음               |
| `absolute` | 가장 가까운 positioned 부모 | 제거      | 부모 기준으로 영향받음 |
| `fixed`    | 뷰포트(화면)                | 제거      | 영향받지 않음          |

#### **중요 포인트**

- `absolute` 사용 시, 부모 요소에 `position: relative`를 명시해야 예측 가능한 위치에 배치됨.
- `fixed`는 뷰포트를 기준으로 하므로 모달 창, 네비게이션 바에 유용함
- `sticky`는 `top: 0` 같은 임계값을 지정해야 동작함.
- `z-index`로 요소의 쌓임 순서를 제어할 수 있음(기본값 0, 값이 클수록 위쪽).

---

### **예제 코드**

#### 1. `relative` + `absolute` 조합 (흔한 패턴)

```html
<div class="parent">
  <div class="child"></div>
</div>
```

```css
.parent {
  position: relative; /* 자식 요소의 기준점이 됨 */
  width: 300px;
  height: 200px;
  background: lightgray;
}

.child {
  position: absolute;
  top: 20px; /* 부모(parent)의 상단에서 20px 떨어진 위치 */
  left: 30px;
  width: 100px;
  height: 50px;
  background: tomato;
}
```

#### 2. `fixed` (고정 네비게이션 바)

```css
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background: navy;
  color: white;
  padding: 1rem;
}
```

#### 3. `sticky` (스크롤 시 헤더 고정)

```css
.header {
  position: sticky;
  top: 0; /* 뷰포트 상단에 도달하면 고정 */
  background: white;
  padding: 1rem;
  border-bottom: 1px solid #ddd;
}
```

---

### **주의사항**

- `absolute` 요소는 문서 흐름에서 **제거**되므로 레이아웃이 깨질 수 있음.
- `fixed`는 모바일 브라우저에서 예상치 못한 동작을 할 수 있음
- `sticky`는 Internet Explorer에서 지원되지 않음⚠️

---

> [Position - absolute vs. fixed](./CSS%20-%20Layout%20-%20Position%20-%20absolute%20vs.%20fixed.md)
