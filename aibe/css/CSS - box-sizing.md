### **CSS Box Model에서 box-sizing과 content-sizing의 차이점**

#### **1. box-sizing**

- **box-sizing**은 **요소의 총 크기 계산 방법**을 결정하는 CSS 속성입니다.
- 기본적으로 **content-box**로 설정되어 있는데, 이 경우 **width**와 **height**가 **내용(content)**만을 기준으로 설정됩니다.
- **box-sizing**을 **border-box**로 설정하면, **width**와 **height**가 **내용(content) + padding + border**를 포함하는 값으로 계산됩니다.

#### **2. content-sizing**

- **content-sizing**은 정확한 용어는 아니지만, **`box-sizing: content-box`**와 동일한 개념으로 이해할 수 있습니다.
- **content-sizing**은 요소의 **내용(content)**만을 기준으로 크기를 계산하며, **padding**과 **border**는 **크기 외부**에 추가됩니다.

---

### **차이점 요약**

| 속성                   | `box-sizing: content-box`                                  | `box-sizing: border-box`                                                       |
| ---------------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **기본 동작**          | `width`와 `height`가 **내용(content)**만을 기준으로 계산   | `width`와 `height`가 **내용(content) + padding + border**를 포함한 크기로 계산 |
| **패딩과 테두리**      | **패딩**과 **테두리**는 **내용 외부**에 추가되어 크기 증가 | **패딩**과 **테두리**는 **전체 크기**에 포함되어 크기 변화 없음                |
| **요소 크기**          | **width** + **padding** + **border** = 총 크기             | **width**는 전체 크기, 패딩과 테두리는 그 안에 포함                            |
| **주로 사용되는 경우** | 기본값, 예전 방식                                          | 레이아웃을 좀 더 **예측 가능**하고 **정확하게** 관리하고 싶을 때               |

---

### **예시로 비교**

#### **1. content-box (기본값)**

```css
div {
  width: 200px;
  padding: 20px;
  border: 10px solid black;
  box-sizing: content-box;
}
```

- **내용(content)** 크기: 200px
- **패딩**(padding) 20px + **테두리**(border) 10px은 **외부에 추가**되어, 총 **크기**는 `200px (content) + 20px (padding) + 10px (border)` = **260px**입니다.

#### **2. border-box**

```css
div {
  width: 200px;
  padding: 20px;
  border: 10px solid black;
  box-sizing: border-box;
}
```

- **전체 크기**는 **200px**로 고정됩니다.
- `padding`과 `border`가 **전체 크기**에 포함되기 때문에 **내용(content)**의 크기는 `200px - 20px (padding) - 10px (border)` = **170px**로 줄어듭니다.

---

### **요약**

- **`box-sizing: content-box`**: 기본 설정. **width**와 **height**는 **내용**만을 기준으로 계산되고, **패딩**과 **테두리**는 그 외부에 추가됩니다.
- **`box-sizing: border-box`**: **width**와 **height**가 **내용 + 패딩 + 테두리**를 포함하여 계산되므로, 요소 크기를 더 **예측 가능**하게 만들 수 있습니다.

**결론**: `border-box`는 레이아웃을 **더 쉽게 조정**하고, `content-box`는 기본값으로 **패딩과 테두리가 크기 계산에 영향을 준다**는 점에서 차이가 있습니다.
