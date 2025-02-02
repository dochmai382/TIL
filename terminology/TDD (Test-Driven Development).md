테스트 주도 개발(TDD, Test-Driven Development)은 **"테스트를 먼저 작성하고, 그 테스트를 통과하는 코드를 개발하는 방법론"**입니다. 백엔드 개발에서 코드의 안정성과 유지보수성을 높이는 핵심 기술이에요.

---
### 📌 **TDD가 왜 필요할까요?**
1. **"코드를 먼저 짜면 버그가 숨어요!"**  
   - 보통은 코드 → 테스트 순서로 개발하지만, 이 경우 예상치 못한 오류가 발생하기 쉽습니다.
   - TDD는 **테스트 → 코드 → 개선** 순서로 진행해 실수를 사전에 방지합니다.

2. **"요구사항을 명확히 이해하지 못하면 코드가 엉망이 돼요!"**  
   - 테스트를 먼저 작성하면 **기능의 목적**을 명확히 정의할 수 있습니다.

### 🚀 **JavaScript TDD 3단계 프로세스 (Red-Green-Refactor)**
**예시: 계산기 모듈 개발**
#### 1️⃣ **RED (실패하는 테스트 작성)**
```javascript
// calculator.test.js
const Calculator = require('./calculator');

test('덧셈 함수는 2 + 3을 더해 5를 반환해야 함', () => {
  const calc = new Calculator();
  expect(calc.add(2, 3)).toBe(5); // Calculator 클래스와 add 메서드가 없음 → 테스트 실패(Red)
});
```

#### 2️⃣ **GREEN (최소한의 코드로 테스트 통과)**
```javascript
// calculator.js
class Calculator {
  add(a, b) {
    return 5; // 하드코딩으로 5 반환 → 테스트 통과(Green)
  }
}

module.exports = Calculator;
```

#### 3️⃣ **REFACTOR (로직 개선)**
```javascript
// calculator.js
class Calculator {
  add(a, b) {
    return a + b; // 일반적인 덧셈 로직으로 변경 → 테스트는 계속 통과!
  }
}

module.exports = Calculator;
```

---

### 🛠️ **JavaScript TDD 설정 가이드**
1. **패키지 설치**
   ```bash
   npm init -y
   npm install --save-dev jest
   ```

2. **package.json 설정**
   ```json
   {
     "scripts": {
       "test": "jest",
       "test:watch": "jest --watchAll"
     }
   }
   ```

3. **테스트 실행**
   ```bash
   npm test          # 기본 실행
   npm run test:watch # 코드 변경 시 자동 재실행
   ```

---

### 💡 **백엔드 API 테스트 예시 (Express.js)**
```javascript
// api.test.js
const request = require('supertest');
const app = require('./app');

test('GET /users는 200 상태 코드를 반환해야 함', async () => {
  const response = await request(app).get('/users');
  expect(response.statusCode).toBe(200);
});

test('POST /signup은 새 사용자를 생성해야 함', async () => {
  const newUser = { email: 'test@test.com', password: '1234' };
  const response = await request(app)
    .post('/signup')
    .send(newUser);
  
  expect(response.statusCode).toBe(201);
  expect(response.body.email).toBe(newUser.email);
});
```

---
### 📌 **JavaScript TDD의 핵심 기술**
1. **Mocking**: 외부 서비스 의존성 제거  
   ```javascript
   // 외부 API 호출 모킹 예시
   jest.mock('axios', () => ({
     get: () => Promise.resolve({ data: { id: 1, title: 'Mocked Data' } })
   }));
   ```

2. **테스트 커버리지**:  
   ```bash
   jest --coverage  # 커버리지 리포트 생성
   ```

3. **비동기 테스트**: `async/await` 활용  
   ```javascript
   test('비동기 데이터 불러오기', async () => {
     const data = await fetchData();
     expect(data).toHaveProperty('success', true);
   });
   ```

---
### 💡 **TDD의 장점**
- **버그 감소**: 테스트 커버리지가 90% 이상일 경우 버그 발생률이 40~80% 감소([NASA 연구](https://www.nasa.gov/))  
- **설계 개선**: 테스트 가능한 코드는 자연스럽게 **모듈화**되고 **의존성이 낮아짐**  
- **문서 역할**: 테스트 코드 자체가 기능 사용 예시가 됨  
- **심리적 안정감**: "이 코드는 분명히 동작한다"는 확신을 줌

---
### ⚠️ **TDD의 단점 (주의점)**
- **초기 학습 곡선**: 테스트 프레임워크(예: pytest, JUnit) 사용법을 익혀야 함  
- **과도한 테스트**: 모든 사소한 변경에 테스트를 작성하면 생산성이 떨어질 수 있음  
- **실제 환경 고려 부족**: DB, 외부 API 연동 테스트는 별도의 전략이 필요함 (Mocking 등)

---

### 🛠️ **백엔드 개발자로서 TDD 시작하기**
1. **도구 선택**:  
   - Python: **pytest** + **unittest**  
   - Java: **JUnit** + **Mockito**  
   - JavaScript: **Jest** + **Supertest**

2. **실전 연습**:  
   ```python
   # 간단한 회원 가입 API 테스트 예시 (Flask)
   def test_signup(client):
       response = client.post('/signup', json={'email': 'test@test.com', 'password': '1234'})
       assert response.status_code == 201
       assert User.query.filter_by(email='test@test.com').first() is not None
   ```

3. **점진적 적용**:  
   - **CRUD 기능** → **비즈니스 로직** → **외부 연동** 순으로 확장  
   - **의존성 주입(DI)**을 활용해 테스트하기 쉬운 구조로 설계

---
### 📚 **JavaScript TDD 학습 자료**
- **공식 문서**: [Jest 공식 가이드](https://jestjs.io/docs/getting-started)  
- **책**: 《JavaScript Testing with Jest》 (이번트 버로우)  
- **강의**: [유튜브 TDD 강의](https://youtu.be/FTrp4RALiDQ) (우아한테크코스)  
- **실습**: [Jest 연습 문제](https://github.com/sapegin/jest-cheat-sheet)
- **연습 사이트**: [Exercism](https://exercism.org/) (TDD 연습 문제 제공)

---

처음엔 테스트 코드 작성이 번거롭게 느껴지지만, **장기적으로 버그를 70% 이상 줄일 수 있다**는 연구 결과가 있습니다. 작은 기능부터 차근차련 시작해보세요! 😊
