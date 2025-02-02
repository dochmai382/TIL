
**미디어 쿼리**는 **반응형 웹 디자인(Responsive Web Design)**을 구현하는 데 사용하는 CSS 기술입니다. 미디어 쿼리는 **화면의 크기**나 **장치의 특성**에 따라 다른 스타일을 적용할 수 있게 해줍니다. 주로 **디바이스의 화면 크기**, **해상도**, **기기 방향(가로/세로)** 등에 맞춰서 스타일을 바꿀 수 있습니다.

---
### 미디어 쿼리 기본 문법
```css
@media (조건) {
  /* 조건에 맞는 경우 적용할 CSS */
}
```
- **조건**에는 화면 너비, 높이, 디바이스의 방향 등이 올 수 있습니다.

### 미디어 쿼리 예시
1. **기본적인 화면 너비에 따른 미디어 쿼리**
    ```css
    /* 기본 스타일 (모든 화면 크기에서 적용) */
    body {
      font-size: 16px;
    }
    
    /* 화면 너비가 768px 이상일 때 */
    @media (min-width: 768px) {
      body {
        font-size: 18px;
      }
    }
    
    /* 화면 너비가 1200px 이상일 때 */
    @media (min-width: 1200px) {
      body {
        font-size: 20px;
      }
    }
    ```
    
2. **디바이스 방향에 따른 스타일 변경**
    ```css
    /* 세로 방향에서 스타일 */
    @media (orientation: portrait) {
      body {
        background-color: lightblue;
      }
    }
    
    /* 가로 방향에서 스타일 */
    @media (orientation: landscape) {
      body {
        background-color: lightgreen;
      }
    }
    ```
    
3. **모바일 장치에 최적화된 미디어 쿼리**
    ```css
    /* 화면 크기가 600px 이하일 때 */
    @media (max-width: 600px) {
      body {
        font-size: 14px;
      }
    }
    ```
    
### 미디어 쿼리를 사용하는 이유
- **반응형 디자인**: 하나의 웹 페이지가 다양한 화면 크기와 디바이스에서 적절하게 보이도록 만들 수 있습니다.
- **웹 페이지 최적화**: 화면 크기에 맞춰 요소의 크기나 레이아웃을 조정하여 사용자 경험을 향상시킬 수 있습니다.
- **애플리케이션 스타일 변경**: 모바일, 태블릿, 데스크탑 등 각기 다른 화면 크기에 맞는 스타일을 쉽게 지정할 수 있습니다.

---
### [[SASS]]와 미디어 쿼리 결합 예시
Sass와 미디어 쿼리를 함께 사용하면 코드의 효율성과 가독성이 더욱 좋아집니다. 예를 들어, Sass에서 미디어 쿼리를 사용할 때 중첩을 활용하면 더욱 간결하게 코드를 작성할 수 있습니다.
```scss
$primary-color: #3498db;

.navbar {
  background-color: $primary-color;

  @media (max-width: 768px) {
    background-color: #2c3e50; /* 작은 화면에서 다른 색상으로 변경 */
  }
}

.button {
  background-color: $primary-color;
  padding: 10px;

  @media (max-width: 600px) {
    padding: 5px; /* 작은 화면에서 버튼 패딩을 줄임 */
  }
}
```

### 결론
- **미디어 쿼리**는 다양한 화면 크기에 맞춰 웹 페이지를 반응형으로 만들 수 있게 해주는 CSS 기술로, 여러 장치에서 최적화된 디자인을 제공할 수 있습니다.
