> 너는 SEO[^SEO]와 html5[^HTML5]에 대해서 잘 아는 개발자야. html에서 중요하고 가장 자주 쓰이는 20개의 태그를 위주로 해서 나에게 html에 대해서 알려줘. 예제 코드(마크다운 여러줄 코드 블록)와 속성(attribute)에 대한 설명을 포함해서. bullet point[^bullet_point]와 nut shell[^nut_shell]로.

---

### **1. `<!DOCTYPE>`**

- **목적**: HTML5 문서의 시작을 나타내며, HTML 문서가 HTML5 형식임을 선언합니다.
  ```html
  <!DOCTYPE html>
  ```

---

### **2. `<html>`**

- **목적**: HTML 문서의 루트 요소로, 모든 HTML 콘텐츠가 이 태그 내에 포함됩니다.
- **속성**: `lang` (언어 설정)
  ```html
  <html lang="en"></html>
  ```

---

### **3. `<head>`**

- **목적**: 문서 메타데이터를 포함하는 섹션 (예: 제목, 문자셋, 스타일시트 등).
  ```html
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
  </head>
  ```

---

### **4. `<meta>`**

- **목적**: 문서의 메타데이터를 정의 (SEO에 중요).
- **속성**: `name`, `content` (예: `description`, `keywords`)
  ```html
  <meta name="description" content="HTML tutorial for beginners" />
  ```

> [!note]
> 메타데이터는 설명해주는 데이터로, 페이지를 해석하는데 필요한 데이터
> 화면에 표시되지 않음

---

### **5. `<title>`**

- **목적**: 문서의 제목을 정의 (브라우저 탭에 표시).
  ```html
  <title>My Website</title>
  ```

---

### **6. `<body>`**

- **목적**: 실제 페이지의 콘텐츠가 들어가는 부분.
  ```html
  <body>
    <h1>Welcome to my website</h1>
    <p>This is a paragraph.</p>
  </body>
  ```

---

### **7. `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`**

- **목적**: 제목을 정의 (SEO에서 중요한 역할).
- **설명**: `<h1>`이 가장 중요한 제목이고, `<h6>`은 가장 작은 제목입니다.
  ```html
  <h1>Main Title</h1>
  <h2>Sub Title</h2>
  ```

---

### **8. `<p>`**

- **목적**: 문단paragraph을 정의.
  ```html
  <p>This is a paragraph of text.</p>
  ```

---

### **9. `<a>`**

- **목적**: 하이퍼링크를 생성.
- **속성**: `href` (링크 URL)
  ```html
  <a href="https://www.example.com">Visit Example</a>
  ```

---

### **10. `<img>`**

- **목적**: 이미지를 삽입.
- **속성**: `src` (이미지 파일 경로), `alt` (이미지 설명, SEO 및 접근성 중요)
  ```html
  <img src="image.jpg" alt="Description of image" />
  ```

> imgur.com : 외부유출 링크 필요할 때 사용 (private 사진 올리지 말 것!)
> => 만약, 링크가 안된다면 로컬로 접속해서 차단된 것

---

### **11. `<ul>`, `<ol>`, `<li>`**

- **목적**: 목록을 생성.
- **`<ul>`**: 순서 없는 목록, **`<ol>`**: 순서 있는 목록, **`<li>`**: 목록 항목.
  ```html
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
  </ul>
  ```

---

### **12. `<div>`**

- **목적**: 구획을 나누는 컨테이너 (레이아웃을 구성할 때 주로 사용).
  ```html
  <div class="container">
    <p>This is a container.</p>
  </div>
  ```

---

### **13. `<span>`**

- **목적**: 인라인 요소를 정의 (주로 스타일링용).
  ```html
  <span style="color:red;">This is red text</span>
  ```

---

### **14. `<form>`**

- **목적**: 사용자 입력을 받기 위한 폼.
- **속성**: `action` (서버로 제출할 URL), `method` (HTTP 방법: `GET`, `POST`)
  ```html
  <form action="/submit" method="post">
    <input type="text" name="name" required />
    <input type="submit" value="Submit" />
  </form>
  ```

---

### **15. `<input>`**

- **목적**: 사용자가 데이터를 입력할 수 있는 필드.
- **속성**: `type`, `name`, `placeholder`, `value`
  ```html
  <input type="text" name="username" placeholder="Enter your username" />
  ```

---

### **16. `<button>`**

- **목적**: 버튼을 생성.
  ```html
  <button type="submit">Submit</button>
  ```

---

### **17. `<link>`**

- **목적**: 외부 리소스(주로 CSS 파일)를 문서에 연결.
- **속성**: `rel` (연결 방식), `href` (파일 경로)
  ```html
  <link rel="stylesheet" href="styles.css" />
  ```

---

### **18. `<script>`**

- **목적**: JavaScript를 문서에 포함.
- **속성**: `src` (외부 JS 파일), `type` (스크립트 유형)
  ```html
  <script src="script.js"></script>
  ```

---

### **19. `<strong>`**

- **목적**: 중요한 텍스트 강조.
  ```html
  <strong>This is important!</strong>
  ```

---

### **20. `<footer>`**

- **목적**: 페이지 하단에 들어가는 콘텐츠를 정의.
  ```html
  <footer>
    <p>&copy; 2025 My Website</p>
  </footer>
  ```

---

### **기타 중요한 속성들**

- `id`: HTML 요소의 고유 식별자
- `class`: 여러 요소에 동일한 스타일을 적용하기 위해 사용
- `style`: 인라인 스타일 정의
- `target`: 링크가 새 창에서 열리도록 설정 (예: `_blank`)

### **결론**

HTML은 웹 페이지의 구조를 정의하는 핵심 언어입니다. 이 20개의 태그와 그 속성들을 이해하면, 웹 페이지를 SEO 친화적이고 접근성 높은 형태로 구축할 수 있습니다. 각 태그와 속성은 웹 문서에서 중요한 역할을 하며, SEO 최적화에 기여할 수 있습니다.

---

> Q. HTML은 프로그래밍 언어인가?
>
> - html은 문서형식이라 정의상 id가 고유식별자이지만, 여러개 같은 id지정해도 오류가 발생하지 않기 때문에 프로그래밍 언어라 할 수 없음

> HTML 주석
>
> - 단축키 : `cmd`+`/`
> - 기능
>   - 메모 혹은 설명
>   - 특정 요소element 비활성화할 때
>   - 사용하던 기능을 더 이상 사용하지 않을 때
>   - 혹시나 모를 클라이언트의 변심 대비

> HTML은 개발자도구를 통해 편집(문서 수정)이 가능함

> inline style 은 권장하지 않음
>
> - 강제 적용됨
> - 테스트할 때 사용
> - html5부터는 디자인적 요소(태그)들 css에 넘김
> - 살아남은 태그 중 하나인 `<strong>` :: SEO 과정에서 읽어들이기 때문

> [[attribute vs. property]]

---

(25. 01. 20 추가)

> emmet 문법 사용 예시
> `p{줄바꿈을 하려면}+p{이렇게}`

> html은 기본적으로 줄바꿈 인식x
> `<br/>` : break 줄바꿈

> 열린 태그 / 닫힌 태그
>
> - html에서 중요한 키워드 :: **태그**
> - 열린태그 : 사이에 컨텐츠/태그가 들어갈 수 있는 태그
> - 닫힌태그 : 그 자체로 종결되는 태그
>   - 예를 들어 `<br>`태그

> `<head>` : 메타 데이터
> `<body>` : 핵심 데이터

> **`div` 태그와 `p`태그**
>
> - `div` 태그는 division을 뜻하고, 영역을 나눔
> - `p`태그와 다른 점은 `<p>`태그는 위, 아래로 마진margin이 있음
> - 일반적으로 `<div>`안에 `<p>`를 넣는 형식으로 진행

<br/>

[^SEO]: Search Engine Optimization. 웹사이트나 페이지가 검색엔진 결과에서 높은 순위를 차지하도록 최적화하는 과정
[^HTML5]: HyperTextMarkupLanguage. 최신 웹 페이지 구조를 정의하는 마크업 언어. 멀티미디어 요소와 앱 개발을 지원하는 새로운 기능들 포함
[^bullet_point]: 정보를 간결하고 명확하게 전달하기 위한 형식으로, 간단한 목록으로 중요한 정보 나열
[^nut_shell]: 핵심적인 내용을 간략히 요약한 형태로, 긴 설명을 짧고 간결하게 압축하여 핵심 정보만 제공
