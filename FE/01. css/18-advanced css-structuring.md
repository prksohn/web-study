## Advanced CSS (11) - Structuring

### CSS Structuring이란?

CSS를 체계적으로 정리하고 관리하는 것 <br>
아래와 같은 문제가 발생하므로 구조화해서 사용

- 이름 겹침
- 클래스가 어디에 쓰이는지 모름
- CSS가 서로 꼬임

### 1. BEM - 모든 태그들 중 하나의 태그에 구체적인 이름 규칙 생성

BEM: Block + Element + Modifier <br>
CSS 클래스 이름을 일정한 규칙으로 짓는 방법 <br>
Element를 계속 중첩해서 이름을 길게 만들지 않는다.

#### `Block` - 하나의 독립적인 UI 덩어리

독립적으로 의미가 있는 하나의 컴포넌트

```html
<nav class="navbar"></nav>

<div class="card"></div>
```

#### `Element` - Block 안에 속해 있는 구성 요소

BEM 에서 `__` underscore로 나타냄, 여러 태그 존재

```html
<div class="card">
  <h2 class="card__title">상품명</h2>
  <p class="card__description">상품 설명</p>
  <button class="card__button">구매</button>
</div>
```

```css
.card {
  border: 1px solid gray;
}

.card__title {
  font-size: 20px;
}

.card__description {
  color: gray;
}

.card__button {
  padding: 10px;
}
```

#### `Modifier` - 같은 컴포넌트인데 상태나 종류가 달라지는 경우

BEM 에서 `--` hyphen으로 나타냄, 같은 block의 다른 버전이나 변형을 나타낼 때

```html
<!-- 기본 버튼 -->
<button class="button">확인</button>
<!-- 주요 버튼 -->
<button class="button button--primary">제출</button>
<!-- 위험한 동작 나타내는 버튼 -->
<button class="button button--danger">삭제</button>
```

```css
.button {
  padding: 10px 20px;
}

.button--primary {
  background: blue;
  color: white;
}

.button--danger {
  background: red;
  color: white;
}
```

```html
<article class="card card--featured"></article>
```

```css
.card {
  /* 기본 스타일 --> */
  padding: 20px;
  border: 1px solid gray;
}

.card--featured {
  /* 추가/변형 스타일 */
  background-color: yellow;
}
```

- `card--featured` : 특별한 버전 / 보통 기본 Block인 card와 함께 사용하는 것이 좋음
- 이름 생성만 다르게 지정한 것뿐 위의 코드 모두 정의는 동일

### 2. Naming Convention - 이름을 짓는 전체적인 규칙

방식이 정해져 있진 않지만 프로젝트 전체에서 일관되게 사용해야 한다.

#### kebab-case - 사용빈도 가장 높음

```css
.user-profile {
}
.primary-button {
}
.card-title {
}
```

#### camelCase - 주로 js 변수명으로 사용

```css
.userProfile {
}
.primaryButton {
}
```

#### snake_case - 사용빈도 낮음

```css
.user_profile {
}
.primary_button {
}
```

### 3. Component CSS - 컴포넌트별로 나눠서 관리

```css
components/
├── Button/
│   ├── Button.jsx
│   └── Button.css
│
├── Card/
│   ├── Card.jsx
│   └── Card.css
│
└── Header/
    ├── Header.jsx
    └── Header.css
```

- react에서 위와 같이 컴포넌트 단위로 관리
- 컴포넌트와 관련 CSS를 가깝게 유지시켜 관리

### 4. Utility CSS - 작은 클래스를 조합해서 사용

작은 역할 하나만 하는 클래스 생성 후 조합하는 방식

```html
<div class="p-20 border rounded">내용</div>
```

```css
.p-20 {
  padding: 20px;
}

.border {
  border: 1px solid gray;
}

.rounded {
  border-radius: 10px;
}
```

- 이런 접근 방식의 대표적인 예: Tailwind CSS

### 5. CSS Modules - 클래스를 컴포넌트 단위로 격리

동일한 클래스 이름이 다른 컴포넌트와 충돌하지 않도록 CSS를 컴포넌트 단위로 격리하는 방식 <br>
BEM + Modules 같이 사용 가능

```react
  Button.module.css
```

```css
.button {
  background-color: blue;
}
```

```css
className={styles.button}  컴포넌트에서 사용
```

- 개념적으로는 `.button` 이 `.Button_button_x7a92` 와 같이 고유한 이름으로 변경 됨
- 실제로는 저 이름으로 변경되는 건 아니지만 다른 컴포넌트와 이름을 겹치지 않도록 처리한다고 생각하면 된다.
