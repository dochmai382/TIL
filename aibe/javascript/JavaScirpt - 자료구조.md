### 1. **객체 (Object)**
- **정의**: 키-값(Key-Value) 쌍으로 데이터를 저장하는 자료구조  
  (예: 사용자 정보, 설정 옵션)
- **주요 메서드**:
  - `Object.keys(obj)`: 키 목록 반환
  - `Object.values(obj)`: 값 목록 반환
  - `Object.entries(obj)`: [키, 값] 배열 반환
  - `obj.hasOwnProperty(key)`: 특정 키 존재 여부 확인
#### 예제 코드
```javascript
const user = {
  name: "김코딩",
  age: 30,
  greet() {
    console.log(`Hello, ${this.name}!`);
  }
};

console.log(Object.keys(user)); // ["name", "age", "greet"]
user.greet(); // "Hello, 김코딩!"
```

---
### 2. **배열 (Array)**
- **정의**: 순서가 있는 데이터 집합 (인덱스로 접근)  
  (예: 목록 데이터, 결과 집합)
- **주요 메서드**:
  - `push()`, `pop()`, `shift()`, `unshift()`: 요소 추가/제거
  - `map()`, `filter()`, `reduce()`: 고차 함수
  - `find()`, `includes()`: 요소 검색
  - `slice()`, `splice()`: 배열 자르기
#### 예제 코드
```javascript
const numbers = [1, 2, 3];
numbers.push(4); // [1, 2, 3, 4]
const doubled = numbers.map(num => num * 2); // [2, 4, 6, 8]
const even = numbers.filter(num => num % 2 === 0); // [2, 4]
```

---
### 3. **Map**
- **정의**: 키-값 쌍을 저장하며 **키 타입 제한 없음** (객체와 달리 함수, 객체도 키로 사용 가능)  
  (예: 복잡한 키 구조 필요 시)
- **주요 메서드**:
  - `set(key, value)`: 값 추가
  - `get(key)`: 값 조회
  - `has(key)`: 키 존재 여부
  - `delete(key)`: 키 삭제
  - `size`: 요소 개수
  - `keys()`, `values()`, `entries()` : 순회
#### 예제 코드
```javascript
const map = new Map();
map.set("name", "박해커");
map.set(42, "The Answer");

console.log(map.get("name")); // "박해커"
console.log(map.has(42)); // true
```

---
### 4. **Set**
- **정의**: **중복 없는 값**을 저장하는 집합  
  (예: 고유 ID 목록)
- **주요 메서드**:
  - `add(value)`: 값 추가
  - `has(value)`: 값 존재 여부
  - `delete(value)`: 값 삭제
  - `size`: 요소 개수
  - `keys()`, `values()`, `entries()` : 순회
#### 예제 코드
```javascript
const set = new Set();
set.add(1);
set.add(2);
set.add(1); // 중복 무시

console.log(set); // Set(2) {1, 2}
console.log(set.has(3)); // false
```

---
### 5. **특수 반복문**
#### 1) `for...of` (배열, Map, Set)
객체의 값을 순회
```javascript
// 배열
const arr = [10, 20, 30];
for (const num of arr) {
  console.log(num); // 10, 20, 30
}

// Map
const map = new Map([["a", 1], ["b", 2]]);
for (const [key, value] of map) {
  console.log(key, value); // "a 1", "b 2"
}
```

#### 2) `for...in` (객체)
```javascript
const obj = { a: 1, b: 2 };
for (const key in obj) {
  console.log(key, obj[key]); // "a 1", "b 2"
}
```

#### 3) `forEach()` (배열, Map, Set)
```javascript
// 배열
[1, 2, 3].forEach(num => console.log(num));

// Set
const set = new Set([1, 2, 3]);
set.forEach(value => console.log(value));
```

---
### **요약 비교표**
| 자료구조 | 특징 | 사용 사례 |
|----------|------|-----------|
| **객체** | 키-값, 키는 문자열/Symbol | 설정 정보, 복잡한 데이터 구조 |
| **배열** | 순서 있는 데이터 | 목록, 스택/큐 구현 |
| **Map** | 다양한 키 타입 허용 | 키가 동적으로 변하는 데이터 |
| **Set** | 중복 불가 | 고유값 관리, 중복 제거 |

---
### **백엔드 개발자 팁**
- **Map**: API의 복잡한 메타데이터 저장 시 유용  
- **Set**: 중복된 요청이나 데이터 필터링 시 활용  
- **배열 메서드**: 데이터베이스 쿼리 결과 처리에 자주 사용 (`map()`, `filter()`)
