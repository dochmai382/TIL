### **화살표 함수 (Arrow Function)**

화살표 함수는 ES6에서 도입된 함수 표현식의 간결한 형태입니다. 기존의 `function` 키워드를 사용한 함수 표현식보다 짧게 작성할 수 있습니다.

#### **1. 여러 줄 본문 처리**

화살표 함수의 본문이 여러 줄일 경우 중괄호 `{}`를 사용하고, `return` 키워드를 명시해야 합니다.

```javascript
// 단일 줄: return 생략 가능
const add = (a, b) => a + b;

// 여러 줄: {}와 return 필수
const getUser = (id) => {
  const user = { id: id, name: "Alice" };
  return user;
};
```

#### **2. `this` 바인딩 차이**

화살표 함수는 자신만의 `this`를 가지지 않고, 상위 스코프의 `this`를 그대로 사용합니다. 이는 일반 함수와의 큰 차이점 중 하나입니다.

```javascript
// 일반 함수: 자신의 this 생성 (호출 방식에 따라 달라짐)
const obj1 = {
  value: 10,
  regularFunc: function () {
    console.log(this.value); // 10 (obj1의 value)
  },
};

// 화살표 함수: 상위 스코프의 this를 고정
const obj2 = {
  value: 20,
  arrowFunc: () => {
    console.log(this.value); // undefined (상위 스코프의 this = 전역)
  },
};
```

---

### **고차 함수 (Higher-Order Function)**

고차 함수는 함수를 인자로 받거나 함수를 반환하는 함수를 말합니다. JavaScript에서는 배열 메서드인 `map`, `filter`, `reduce`, `forEach` 등이 대표적인 고차 함수입니다.

#### **1. `map`**

배열의 각 요소에 대해 함수를 적용하고, 그 결과를 **새로운 배열**로 반환합니다.

```javascript
const numbers = [1, 2, 3];
const doubled = numbers.map((num) => num * 2);
console.log(doubled); // [2, 4, 6]
```

#### **2. `filter`**

배열의 각 요소에 대해 조건을 검사하고, **조건을 만족**하는 요소만 **새로운 배열**로 반환합니다.

```javascript
const evenNumbers = numbers.filter((num) => num % 2 === 0);
console.log(evenNumbers); // [2]
```

#### **3. `reduce`**

배열의 각 요소에 대해 누적값과 현재값을 사용하여 **하나의 결과값을 반환**합니다.

```javascript
const sum = numbers.reduce((acc, cur) => acc + cur, 0);
console.log(sum); // 6
```

#### **4. `forEach`**

배열의 각 요소에 대해 함수를 실행합니다. 반환값은 없습니다.

```javascript
numbers.forEach((num) => console.log(num)); // 1, 2, 3
```

> `forEach`의 경우 기대하는 값이 나오지 않을 수 있음

---

### **구조분해할당 (Destructuring)**

배열이나 객체의 값을 추출하여 변수에 할당하는 방법입니다.

> 타입스크립트의 인터페이스라는 개념 때문에 중요!!

#### **1. 객체 분해**

```javascript
const user = { id: 1, name: "Bob", age: 30 };
const { id, name } = user;
console.log(id); // 1
```

#### **2. 배열 분해**

```javascript
const [first, second] = [10, 20];
console.log(first); // 10
```

#### **3. 중첩 분해**

```javascript
const config = { db: { host: "localhost", port: 3306 } };
const {
  db: { host },
} = config;
console.log(host); // "localhost"
```

---

### **스프레드 연산자 (Spread Operator)**

스프레드 연산자 `...`는 배열이나 객체를 펼쳐서 개별 요소로 분리합니다.

> 파라미터에서 쓰이는 경우 : 나머지
> 값에 쓰이는 경우: (펼쳐서) 복사를 의미 = 사본

> [!note] [깊은 복사 vs. 얕은 복사 vs. 동적할당](./깊은%20복사%20vs.%20얕은%20복사%20vs.%20동적할당.md)

#### **1. 배열 복사/결합**

```javascript
const arr1 = [1, 2];
const arr2 = [...arr1, 3]; // [1, 2, 3]
```

#### **2. 객체 복사/병합**

```javascript
const objA = { a: 1 };
const objB = { ...objA, b: 2 }; // { a: 1, b: 2 }
```

#### **3. 함수 인자 전달**

```javascript
const nums = [1, 2, 3];
Math.max(...nums); // 3
```

---

### **나머지 매개변수 (Rest Parameters)**

나머지 매개변수는 함수의 매개변수에서 사용되며, 여러 개의 인수를 배열로 묶어줍니다.

#### **1. 가변 인자 처리**

```javascript
function sum(...args) {
  return args.reduce((acc, cur) => acc + cur, 0);
}
console.log(sum(1, 2, 3)); // 6
```

#### **2. 구조분해 + Rest**

```javascript
const [first, ...rest] = [1, 2, 3];
console.log(rest); // [2, 3]
```

---

### **🚨 핵심 정리**

1. **화살표 함수**

   - `this`가 상위 스코프를 가리킴 → **이벤트 핸들러나 메서드에 부적합**.
   - **간결한 표현** → `map`, `filter`와 조합해 가독성 ↑.

2. **고차 함수**

   - `map`/`filter` → **새 배열 생성** (원본 불변).
   - `reduce` → **복잡한 데이터 가공** (ex: 통계 계산).

3. **구조분해할당**

   - **API 응답 데이터 추출**에 유용 (ex: `const { data } = response;`).

4. **스프레드 연산자**

   - **불변성 유지** → React 상태 관리, Redux에서 필수.

5. **나머지 매개변수**
   - **동적 인자 처리** → API 라우터 파라미터(ex: Express.js)에 활용.

---

### **🔖 백엔드 개발자 팁**

- **`reduce`** → DB 쿼리 결과 집계 (ex: 총 주문 금액 계산).
- **스프레드 연산자** → 설정 객체 병합 (ex: `const config = { ...defaultConfig, ...userConfig }`).
- **나머지 매개변수** → 가변 경로 처리 (ex: `/api/users/:ids`).
