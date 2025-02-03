JavaScript의 예외 처리는 주로 `try...catch` 문을 사용하여 오류를 잡고 적절한 대응을 하는 방식으로 이루어진다. 또한, `throw`를 사용하여 직접 예외를 발생시키거나, `finally`를 활용해 예외 발생 여부와 관계없이 실행해야 할 코드를 작성할 수도 있다.

### 1. 기본적인 `try...catch`

```javascript
try {
  let result = 10 / 0; // 0으로 나누기 (JavaScript에서는 Infinity)
  console.log(result);
} catch (error) {
  console.error("오류 발생:", error.message);
}
```

- `try` 블록: 실행할 코드를 넣는다.
- `catch` 블록: 오류가 발생하면 `catch` 블록이 실행되며, `error` 객체를 통해 오류 정보를 확인할 수 있다.

### 2. `throw`를 사용한 예외 발생

```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error("0으로 나눌 수 없습니다.");
  }
  return a / b;
}

try {
  console.log(divide(10, 0));
} catch (error) {
  console.error("예외 발생:", error.message);
}
```

- `throw`를 사용하여 직접 예외를 발생시킬 수 있다.
- `Error` 객체를 생성하여 사용자 정의 오류 메시지를 포함할 수 있다.

### 3. `finally` 블록

```javascript
try {
  console.log("실행 중...");
  throw new Error("강제 오류 발생!");
} catch (error) {
  console.error("오류 처리:", error.message);
} finally {
  console.log("이 코드는 항상 실행됩니다.");
}
```

- `finally` 블록은 오류 발생 여부와 관계없이 항상 실행된다.
- 주로 정리 작업(예: 파일 닫기, 리소스 해제 등)에 사용된다.

> [!NOTE] > [JavaScript - 예외처리 finally](./JavaScript%20-%20예외처리%20finally.md)

<br>

## `try-catch`기능 (2) 흐름제어

### 🎯 **1. `try-catch`로 흐름을 변경하는 예제**

```javascript
function safeDivide(a, b) {
  try {
    if (b === 0) {
      throw new Error("0으로 나눌 수 없습니다.");
    }
    return a / b;
  } catch (error) {
    console.error("오류 발생:", error.message);
    return null; // 오류 발생 시 기본값 반환 (흐름 제어)
  }
}

console.log(safeDivide(10, 2)); // 정상 실행 (5 출력)
console.log(safeDivide(10, 0)); // 오류 발생 → 기본값 null 반환
```

✅ 예외가 발생하면 catch에서 `null`을 반환하여 프로그램이 멈추지 않고 정상 흐름을 유지할 수 있음.  
✅ 즉, **예외를 잡고 다른 코드가 실행될 수 있도록 흐름을 변경**하는 역할을 함.

---

### 🎯 **2. `try-catch`로 반복문 흐름 제어**

반복문 안에서 `try-catch`를 사용하면 **오류가 발생해도 반복을 멈추지 않고 계속 진행할 수 있어**.

```javascript
const numbers = [10, 5, 0, 20];

for (let num of numbers) {
  try {
    console.log("결과:", 100 / num);
    if (num === 5) throw new Error("강제 오류 발생!"); // 특정 조건에서 강제 오류
  } catch (error) {
    console.warn("오류:", error.message);
  }
}
console.log("프로그램 계속 실행됨");
```

✅ `0`으로 나누거나 특정 숫자에서 오류가 발생해도 **반복문이 멈추지 않고 계속 진행됨**.  
✅ 즉, **`try-catch`가 없으면 프로그램이 멈췄겠지만, 예외를 잡고 흐름을 이어갈 수 있음**.

---

### 🎯 **3. `try-catch`를 활용한 `while` 루프 제어**

반복문 내에서 `try-catch`를 사용하면 **안정적인 입력을 받을 수 있음**.

```javascript
function getValidNumber() {
  while (true) {
    try {
      let input = prompt("숫자를 입력하세요:");
      let number = Number(input);
      if (isNaN(number)) throw new Error("숫자가 아닙니다.");
      return number; // 정상 입력되면 반환
    } catch (error) {
      console.warn("오류:", error.message);
      alert("올바른 숫자를 입력하세요!");
    }
  }
}

// 사용자가 숫자를 입력할 때까지 반복
console.log("입력한 숫자:", getValidNumber());
```

✅ `while (true)`로 무한 반복하지만,  
✅ 예외가 발생하면 **catch에서 안내 메시지를 띄우고 다시 입력받음** → 흐름을 제어함.

---

### 🎯 **4. `try-catch-finally`로 흐름을 완전히 제어**

```javascript
function processTask() {
  try {
    console.log("작업 시작");
    throw new Error("작업 중 오류 발생!");
  } catch (error) {
    console.warn("오류 처리:", error.message);
    return; // 여기서 return을 해도
  } finally {
    console.log("정리 작업 실행!"); // finally는 실행됨
  }
  console.log("이 코드는 실행되지 않음"); // return 때문에 실행 안 됨
}

processTask();
```

✅ `return`이 있어도 `finally`가 실행됨 → **흐름을 확실히 제어 가능**.  
✅ 즉, 오류가 발생하더라도 **특정 작업을 수행한 후 함수 종료**가 가능함.

---

### 🔥 **결론: `try-catch`는 흐름 제어 기능이 있다!**

✅ **프로그램이 멈추지 않도록 예외를 처리하면서 흐름을 유지**할 수 있음.  
✅ **반복문 안에서 개별 오류를 무시하고 계속 실행 가능**.  
✅ **사용자 입력 같은 경우 오류가 발생하면 다시 요청하도록 흐름을 조절**.  
✅ **`finally`를 활용하면 예외 발생 여부와 관계없이 정리 작업을 강제 실행**할 수 있음.

즉, `try-catch`는 단순한 오류 처리를 넘어서 **프로그램의 실행 흐름을 더 유연하게 조절하는 기능**도 한다!
