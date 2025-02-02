### **부트스트랩의 유래**

- **2011년** 트위터(Twitter)의 개발자 **Mark Otto**와 **Jacob Thornton**이 내부 도구로 개발 (초기 이름: **Twitter Blueprint**)
- 트위터의 디자인 일관성을 유지하기 위해 만들어졌고, 이후 **오픈소스**로 공개되며 전 세계적으로 널리 사용됨
- 현재는 **v5**가 최신 버전 (jQuery 의존성 제거, 더 가벼워짐)

---

### 부트스트랩에서 알아야 할 몇 가지 중요한 점

#### 1) **반응형 웹 디자인 (Responsive Web Design)**

- 부트스트랩은 기본적으로 **모바일 우선(Mobile-first)** 디자인을 채택하고 있습니다. 즉, 모바일 화면에서부터 시작해 점차적으로 더 큰 화면으로 디자인을 확장할 수 있습니다.
- 부트스트랩의 그리드 시스템(12열 기준)은 다양한 화면 크기에 맞춰 레이아웃을 자동으로 조정합니다.
- [[BootStrap - Breakpoints]]

#### 2) **그리드 시스템 (Grid System)**

- 부트스트랩은 **12열 그리드 시스템**을 사용하여 레이아웃을 쉽게 나눌 수 있습니다. `col-`, `col-md-`, `col-lg-`와 같은 클래스를 이용해 다양한 화면 크기에 맞춰 요소들을 배치할 수 있습니다.
- [[Bootstrap - Grid System]]

#### 3) **클래스 기반의 스타일링 (Class-based Styling)**

- 부트스트랩은 미리 정의된 많은 CSS 클래스를 제공합니다. 예를 들어, `btn`, `btn-primary`, `container`, `navbar` 등 클래스를 사용하여 스타일을 쉽게 적용할 수 있습니다.
- 별도의 CSS를 작성하지 않고, 기본 클래스를 사용해 요소의 스타일을 빠르게 수정할 수 있습니다.
- [[Bootstrap - Semantic Colors]]

#### 4) **컴포넌트 (Components)**

- 부트스트랩은 다양한 UI 컴포넌트를 제공합니다. 예를 들어, 버튼, 카드, 네비게이션 바, 모달, 알림창 등 웹 사이트에 자주 사용되는 컴포넌트를 미리 만들어놓았기 때문에, 개발자가 직접 구현할 필요 없이 바로 사용할 수 있습니다.

#### 5) **자바스크립트 플러그인 (JavaScript Plugins)**

- 부트스트랩은 기본적으로 여러 JavaScript 플러그인을 내장하고 있습니다. 예를 들어, **모달 창**, **드롭다운 메뉴**, **슬라이더** 등을 쉽게 구현할 수 있습니다.
- 이러한 플러그인은 jQuery를 기반으로 작동하지만, 최신 버전인 부트스트랩 5부터는 jQuery를 사용하지 않고 **순수 JavaScript**로 작성되었습니다.

#### 6) **자체적인 아이콘 세트 (Icons)**

- 부트스트랩은 **아이콘**을 제공하지 않지만, 최신 버전에서는 **Bootstrap Icons**라는 별도의 아이콘 세트를 지원합니다. 이를 통해 다양한 아이콘을 쉽게 사용할 수 있습니다.

#### 7) **미디어 쿼리 (Media Queries)**

- 부트스트랩은 여러 가지 [[미디어 쿼리 (Media Queries)]]를 제공하여 다양한 화면 크기에서 적절한 레이아웃을 자동으로 조정합니다. 모바일, 태블릿, 데스크탑에서 모두 최적화된 웹 페이지를 만들 수 있습니다.

#### 8) **커스터마이징 가능**

- 부트스트랩은 기본적으로 제공되는 스타일을 커스터마이징할 수 있습니다. **[[SASS]]**를 사용하면 색상, 레이아웃, 폰트 등 다양한 스타일을 프로젝트에 맞게 수정할 수 있습니다.

#### 9) **빠른 개발**

- 미리 정의된 CSS와 JavaScript로 인해 부트스트랩은 빠르게 웹 페이지를 개발할 수 있게 도와줍니다. 특히, 프론트엔드가 익숙하지 않은 개발자에게 매우 유용합니다.

#### 10) **다양한 브라우저 호환성**

- 부트스트랩은 최신 브라우저뿐만 아니라, 구형 브라우저도 지원하여, 개발자가 다양한 환경에서 웹 사이트가 정상적으로 작동하도록 도와줍니다.

---

### **예제 코드**

#### 1. 기본 템플릿 (필수 코드 구조)

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <!-- 필수 메타 태그 -->
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <!-- Bootstrap CSS -->
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
      rel="stylesheet"
    />
    <title>부트스트랩 예제</title>
  </head>
  <body>
    <!-- 컨텐츠 -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
  </body>
</html>
```

#### 2. 반응형 그리드 레이아웃

```html
<div class="container">
  <div class="row">
    <div class="col-12 col-md-6 col-lg-4 bg-light p-3">
      모바일: 12열, 태블릿: 6열, 데스크톱: 4열
    </div>
    <div class="col-12 col-md-6 col-lg-4 bg-secondary p-3">
      동일한 구조 반복
    </div>
  </div>
</div>
```

#### 3. 네비게이션 바 + 카드 컴포넌트

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">로고</a>
    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#navbarNav"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" href="#navbarNav">
      <div class="navbar-nav">
        <a class="nav-link active" href="#">홈</a>
        <a class="nav-link" href="#">메뉴1</a>
      </div>
    </div>
  </div>
</nav>

<div class="card m-3" style="width: 18rem;">
  <img src="이미지주소" class="card-img-top" />
  <div class="card-body">
    <h5 class="card-title">카드 제목</h5>
    <p class="card-text">카드 내용</p>
    <a href="#" class="btn btn-primary">버튼</a>
  </div>
</div>
```

---

### **💡 백엔드 개발자에게 중요한 이유**

1. **관리자 페이지 제작** → 빠르게 UI 구성 가능
2. **API 테스트용 프론트엔드** → 간단한 폼/테이블 구현
3. **협업 시 프론트엔드 코드 이해** → Bootstrap 구조를 알면 커뮤니케이션 용이

---

### **주의사항**

- **과도한 의존성**: Bootstrap 스타일이 모든 상황에 맞지 않을 수 있음
- **성능 이슈**: 사용하지 않는 컴포넌트를 포함하면 파일 크기 증가 → [PurgeCSS](https://purgecss.com/)로 최적화 가능
