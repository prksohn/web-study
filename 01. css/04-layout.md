## 레이아웃 Layout (Flexbox)

### display란?

HTML 요소를 화면에 어떻게 배치할지 결정하는 속성

```css
선택자 {
  display: block;

  display: inline;

  display: inline-block;

  display: flex;

  display: none;
}
```

### 1. Block - 한 줄 전체

한 줄 전체를 차지하는 요소, 세로로 이어짐

대표적인 태그

```css
선택자 {
  div
  header
  main
  section
  article
  footer
  p
  h1 - h6
}
```

### 2. Inline - 내용만큼의 공간

내용만큼만 공간 차지, 가로로 이어짐 <br>
`width` `height` 사용 제한적

대표적인 태그

```css
선택자 {
  span
  a
  strong
  em
}
```

### 3. Inline-block - 가로 배치, 크기 지정

가로로 한 줄에 배치되면서 `block` 처럼 크기 조절 가능

```css
선택자 {
  display: inline-block;
}
```

- `display: block` + `display: inline` 특징이 합쳐진 것
- 작은 버튼이나 메뉴를 옆으로 배치하면서 각각 크기를 지정하고 싶을 때 사용
- 요즘은 여러 요소 정렬할 때 `inline-block` 보다 `flex` 사용 빈도 높음

### 4. None - 숨김

화면에 보이지도 않고 공간도 차지 하지 않음

```css
선택자 {
  display: none;
}
```

- 원래는 존재하지만 특정 상황에서 숨겨야할 때 사용
- 모바일에서 메뉴바 버튼 클릭 시 상세 메뉴 나타나게 할 때 (`display: block`)
- `display: none;` : 화면에 안보이고 자리도 삭제
- `visibility: hidden;` : 화면에 안보이지만 자리 유지

### 5. Flex - 가로, 세로 배치 레이아웃

자식 요소를 `가로`, `세로` 로 배치하는 레이아웃 방식

- `display: flex` : Flexbox 시작 선언
- `display: flex` : 부모 요소 (Flex container), 항상 부모 요소에 적용
- `justify-content`, `align-items` : 자식 요소 (Flex item)
- `justify-content`, `align-items` 를 사용하려면 `display: flex` 선언 필수
- `display: flex` 는 `flex-direction: row` 가 생략된 것 (별도 선언 불필요)

```html
// 부모 요소 (Flex container)
<div class="container">
  // 자식 요소 (Flex item)
  <div>1</div>
  <div>2</div>
  <div>3</div>
</div>
```

```css
.container {
  display: flex; // 출력 -> 1 2 3
}
```

### 6. justify-content - 주측 방향 정렬

`주축 (Main Axis)` 방향으로 정렬

```css
선택자 {
  justify-content: flex-start;  // 가로 방향 좌측 정렬 (기본값)
  justify-content: center;  // 가로 방향 중앙 정렬
  justify-content: flex-end;  // 가로 방향 우측 정렬
  justify-content: space-between;  // 양끝 정렬 기준으로 사이 여백
  justify-content: space-around;  // 양끝 정렬 기준으로 사이 여백, 양쪽 여백 포함
  justify-content: space-evenly;  // 모든 간격 동일
}
```

- `display: flex;` 일 때 : 가로 정렬
- `display: column;` 일 때 : 세로 정렬

### 7. align-items - 교차축 방향 정렬

`교차축 (Cross Axis)` 방향으로 정렬

```css
선택자 {
  align-items: center;  // 세로 방향 중앙 정렬 (기본값)
  align-items: flex-start;  // 세로 방향 상단 정렬
  align-items: flex-end;  // 세로 방향 하단 정렬
}
```

- `display: flex;` 일 때 : 세로 정렬
- `display: column;` 일 때 : 가로 정렬

### 8. gap - items 사이 간격

자식 요소 사이 간격을 줄 때, `margin` 보다 `gap` 사용 <br>
더 간단하고 유지보수 용이

```css
선택자 {
  display: flex; // Flexbox에 간격을 주기 위해 필요
  gap: 20px;
}
```

### 9. flex-direction - 배치 방향

자식 요소 배치 방향 지정

#### row - 주축 가로 (기본값)

생략 가능

```css
선택자 {
  display: flex;  // 이미 안에 포함되어 있기 때문에,
  flex-direction: row;  // 생략 가능
  justify-content: flex-start; // 가로 방향 좌측 정렬
  align-items: center;  // 세로 방향 중앙 정렬
}
```

#### column - 주축 세로

```css
선택자 {
  display: flex;  // 먼저 선언 필수
  flex-direction: column;  // 단독 사용 불가
  justify-content: flex-start;  // 세로 방향 상단 정렬
  align-items: center;  // 가로 방향 중앙 정렬
}
```

- 메뉴를 세로로 정렬하고 싶을 때 사용 가능
