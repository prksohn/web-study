## Advanced CSS (3) - Pseudo-element

### Pseudo-element - 의사 클래스

요소의 특정 부분을 선택하거나 가상의 내용을 추가 (특정 부분/가상 요소)

```css
선택자::pseudo-element {
  /* 적용할 스타일 */
}
```

### 1. `::before` - 요소 앞에 가상 요소 생성

요소의 내용 앞에 가상의 요소 생성

```css
선택자::before {
  content: '';
}
```

- `content` 속성이 거의 항상 필요, 맨 위에 생성

### 2. `::after` - 요소 뒤에 가상 요소 생성

요소의 내용 뒤에 가상의 요소 생성

```css
선택자::after {
  content: '';
}
```

- 단순히 글자 넣는 용도보다 장식용 요소를 만들 때 주로 사용
- `content: ''` -> 아무것도 입력되지 않았지만 CSS로 크기와 배경 등을 지정하면 장식용 요소로 사용 가능

### 3. `::first-letter` - 첫 번째 글자 선택

첫 번째 글자에만 스타일 적용 (기사에서 자주 쓰이는 Drop Cap 효과)

```css
선택자::first-letter {
  /* 적용할 스타일 */
}
```

### 4. `::first-line` - 첫 번째 줄 선택

```css
선택자::first-line {
  /* 적용할 스타일 */
}
```

- 화면 크기에 따라 첫 번째 줄에 들어가는 글자가 달라짐

### 5. `::placeholder` - placeholder 텍스트 선택

`input` 이나 `textarea` 의 `placeholder 텍스트` 선택 <br>
해당 placeholder에만 스타일 적용

```css
선택자::placeholder {
  /* 적용할 스타일 */
}
```

### 6. `::selection` - 드래그로 선택한 부분의 스타일링

#### 모든 텍스트 스타일링 적용

사용자가 마우스로 텍스트를 드래그해서 선택했을 때의 스타일링

```css
::selection {
  /* 적용할 스타일 */
}
```

#### 특정 요소에만 스타일링 적용

지정한 특정 요소 안에서 선택한 텍스트에만 드래그했을 경우 스타일링 적용

```css
선택자::selection {
  /* 적용할 스타일 */
}
```

### 7. `::marker ` - `<li>` 목록 기호(Bullet)/번호 선택

```css
li::marker {
  /* 적용할 스타일 */
}
```

- `<ul>` , `<ol>` 모두에서 사용 가능
