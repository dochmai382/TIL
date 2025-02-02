단축 평가(Short-circuit Evaluation)는 **논리 연산자(`&&`, `||`)를 사용할 때, 표현식을 최소한으로 평가하는 방식**입니다. 이는 코드를 간결하게 만들고, 불필요한 연산을 줄여 성능을 최적화하는 데 유용합니다. 특히 JavaScript에서 자주 사용되니 꼭 이해해 두세요! 😊

---
### 📌 **단축 평가의 기본 개념**
1. **논리 연산자의 동작 원리**:  
   - `&&` (AND): **첫 번째 false 값을 반환** (모두 참이면 마지막 값 반환)  
   - `||` (OR): **첫 번째 true 값을 반환** (모두 거짓이면 마지막 값 반환)  

2. **핵심 아이디어**:  
   - **필요한 부분만 평가** → 나머지는 무시  
   - 예) `A && B`: `A`가 false면 `B`는 평가하지 않음  
   - 예) `A || B`: `A`가 true면 `B`는 평가하지 않음  

---

### 🚀 **단축 평가의 활용 예시**
#### 1. **AND (`&&`) 단축 평가**  
   - **용도**: 조건이 참일 때만 실행  
   ```javascript
   let isLoggedIn = true;
   isLoggedIn && console.log("로그인 성공!");  // "로그인 성공!" 출력
   ```

   - **예시**: 객체 프로퍼티 접근 (Optional Chaining 대체)  
   ```javascript
   let user = { name: "John" };
   let age = user && user.age;  // user.age가 없으므로 undefined
   console.log(age);  // undefined
   ```

#### 2. **OR (`||`) 단축 평가**  
   - **용도**: 기본값 설정  
   ```javascript
   let input = "";
   let username = input || "Guest";  // input이 falsy이므로 "Guest" 할당
   console.log(username);  // "Guest"
   ```

   - **예시**: 함수 인자 기본값 설정  
   ```javascript
   function greet(name) {
       name = name || "Guest";
       console.log(`Hello, ${name}!`);
   }
   greet();  // "Hello, Guest!"
   ```

---

### 💡 **비전공자를 위한 이해법**
1. **AND (`&&`)**:  
   - "모두 OK야?" → 첫 번째로 거짓인 사람이 나오면 바로 끝!  
   - 예) 친구들이 모두 와야 파티 시작 → 한 명이라도 안 오면 파티 취소  

2. **OR (`||`)**:  
   - "아무나 한 명만 와도 OK!" → 첫 번째로 참인 사람이 나오면 바로 끝!  
   - 예) 친구 1명이라도 오면 파티 진행 → 아무도 안 오면 기본 음식 주문  

---

### 📚 **실제 코드에서의 활용**
1. **조건부 렌더링 (React 등)**:  
   ```javascript
   const isAdmin = true;
   const adminPanel = isAdmin && <AdminPanel />;  // isAdmin이 true일 때만 렌더링
   ```

2. **기본값 설정**:  
   ```javascript
   const config = {
       port: process.env.PORT || 3000,  // 환경 변수가 없으면 3000 사용
   };
   ```

3. **에러 방지 (객체 프로퍼티 접근)**:  
   ```javascript
   let user = null;
   let name = user && user.name;  // user가 null이므로 undefined 반환 (에러 방지)
   ```

---

### ⚠️ **주의사항**
1. **의도치 않은 동작**:  
   - `0`, `""`, `false` 등 false 값이 유효한 값일 때 문제 발생  
   ```javascript
   let count = 0;
   let result = count || 10;  // 0은 false이므로 10 할당 (의도치 않은 동작)
   ```

2. **명확성**:  
   - 단축 평가가 과도하게 사용되면 가독성이 떨어질 수 있음  
   - **Optional Chaining(`?.`)**, **Nullish Coalescing(`??`)** 등 대체 문법 사용 권장  

---

### 🔥 **Optional Chaining과 Nullish Coalescing**
1. **Optional Chaining (`?.`)**:  
   - 객체 프로퍼티 접근 시 `null` 또는 `undefined`면 평가 중단  
   ```javascript
   let user = { name: "John" };
   let age = user?.age;  // user.age가 없으므로 undefined
   ```

2. **Nullish Coalescing (`??`)**:  
   - `null` 또는 `undefined`일 때만 기본값 할당  
   ```javascript
   let count = 0;
   let result = count ?? 10;  // 0은 유효한 값이므로 0 할당
   ```

---

### 📝 **정리**
| 연산자  | 설명                 | 예시                                         |
| ---- | ------------------ | ------------------------------------------ |
| `&&` | 첫 번째 false 값 반환    | `A && B` → `A`가 false면 `A` 반환              |
| ``   | 첫 번째 true 값 반환     | \`A B\`→ `A`가 true면 `A` 반환                 |
| `?.` | Optional Chaining  | `user?.name` → `user`가 없으면 `undefined`     |
| `??` | Nullish Coalescing | `A ?? B` → `A`가 `null`/`undefined`면 `B` 반환 |

---

❓ **예상 질문**  
Q: 단축 평가와 Optional Chaining의 차이는?  
A: 단축 평가는 논리 연산자(`&&`, `||`)를 사용해 평가를 생략하는 방식이고, Optional Chaining은 객체 프로퍼티 접근 시 `null`/`undefined`면 평가를 중단합니다.  

Q: `||`와 `??`의 차이는?  
A: `||`는 **false 값**(`0`, `""`, `false` 등)일 때 기본값을 할당하지만, `??`는 **`null`/`undefined`일 때만** 기본값을 할당합니다.  
