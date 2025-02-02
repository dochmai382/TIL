부트스트랩의 그리드 시스템은 **12개의 열을 기준으로 웹 페이지 레이아웃을 구성**하는 방법입니다. 이를 통해 다양한 화면 크기에서 레이아웃을 자동으로 조정할 수 있습니다. 부트스트랩의 그리드 시스템은 **flexbox**를 기반으로 하며, **반응형 디자인**을 쉽게 구현할 수 있습니다.

---

### 기본 구조

부트스트랩의 그리드 시스템은 `container` 안에 `row`와 `col-*` 클래스를 사용하여 요소들을 배치합니다.

- **Container**: 그리드 시스템을 감싸는 최상위 요소로, 레이아웃을 중앙에 배치하거나 일정한 너비를 설정합니다.
- **Row**: 그리드의 한 줄을 구성하는 요소로, 여러 개의 열(`col-*`)을 포함합니다.
- **Column (`col-*`)**: 각 열을 정의하는 요소로, 화면 크기에 따라 너비가 자동으로 조정됩니다.

### 예시 코드

```html
<div class="container">
  <div class="row">
    <div class="col-12 col-md-6 col-lg-4">
      <div class="p-3 mb-2 bg-primary text-white">1번 항목</div>
    </div>
    <div class="col-12 col-md-6 col-lg-4">
      <div class="p-3 mb-2 bg-success text-white">2번 항목</div>
    </div>
    <div class="col-12 col-md-6 col-lg-4">
      <div class="p-3 mb-2 bg-warning text-white">3번 항목</div>
    </div>
  </div>
</div>
```

#### 설명:

- `col-12`: 화면 크기와 관계없이 12열을 차지합니다 (즉, 한 줄을 모두 채웁니다).
- `col-md-6`: 중간 크기(모바일을 제외한 중간 화면 크기 이상)에서 6열을 차지합니다.
- `col-lg-4`: 큰 화면에서는 4열을 차지합니다.

이처럼 `col-*` 클래스를 이용해 화면 크기에 따라 유동적으로 열의 너비를 조정할 수 있습니다.
