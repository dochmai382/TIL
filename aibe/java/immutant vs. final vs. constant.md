### 1. **Immutable (불변 객체)**  
✔️ **정의**: **태어날 때부터 끝까지 상태가 변하지 않는 객체** (ex: 주민등록번호, 출생년도)  
✔️ **특징**:  
   - 객체 **내부 데이터를 수정할 수 없는 설계** (Java의 `String`, `Integer` 등)  
   - **변경 시 새 객체 생성** → 메모리 효율은 떨어지지만 **안전성 ↑**  
```java
// Java 예시
String name = "철수";  // "철수"라는 String 객체 생성
name = name + "님";    // "철수님"이라는 완전히 새로운 String 객체 생성
```

---
### 2. **final (최종 변수)**  
✔️ **정의**: **한 번 할당하면 재할당 불가능한 변수** (ex: 결혼한 배우자 → 재혼 불가)  
✔️ **특징**:  
   - **변수에 대한 제약** (객체 내부 상태 변경은 가능!)  
   - Java에서 **상수(constant)** 만들 때는 `static final` 조합 사용  
```java
// Java 예시
final List<String> list = new ArrayList<>();  // 재할당은 X
list.add("사과");  // 객체 내부 상태 변경은 O (Mutable 객체)
```

---
### 3. **Constant (상수)**  
✔️ **정의**: **프로그램 전체에서 고정된 값** (ex: 원주율 π=3.14, 최대 사용자 수)  
✔️ **특징**:  
   - Java: `public static final`로 선언 + **대문자_스네이크_케이스**  
   - JavaScript: `const` (재할당 금지, but 객체 내부 변경 가능)  
```java
// Java 예시 (상수)
public static final double PI = 3.141592;
```

```javascript
// JavaScript 예시
const MAX_USERS = 100;  // 재할당 X
const person = { name: "철수" };
person.age = 20;  // 객체 내부 변경 O
```

---
### 🧩 **차이점 한눈에 보기**  
| 개념            | 대상  | 변경 가능 여부       | Java 예시                       | JavaScript 예시           |     |
| ------------- | --- | -------------- | ----------------------------- | ----------------------- | --- |
| **Immutable** | 객체  | **객체 자체 변경 X** | `String`, `LocalDate`         | `Object.freeze()`       |     |
| **final**     | 변수  | **변수 재할당 X**   | `final int x = 10;`           | `let x = 10;` (재할당 금지X) |     |
| **Constant**  | 값   | **값 자체 변경 X**  | `static final int MAX = 100;` | `const MAX = 100;`      |     |

---
### 💡 **왜 중요할까요?**  
- **Immutable**: 멀티스레드 환경에서 **안전성 보장** (Spring에서 자주 사용)  
- **final**: 실수로 인한 변수 재할당 방지 → **버그 예방**  
- **Constant**: 매직 넘버 제거 → **가독성 ↑ 유지보수성 ↑**

---
### 📚 **추가 TIP**  
- **Spring에서 Immutable** → `@Value` 어노테이션으로 설정 파일 주입 시 사용  
- **final 클래스** (ex: `String`) → 상속 불가능 (보안 강화)  
- **JavaScript**에서는 `const`가 재할당만 막는다는 점 주의! (Immutable ≠ const)

