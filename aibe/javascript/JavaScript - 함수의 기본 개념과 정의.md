JavaScript에서 함수는 특정 작업을 수행하기 위한 독립된 코드 블록으로, 프로그램의 재사용성과 가독성을 높임

---

### **1. 함수 정의 방법**

- **함수 선언문 (Function Declaration)**:

  ```javascript
  function sum(a, b) {
    return a + b;
  }
  ```

  - **호이스팅 O**: 코드 실행 전에 메모리에 등록 → 어디서든 호출 가능.
  - **전역/함수 스코프**에 등록.

- **함수 표현식 (Function Expression)**:

  ```javascript
  const multiply = function (a, b) {
    return a * b;
  };
  ```

  - **호이스팅 X**: 변수 할당 이후에만 사용 가능.
  - **유연성 ↑**: 변수에 할당해 동적 생성 가능 (클로저, 모듈화에 활용).

- **화살표 함수 (Arrow Function)**:

  ```javascript
  const divide = (a, b) => a / b;

  const multiply = (a, b) => {
    return a * b;
  };
  ```

  - `this` **바인딩 X**: 상위 스코프의 `this`를 그대로 사용 (객체 메서드에 부적합).
  - **간결한 표현**: `return` 생략 가능 (한 줄일 때).

---

### **2. 함수 선언 vs 함수 표현식**

| 구분            | 함수 선언문        | 함수 표현식              |
| --------------- | ------------------ | ------------------------ |
| **호이스팅**    | O                  | X                        |
| **사용 시점**   | 선언 전 호출 가능  | 할당 후 호출 가능        |
| **적합한 경우** | 공통 유틸리티 함수 | 조건부 생성, 클로저 활용 |

---

### **3. 기본 매개변수 (Default Parameters)**

```javascript
function createUser(name = "Guest", age = 0) { ... }
```

- **목적**: 인수 누락 시 기본값으로 대체 → **안정성 ↑**
- **백엔드 활용**: API 파라미터 검증, DB 쿼리 기본값 설정.

---

### **4. 나머지 매개변수 (Rest Parameters)**

```javascript
function logItems(...items) {
  console.log(items); // 배열로 받음
}
```

- **목적**: 가변 인자 처리 → `arguments` 객체 대체.
- **백엔드 활용**: 동적 엔드포인트 처리 (ex: `/api/users/:id1/:id2`).

---

### **5. 콜백 함수 (Callback Function)**

```javascript
function fetchData(callback) {
  setTimeout(() => callback("Done!"), 1000);
}
```

- **목적**: 비동기 작업 후 실행 (ex: 파일 읽기, DB 조회).
- **주의**: **콜백 지옥(Callback Hell)** → `Promise`/`async-await`로 해결.
- **백엔드 예시**: Express.js 미들웨어, 라우트 핸들러.

---

### **6. 클로저 (Closure) & 렉시컬 환경**

```javascript
function createCounter() {
  let count = 0;
  return () => count++; // 클로저: count 변수에 접근 유지
}
```

- **클로저**: 클로저를 통해 내부 함수는 외부 함수의 변수에 접근 가능
  - 은닉화로 안전한 데이터 보관
- **렉시컬 환경**: 함수가 **정의된 위치**의 변수 스코프를 기억.
- **백엔드 활용**:
  - **캐시 시스템**: 상태 은닉으로 데이터 보호.
  - **미들웨어 팩토리**: 설정을 기반으로 동적 함수 생성.

---

### **7. 스코프 (Scope)**

- **전역 스코프**: 어디서든 접근 가능 → **남용 시 위험** (변수 충돌).
- ~~**함수 스코프**: `var`로 선언된 변수는 함수 내에서만 접근.~~ => [JavaScript - var에 대해서](/git_til/aibe/javascript/JavaScript%20-%20var에%20대해서.md)
- **블록 스코프**: `let`/`const` → `{}` 단위로 접근 제한.
- **백엔드 팁**: 모듈 단위 스코프 활용 → `module.exports`로 필요한 것만 노출.

```javascript title:'var vs. let/const (함수 스코프 vs. 블록 스코프)'
// var (함수 스코프)
function varExample() {
  if (true) {
    var a = 10;
  }
  console.log(a); // 10 → 블록({})을 무시하고 함수 전체에서 접근 가능
}

// let (블록 스코프)
function letExample() {
  if (true) {
    let b = 20;
  }
  console.log(b); // ReferenceError: b is not defined
}
```

```javascript title:'전역 스코프 오염 문제'
let globalVar = "전역 변수";

function modifyGlobal() {
  globalVar = "함수 내에서 수정"; // 전역 변수 변경 (위험!)
}

function createLocal() {
  let localVar = "로컬 변수"; // 함수 스코프로 격리
}
```

---

### **8. 반환값 (Return Value)**

- **명시적 반환**: `return` 없으면 `undefined` 반환.
- **순수 함수**: 동일 입력 → 동일 출력 (ex: 계산기 함수).
- **부수 효과**: 반환값 외에 외부 상태 변경 (ex: DB 업데이트).

```javascript title:'명시적 반환 vs. 암시적 반환'
// 명시적 반환 (Explicit Return)
function add(a, b) {
  return a + b; // 반환값: 숫자
}
console.log(add(2, 3)); // 5

// 암시적 반환 (Implicit Return - 화살표 함수)
const multiply = (a, b) => a * b; // return 생략 가능
console.log(multiply(2, 3)); // 6

// 반환값 없을 경우 → undefined
function noReturn() {
  console.log("Hello");
}
console.log(noReturn()); // undefined
```

---

### **🚨 백엔드 개발자에게 중요한 포인트**

1. **에러 핸들링 필수**:

   ```javascript
   function readFile(path) {
     try {
       const data = fs.readFileSync(path);
       return data;
     } catch (error) {
       console.error("백엔드 로깅 필수:", error);
       throw error;
     }
   }
   ```

2. **모듈화**:

   - 함수 단위로 비즈니스 로직 분리 (ex: `auth.js`, `database.js`).

3. **비동기 처리**:

   - `async/await` + `try/catch`로 DB 연결, 외부 API 호출 관리.

   ```javascript
   async function getUser(id) {
     const query = "SELECT * FROM users WHERE id = ?";
     return await db.execute(query, [id]);
   }
   ```

4. **메모리 관리**:

   - 클로저로 인한 메모리 누수 주의 → 불필요한 참조 제거.

5. **`this` 컨텍스트 주의**:
   - 화살표 함수의 `this`는 백엔드에서 예상치 못한 동작 유발 가능 (ex: Express.js 라우터).

---

### **🔖 핵심 요약**

- **함수 선언문**: 호이스팅 ⭕ → 전역 유틸리티 함수에 적합.
- **화살표 함수**: `this` 바인딩 ❌ → 콜백, 간단한 로직에 사용.
- **클로저**: 상태 은닉 → 캐시, 설정 관리에 활용.
- **콜백 → Promise**: 비동기 코드 가독성 향상.
- **스코프 관리**: `let`/`const` + 모듈화로 변수 충돌 방지.
