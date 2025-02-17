### **1. 컨테이너 (Container)**

컨테이너는 여러 개의 **아이템**들을 **감싸고 있는 큰 상자**라고 생각하시면 됩니다.

- 예를 들어, 책을 여러 권 가지고 있다고 생각해보세요. 이 책들을 넣을 수 있는 **책장이 컨테이너**라고 할 수 있습니다.
- 이 책장 안에 있는 책들은 **아이템**이 되는 거죠.
- 컨테이너는 책들이 어떻게 배치될지, 정렬될지, 크기가 어떻게 될지를 **관리**하는 역할을 합니다.

### **2. 아이템 (Item)**

아이템은 컨테이너 안에 들어가는 **개별적인 항목들**입니다. 예를 들어, 책장 안에 들어 있는 각 **책**들이 아이템에 해당합니다.

- 아이템은 컨테이너 안에서 **배치**되거나 **정렬**될 수 있습니다.
- 책은 크기나 위치가 다를 수 있겠지만, 책장을 기준으로 잘 정리되도록 배치됩니다.

### **차이점**

- **컨테이너**는 여러 아이템을 감싸는 **큰 박스**입니다. 아이템들이 어떻게 배치될지 정해주는 역할을 하죠.
- **아이템**은 그 큰 박스 안에 들어가는 **개별적인 물건들**입니다.

### **예시 코드: 책장(컨테이너)과 책(아이템)**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>컨테이너와 아이템 예시</title>
    <style>
      /* 책장(컨테이너) 스타일 */
      .container {
        display: flex; /* 아이템들을 가로로 정렬 */
        justify-content: space-between; /* 책들 사이에 간격을 두기 */
        align-items: center; /* 책을 세로로 가운데 정렬 */
        height: 100vh; /* 화면 높이만큼 크기 설정 */
        padding: 20px;
        background-color: lightgray; /* 배경 색 */
      }

      /* 책(아이템) 스타일 */
      .item {
        width: 100px; /* 책 크기 */
        height: 150px; /* 책 크기 */
        background-color: coral; /* 책 색상 */
        display: flex;
        justify-content: center; /* 책 제목을 가운데 정렬 */
        align-items: center; /* 책 제목을 세로로 가운데 정렬 */
        color: white; /* 글자 색 */
        font-size: 16px;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="item">책 1</div>
      <div class="item">책 2</div>
      <div class="item">책 3</div>
    </div>
  </body>
</html>
```

### 설명:

- **컨테이너**는 `.container`로 지정된 `div`로, 여기에 **책들**을 담고 있는 책장이 됩니다. 이 책장은 `flex`라는 특수한 방법으로 책들을 **가로로 배치**하고, 책들 사이에 일정한 **간격**을 둡니다.
- **아이템**은 `.item`으로 지정된 각 `div`로, 각각의 책을 의미합니다. 각 책은 크기가 일정하고, 가운데 정렬된 제목을 가지고 있습니다.

이 예시에서 **컨테이너**는 책장을, **아이템**은 책들을 의미하는 거죠. 책장(컨테이너)은 책들(아이템)을 어떻게 배치할지를 관리합니다.

### 간단히 요약:

- **컨테이너**: 여러 개의 아이템을 **담고 있는 상자**.
- **아이템**: 그 상자 안에 들어있는 **책**들.
