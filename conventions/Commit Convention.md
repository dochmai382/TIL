### **🔍 Commit Convention이 뭔가요?**  
- Git으로 코드를 저장할 때, 커밋 메시지를 **일관된 규칙**으로 작성하는 것  
  → 마치 "일기 쓰듯이" 규칙을 정해두는 거예요.  
  - 예: `feat: 로그인 API 추가`, `fix: 회원가입 버그 수정`

---
### **📜 기본 규칙 (타입 + 제목 + 설명)**  
#### 1️⃣ **타입 (Type)**  
| 타입         | 설명                    | 백엔드 예시                         |
| ---------- | --------------------- | ------------------------------ |
| `feat`     | **새 기능 추가**           | `feat: 회원 탈퇴 API 구현`           |
| `fix`      | **버그 수정**             | `fix: NullPointerException 해결` |
| `docs`     | 문서 수정 (README, 주석 등)  | `docs: API 명세서 업데이트`           |
| `style`    | 코드 포맷팅 (들여쓰기, 세미콜론 등) | `style: 코드 컨벤션 적용`             |
| `refactor` | **리팩토링** (기능 변경 X)    | `refactor: Service 레이어 분리`     |
| `test`     | 테스트 코드 추가/수정          | `test: UserService 단위 테스트 추가`  |
| `chore`    | 빌드 설정, 라이브러리 추가 등 잡일  | `chore: Spring Boot 3.2로 버전 업` |
#### 2️⃣ **제목 (Subject)**  
- **50자 이내**로 명확하게!  
- **동사 원형**으로 시작 (Add, Fix, Update 등)  
  - ❌ Bad: `fixed login bug`  
  - ✅ Good: `fix: Resolve JWT token expiration issue`  

#### 3️⃣ **본문 (Body) - 선택사항**  
- **"왜 수정했는지"**, **"어떻게 수정했는지"** 설명  
  ```  
  feat: Add email verification API  
    
  - SMTP 서버 연동  
  - 이메일 인증 로직 구현  
  - 관련 테스트 코드 작성  
  ```  

#### 4️⃣ **꼬리말 (Footer) - 선택사항**  
- 이슈 트래커 ID 연결 (예: `Closes #12`, `Ref #34`)  

---
### **🚨 주의사항 **  
1. **처음엔 어색해도 OK!**  
   - 평소에 **타입을 외우고**, 연습용 프로젝트에 적용해보세요.  
   - 예: `git commit -m "feat: Add GET /api/users endpoint"`  

2. **백엔드 개발자라면 더 중요!**  
   - API 개발, DB 스키마 변경, 보안 이슈 등을 커밋 메시지로 관리하면  
     **나중에 버그 추적이 쉬워집니다.**  

3. **팀 프로젝트에선 필수!**  
   - 팀원들과 **컨벤션을 미리 정해두고** → **일관성 있게** 사용하세요.  
   - 예: `[BE] feat: Add Spring Security config` (프론트/백 구분)

---
### **✏️ 연습해보세요! (백엔드 예시)**  
1. **기능 추가**:  
   ```
   feat: Implement user profile update API  
   
   - Add PUT /api/users/{id} endpoint  
   - Add validation for nickname and email  
   ```  

2. **버그 수정**:  
   ```
   fix: Prevent SQL injection in search query  
   
   - Use JPA Criteria API for parameter binding  
   ```  

3. **리팩토링**:  
   ```
   refactor: Optimize database connection pool  
   
   - Change HikariCP settings for better performance  
   ```

---
### **🛠️ 도구 추천**  
- **IntelliJ Git Plugin**: 커밋 메시지 템플릿을 설정해 자동 완성 가능 (Java 개발자 필수!)  
- **Conventional Commits**: [공식 사이트](https://www.conventionalcommits.org/)에서 규칙 확인  
