### **📌 `var` 사용 금지 이유 & 현대적 대안**  

#### **1. `var`의 문제점**  
- **함수 스코프(Function Scope)**:  
  ```javascript  
  function example() {  
    if (true) {  
      var x = 10;  
    }  
    console.log(x); // 10 → 블록(`{}`) 무시하고 함수 전체에 영향  
  }  
  ```  
  - **블록 스코프 무시** → `if`, `for` 등에서 변수 누출 발생  

- **호이스팅(Hoisting)**:  
  ```javascript  
  console.log(y); // undefined (에러 X)  
  var y = 5;  
  ```  
  - **선언부만 끌어올림** → 초기화 전 사용 시 `undefined` 할당  

- **재선언 허용**:  
  ```javascript  
  var z = 1;  
  var z = 2; // 오류 없이 재선언 → 버그 위험 ↑  
  ```  

---

#### **2. `let` & `const` (ES6+)**  
- **블록 스코프(Block Scope)**:  
  ```javascript  
  if (true) {  
    let a = 10;  
    const b = 20;  
  }  
  console.log(a); // ReferenceError  
  ```  

- **재할당 가능 여부**:  
  - `let`: 재할당 ⭕  
  - `const`: 재할당 ❌ (단, **객체 내부 프로퍼티는 수정 가능**)  

- **TDZ(Temporal Dead Zone)**:  
  ```javascript  
  console.log(c); // ReferenceError (TDZ 구간)  
  let c = 30;  
  ```  

---

### **3. 왜 `var`를 버려야 할까?**  
1. **예측 불가능한 버그**  
   - 변수 중복 선언, 스코프 누출 → **대규모 프로젝트에서 치명적**  
2. **협업 어려움**  
   - 팀원들이 변수 사용 범위 파악 불가  
3. **모던 자바스크립트 표준 탈락**  
   - `let`/`const`가 모든 케이스 대체 가능  

---

### **4. 백엔드 개발자 관점에서의 핵심**  
- **모듈화**:  
  - `const`로 모듈 내 상수 정의 (ex: `const DB_CONFIG = {...};`)  
- **보안**:  
  - 스코프 제한으로 민감한 데이터 노출 방지  
- **클로저 활용**:  
  ```javascript  
  function createAuth() {  
    const token = "secret"; // 스코프로 보호  
    return { getToken: () => token };  
  }  
  ```  
- **에러 방지**:  
  - `const` 사용으로 의도치 않은 재할당 차단  

---

### **🚨 실무에서의 Best Practices**  
1. **기본적으로 `const` 사용**  
   - 변경 필요 시에만 `let`으로 전환  
2. **전역 변수 최소화**  
   - 모듈 시스템(`import`/`export`) 활용  
3. **스코프 철저히 제한**  
   - 함수/블록 내에서만 필요한 변수는 해당 영역에 선언  
4. **린팅 도구 사용**  
   - `ESLint`로 `var` 사용 금지 규칙 적용  

---

### **🔖 결론**  
- **`var`는 레거시 코드에서만 만난다고 생각하세요!**  
- **`let`** → 재할당 필요한 변수 (ex: 루프 카운터)  
- **`const`** → 90% 이상의 경우 사용 (ex: 설정값, 모듈)