객체(Object)와 클래스(Class)는 JavaScript에서 **데이터와 기능을 구조화**하는 핵심 개념입니다.

---

### **1. 객체 (Object)**

- **정의**: 키-값(Key-Value) 쌍으로 이루어진 데이터의 집합  
  (예: 사용자 정보, 상품 데이터 등)
- **중요한 점**:
  - 객체는 **메서드(함수)**를 포함할 수 있습니다.
  - `this` 키워드로 자신의 프로퍼티에 접근합니다.
  - **ES6**에서 프로퍼티 축약, 계산된 프로퍼티 등 편의 기능이 추가되었습니다.

#### **예제 코드**

```javascript
// 객체 리터럴로 생성
const user = {
  name: "김코딩", // 프로퍼티
  age: 30,
  greet() {
    // 메서드
    console.log(`안녕하세요, ${this.name}님!`);
  },
};

user.greet(); // "안녕하세요, 김코딩님!"
```

> [!note] > [함수 vs. 메서드](./함수%20vs.%20메서드.md)

---

### **2. 클래스 (Class)**

- **정의**: 객체를 생성하기 위한 **템플릿** (ES6에서 도입)  
  (예: 사용자, 상품 등의 유사한 객체를 일관적으로 생성)
- **중요한 점**:
  - `constructor()`로 초기화합니다.
  - `extends`로 **상속**이 가능합니다.
  - **캡슐화**, **다형성** 등 OOP 개념을 적용할 수 있습니다.

#### **예제 코드**

```javascript
// 기본 클래스
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  // 메서드
  greet() {
    console.log(`안녕하세요, ${this.name}님!`);
  }

  // 정적 메서드 (인스턴스 없이 호출)
  static isAdult(age) {
    return age >= 19;
  }
}

// 클래스 상속
class AdminUser extends User {
  constructor(name, age, role) {
    super(name, age); // 부모 클래스의 constructor 호출
    this.role = role;
  }

  // 메서드 오버라이딩
  greet() {
    console.log(`관리자 ${this.name}님, 환영합니다!`);
  }
}

// 사용 예시
const user1 = new User("박해커", 25);
user1.greet(); // "안녕하세요, 박해커님!"

const admin = new AdminUser("최관리", 30, "admin");
admin.greet(); // "관리자 최관리님, 환영합니다!"

console.log(User.isAdult(20)); // true (정적 메서드)
```

---

### **객체 vs 클래스 핵심 차이**

| 구분     | 객체 (Object)            | 클래스 (Class)            |
| -------- | ------------------------ | ------------------------- |
| **목적** | 단일 데이터 묶음         | 객체를 생성하는 템플릿    |
| **생성** | 리터럴(`{}`)로 즉시 생성 | `new` 키워드로 인스턴스화 |
| **상속** | 프로토타입 체인 사용     | `extends`로 명시적 상속   |

---

### **주의할 점**

1. **`this` 바인딩**:
   - 화살표 함수는 자신의 `this`를 가지지 않으므로, **클래스 메서드**에서는 일반 함수를 사용합니다.
2. **캡슐화**:
   - JavaScript는 기본적으로 접근 제한자가 없지만, `#`을 사용해 **private 필드**를 구현할 수 있습니다.  
     (예: `#password = "secret";`)
3. **프로토타입**:
   - 클래스는 내부적으로 **프로토타입 기반**으로 동작합니다.

---

### **백엔드 개발자를 위한 팁**

- 백엔드(Node.js)에서도 **클래스**를 활용해 서비스 로직을 구조화합니다.
- 데이터베이스 모델링 시 클래스를 사용해 **엔티티(Entity)**를 정의합니다.  
  (예: `User`, `Product` 클래스)
