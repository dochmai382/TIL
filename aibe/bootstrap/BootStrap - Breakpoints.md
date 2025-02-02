**중단점(Breakpoints)**은 반응형 웹 디자인에서 화면 크기에 따라 레이아웃을 다르게 구성하기 위해 사용하는 기준점입니다. 부트스트랩은 **5가지 기본 중단점**을 제공합니다.

---

각 중단점은 화면의 너비에 따라 레이아웃을 다르게 적용할 수 있도록 설정됩니다. 부트스트랩 5에서 제공하는 기본 중단점은 다음과 같습니다:

- **xs** (Extra small): `< 576px` (모바일)
- **sm** (Small): `≥ 576px` (스몰 화면)
- **md** (Medium): `≥ 768px` (중간 화면, 태블릿)
- **lg** (Large): `≥ 992px` (큰 화면, 데스크탑)
- **xl** (Extra large): `≥ 1200px` (더 큰 화면)
- **xxl** (Extra Extra large): `≥ 1400px` (최대 크기)

### 중단점 사용 예시

```html
<div class="container">
  <div class="row">
    <div class="col-12 col-sm-6 col-md-4">
      <div class="p-3 mb-2 bg-primary text-white">아이템 1</div>
    </div>
    <div class="col-12 col-sm-6 col-md-4">
      <div class="p-3 mb-2 bg-success text-white">아이템 2</div>
    </div>
    <div class="col-12 col-sm-6 col-md-4">
      <div class="p-3 mb-2 bg-warning text-white">아이템 3</div>
    </div>
  </div>
</div>
```

이 코드에서:

- **`col-12`**: 모든 화면 크기에서 12열을 차지합니다 (전체 너비).
- **`col-sm-6`**: `sm` 이상 화면에서 6열을 차지합니다.
- **`col-md-4`**: `md` 이상 화면에서 4열을 차지합니다.

중단점 덕분에 각 화면 크기별로 레이아웃을 쉽게 조정할 수 있습니다.
