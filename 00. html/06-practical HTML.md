## 실무 Practical HTML

### 1. Semantic HTML

의미가 더 명확한 HTML

(1)

```html
<div>
  <h1>제목</h1>
</div>
```

(2)

```html
<header>
  <h1>제목</h1>
</header>
```

- (1) 보다 (2)의 구조가 의미를 더 명확하게 표현
- `div` 를 무조건 사용하지 않고, 의미에 맞는 태그를 사용한다.

### 2. 웹 접근성

- 의미가 없는 `img` 의 `alt` 는 생략 가능
- `button` : 동작 실행
- `a` : 페이지 이동
- `name` : 서버에 데이터 전달할 때 데이터 구분하는 이름
- 사용자 입력 -> 아이디: hong123, 서버 데이터 -> username = hong123

### 3. `required` - form 사용자 입력 필수

사용자가 값을 입력하지 않으면 다음으로 이동할 수 없도록 할 때

```html
<form>
  <label for="email">이메일</label>
  <input type="email" id="email" name="email" required />

  <button type="submit">제출</button>
</form>
```

### 4. SEO 기본 - 검색 엔진 최적화 (Search Engine Optimization)

검색 엔진이 웹 페이지의 내용을 잘 이해하고 검색 결과에 적절하게 보여줄 수 있도록 만드는 것

- `title` : 페이지의 제목을 명확하게 작성
- `h1`-`h6` : 제목으로 콘텐츠의 계층 구조 표현

### 5. HTML 작성 팁

- 이 콘텐츠 의미가 무엇인가?
  : 페이지의 머리말인가? 메뉴인가?
- 그 의미에 맞는 HTML 태그 선택
  : `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`
- 필요한 속성 추가
  : `class`, `id`, `href`, `src`, `alt`, `name`, `value`
- 사용자에게 제대로 사용할 수 있는 구조인지 확인
  : `label`, `alt`, `button`, `a`, `heading`
- css 와 js 연결
  : 디자인 + 동작
