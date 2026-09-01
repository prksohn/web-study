## CSS Basic

### CSS란?

Cascading Style Sheets, HTML의 디자인을 담당하는 언어

### 외부 CSS

HTML과 CSS를 별도의 파일로 분리하는 방식 <br>
별도의 `style.css` 파일 생성

### HTML과 CSS 연결

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <title>제목</title>

    <link rel="stylesheet" href="폴더명/style.css" />
  </head>
</html>
```

- `rel="stylesheet"` : 이 파일은 스타일 시트라고 브라우저에게 알려주는 역할
- `style.css` : CSS 파일 위치
- 파일 경로 : `index.html` 기준
- 지정 경로 파일명과 실제 파일명과 동일 해야함

### 기본 문법

```css
선택자 {
  속성: 값;
}
```

- `선택자 Selector` : 스타일을 적용할 요소
- `속성 Property` : 무엇을 변경할 것인지
- `값 Value` : 속성에 들어가는 실제 값
- `중괄호 { }` : 동작, 실행
- `세미콜론 ;` : 속성 종료
- `콜론 :` : 속성과 값을 연결
- `/* */` : 주석
- 여러 선택자가 존재 할 경우 위 -> 아래순으로 동작한다.
- 같은 선택자의 경우, 마지막에 선언된 것이 적용

### 작성 순서

```css
width

height

margin

padding

background

font

display

position
```
