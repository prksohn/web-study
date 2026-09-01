## Advanced CSS (8) - Transition

### Transition이란? - 자연스럽게 보이게 해주는 효과

CSS 속성이 바뀔 때 그 변화를 일정 시간 동안 부드럽게 만들어주는 것

```css
.button {
  background-color: black;
  transition: background-color 0.3s ease;
}

.button:hover {
  background-color: gray;
}
```

- 해당 요소를 마우스를 올리면 기존 색상 -> 천천히 변화 -> gray로 변경
- 직접적인 변화를 주는 것 `:hover`
- 그 변화가 부드럽게 일어나도록 해주는 것 : `transition`

### 1. `transition-property` - 어떤 속성을 변화

어떤 속성을 부드럽게 변화시킬 것인지 지정

```css
선택자 {
  transition-property: background-color;
  transition-property: transform, background-color;
  transition-property: all;
}
```

- background-color의 변화에 transition 적용
- 여러 개 동시에 선언 가능
- `all` : 변화 가능한 여러 속성에 모두 적용
- `all` 보다 필요한 속성을 정확하게 명시하는 것이 좋음

### 2. `transition-duration` - 얼마나 걸리는지

변화하는 데 얼마나 걸릴 것인지 지정

```css
선택자 {
  transition-duration: 0.3s;
}
```

- 1s = 1000ms
- 0.5s = 500ms
- 0.3s = 300ms
- 0.1s = 100ms

### 3. `transition-timing-function` - 변화 속도 어떻게 진행

변화 속도가 시간에 따라 어떻게 진행 될 것인지 지정

```css
선택자 {
  transition-timing-function: linear;
  transition-timing-function: ease;
  transition-timing-function: ease-in;
  transition-timing-function: ease-out;
  transition-timing-function: ease-in-out;
}
```

- `linear` : 처음부터 끝까지 일정한 속도로 변화
- `ease` : 처음과 끝 부분의 속도가 자연스럽게 변화 / 주로 사용
- `ease-in` : 처음에는 느리고 점점 빨라지는 형태
- `ease-out` : 처음에는 빠르고 끝에서 느려지는 형태 / 꽤 사용
- `ease-in-out` : 시작과 끝이 느리고 가운데가 상대적으로 빠른 형태

### 4. `transition-delay` - 변화 시작 전 웨이팅 시간

변화 시작 하기 전에 얼마나 기다릴 것인지 지정

```css
선택자 {
  transition-delay: 1s;
}
```

- 상태가 바뀐 후 1초 기다렸다가 transition 시작

### Transition Shorthand (축약형)

```css
선택자 {
  transition-property: transform;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;

  transition: 어떤 속성 얼마동안 어떤 속도로;
  transition: property duration timing-function delay;
  transition:
    transform 0.3s ease,
    background-color 0.3s ease;
}
```

- transform을 0.3초 동안 ease 방식으로 0초 기다렸다가 변화 시켜라는 의미
- 따로 작성하지 않고 주로 축약형으로 사용
- 보통은 delay 지정하지 않고 생략
- transition은 :hover 등의 클래스가 아닌 기본 상태에 작성
- 여러 속성에도 적용 가능
- width으로 transition 가능하지만, 어떤 속성들은 애니메이션처럼 중간 값을 계산하기 어려워 적합하지 않음
- transform, opacity를 부드러운 UI 움직임에 주로 사용
- transition : hover 효과 등 상태 변화 반응
- animation : 여러 단계를 자동으로 움직임 - 추후 Animation에서 자세히

### 자주 사용하는 패턴

#### 카드가 위로 올라오기

```css
.card {
  transition: transform 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
}
```

#### 버튼 살짝 커지기

```css
.button {
  transition: transform 0.2s ease;
}

.button:hover {
  transform: scale(1.05);
}
```

#### `opacity` 란?

요소의 투명도 조절

```css
.button {
  opacity: 1;
  transition: opacity 0.2s ease;
}

.button:hover {
  opacity: 1; /* = 100% 불투명 */
  opacity: 0.75; /* 75% 보임 */
  opacity: 0.5; /* 50% 보임 */
  opacity: 0.25; /* 25% 보임 */
  opacity: 0; /* 0% 완전히 투명 */
}
```

- hover 했을 때 1.0 -> 0.9 -> 0.8 -> 0.7 -> 0.6 -> 0.5 처럼 서서히 투명해짐
- transition이 없다면 마우스 올리는 순간 바로 0.5로 변형
- 따라서 보통 `transform` + `opacity` 같이 사용
- `opacity: 0` : 안 보일 뿐 요소 자체는 존재
- `display: none` : 요소가 화면 레이아웃에서 사라짐
- opacity -> 페이드 인/아웃 같은 시각적 효과에 유용
