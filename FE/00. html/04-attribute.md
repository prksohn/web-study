## 속성 Attribute

태그에 추가적인 정보를 제공할 때

```html
<태그 속성="속성값">내용</태그>
```

### 1. `class` - 요소 그룹으로 묶기

이름을 붙여 그룹화할 때, (.class명)

```html
<p class="text">내용</p>
```

- `"text"` : `class` 이름
- 여러 요소에 같은 `class` 를 사용해 그룹 생성 가능
- css에서 사용 빈도 높음 -> `class` 를 이용해 스타일 적용
- js에서도 사용

```html
<p class="text">첫 번째 내용</p>
<p class="text">두 번째 내용</p>
<p class="text">세 번째 내용</p>
```

### 2. `id` - 요소 식별

고유한 식별자를 부여할 때, (#id명)

```html
<h1 id="main-title">제목</h1>
```

- 하나의 문서에서 특정 요소 구분하기 위한 고유한 이름으로 사용
- css, js에서도 사용

### 3. `href` - 링크 주소

링크가 이동할 주소를 지정, `a` 와 함께 사용

```html
<a href="https://...">내용</a>
```

### 4. `src` - 파일 위치

파일 위치 지정할 때, `img` 와 함께 사용

```html
<img src="폴더명/파일명.jpg" alt="대체 텍스트" />
```

### 5. `alt` - 이미지 설명

`img` 에서 사용하는 이미지 대체 텍스트

```html
<img src="폴더명/파일명.jpg" alt="대체 텍스트" />
```

- 이미지가 정상적으로 표시되지 않거나, 화면을 직접 보지 못하는 사용자가 웹 페이지를 이용할 때를 대비

### 6. `name` - form 데이터의 이름

form 데이터를 식별하는 이름

```html
<input type="text" name="username" />
```

- 사용자가 입력한 데이터를 서버에 전달할 때 어떤 이름으로 전달할지 구분하기 위해
- `username` : 사용자가 입력한 이름

### 7. `value` - 값

form 데이터의 값 <br>

`input`, `button` 등의 폼 요소에서 자주 사용

```html
<input type="text" name="username" value="홍길동" />
```

- 홍길동 -> `input` 의 기본값
