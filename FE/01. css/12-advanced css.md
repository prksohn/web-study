## Advanced CSS (5) - Cascade

### Cascade란?

여러 CSS 규칙이 같은 요소에 적용될 때, 어떤 규칙을 최종적으로 적용할지 결정하는 우선순위 시스템

#### 1. Source Order - 작성 순서

동일한 조건이라면 나중에 선언된 CSS가 적용

```css
.text {
  color: blue;
}

.text {
  color: red;
}
```

- 같은 선택자에 같은 요소 지정 했을 경우 : 나중에 선언된 css가 적용
- 단순히 아래쪽의 css가 적용되는 게 아니라,
- 나중에 선언된 css가 적용되는

#### 2. Inheritance - 상속

부모의 스타일이 자식에게 전달

```html
<div class="parent">
  <p>Hello</p>
</div>
```

```css
.parent {
  color: blue;
}
```

- 자식 요소에는 color을 지정하지 않았어도 부모 스타일을 상속 받아 적용
- 모든 css 속성에 적용되는 건 아님 (상속되는 속성/상속되지 않는 속성 존재)

#### 상속 되는 속성 - 텍스트 관련

```css
color
font-family
font-size
font-weight
line-height
text-align
```

#### 상속 되지않는 속성

```css
width
height
margin
padding
border
background
```

#### 강제로 상속 사용 - `inherit`

```css
.parent {
  color: blue;
}

.child {
  color: inherit;
}
```

#### 3. `!important` - 가장 높은 우선 순위

해당 선언의 우선순위를 가장 높게 설정

```css
.text {
  color: blue;
}

.text {
  color: red !important;
}
```

- `!important` > `#id` > `.class`
- `!important` 를 여러 곳에 선언할 경우 CSS 수정이 복잡해지므로 (유지보수 난이)
- 정말 필요한 경우에만 사용 -> 외부 CSS를 강제로 덮어야 하는 경우 등 제한적으로

#### 4. `@layer` - Cascade Layer 생성

CSS 규칙들을 계층별로 그룹화하고, 어떤 그룹이 우선할지 명확하게 정하는 기능

```css
@layer reset {
  /* reset 
  브라우저 기본 스타일을 원하는 형태로 초기화
  *의 box-sizing,
  <body>, <h1-3> 등에 기본 margin 등
  */
}

@layer base {
  /* 사이트 기본 스타일
   font-family, color, background, font 등
   */
}

@layer components {
  /* 컴포넌트 (버튼, 카드, 모달 등의 UI) */
}

@layer utilities {
  /* 유틸리티
  (margin, display, text-align 같은 작은 목적의 재사용 CSS)
  */
}
```

- 프로젝트가 커질수록 CSS끼리 서로 덮어쓰는 경우 발생
- 이때 `@layer` 사용 시, 위의 구조로 우선 순위를 명시적으로 생성 가능

##### 구조의 우선순위

```css
@layer base {
  p {
    color: blue;
  }
}

@layer components {
  p {
    color: red;
  }
}
```

- components 쪽의 규칙이 더 높은 Layer 우선순위 가짐
- 단순히 나중에 선언했기 때문이 아닌,
- Layer의 순서를 결정할 때 처음 선언된 순서가 중요
- 하지만 @layer가 있다고 무조건 모든 CSS보다 강한 건 아님
- Layer 밖에 있는 일반 CSS도 우선순위 계산에 관여
- 추후 Specificity에서 자세히
