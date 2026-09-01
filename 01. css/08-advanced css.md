## Advanced CSS (1) - CSS Variable

### CSS 변수

반복해서 사용하는 값을 하나의 이름으로 저장하고 재사용하는 기능

```css
.button {
  background-color: #2563eb;
}

.link {
  color: #2563eb;
}

.badge {
  border-color: #2563eb;
}
```

```css
:root {
  --primary-color: #2563eb;
  --font-size: 16px;
  --border-radius: 8px;
}

.button {
  background-color: var(--primary-color);
}

.link {
  color: var(--primary-color);
}

.badge {
  border-color: var(--primary-color);
}
```

- 같은 색상 값을 여러 곳에서 사용 시, 추후 색상 변경할 때 여러 곳을 찾아서 수정해야한다.
- CSS 변수로 지정 할 경우 해당 변수 선언 값만 변경
- 변수 선언 방법: 이름 앞에 `--` 사용
- `--primary-color`, `--font-size`, `--border-radius`
- 전역적으로 사용할 변수는 `:root {}` 에 선언
- `:root {}` : 문서의 최상위 요소 (=`<html>`)
- `var()` : `:root {}` 에 선언한 변수를 가져와서 사용
- 변수명은 자유롭게 생성 가능하나, 의미가 드러나는 이름으로 사용
- 색상, 크기, 간격, 테두리 변경, 폰트 크기, 그림자 등등 모두 적용 가능
- CSS 변수는 특정 자료형 변수라기보다 CSS에서 사용할 값을 저장하는 Custom Property
- JS 에서 CSS 변수 변경 가능 -> 런타임에 JS에서 선언한 값으로 변경 됨
- Java 변수처럼 특정 계산 결과가 저장되는 것이 아니라,
- Custom Property 값으로 토큰을 저장해두고,
- `var()` 가 사용될 때 CSS 문맥에 대입 된다.

### 1. 변수 `상속(Inheritance)`

```css
.parent {
  --text-color: blue;
}

<div class="parent">
  <p>Hello</p>
</div>
```

- `<p>` 에는 `--text-color` 를 직접 선언하지 않고 사용 가능 (부모->자식)
- 이 특성으로 컴포넌트별 값을 재선언시 해당하는 컴포넌트만 별도 사용 가능

### 2. Theme (`Light Theme`, `Dark Theme`)

```css
:root { /* light theme */
  --background-color: white;
  --text-color: black;
}

.dark { /* dark theme */
  --background-color: #111827;
  --text-color: white;
}

body { /* dark theme */
  background-color: var(--background-color);
  color: var(--text-color);
}

<body class="dark"> /* html 연결 */
```

- 추후 `Design Tokens` 과 연계

### 3. `Fallback` - 첫 번째 값이 존재하지 않을 경우 두 번째 값 사용

```css
color: var(--text-color, black);
```

- `--text-color` 존재하면 그것을 사용하고, 없으면 black 사용

```css
color: var(--button-text-color, var(--text-color, black));
```

- `--button-text-color` 없으면 `--text-color` 없으면 `black` 처럼 다중 상속 가능

### 4. 컴포넌트에서 변수 활용

```css
.button { /* 기본값: blue/white) */
  background-color: var(--button-bg, blue);
  color: var(--button-text, white);
}

.button-danger {
  --button-bg: red;
}

<button class="button button-danger">
  Delete
</button>
```

- Button CSS 자체를 복제할 필요 없이 자체 확장해서 적용 가능

### 5. 변수 구조

```css
:root {
  /* Colors */
  --color-primary: #2563eb;
  --color-secondary: #7c3aed;
  --color-text: #111827;
  --color-background: #ffffff;
  --color-border: #e5e7eb;

  /* Spacing */
  --spacing-sm: 8px;
  --spacing-md: 16px;
  --spacing-lg: 24px;

  /* Radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;

  /* Typography */
  --font-size-sm: 14px;
  --font-size-md: 16px;
  --font-size-lg: 20px;
}

.card {
  padding: var(--spacing-md);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  background: var(--color-background);
  color: var(--color-text);
}
```

- `:root` 에 먼저 선언 후, 선택자에 가져와서 사용
