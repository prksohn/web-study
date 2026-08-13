## Grid

### Grid란?

웹페이지를 가로 x 세로의 격자 형태로 배치하는 속성

```css
부모 요소 {
  display: grid;
}
```

- `display: grid` : 부모 요소에 선언 (=`Grid Container`)
- `Grid Items` : 자식 요소

### 1. `grid-template-columns` - 가로 칸 개수

가로 칸(열)을 몇 개 만들지 정하는 속성

```css
부모 요소 {
  display: grid;

  grid-template-columns: 1fr 1fr 1fr;
  grid-template-columns: 1fr 2fr;
}
```

### 2. `grid-template-rows` - 세로 줄 개수

세로 줄(행)을 몇 개 만들지 정하는 속성

```css
부모 요소 {
  display: grid;

  grid-template-rows: 100px 200px;
}
```

- `100px 200px` : 첫번째 행은 100px, 두번째 행은 200px
- 보통은 굳이 지정하지 않고, `grid-template-columns` 만 지정

### 3. `gap` - 칸 사이 간격

칸 사이 간격

```css
부모 요소 {
  display: grid;

  grid-template-columns: 1fr 1fr 1fr;

  gap: 20px;
  column-gap: 20px;
  row-gap: 10px;
}
```

- `gap` : 기본값으로 행/열 모두 적용
- `column-gap` : 가로(열)만 간격 별도 적용
- `row-gap` : 세로(행)만 간격 별도 적용

### 4. `repeat()` - 칸 사이 간격 단축어

칸 사이 간격을 줄여서 쓰는 단축어

```css
부모 요소 {
  display: grid;

  grid-template-columns: 1fr 1fr 1fr;
  grid-template-columns: repeat(3, 1fr);
  grid-template-columns: repeat(원하는 칸의 횟수, 칸의 크기);
}
```

- `repeat(3, 1fr)` : `1fr` 을 3번 반복해라

### 5. `minmax()` - 최소 크기와 최대 크기 지정

최소값과, 최대값 지정

```css
부모 요소 {
  display: grid;

  grid-template-columns: minmax(최소값, 최대값);
  grid-template-columns: minmax(200px, 1fr);
  grid-template-columns: repeat(3, minmax(200px, 1fr));
}
```

- "열은 최소 200px은 유지하고, 공간이 남으면 1fr까지 늘어나게" 하라는 의미
- `repeat(열의 개수, minmax(최소값, 최대값));` 합쳐서 사용 가능
- : 3개의 열 + 각 열은 최소 200px + 공간이 남으면 1fr까지 늘어난다.
- 이때 화면이 너무 좁아지면 3개의 열을 억지로 유지하려 하기 때문에, 화면에 안 들어갈 수 있음
- 이럴 때 `auto-fit` 사용

### 6. `auto-fit` - 반응형 Grid

화면 크기에 따라 크기 자동 지정, 반응형 Grid

```css
부모 요소 {
  display: grid;

  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```

- "200px짜리 카드가 들어갈 수 있는 만큼 열을 자동으로 생성" 하라는 의미
- 화며 크기에 따라 자동으로 크기 변경
- 상품 목록, 이미지 갤러리, 카드 리스트 같은 레이아웃 만들 떄 사용

### 7. `grid-column`, `grid-row`- 특정 카드의 크기 별도 지정

여러 카드 목록 중에 특정 카드의 크기만 별도 지정해줄 때, `큰 메인 카드 + 작은 카드` 등

```css
부모 요소 {
  display: grid;

  grid-template-columns: repeat(3, minmax(200px, 1fr));
}

부모 요소:first-child {
  grid-column: span 원하는 칸의 개수;
  grid-column: 시작 선 / 종료 선;
  grid-row: span 원하는 칸의 개수;
}
```

- `grid-column` : 기본적으로 한 칸 차지 (가로 방향)
- 첫 번째 카드를 가로로 여러칸을 차지할 때 사용
- `span 원하는 칸 개수` : 현재 위치에서 원하는 개수의 열 차지

- `grid-column: 1 /3` : 칸 번호가 아닌 선의 번호 (즉 선의 번호-칸 번호와 동일)

- `grid-row` : 기본적으로 한 줄 차지 (세로 방향)
- 첫 번째 카드를 세로로 여러칸을 차지할 때 사용

- 주의 ! 반응형에서는 화면이 좁아졌을 때 문제가 생기는데,
- 이때 큰 화면에서는 여러 칸 차지하게 하고,
- 작은 화면에서는 다시 1칸으로 돌리는 방식을 사용
- 이러한 문제점을 `Responsive Design + Media Query` 로 보완
