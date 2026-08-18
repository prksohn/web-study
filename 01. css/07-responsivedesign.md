## Responsive Design

### Responsive Design이란?

화면 크기나 환경이 달라져도 웹페이지가 적절하게 보이도록 만드는 것

### 1. `%`, `vw/vh`, `max-width`, `min-width` - 유동적인 크기

```css
선택자 {
  width: 100%;
}
```

- `%` : 부모 요소의 너비를 기준으로 부모 크기에 따라 움직임
- `vh` : 브라우저 화면 기준, 화면 높이의 % (viewport height)
- `vw` : 브라우저 화면 기준, 화면 너비의 % (viewport width)
- `max-width` : 너무 커지지 않게 = 최대 크기
- `min-width` : 너무 작아지지 않게 = 최소 크기
- `margin: 0 auto` : 남는 좌우 공간을 자동으로 나눠서 가운데 배치

### 2. `Media Query` - 특정 조건에서만 css를 적용

#### 사용 용도

`auto-fit`, `minmax()` 도 반응형이지만 <br>
같은 레이아웃을 자동으로 줄였다 늘렸다 할 때 사용하고, <br>
레이아웃 자체를 변경하고 싶을 때 -> `Media Query` 사용 <br>
모바일에서 햄버거바로 메뉴를 숨기고 버튼을 보여줄 때 주로 사용

```css
@media (조건) {
  /* 조건이 맞을 때 사용할 css */
}

@media (max-width: 600px) {
  .products {
    grid-template-columns: 1fr;
    /* 화면 너비가 600px 이하라면, .products를 1열로 만들어라. */
  }
}
```

- 조건에 따른 Grid, Flex 방향, 글자 크기, 여백, 메뉴, 이미지, 버튼 등 모두 변경 가능
- 상품 카드는 보통 브라우저가 알아서 카드 개수 조절 하기 때문에 `auto-fit` 으로 충분
- pc와 모바일에서 구조가 바뀐다면, `Media Query` 가 적합

### 3. `Desktop First`, `Mobile First` - 화면 생성 순서

```css
/* pc */
.products {
  grid-template-columns: repeat(4, 1fr);
}

/* 태블릿, 모바일 */
@media (max-width: 768px) {
}
```

- `Desktop First` : pc 화면 먼저 생성 후 태블릿,모바일 화면 생성
- `Mobile First` : 모바일을 기본으로 생성 후 pc 화면으로 확장

### 4. `Breakpoint` - 레이아웃을 바꾸기로 결정한 화면 너비

```css
@media (max-width: 768px) {
}
```

- `768px` : 하나의 Breakpoint
- 디자인마다 몇 px에서 깨지는지에 따라 조정
- 즉, 반응형에서는 기기보다 콘텐츠를 기준으로 조정

### 5. 이미지 반응형 만들기

```css
/* 부모 너비에 맞춰 이미지 크기 조정 */
img {
  width: 100%;
  height: auto;
}

/* 일정한 영역을 채우고 싶을 때 */
선택자 img {
  width: 100%;
  height: 250px;
  object-fit: cover;
}
```

- `object-fit: cover;` : 이미지 비율 유지하면서 영역을 꽉 채울 때

### 6. `box-sizing: border-box` - 전체 문서 크기 조정

```css
* {
  box-sizing: border-box;
}

선택자 {
  width: 300px;
  padding: 20px;
}
```

- 모든 문서에 `box-sizing: border-box` 적용 시, `padding`, `border` 를 포함해서 300px로 계산되서 크기 예측 용이

### 7. `overflow` - 모바일에서 가로 스크롤이 생길 경우

모바일에서 화면이 옆으로 밀릴 경우, <br>
`width: 500px` 와 같은 고정 너비가 있거나 <br>
`width: 100vw` 와 padding 등이 조합되어 예상보다 커졌거나, <br>
Grid 아이템의 최소 크기가 너무 크거나, <br>
긴 텍스트가 줄바꿈되지 않는 등의 문제 발생

### 8. `clamp()` - 반응형 글자

```css
선택자 {
  font-size: clamp(최소값, 선호값, 최대값);
  font-size: clamp(32px, 5vw, 64px);
}
```

- 최소 32px, 화면 크기에 따라 5vw로 변화, 최대 64px
- 위 처럼 작성 시, `Media Query` 를 여러개 작성하지 않고도 글자 크기 변경 가능

### 9. `Media Query` 와 `clamp()` 차이

```css
@media (max-width: 768px) {
  선택자 {
    font-size: 32px;
  }
}

선택자 {
  font-size: clamp(32px, 5vw, 64px);
}
```

- `@media` : 특정 지점에서 디자인 변경
- `clamp()` : 화면 크기에 따라 자연스럽게 변화

### 10. 반응형 구현 순서

#### (1) 기본 구조

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
```

#### (2) Flex/Grid로 배치

```css
.products {
  display: grid;
}
```

#### (3) 자동으로 해결할 수 있는지 확인

```css
grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
```

#### (4) 구조가 달라져야 한다면

```css
@media (조건) {
}
```

#### (5) 모바일/태블릿/PC에서 테스트

작은 화면 -> 중간 화면 -> 큰 화면

#### (6) 깨지는 지점에서 Breakpoint 설정

```css
@media (min-width: ???px) {
}
```
