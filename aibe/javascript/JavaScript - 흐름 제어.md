### 📌 **1. 조건문 (Conditional Statements)**  
프로그램이 **특정 조건에 따라 다른 코드를 실행**하도록 합니다.  
**➔ 예시**: "버튼을 클릭했을 때 로그인 상태면 프로필을 보여주고, 아니면 로그인 창을 띄워라"
#### (1) **`if` 문**  
```javascript
if (조건1) {
  // 조건1이 참일 때 실행
} else if (조건2) {
  // 조건2가 참일 때 실행
} else {
  // 모든 조건이 거짓일 때 실행
}
```

**🔍 예제**  
```javascript
const score = 85;

if (score >= 90) {
  console.log("A학점");
} else if (score >= 80) {
  console.log("B학점");  // 이 코드가 실행됨
} else {
  console.log("C학점");
}
```

#### (2) **`switch` 문**  
여러 조건을 **값 비교**로 분기할 때 사용 (※ `break` 필수!)  
```javascript
switch (변수) {
  case 값1:
    // 변수가 값1과 일치할 때 실행
    break;
  case 값2:
    // 변수가 값2와 일치할 때 실행
    break;
  default:
    // 모든 case와 일치하지 않을 때 실행
}
```

**🔍 예제**  
```javascript
const fruit = "사과";

switch (fruit) {
  case "사과":
    console.log("🍎");  // 실행됨
    break;
  case "바나나":
    console.log("🍌");
    break;
  default:
    console.log("❓");
}
```

---

### 📌 **2. 반복문 (Loops)**  
**동일한 작업을 반복**할 때 사용합니다.  
**➔ 예시**: "쇼핑몰 장바구니 목록을 하나씩 렌더링하라"

#### (1) **`for` 문**  
```javascript
for (초기값; 조건식; 증감식) {
  // 조건식이 참인 동안 반복 실행
}
```

**🔍 예제**  
```javascript
// 1부터 5까지 출력
for (let i = 1; i <= 5; i++) {
  console.log(i);  // 1, 2, 3, 4, 5
}
```

#### (2) **`while` 문**  
조건식이 참인 동안 계속 반복  
```javascript
while (조건식) {
  // 코드 실행
}
```

**🔍 예제**  
```javascript
let count = 0;

while (count < 3) {
  console.log("Hello!");  // 3번 출력
  count++;
}
```

#### (3) **`for...of` 문** (배열 순회)  
```javascript
const arr = [1, 2, 3];
for (const item of arr) {
  console.log(item);  // 1, 2, 3
}
```

#### (4) **`for...in` 문** (객체 키 순회)  
```javascript
const obj = { a: 1, b: 2 };
for (const key in obj) {
  console.log(key);  // "a", "b"
}
```

---

### 📌 **3. 제어문 (Control Flow)**  
반복문이나 조건문의 실행 흐름을 제어합니다.  

#### (1) **`break`**  
- 반복문 또는 `switch` 문 **즉시 종료**  
```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) break;  // i가 5가 되면 반복문 종료
  console.log(i);  // 0,1,2,3,4
}
```

#### (2) **`continue`**  
- 현재 반복을 건너뛰고 **다음 반복으로 이동**  
```javascript
for (let i = 0; i < 5; i++) {
  if (i === 2) continue;  // i=2는 건너뜀
  console.log(i);  // 0,1,3,4
}
```

#### (3) **`return`** (함수 내부)  
- 함수 실행을 종료하고 **값 반환**  
```javascript
function isAdult(age) {
  if (age < 19) return false;  // 여기서 함수 종료
  return true;
}
```

---

### 🚨 **주의사항 & 팁**  
1. **무한 루프 주의**: `while` 문에서 조건식이 항상 참이 되면 프로그램이 멈춥니다.  
   ```javascript
   // 절대 이렇게 작성하지 마세요! ❌
   while (true) {
     console.log("무한 반복...");
   }
   ```

2. **동등 연산자(`==`) vs 일치 연산자(`===`)**  
   - `===`는 **타입까지 체크** → 대부분 `===` 사용을 권장합니다.  
   ```javascript
   if (1 == "1")  // true (타입 변환 발생)
   if (1 === "1") // false
   ```

3. **삼항 연산자**  
   간단한 조건문은 한 줄로 작성 가능합니다.  
   ```javascript
   const isRainy = true;
   const message = isRainy ? "우산을 챙겨라" : "선크림 발라라";
   ```

---

### 💡 **Java vs JavaScript 차이**  
- **Java**: `for` 문 외에 `향상된 for문` (ex: `for (int num : numbers)`)  
- **JavaScript**: `for...of`, `for...in`으로 배열/객체 순회  
- **공통점**: `if`, `switch`, `while` 문법은 거의 동일합니다.
