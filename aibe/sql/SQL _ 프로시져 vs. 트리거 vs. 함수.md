**프로시저(Procedure)**, **트리거(Trigger)**, **함수(Function)**는 데이터베이스에서 사용되는 프로그래밍 객체입니다. 각각의 정의와 차이점을 명확히 이해하면 데이터베이스 작업을 더 효율적으로 설계할 수 있습니다.

---

### 1. **프로시저 (Procedure)**
- **정의**:  
  - SQL 문을 묶어서 **하나의 작업 단위로 실행**하는 코드 블록.  
  - 입력 매개변수를 받고, 출력 매개변수를 반환할 수 있습니다.  
  - **반환값이 없거나 선택적**입니다.  
- **사용 목적**:  
  - 반복적인 작업을 자동화하거나 복잡한 로직을 캡슐화.  
  - 예: 데이터 삽입, 업데이트, 삭제, 조회 등.

#### 예제 (MySQL)
```sql
DELIMITER //
CREATE PROCEDURE GetUser(IN userId INT)
BEGIN
  SELECT * FROM users WHERE id = userId;
END //
DELIMITER ;

-- 호출
CALL GetUser(1);
```

---

### 2. **트리거 (Trigger)**
- **정의**:  
  - 데이터베이스에서 **특정 이벤트(INSERT, UPDATE, DELETE)**가 발생할 때 **자동으로 실행**되는 코드 블록.  
  - **반환값이 없습니다**.  
- **사용 목적**:  
  - 데이터 무결성 유지, 로깅, 감사(audit) 등.  
  - 예: 특정 테이블에 데이터가 삽입될 때 로그를 기록.

#### 예제 (MySQL)
```sql
CREATE TRIGGER before_user_insert
BEFORE INSERT ON users
FOR EACH ROW
BEGIN
  SET NEW.created_at = NOW();
END;

-- users 테이블에 데이터 삽입 시 created_at 자동 설정
INSERT INTO users (name) VALUES ('김코딩');
```

---

### 3. **함수 (Function)**
- **정의**:  
  - **입력 매개변수**를 받아 **단일 값**을 반환하는 코드 블록.  
  - **반드시 반환값이 있어야 합니다**.  
- **사용 목적**:  
  - 계산, 데이터 변환, 조건 검사 등.  
  - 예: 두 수의 합계 계산, 문자열 포맷팅.

#### 예제 (MySQL)
```sql
DELIMITER //
CREATE FUNCTION CalculateTax(price DECIMAL(10,2)) RETURNS DECIMAL(10,2)
BEGIN
  DECLARE tax DECIMAL(10,2);
  SET tax = price * 0.1;
  RETURN tax;
END //
DELIMITER ;

-- 호출
SELECT CalculateTax(100); -- 10.00
```

---
### **차이점 요약**
| 구분 | 프로시저 (Procedure) | 트리거 (Trigger) | 함수 (Function) |
|------|----------------------|------------------|-----------------|
| **실행 방식** | 수동 호출 (`CALL`) | 자동 실행 (이벤트 발생 시) | 수동 호출 (`SELECT`) |
| **반환값** | 없거나 선택적 | 없음 | 필수 (단일 값) |
| **매개변수** | 입력/출력 가능 | 없음 | 입력만 가능 |
| **사용 목적** | 복잡한 로직 처리 | 데이터 무결성, 로깅 | 계산, 변환 |

---
### **백엔드 개발자를 위한 팁**
1. **프로시저**:  
   - 복잡한 비즈니스 로직을 데이터베이스 레벨에서 처리할 때 유용.  
   - 예: 주문 처리, 배치 작업.

2. **트리거**:  
   - 데이터 변경 시 추가 작업이 필요할 때 사용.  
   - 예: 로그 기록, 데이터 유효성 검사.

3. **함수**:  
   - 데이터 조회 시 계산이 필요할 때 사용.  
   - 예: 세금 계산, 할인율 적용.

---

### **예제 시나리오**
#### 1. **프로시저**: 사용자 정보 업데이트
```sql
CREATE PROCEDURE UpdateUser(IN userId INT, IN newName VARCHAR(255))
BEGIN
  UPDATE users SET name = newName WHERE id = userId;
END;

CALL UpdateUser(1, '박해커');
```

#### 2. **트리거**: 로그 기록
```sql
CREATE TRIGGER after_user_update
AFTER UPDATE ON users
FOR EACH ROW
BEGIN
  INSERT INTO user_logs (user_id, action) VALUES (OLD.id, 'UPDATE');
END;
```

#### 3. **함수**: 할인율 계산
```sql
CREATE FUNCTION CalculateDiscount(price DECIMAL(10,2), discountRate DECIMAL(5,2)) RETURNS DECIMAL(10,2)
BEGIN
  RETURN price * (1 - discountRate);
END;

SELECT CalculateDiscount(100, 0.2); -- 80.00
```

---

### **주의사항**
1. **트리거 남용 금지**:  
   - 트리거가 많으면 디버깅이 어려워질 수 있습니다.  
2. **함수와 프로시저의 성능**:  
   - 복잡한 로직은 애플리케이션 레벨에서 처리하는 것이 나을 수 있습니다.  
3. **데이터베이스 종류에 따른 차이**:  
   - MySQL, PostgreSQL, Oracle 등 DBMS마다 문법이 조금 다를 수 있습니다.

