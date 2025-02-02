JavaScript에서 변수명, 함수명 등을 지을 때 **명명 규칙(Naming Convention)**은 코드의 가독성과 유지보수성을 높이는 데 매우 중요합니다. 다음은 널리 사용되는 규칙과 예시입니다.

---
### **1. 기본 규칙**
1. **문자 시작**:  
   - 반드시 문자(`a-z`, `A-Z`), `$`, `_`로 시작해야 합니다.  
   - 숫자로 시작할 수 없습니다.  
   ```javascript
   let name;  // O
   let _name; // O
   let $name; // O
   let 1name; // X
   ```

2. **대소문자 구분**:  
   - `myVar` ≠ `myvar` (다른 변수로 인식).

3. **예약어 금지**:  
   - `function`, `let`, `class` 등 JavaScript 예약어는 사용할 수 없습니다.  
   ```javascript
   let function = "hello"; // X
   ```

4. **특수 문자 금지**:  
   - `-`(하이픈)은 변수명에 사용할 수 없습니다.  
   ```javascript
   let user-name; // X
   ```

---

### **2. 표기법 (Case Styles)**
#### 1) **camelCase** (변수, 함수, 메서드)  
- 첫 단어는 소문자, 이후 단어의 첫 글자는 대문자.  
- **일반 변수, 함수**에 사용됩니다.  
  ```javascript
  let userName = "Kim";
  function getUserData() { ... }
  ```

#### 2) **PascalCase** (클래스, 생성자 함수)  
- 모든 단어의 첫 글자를 대문자로 작성.  
- **클래스, 컴포넌트**에 사용됩니다.  
  ```javascript
  class UserProfile { ... }
  function Car(model) { ... }
  ```

#### 3) **UPPER_CASE_SNAKE_CASE** (상수)  
- 단어를 모두 대문자로 작성하고 `_`로 구분.  
- **고정된 값(상수)**에 사용됩니다.  
  ```javascript
  const MAX_COUNT = 100;
  const API_ENDPOINT = "https://api.example.com";
  ```

#### 4) **snake_case** (일부 컨벤션)  
- 단어를 `_`로 구분 (JavaScript에서는 덜 사용됨).  
  ```javascript
  let user_name = "Lee"; // 프론트엔드보다 백엔드 언어에서 더 흔함
  ```

>[!tip]
>[[네이밍 케이스 종류]]


---
### **3. 의미 있는 이름 짓기**
#### 1) **변수**:  
- **무엇을 저장하는지 명확히 표현**.  
  ```javascript
  // Bad
  let d = 10; 

  // Good
  let daysSinceLastLogin = 10;
  ```

#### 2) **함수**:  
- **동작을 설명하는 동사**로 시작.  
  ```javascript
  // Bad
  function data() { ... }

  // Good
  function fetchUserData() { ... }
  ```

#### 3) **불리언(Boolean)**:  
- `is`, `has`, `can` 등으로 시작해 상태를 명시.  
  ```javascript
  let isLoggedIn = true;
  let hasPermission = false;
  ```

#### 4) **배열**:  
- 복수형 명사 또는 `List` 접미사 사용.  
  ```javascript
  let users = ["Kim", "Lee"];
  let colorList = ["red", "blue"];
  ```

#### 5) **이벤트 핸들러**:  
- `handle` 또는 `on` 접두사 사용.  
  ```javascript
  function handleClick() { ... }
  function onSubmit() { ... }
  ```

---
### **4. 주의사항**
1. **축약어 지양**:  
   - `usrNm` (X) → `userName` (O).  
2. **일관성 유지**:  
   - 프로젝트 내에서 동일한 컨벤션을 따르세요.  
3. **약어 처리**:  
   - `XMLHTTPRequest` (X) → `XmlHttpRequest` (O).  

---
### **5. 예제 코드**
```javascript
// 변수 (camelCase)
let itemPrice = 5000;
let isItemAvailable = true;

// 함수 (camelCase + 동사)
function calculateTotalPrice() { ... }

// 클래스 (PascalCase)
class ShoppingCart { ... }

// 상수 (UPPER_CASE_SNAKE_CASE)
const TAX_RATE = 0.1;
```

---
### **6. 백엔드 개발자를 위한 팁**
- **Node.js**에서도 동일한 컨벤션이 적용됩니다.  
- **데이터베이스 필드명**은 `snake_case`를 사용하는 경우가 많습니다.  
  ```javascript
  // MongoDB 예시
  const userSchema = new Schema({
    user_name: String,
    created_at: Date
  });
  ```

명명 규칙을 잘 지키면 코드가 직관적이고 협업이 수월해집니다. 🛠️