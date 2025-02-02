### **1. 기준점이 다릅니다.**

- **`absolute`**  
  → **가장 가까운 "위치가 지정된 부모 요소"**를 기준으로 위치합니다.  
  → 부모 중에 `relative`, `absolute`, `fixed`가 **하나라도 있으면 그 부모를 기준**으로 움직입니다.  
  → 부모가 모두 `static`(기본값)이면 **브라우저 화면(뷰포트)**을 기준으로 합니다.

- **`fixed`**  
  → 무조건 **브라우저 화면(뷰포트)**을 기준으로 합니다.  
  → 부모 요소와 관계없이 **화면 전체**에서 위치를 잡습니다.

---

### **2. 스크롤 시 동작이 다릅니다.**

- **`absolute`**  
  → 스크롤을 내리면 **부모 요소와 함께 움직입니다.**  
  → 예: 부모 박스 안에 있는 작은 박스

- **`fixed`**  
  → 스크롤을 내려도 **화면에 고정되어 따라옵니다.**  
  → 예: 화면 하단의 "채팅 버튼", 상단의 "고정 메뉴"

---

### **3. 예시로 이해하기**

```html
<div class="parent">
  <div class="absolute-box">absolute</div>
  <div class="fixed-box">fixed</div>
</div>
```

```css
.parent {
  position: relative; /* absolute-box의 기준이 됨 */
  height: 2000px; /* 스크롤 테스트를 위해 높이 설정 */
  background: lightgray;
}

.absolute-box {
  position: absolute;
  top: 20px;
  left: 20px;
  background: tomato;
}

.fixed-box {
  position: fixed;
  top: 20px;
  right: 20px;
  background: navy;
  color: white;
}
```

- **결과**
  - `absolute-box`는 회색 부모 박스 안에서 (20px, 20px) 위치에 고정됩니다.
  - `fixed-box`는 화면 오른쪽 상단 (20px, 20px)에 고정되며, 스크롤을 내려도 계속 보입니다.

---

### **4. 정리 표**

| 구분       | `absolute`             | `fixed`                         |
| ---------- | ---------------------- | ------------------------------- |
| **기준점** | 부모 요소 or 화면      | 무조건 화면                     |
| **스크롤** | 부모와 함께 움직임     | 화면에 고정                     |
| **용도**   | 부모 내 특정 위치 배치 | 화면에 고정된 요소 (버튼, 메뉴) |

---

### **💡 초보자 팁**

- `absolute`를 쓸 땐 **부모에 `position: relative`를 꼭 추가**하세요!
- `fixed`는 모바일에서 가상 키보드가 나타날 때 의도치 않게 움직일 수 있어요. 주의!
