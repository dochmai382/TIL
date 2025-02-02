# Favicon

- 웹 브라우저의 탭, 북마크, **즐겨찾기** 목록 등에 표시되는 작은 아이콘
- **목적**: 사용자가 웹사이트를 쉽게 식별하도록 돕는 것
- 이미지 파일 형식 : `.ico`, `.png`, `.svg`

### 활용

1. 이미지 에셋 다운로드
1. [Realfavicongenerator.net](https://realfavicongenerator.net/) 접속 → Pick your favicon image
   ![[Pasted image 20250119204708.png|400]]
1. 생성 페이지 하단 `next` 클릭
   ![[Pasted image 20250119204749.png|500]]
1. 생성된 favicon package `download`
1. html 내 `<head>` 태그에 아래 코드 붙여 넣음
   ```html
   <link rel="icon" type="image/png" href="/favicon-96x96.png" sizes="96x96" />
   <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
   <link rel="shortcut icon" href="/favicon.ico" />
   <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
   <link rel="manifest" href="/site.webmanifest" />
   ```

---

(25. 01. 20 추가)

> 위 과정에서 발생할 수 있는 실수
>
> - 경로 실수
> - 패키지 파일 위치
> - 아직 빌드가 끝나지 않았는데 확인
> - 커밋 & 푸시 안함
> - 캐싱 문제 (**웹 캐시**)

> [!note] > [[path 경로 지정 방법]]

---

# Open Graph (OG) 태그

- Facebook에서 개발한 메타 태그 표준
- 목적: 소셜 미디어 플랫폼에서 웹사이트를 공유할 때 콘텐츠 미리보기를 제어
- 역할:
  - 콘텐츠의 **미리보기 정보**(제목, 설명, 이미지)를 사용자가 지정하여 표시
  - 클릭률을 높이고, 공유 시 일관된 정보 전달
  - 페이지가 더 매력적으로 보이도록 디자인 제어
  - **브랜딩과 트래픽 증가를 위해 필수적인 요소**

## 주요 태그

- `og:title` : 콘텐츠의 제목 설정
- `og:description` : 콘텐츠의 간략한 설명 (SEO에도 도움)
- `og:imgae` : 공유시 표시되는 썸네일 이미지 URL
- `og:url` : 공유된 콘텐츠의 URL을 지정 (정확한 URL로 리다이렉트 가능)
- `og:type` : 콘텐츠 유형을 지정. 예: `website`, `article`, `video`, `music` 등
- `og.site_name` : 웹사이트의 이름을 설정 (사이트의 브랜드 이름)
- `og:locale` : 콘텐츠의 언어와 지역 설정. 기본값은 `en_US`

### 예제

```html
<head>
  <meta property="og:title" content="Welcome to My Blog" />
  <meta
    property="og:description"
    content="Learn about HTML, CSS, and web development."
  />
  <meta property="og:image" content="https://example.com/blog-image.jpg" />
  <meta property="og:url" content="https://example.com/my-blog" />
  <meta property="og:type" content="article" />
  <meta property="og:site_name" content="My Blog" />
  <meta property="og:locale" content="en_US" />
</head>
```

## **왜 OG 태그가 중요한가?**

1. **소셜 미디어에서 더 나은 표시**
   - 이미지와 텍스트가 제대로 구성되어 더 매력적인 미리보기 제공.
2. **CTR(클릭률) 증가**
   - 매력적인 미리보기가 클릭을 유도.
3. **브랜드 일관성**
   - 공유될 때 사이트 이름과 정보를 일관되게 유지.
4. **SEO 및 SMO(Social Media Optimization)**
   - OG 태그는 간접적으로 검색 노출과 소셜 미디어 트래픽에도 영향을 미침.

---

## **SEO와 OG 태그의 연관성**

1. **사용자 경험 개선**:
   - SEO는 검색엔진에서의 가시성을 높이고,
   - OG 태그는 소셜 미디어 공유 시 매력적인 미리보기를 제공해 더 많은 클릭을 유도.
1. **트래픽 증가**:
   - SEO로 검색엔진에서,
   - OG 태그로 소셜 미디어에서 더 많은 사용자 유입 가능.
1. **브랜딩 효과**:
   - OG 태그를 통해 소셜 미디어에서 브랜드의 일관된 이미지와 정보를 유지하고, 검색엔진에서도 브랜드 신뢰도를 높임.

> - **SEO**는 검색엔진에서의 **노출과 가시성**을 높이는 데 초점이 맞춰져 있고, **OG 태그**는 소셜 미디어에서의 **공유와 클릭 유도**에 중점을 둠
> - 두 기술을 적절히 조합하면, 검색엔진과 소셜 미디어 모두에서 효과적인 트래픽 유입과 사용자 경험을 제공 가능

### **실제 코드 예시**

SEO와 OG 태그를 통합적으로 작성한 예시:

```html
<head>
  <!-- SEO 태그 -->
  <title>Learn HTML and SEO Basics</title>
  <meta
    name="description"
    content="Master the basics of HTML, SEO, and Open Graph Tags."
  />
  <meta name="keywords" content="HTML, SEO, Open Graph, Web Development" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- OG 태그 -->
  <meta property="og:title" content="Learn HTML and SEO Basics" />
  <meta
    property="og:description"
    content="Master the basics of HTML, SEO, and Open Graph Tags."
  />
  <meta property="og:image" content="https://example.com/thumbnail.jpg" />
  <meta property="og:url" content="https://example.com/seo-guide" />
  <meta property="og:type" content="website" />
  <meta property="og:site_name" content="My Web Development Blog" />
</head>
```

---

(25. 01. 20 추가)

> [[이미지 주소 복사 vs. 이미지 파일 링크]]

> raw ?

> 캐싱
>
> - 슬랙 같은 협업 툴은 효율적인 공유를 위해 캐싱 기능을 제공함
> - 캐싱이 없다면
>   - 데이터를 조회할 때마다 새로운 요청시 fee 발생
> - 캐싱 단위 :
>   - 슬랙의 경우 주소(url) 단위로 캐싱 처리
> - 캐싱 방지 전략
>   - 조금이라도 주소가 다르다면 캐싱이 안됨 == 주소 변경시
>   1.  파일명 or 레포지토리명을 바꾼다
>   2.  버전 붙이기 (쿼리 문자열 방식) = url 수정
>       1. `?` 또는 `#`을 붙이면 별도의 작업으로 인식됨
>       2. `#`의 경우 원래 북마킹 용도로 사용했지만 요즘은 거의 사용하지 않음
>       3. 예시) github.io/review/250120.html?v1
