## 스타일링 Styling

### 1. 기본 Reset

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

- `*` : 모든 요소에 적용
- 브라우저마다 다른 기본 여백을 없애고 일정한 기준에서 작업하기 위해 사용

### 2. 폰트 색상 변경

#### 색상 이름으로 변경 - `color`

```css
선택자 {
  color: hotpink;
}
```

#### HEX 색상으로 변경

사용 빈도 가장 높음

```css
선택자 {
  color: #ff69b4;
}
```

#### RGB로 변경

```css
선택자 {
  color: rgb(255, 0, 0);
}
```

### 3. 배경색 변경 - `background-color`

```css
선택자 {
  background-color: hotpink;
}
```

### 4. 폰트 변경 - `font-family`

```css
선택자 {
  font-family: Arial, sans-serif;
}
```

### 5. 폰트 사이즈 변경 - `font-size`

```css
선택자 {
  font-size: 16px;
}
```

- 주로 제목 32-48px, 소제목 20-24px, 본문 16px 사용

### 6. 폰트 굵기 - `font-weight`

```css
선택자 {
  font-weight: bold;
}
```

- 400; : 일반
- 500; : 미디움
- 700; : 굵게

### 7. 글자 정렬 - `text-align`

```css
선택자 {
  text-align: left;
  text-align: center;
  text-align: right;
}
```

### 8. 가로, 세로 크기 - `width`, `height`

```css
선택자 {
  width: 200px;   // 가로
  height: 300px;  // 세로
}
```

### 9. 요소 바깥 여백 - `margin`

```css
선택자 {
  margin: 20px;   // 상하좌우 모두 적용
  margin-top: 20px;
  margin-right: 20px;
  margin-bottom: 20px;
  margin-left: 20px;

}
```

### 10. 요소 안쪽 여백 - `padding`

```css
선택자 {
  padding: 20px;
}
```

### 11. 테두리 - `border`

```css
선택자 {
  border: 1px solid black;  // 두께 스타일 색상
}
```

### 12. 요소 크기 계산 방식 - `Box-sizing`

요소의 크기 `width` , `height` 를 어떻게 계산할지 정하는 속성

```css
선택자 {
  box-sizing: content-box;  // 기본값
  box-sizing: border-box;   // 주로 사용
}
```

- 내부 `content` 기준으로 -> `padding` -> `border` -> `margin` 순

#### `content-box` 예시

`width` = `content` 만 포함

```css
.box {
    width: 300px;   // 300px
    padding: 20px;  // 20px + 20px
    border: 10px solid black;  // 10px + 10px
}
```

#### `border-box` 예시

`width` = `content` + `padding` + `border` 모두 포함

```css
.box {
    width: 300px;
    padding: 20px;
    border: 10px solid black;

    box-sizing: border-box;  // 총 300px (content + padding + border)
}
```
