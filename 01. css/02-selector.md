## 선택자 Selector

### Selector란?

어떤 HTML 요소에 CSS를 적용할지 선택하는 문법

```css
선택자 {
  속성: 값;
}
```

### 1. `Tag Selector` - 태그 이름으로 선택

```html
<p>내용</p>
```

```css
p {
  color: blue;
}
```

- 모든 `p` 태그에 적용

### 2. `Class Selector` - Class 이름으로 선택

- `.class명`
- 여러 요소에서 사용 가능
- 사용 빈도 가장 높음

```html
<p class="text">내용</p>
```

```css
.text {
  color: hotpink;
}
```

- `.class명` : HTML의 `class="class명"` 으로 선언
- 여러 요소에 동일한 class명 사용 시, 해당 class명을 가진 요소들 모두 적용
  <br>

```html
<button class="class명1 class명2">버튼</button>
```

```css
.class명1 {
  padding: 10px;
}

.class명2 {
  background-color: hotpink;
}
```

- `class="class명1 class명2"` 와 같이 여러 개의 `class` 도 가능

### 3. `ID Selector` - 고유한 식별자

- `#id명`
- 한 페이지에 하나만 사용 가능
- 특정 요소 식별

```html
<p id="id명">내용</p>
```

```css
#p {
  color: blue;
}
```

### 4. `Group Selector` - 여러 요소 한번에 선택

요소 사이에 `,` 로 구분

```css
h1,
p,
button {
  color: green;
}
```

### 5. `Descendant Selector` - 후손 선택자

공백 사용

```html
<header>
  <h1>내용</h1>
</header>
```

```css
header h1 {
  color: red;
}
```

- `header` 안에 있는 모든 `h1` 선택 가능

### 6. `Child Selector` - 자식 선택자

직계 자식만 선택 가능

```html
<nav>
  <a>내용</a>
</nav>
```

```css
nav > a {
  color: black;
}
```

- `nav' 의 직계 자식 `a` 만 선택 가능

### 선택자 사용 가능 범위

- `head` : 선택자 사용 불가
- `header`, `main`, `footer`, `body` : 모두 선택자 사용 가능
- 보통 `body` 만 태그 선택자를 사용하고, 그 외에는 클래스 선택자 로 사용

#### 태그 선택자

모두 태그 이름으로 바로 선택 가능

```css
body {
  background-color: #f5f5f5;
}

header {
  background-color: hotpink;
}

main {
  padding: 20px;
}

footer {
  text-align: center;
}
```

#### Class 선택자

사용 빈도 가장 높음

```css
.header {
  background-color: hotpink;
}

.main {
  padding: 20px;
}

.footer {
  text-align: center;
}
```

#### ID 선택자

가능하지만 자주 사용하지 않음

```css
#header {
  background-color: hotpink;
}

#main {
  padding: 20px;
}

#footer {
  text-align: center;
}
```
