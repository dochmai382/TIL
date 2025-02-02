### 📌 **JavaScript의 정의와 특징**

1. **정의**:

   - JavaScript는 **웹 페이지를 동적으로 만드는 스크립트 언어**입니다.
   - HTML/CSS와 함께 웹 개발의 3대 요소 중 하나입니다.
   - 최근에는 프론트엔드뿐만 아니라 백엔드(Node.js), 모바일 앱(React Native), 데스크톱 앱(Electron) 등 다양한 분야에서 사용됩니다.

2. **특징**:
   - **인터프리터 언어**: 코드를 한 줄씩 실행 (컴파일 필요 없음)
   - **동적 타입**: 변수의 타입이 실행 시점에 결정 (유연하지만, 주의 필요)
   - **이벤트 기반**: 사용자 동작(클릭, 스크롤 등)에 반응
   - **비동기 처리**: `Promise`, `async/await`로 비동기 작업 처리 가능

---

### 🚀 **JavaScript 기본 문법 구조**

1. **변수 선언**:
   - `var`: 함수 스코프 (호이스팅 발생)
   - `let`: 블록 스코프 (재할당 가능)
   - `const`: 블록 스코프 (재할당 불가능, 상수)
   ```javascript
   var name = "John"; // 함수 스코프
   let age = 30; // 블록 스코프
   const PI = 3.14; // 상수
   ```

> [JavaScript 명명 규칙](/git_til/conventions/JavaScript%20명명%20규칙.md)

> [JavaScript - var에 대해서](/git_til/aibe/javascript/JavaScript%20-%20var에%20대해서.md)

2. **타입**:
   - **원시 타입**: `String`, `Number`, `Boolean`, `null`, `undefined`, `Symbol`, `BigInt`
   - **객체 타입**: `Object`, `Array`, `Function`, `Date` 등
   ```javascript
   let text = "Hello"; // String
   let count = 10; // Number
   let isActive = true; // Boolean
   let user = { name: "John" }; // Object
   ```

> Q. 왜 문자가 아니라 문자열인가?
>
> - 초기 컴퓨터는 메모리가 작아서 문자를 하나하나의 character 형태로 저장했음
> - 문자를 저장하고 배열로 묶어서 저장하는 것이 일반적이었음 (문자배열)
> - 컴퓨터 성능이 발전하면서 줄string처럼 하나의 문자를 관리하자 == 문자열
> - 문자열의 특징 :
>   - 0 ~ n개로 길이가 있음

> [!note] >[undefined vs. null](/git_til/aibe/javascript/undefined%20vs.%20null.md)

3. **연산자**:
   - 산술: `+`, `-`, `*`, `/`, `%`
   - 비교: `==`, `===`, `!=`, `!==`
   - 논리: `&&`, `||`, `!`
   ```javascript
   let sum = 10 + 5; // 15
   let isEqual = 10 === "10"; // false (타입까지 비교)
   ```

---

### 📌 **스코프(Scope)**

1. **스코프란?**

   - 변수가 접근 가능한 범위를 말합니다.
   - **전역 스코프**: 코드 전체에서 접근 가능
   - **지역 스코프**: 함수 또는 블록(`{}`) 내에서만 접근 가능

2. **예시**:

   ```javascript
   let globalVar = "전역 변수"; // 전역 스코프

   function myFunction() {
     let localVar = "지역 변수"; // 함수 스코프
     console.log(globalVar); // 접근 가능
   }
   console.log(localVar); // 접근 불가능 (에러 발생)
   ```

---

### 🚀 **일급 객체(First-Class Citizen)**

1. **일급 객체란?**

   - JavaScript에서 함수는 **일급 객체**입니다.
   - 즉, 함수를 변수에 할당하거나, 인자로 전달하거나, 반환값으로 사용할 수 있습니다.

2. **예시**:

   ```javascript
   // 1. 변수에 할당
   let greet = function () {
     console.log("Hello!");
   };

   // 2. 인자로 전달
   function executeFunction(func) {
     func();
   }
   executeFunction(greet); // "Hello!"

   // 3. 반환값으로 사용
   function createGreeting() {
     return function () {
       console.log("Hi!");
     };
   }
   ```

---

### 📌 **호이스팅(Hoisting)**

1. **호이스팅이란?**

   - 변수와 함수 선언이 코드의 최상단으로 끌어올려지는 현상입니다.
   - 단, **선언만 끌어올려지고, 할당은 그대로 유지**됩니다.

2. **예시**:

   ```javascript
   console.log(x); // undefined (호이스팅 발생)
   var x = 10;

   // 함수 호이스팅
   sayHello(); // "Hello!" (함수 선언 전체가 호이스팅됨)
   function sayHello() {
     console.log("Hello!");
   }
   ```

---

### 🚀 **타입과 연산자**

1. **타입 변환**:

   - **동적 타입** 언어이므로, 타입이 유연하게 변환됩니다.

   ```javascript
   let num = 10;
   let str = "20";
   console.log(num + str); // "1020" (문자열로 변환)
   ```

2. **엄격한 비교(`===`)**:
   - 타입과 값을 모두 비교합니다.
   ```javascript
   console.log(10 == "10"); // true (값만 비교)
   console.log(10 === "10"); // false (타입과 값 비교)
   ```

---

### 💡 **비전공자를 위한 이해법: 변수와 타입**

- **변수**는 **상자**라고 생각하세요.
  - `let`: 내용물을 바꿀 수 있는 상자
  - `const`: 내용물을 바꿀 수 없는 상자
- **타입**은 상자에 들어갈 **물건의 종류**입니다.
  - 숫자, 문자열, 불리언 등 다양한 물건을 넣을 수 있지만, 잘못된 물건을 넣으면 문제가 생깁니다.

---

### 📌 **논리 연산자 (Logical Operators)**

#### 1. **AND (`&&`)**

- **모든 조건이 참일 때** `true` 반환 (단축 평가: 첫 번째 거짓 값 반환)

```javascript
console.log(true && true); // true
console.log(10 > 5 && 3 < 2); // false (3 < 2가 거짓)

// 실제 활용: 조건이 모두 충족될 때만 실행
isLoggedIn && renderDashboard(); // 로그인 시 대시보드 표시
```

#### 2. **OR (`||`)**

- **하나 이상 참이면** `true` 반환 (단축 평가: 첫 번째 참 값 반환)

```javascript
console.log(false || true); // true
console.log(0 || "Hello"); // "Hello" (0은 falsy)

// 실제 활용: 기본값 설정
const username = inputName || "Guest"; // 입력 없으면 "Guest" 할당
```

#### 3. **NOT (`!`)**

- **참/거짓을 반전**

```javascript
console.log(!true); // false
console.log(!0); // true (0은 falsy)

// 실제 활용: 상태 토글
let isActive = false;
isActive = !isActive; // true로 변경
```

> [!note] >[[단축 평가 (Short-circuit Evaluation)]]

---

### 🚀 **삼항 연산자 (Ternary Operator)**

- **간단한 조건문을 한 줄로 처리**
- **구조**: `조건 ? 참일 때 값 : 거짓일 때 값`

#### 1. 기본 사용 예시

```javascript
let age = 20;
let status = age >= 18 ? "성인" : "미성년자"; // "성인"
```

#### 2. 중첩 삼항 연산자 (주의: 가독성 ↓)

```javascript
let score = 85;
let grade = score >= 90 ? "A" : score >= 80 ? "B" : score >= 70 ? "C" : "F"; // "B"
```

#### 3. 백엔드 활용 예시

```javascript
// API 응답 처리
const response = {
  data: user ? user.name : null, // user가 있으면 name, 없으면 null
};

// 환경 변수 설정
const port = process.env.PORT || 3000; // OR 연산자와 함께 사용
```

---

### 💡 **비전공자를 위한 이해법**

1. **AND (`&&`)** → "모두 OK야?" (친구들이 모두 와야 파티 시작)
2. **OR (`||`)** → "아무나 한 명만 와도 OK!" (친구 1명이라도 오면 파티 진행)
3. **삼항 연산자** → "Yes or No 선택지" (자판기 버튼: 커피☕️ or 차🍵)

---

### 📚 **학습 방법**

1. **간단한 조건문을 삼항 연산자로 바꿔보기**

   ```javascript
   // Before
   let message;
   if (isRainy) {
     message = "우산을 챙기세요!";
   } else {
     message = "날씨가 좋습니다!";
   }

   // After
   let message = isRainy ? "우산을 챙기세요!" : "날씨가 좋습니다!";
   ```

2. **논리 연산자로 기본값 처리 연습**

   ```javascript
   // 사용자 설정이 없으면 기본 테마 적용
   const theme = userSettings.theme || "light";
   ```

3. **실전 문제**
   - **문제**: `temperature` 변수가 30 이상이면 "Hot", 20~29면 "Warm", 20 미만이면 "Cool" 출력
   - **정답**:
     ```javascript
     let temperature = 25;
     let result =
       temperature >= 30 ? "Hot" : temperature >= 20 ? "Warm" : "Cool";
     console.log(result); // "Warm"
     ```

---

### ⚠️ **주의사항**

- **삼항 연산자 중첩은 2번 이상 금지** → `if-else`로 리팩토링 권장
- **논리 연산자 남용** → `&&`로 복잡한 로직 처리 시 가독성 저하

---

❓ **예상 질문**  
Q: `false || "Hello"`의 결과는 왜 "Hello"인가요?  
A: **OR 연산자**는 첫 번째 참(false가 아닌) 값을 반환합니다. `false`는 false이므로 다음 값인 "Hello"가 반환됩니다.

Q: 삼항 연산자를 백엔드에서 어디에 쓸 수 있나요?  
A: **환경 변수 설정**, **에러 메시지 동적 처리**, **DTO 객체에서 조건부 필드 추가** 등에 활용됩니다!
