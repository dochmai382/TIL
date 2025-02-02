CSS 박스모델은 HTML 요소를 렌더링할 때의 구조와 여백, 경계 등을 정의하는 기본적인 개념

---

### CSS 박스모델 핵심 개념

- **4가지 영역**으로 구성:
  1. **Content**: 요소의 실제 내용이 들어가는 공간 (텍스트, 이미지 등).
  2. **Padding**: Content와 Border 사이의 내부 여백.
  3. **Border**: Padding과 Margin 사이의 경계선.
  4. **Margin**: 요소와 다른 요소 사이의 외부 여백.

---

### 주요 속성

1. **`box-sizing`**

   - 요소 크기 계산 방식을 지정.
   - 기본값: `content-box` (content만 width/height에 포함).
   - `border-box`: padding과 border를 포함한 크기를 지정.

2. **`margin`**

   - 요소의 외부 공간을 정의.
   - 상하좌우 각각 또는 한꺼번에 지정 가능:
     ```css
     margin: 10px; /* 모든 방향 동일 */
     margin: 10px 20px; /* 상하 10px, 좌우 20px */
     margin: 10px 15px 20px 25px; /* 상 우 하 좌 */
     ```

3. **`padding`**

   - 내부 여백을 정의:
     ```css
     padding: 15px; /* 모든 방향 동일 */
     ```

4. **`border`**
   - 경계선을 정의 (굵기, 스타일, 색상):
     ```css
     border: 2px solid #000; /* 두께, 선 스타일, 색상 */
     ```

---

### 간단한 사용법

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CSS Box Model</title>
    <style>
      .box {
        width: 200px; /* 콘텐츠 영역 너비 */
        padding: 20px; /* 내부 여백 */
        border: 5px solid #333; /* 경계선 */
        margin: 10px; /* 외부 여백 */
        box-sizing: border-box; /* 전체 너비 계산 방식 */
      }
    </style>
  </head>
  <body>
    <div class="box">박스 모델 예제</div>
  </body>
</html>
```

---

> `<div>`는 컨테이너 개념으로 아래와 같은 이유로 style 지정
>
> - 초기값 설정
> - 공통된 속성

> css작성시
> `* { margin: 0; padding: 0; }`
> 위와 같이 설정하지 않으면 내가 디자인한 것과 결과가 달라짐
> 그렇기 때문에 `*`로 전체 지정

> [마진 병합 현상 (Margin Collapsing)](</git_til/aibe/css/마진%20병합%20현상%20(Margin%20Collapsing).md>)

> [CSS - box-sizing](/git_til/aibe/css/CSS%20-%20box-sizing.md)
