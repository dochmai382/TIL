# Emmet이란?

- HTML과 CSS의 빠른 코딩을 돕는 도구
- 간결한 단축키를 사용해 긴 코드를 효율적으로 생성할 수 있게 해줌
  - 개발자가 빠르게 구조를 작성하고, 반복적인 작업 줄일 수 있음
- 지원 : `VSCode`, `Sublime Text`, `Atom` 등 여러 코드 에디터에서 지원됨

## **Emmet 기본 문법**

1. **태그 생성**
   - Emmet을 사용하면 태그를 빠르게 생성 가능
   - 예: `div` → `<div></div>`
1. **태그에 클래스나 아이디 추가**
   - 클래스는 `.`(dot)으로, 아이디는 `#`(hash)로 지정
   - 예: `div.container` → `<div class="container"></div>`
   - 예: `#header` → `<div id="header"></div>`
1. **중첩된 태그 생성**

   - `>`를 사용하여 태그를 중첩 가능
   - 예: `div>ul>li` →
     ```html
     <div>
       <ul>
         <li></li>
       </ul>
     </div>
     ```

1. **반복되는 태그 생성**

   - `*`을 사용하여 반복 가능
   - 예: `ul>li*5` →
     ```html
     <ul>
       <li></li>
       <li></li>
       <li></li>
       <li></li>
       <li></li>
     </ul>
     ```

1. **텍스트 추가**

   - `{}`를 사용하여 텍스트를 추가
   - 예: `div{Hello, World!}` → `<div>Hello, World!</div>`

1. **속성 추가**

   - `[]`를 사용하여 태그에 속성을 추가
   - 예: `input[type="text"]` → `<input type="text">`
   - 예: `a[href="https://example.com"]` → `<a href="https://example.com"></a>`

1. **두 번째 레벨 중첩**

   - `+`를 사용하여 같은 수준의 태그를 추가
   - 예: `div+ul>li` →
     ```html
     <div></div>
     <ul>
       <li></li>
     </ul>
     ```

1. **문자열 반복**
   - `*`와 `{}`를 결합하여 문자열을 반복 가능
   - 예: `ul>li*3{Item $}` →
     ```html
     <ul>
       <li>Item 1</li>
       <li>Item 2</li>
       <li>Item 3</li>
     </ul>
     ```

### **복합 예시**

1. **복잡한 구조**
   - 예: `div.container>header+main>section*2>article>p{Lorem ipsum}`
   - 결과:
     ```html
     <div class="container">
       <header></header>
       <main>
         <section>
           <article>
             <p>Lorem ipsum</p>
           </article>
         </section>
         <section>
           <article>
             <p>Lorem ipsum</p>
           </article>
         </section>
       </main>
     </div>
     ```
2. **특정 속성을 가진 여러 요소 생성**
   - 예: `input[type="text"]*3`
   - 결과:
     ```html
     <input type="text" />
     <input type="text" />
     <input type="text" />
     ```

> [!Note]
> [Emmet: cheat-sheet](https://docs.emmet.io/cheat-sheet/)
