<!-- ![Screenshot 2025-01-27 at 9.23.51 AM.png](../../images/Screenshot%202025-01-27%20at%209.23.51%20AM.png) -->

<img src="../../images/Screenshot%202025-01-27%20at%209.23.51%20AM.png" width="500">

**① JavaScript는 클라이언트와 서버 모두에서 실행 가능**

- JavaScript는 원래 브라우저에서 동작하는 클라이언트 사이드 언어로 시작했지만, Node.js와 같은 런타임 환경 덕분에 서버 사이드에서도 실행할 수 있습니다. 따라서 이 설명은 맞습니다.

**⑤ JavaScript는 객체 지향 언어** ❓

- JavaScript는 [프로토타입 기반](../javascript/프로토타입%20기반.md)의 객체 지향 언어입니다. 클래스 기반은 아니지만, 객체를 생성하고 상속을 구현할 수 있습니다. 따라서 이 설명도 맞습니다.
  > ES6와 node.js의 등장으로 `객체 지향 언어`에 도달했다고 보는 시각도 있음

### 나머지 옵션은 틀린 설명입니다:

- **② JavaScript는 브라우저에서만 동작**  
  → Node.js 덕분에 서버에서도 실행 가능하므로 틀린 설명입니다.
- **③ JavaScript는 정적 언어**  
  → JavaScript는 동적 타입 언어로, 변수의 타입이 실행 시점에 결정됩니다.
- **④ JavaScript는 컴파일 언어**  
  → JavaScript는 인터프리터 언어로, 컴파일 없이 실행됩니다.

따라서 정답은 **①과 ⑤**입니다! 😊

---

<br>

<!-- ![Screenshot 2025-01-27 at 9.25.57 AM.png](../../images/Screenshot%202025-01-27%20at%209.25.57%20AM.png) -->

<img src="../../images/Screenshot%202025-01-27%20at%209.25.57%20AM.png" width="500">

**② let과 const는 블록 스코프를 가진다**

- `let`과 `const`는 블록 스코프(block scope)를 가지므로, `{}`(중괄호) 안에서 선언된 변수는 블록 외부에서 접근할 수 없습니다. 이 설명은 맞습니다.

### 나머지 옵션은 틀린 설명입니다:

- **① var는 블록 스코프를 가진다**  
  → `var`는 함수 스코프(function scope)를 가지며, 블록 스코프를 가지지 않습니다. 따라서 틀린 설명입니다.
- **③ const는 재할당이 가능하다**  
  → `const`는 재할당이 불가능합니다. 상수로 선언된 변수는 한 번 할당된 값을 변경할 수 없습니다.
- **④ let은 재선언이 가능하다**  
  → `let`은 재선언이 불가능합니다. 같은 스코프 내에서 동일한 변수명으로 재선언하면 에러가 발생합니다.
- **⑤ var는 재선언이 불가능하다**  
  → `var`는 재선언이 가능합니다. 같은 스코프 내에서 동일한 변수명으로 재선언해도 에러가 발생하지 않습니다.

따라서 정답은 **②**입니다! 😊
