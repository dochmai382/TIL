**시맨틱 컬러**는 부트스트랩에서 사용되는 의미론적 색상으로, 주로 **상태(state)나 역할(semantic)**을 나타내는 데 사용됩니다. 예를 들어, `primary`, `secondary`, `success`, `danger`와 같은 색상은 디자인의 목적에 맞게 특정 역할을 강조하는 데 사용됩니다.

---

### 기본 시맨틱 컬러

부트스트랩은 기본적으로 다음과 같은 시맨틱 컬러 클래스를 제공합니다:

- **Primary**: 기본적인 주요 색상. 주로 버튼, 링크, 강조 표시 등에 사용됩니다.
- **Secondary**: 두 번째 중요 색상. `primary`보다 덜 강조된 요소에 사용됩니다.
- **Success**: 성공적인 작업이나 긍정적인 상태를 나타냅니다.
- **Danger**: 위험하거나 경고가 필요한 상태를 나타냅니다.
- **Warning**: 주의가 필요한 상태를 나타냅니다.
- **Info**: 정보성 메시지나 상태를 나타냅니다.
- **Light**: 밝은 색상. 배경이나 강조된 텍스트 등에 사용됩니다.
- **Dark**: 어두운 색상. 강조된 배경이나 텍스트에 사용됩니다.

### 시맨틱 컬러 사용 예시

```html
<button class="btn btn-primary">주요 버튼</button>
<button class="btn btn-secondary">보조 버튼</button>
<button class="btn btn-success">성공 버튼</button>
<button class="btn btn-danger">위험 버튼</button>
<button class="btn btn-warning">주의 버튼</button>
<button class="btn btn-info">정보 버튼</button>
<button class="btn btn-light">밝은 버튼</button>
<button class="btn btn-dark">어두운 버튼</button>
```

#### 설명:

- 각 버튼에 적용된 클래스(`btn btn-primary`, `btn btn-success` 등)는 해당 상태를 나타내는 색상과 의미를 반영합니다.
- 예를 들어, **`btn-danger`**는 사용자가 클릭할 때 위험한 작업을 실행할 수 있는 버튼에 적합하고, **`btn-success`**는 성공적인 작업을 나타냅니다.
