### ES6의 정의
ES6(ECMAScript 2015)는 JavaScript의 주요 업데이트로, 2015년에 출시되었습니다. 이 버전은 현대적인 프로그래밍을 지원하기 위해 다양한 새 기능과 문법을 도입했습니다.

### ES6의 배경
ES6가 나온 배경은 다음과 같습니다:
1. **현대적 요구 충족**: 웹 애플리케이션의 복잡성이 증가하면서, 더 강력하고 효율적인 언어 기능이 필요해졌습니다.
2. **개발자 생산성 향상**: ES6는 코드를 더 간결하고 읽기 쉽게 만들어 개발자의 생산성을 높이기 위해 설계되었습니다.
3. **표준화 필요**: JavaScript의 다양한 구현을 표준화하여 브라우저 간 호환성을 개선하고자 했습니다.
4. **커뮤니티 요구**: 개발자 커뮤니티에서 모던 프로그래밍 언어 기능에 대한 요구가 증가했고, 이에 따라 ES6가 개발되었습니다.
### **📌 ES6의 주요 기능 (10가지로 압축)**
#### 1. **`let` & `const` (변수 선언)**  
- **`var`의 문제점** (`함수 스코프`, 호이스팅)을 해결  
- **`let`**: 블록 스코프 + 재할당 가능  
- **`const`**: 블록 스코프 + 재할당 불가 (상수)  
```javascript
let name = "철수";
name = "영희";  // 가능

const PI = 3.14;
PI = 5;  // ❌ Error!
```

#### 2. **화살표 함수 (Arrow Function)**  
- **간결한 문법** + **`this` 바인딩 방식 변경** (상위 스코프의 `this`를 가짐)  
```javascript
// 기존 함수
function add(a, b) { return a + b; }

// 화살표 함수
const add = (a, b) => a + b;
```

#### 3. **템플릿 리터럴 (Template Literal)**  
- **백틱(`)**으로 문자열 + 변수 삽입 (`${}`)  
```javascript
const name = "철수";
console.log(`안녕하세요, ${name}님!`);  // "안녕하세요, 철수님!"
```

#### 4. **비구조화 할당 (Destructuring)**  
- **객체/배열**을 쉽게 분해해서 변수 할당  
```javascript
// 객체
const user = { name: "철수", age: 20 };
const { name, age } = user;  // name = "철수", age = 20

// 배열
const [first, second] = [1, 2];  // first = 1, second = 2
```

#### 5. **기본 매개변수 (Default Parameters)**  
- 함수의 **파라미터 기본값 설정**  
```javascript
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}
greet();  // "Hello, Guest!"
```

#### 6. **Rest & Spread 연산자**  
- **Rest (`...`)**: 함수 파라미터를 배열로 묶기  
- **Spread (`...`)**: 배열/객체를 펼치기  
```javascript
// Rest
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b);
}
sum(1, 2, 3);  // 6

// Spread
const arr1 = [1, 2];
const arr2 = [...arr1, 3];  // [1, 2, 3]
```

#### 7. **클래스 (Class)**  
- 객체 지향 프로그래밍을 위한 **문법적 설탕** (Prototype 기반)  
```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(`Hello, ${this.name}!`);
  }
}

const 철수 = new Person("철수");
철수.greet();  // "Hello, 철수!"
```

#### 8. **모듈 (Module)**  
- **`import`/`export`**로 코드를 모듈화  
```javascript
// math.js
export const add = (a, b) => a + b;

// main.js
import { add } from './math.js';
```

#### 9. **프로미스 (Promise)**  
- **비동기 작업**을 편리하게 처리 (콜백 지옥 해결)  
```javascript
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve("데이터 받음!"), 1000);
  });
};

fetchData()
  .then(data => console.log(data))  // "데이터 받음!"
  .catch(error => console.error(error));
```

#### 10. **새로운 데이터 구조**  
- **`Map`**, **`Set`**, **`Symbol`** 추가  
```javascript
const map = new Map();
map.set("name", "철수");  // 키-값 저장

const set = new Set([1, 2, 2, 3]);  // 중복 허용 X → [1, 2, 3]
```

---
### **🚀 ES6가 중요한 이유**  
1. **코드 가독성** ↑ (화살표 함수, 템플릿 리터럴)  
2. **유지보수성** ↑ (모듈화, 클래스)  
3. **비동기 처리** 간소화 (Promise → async/await의 기반)  
4. **모던 프레임워크** (React, Vue, Angular)가 ES6 기반으로 동작  

---
### **💡 실전 팁**  
- **Babel**: ES6+ 코드를 구형 브라우저에서 호환되게 변환  
- **Polyfill**: 새로운 메서드 (ex: `Array.includes()`)를 구형 환경에서 사용 가능하게 함  
