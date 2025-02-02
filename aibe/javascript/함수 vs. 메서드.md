함수(Function)와 메서드(Method)의 차이는 **"소속"**과 **"동작 방식"**에 있습니다.  
아래에 핵심 차이와 예시를 설명드릴게요.

---
### 1. **정의**
- **함수 (Function)**:  
  - 독립적으로 정의되고 호출되는 코드 블록.  
  - **어디서든 직접 호출**할 수 있습니다.  
  - 예: `sum()`, `setTimeout()`

- **메서드 (Method)**:  
  - **객체에 속한 함수**.  
  - 객체의 프로퍼티로 저장되며, **객체를 통해 호출**됩니다.  
  - 예: `user.greet()`, `array.map()`

---
### 2. **핵심 차이**
| 구분             | 함수 (Function)                                           | 메서드 (Method)       |
| -------------- | ------------------------------------------------------- | ------------------ |
| **소속**         | 독립적                                                     | 객체에 종속적            |
| **호출 방식**      | `함수명()`                                                 | `객체.메서드명()`        |
| **`this` 바인딩** | 전역 객체 (예: `window`) <br> (※ strict mode에서는 `undefined`) | **자신이 속한 객체**를 가리킴 |
| **사용 목적**      | 재사용 가능한 일반 로직                                           | 객체의 상태를 변경하거나 활용   |

---
### 3. **예시 코드**
#### **함수 (Function)**
```javascript
// 1. 독립적인 함수
function sayHello() {
  console.log("Hello!");
}

sayHello(); // "Hello!" (직접 호출)

// 2. 변수에 할당된 함수
const add = (a, b) => a + b;
console.log(add(2, 3)); // 5
```

#### **메서드 (Method)**
```javascript
const user = {
  name: "Kim",
  // 객체 내부에 정의된 메서드
  greet: function() {
    console.log(`Hi, I'm ${this.name}!`); // this = user 객체
  }
};

user.greet(); // "Hi, I'm Kim!" (객체를 통해 호출)

// 배열의 메서드 예시
const numbers = [1, 2, 3];
numbers.push(4); // push는 배열 객체의 메서드
```

---
### 4. **`this` 바인딩 차이 (중요!)**
- **메서드**의 `this`는 **호출한 객체**를 가리킵니다.  
- **일반 함수**의 `this`는 **전역 객체** (브라우저: `window`, Node.js: `global`)를 가리킵니다.  
  (※ 단, **strict mode**에서는 `undefined`)

```javascript
const obj = {
  name: "Object",
  method() {
    console.log(this.name); // "Object" (메서드의 this = obj)
  },
  arrowMethod: () => {
    console.log(this.name); // undefined (화살표 함수는 this를 바인딩하지 않음)
  }
};

function standaloneFunc() {
  console.log(this); // 전역 객체 (strict mode에서는 undefined)
}

obj.method();        // "Object"
standaloneFunc();    // (전역 객체)
```

---
### 5. **주의사항**
- **화살표 함수**는 자신의 `this`를 가지지 않아 메서드로 사용하면 **예상치 못한 동작**이 발생할 수 있습니다.  
- 메서드는 **객체의 상태를 조작**하기 위해 주로 사용됩니다.  
- 함수는 **재사용성**을 높이기 위해 독립적으로 설계합니다.

---
### 🤔 **백엔드 개발자 관점에서**  
- 백엔드(Node.js)에서도 **객체와 메서드**를 활용해 서비스 로직을 구조화합니다.  
- 예: 데이터베이스 모델 클래스의 메서드 (`User.save()`, `Product.find()`), API 핸들러 등  
- **메서드 체이닝** (예: `array.map().filter()`)도 자주 사용됩니다.  

