# **CSS 개요**

- **CSS**(Cascading[^cascading] Style Sheets): HTML 요소의 스타일을 정의하는 언어.
- 웹 페이지의 **디자인**과 **레이아웃**을 설정하는 데 사용됨.
- CSS는 HTML 문서의 **스타일**을 별도로 정의하여 적용.

#### HTML과 CSS의 분리 이점

- 코드의 가독성과 유지보수성 향상
- 동일 HTML에 다양한 스타일 적용 가능
- 여러 페이지에 일관된 스타일 적용 용이

> 개발은 분리해서 하는 것이 표준

# CSS 기본 문법

- **형식**: `selector { property: value; }`

  - `selector`: 스타일을 적용할 HTML 요소.
  - `property`: 적용할 스타일의 속성.
  - `value`: 속성의 값.

  ```css
  selector {
    property: value;
  }
  ```

# **CSS 작성 방법**

> 이미 정의되어 있는 css 형태를 가져다 쓰는 것이 일반적

> CSS 원하는 스타일을 GPT에 물어봐서 하는 것도 좋음

- **외부 스타일시트**:
  - HTML 문서와 별도로 CSS 파일을 만들어 링크
    ```html
    <link rel="stylesheet" href="styles.css" />
    ```

> 외부 스타일의 경우
>
> 1. CDN[^CDN]이 깨지면 스타일도 깨짐
> 2. html 구조만으로는 어떻게 디자인되었는지 확인 불가

- **내부 스타일시트**:
  - HTML `<head>` 안에 `<style>` 태그로 스타일 작성.
    ```html
    <style>
      p {
        color: blue;
      }
    </style>
    ```

> 모든 스타일을 내부 스타일시트로 적용시 :
>
> - `<head>` 가 길어지는 것은 좋지 않음
> - 동일 스타일 적용시 유지보수 힘듦
>   -> 그렇기 때문에 외부 스타일시트로 설정

- **인라인 스타일**:
  - HTML 태그에 직접 스타일을 작성.
    ```html
    <p style="color: blue;">Text</p>
    ```

> 인라인 스타일 지정시 생기는 의문 2가지
>
> 1. 왜 여기만 지정되는가?
>    - 기본적 인라인 스타일은 해당 태그만 선택됨
> 2. 지정되는 범위는 어디까지인가?
>    - 하위 태그 존재 시 스타일 상속됨
>    - 가까운 곳에 더 영항을 받음 (우선순위)

---

# **CSS 선택자(Selector)**

- **요소 선택자**: HTML 태그 이름으로 스타일 적용.
  ```css
  p {
    color: red;
  }
  ```
- **클래스 선택자**: `.`을 사용하여 클래스를 가진 요소에 스타일 적용.

  ```css
  .button {
    background-color: green;
  }
  ```

  > 클래스 선택자의 경우 공백을 기준으로하여 여러개 지정 가능
  > `<p class="one two"></p>`

- **아이디 선택자**: `#`을 사용하여 특정 아이디를 가진 요소에 스타일 적용.
  ```css
  #header {
    font-size: 24px;
  }
  ```

> `*` : 전체 선택 / 글씨체 종류 지정 등

---

# **CSS 속성(Property)**

- **색상 관련**: `color`, `background-color`.
- **폰트 관련**: `font-size`, `font-family`.
- **크기 관련**: `width`, `height`, `padding`, `margin`.
- **배경 관련**: `background-image`, `background-color`.
- **레이아웃 관련**: `display`, `position`, `flex`.

## 프로퍼티 크기 단위

- `px`: 픽셀 단위, 절대값
- `%` : 상위 태그 크기에 비례
- `em` : font size에 영향을 받음
  - `rem` : root를 기준
    - font-size는 계속 바뀔 수 있음. 그렇기 때문에 절대적인 기준이 필요함
    - 절대적인 기준 == root
    - `em`보다 `rem`을 더 많이 사용
- viewport의 경우 `vh`, `vw` 많이 사용

## 상속

- 상속되는 속성:
  - 폰트 관련 속성 (예: `font-family`, `color` 등)
- 상속되지 않는 속성:
  - 레이아웃 및 크기 관련 속성 (예: `width`, `height`, `margin` 등)
- **상속의 이점**
  - 중복 코드 감소
  - 스타일 관리 효율성 향상

> [!note] >[[attribute vs. property]]

---

# CSS 기본 스타일링 예시\*\*

```css
/* 텍스트 색상 및 배경색 설정 */
p {
  color: blue;
  background-color: lightgray;
}

/* 클래스 선택자 */
.button {
  font-size: 16px;
  padding: 10px;
}

/* 아이디 선택자 */
#header {
  text-align: center;
}
```

> css 주석 `/* */`

---

# 결합자

> [CSS - 결합자 (Selectors)](<./CSS%20-%20결합자%20(Selectors).md>)

---

# **CSS 우선순위 (Specificity)**

> [CSS - 우선순위, 명시도](./CSS%20-%20우선순위,%20명시도.md)

- **ID** 선택자가 가장 높은 우선순위를 가짐 (`#id`).
- **클래스** 선택자 다음 (`.class`).
- **요소** 선택자 (`div`, `p` 등) 우선순위 낮음.
  > 선택자는 좁아질수록 우선순위가 높다

---

[^CDN]: CDN(Content Delivery Network)은 전 세계에 분산된 서버 네트워크를 통해 사용자에게 웹 콘텐츠(예: HTML, CSS, JavaScript 파일, 이미지, 동영상 등)를 더 빠르고 효율적으로 전달하기 위한 시스템
