### **Sass (Syntactically Awesome Stylesheets)**
**Sass**는 **CSS**를 확장한 스타일시트 언어입니다. CSS를 더 효율적으로 작성할 수 있게 도와주는 도구로, 주로 **변수**, **중첩(Nesting)**, **믹스인(Mixins)**, **함수(Functions)** 등을 활용해 스타일을 더 구조적이고 유지보수하기 쉬운 방식으로 작성할 수 있게 해줍니다.

---
#### Sass의 주요 특징
- **변수 (Variables)**: 값을 변수로 저장하여 재사용할 수 있습니다. 예를 들어, 색상, 폰트 크기 등을 변수로 선언해두고 여러 곳에서 재사용할 수 있습니다. 
    ```scss
    $primary-color: #3498db;
    
    body {
      color: $primary-color;
    }
    ```
    
- **중첩 (Nesting)**: CSS 선택자를 중첩하여 계층적인 구조를 자연스럽게 표현할 수 있습니다.
    ```scss
    .navbar {
      background-color: #333;
      
      ul {
        list-style: none;
        
        li {
          display: inline-block;
          
          a {
            color: white;
            text-decoration: none;
          }
        }
      }
    }
    ```
    
- **믹스인 (Mixins)**: 여러 CSS 속성을 재사용 가능한 블록으로 묶어 놓고 필요할 때마다 사용할 수 있습니다.
    ```scss
    @mixin border-radius($radius) {
      -webkit-border-radius: $radius;
      -moz-border-radius: $radius;
      border-radius: $radius;
    }
    
    .box {
      @include border-radius(10px);
    }
    ```
    
- **함수 (Functions)**: Sass에서 함수를 만들어, 값을 계산하거나 반환할 수 있습니다.
    ```scss
    @function calculate-rem($px) {
      @return $px / 16px * 1rem;
    }
    
    .text {
      font-size: calculate-rem(24px);
    }
    ```
#### Sass의 두 가지 문법
Sass는 두 가지 문법을 제공합니다:
- **.scss** (Sassy CSS): CSS와 호환되는 문법으로 더 직관적이고 쉽게 사용할 수 있습니다.
- **.sass** (Old Sass): 중괄호와 세미콜론을 생략한 문법입니다.

**예시**: `style.scss` 파일을 작성한 후, 컴파일해서 `style.css`로 변환해야 합니다. 이를 위해서는 **Node.js** 환경에서 **Sass** 컴파일러를 사용하거나, **빌드 도구(예: Webpack)** 등을 설정해야 합니다.

### 결론
- **Sass**는 CSS를 더 효율적이고 유지보수하기 쉽게 작성할 수 있도록 도와주는 도구로, 변수, 중첩, 믹스인 등을 활용하여 코드를 구조화할 수 있게 합니다.
