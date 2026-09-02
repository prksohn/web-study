## Advanced CSS (9) - Animation

### Animation이란?

사용자 행동을 기다리지 않고 움직임의 과정을 직접 정의

```css
@keyframes {
  /* 기본 문법 */
}

@keyframes move {
  from {
    transform: translateX(0);
  }

  to {
    transform: translateX(100px);
  }
}
```

- `@keyframes` : Animation이 어떻게 움직일지 정의, 중간 상태까지 자유롭게 지정 가능
- 선택자 : Animation을 어떻게 실행할지 작성
- `from` : 시작 상태
- `to` : 끝 상태
- `from`, `to` 대신 `%` 사용 가능
- 마우스 올렸을 때만 Animation 실행하고 싶다면 : `:hover` 랑 같이 사용 가능
- 페이지에 들어왔을 때 자동으로 Animation 시작되는 경우 : 기본 선택자에 선언

#### 실제 사용 코드

```html
<div class="box"></div>
```

```css
선택자 {
  animation: move 1s; /* 그 동작을 언제, 얼마나, 어떤 속도로, 몇 번 */
}

/* from - to 사용 */
/* 무슨 동작을 할 것인지 - 움직임의 내용 */
@keyframes move {
  from {
    transform: translateX(0);
  }

  to {
    transform: translateX(100px);
  }
}

/* % 사용 */
@keyframes move {
  0% {
    transform: translateX(0);
  }

  50% {
    transform: translateX(100px);
  }

  100% {
    transform: translateX(0);
  }
}
```

### 1. `animation-name` - 애니메이션 이름

```css
선택자 {
  animation-name: move; /* @keyframes move 의 이름 */
}


@keyframes move {
  ...
}
```

### 2. `animation-duration` - 실행 소요 시간

Animation이 한 번 실행되는 데 걸리는 시간

```css
선택자 {
  animation-duration: 2s;
}
```

- 한 번의 animation이 2초동안 진행

### 3. `animation-delay` - 시작 전 기다리는 시간

Animation을 시작하기 전에 기다리는 시간

```css
선택자 {
  animation-delay: 1s;
}
```

- 1초 대기 후 Animation 시작

### 4. `animation-timing-function` - 속도 변화 방식

Animation 속도 변화 방식

```css
선택자 {
  animation-timing-function: linear;
  animation-timing-function: ease;
  animation-timing-function: ease-in;
  animation-timing-function: ease-out;
}
```

- `linear` : 일정한 속도
- `ease` : 자연스럽게
- `ease-in` : 느리게 시작
- `ease-out` : 느리게 끝남

### 5. `animation-iteration-count` - 반복 횟수

Animation 반복 횟수

```css
선택자 {
  animation-iteration-count: 1;
  animation-iteration-count: infinite;
}
```

- `infinite` : 무한 반복 - 로딩 아이콘에서 사용

### 6. `animation-direction` - 반복 방향

반복할 때 어느 방향으로 움직일 것인지

```css
선택자 {
  animation-direction: normal;
  animation-direction: reverse;
  animation-direction: alternate;
  animation-direction: alternate-reverse;
}
```

- `normal` : 0% -> 100% 방향으로 진행
- `reverse` : 100% -> 0% 방향으로 진행
- `alternate` : 0% -> 100% -> 100% -> 0% -> 0% -> 100% 처럼 번갈아 왔다 갔다 하는 효과 만들 때
- `alternate-reverse` : 100% -> 0% -> 0% -> 100% -> 100% -> 0% 로 반대로 시작

### 7. `animation-fill-mod` - 시작 전, 끝난 후 어떤 상태 유지할 건지

Animation 시작하기 전이나 끝난 후에 어떤 상태를 유지할지 결정

```css
선택자 {
  animation-fill-mod: none;
  animation-fill-mod: forwards;
  animation-fill-mod: backwards;
  animation-fill-mod: both;
}
```

#### `none` - Animation이 끝나면 원래 상태로 되돌아감

```css
선택자 {
  animation: move 1s;
}
```

#### `forwards` - Animation이 끝나면 마지막 상태 유지

```css
선택자 {
  animation: move 1s forwards;
}
```

#### `backwards` - 기다리는 동안 keyframes 시작 상태 유지

`animation-delay` 가 있을 때, Animation 시작 전 기다리는 동안 keyframes 시작 상태 유지

```css
선택자 {
  animation: move 1s 2s backwards;
}
```

#### `both` - `forwards` + `backwards`

`animation-delay` 가 있을 때, Animation 시작 전 기다리는 동안 keyframes 시작 상태 유지

```css
선택자 {
  animation-fill-mode: both;
}
```

- Animation 시작 전 : `backwards`
- Animation 시작 후 : `forwards`

### 6. Animation Shorthand (축약형)

```css
선택자 {
  animation: move 2s ease 1s infinite;
  animation: Animation이름 실행시간 속도 변화방식 웨이팅시간 반복;

  animation: move 2s ease 1s infinite alternate forwards; /* animation-direction, fill-mode 추가 */
}
```

- `animation: move 2s ease;` 이 정도만 자유롭게 적을 수 있어도 괜찮음

### 자주 사용하는 패턴

#### 계속 회전하는 아이콘

```css
@keyframes spin {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

.loading {
  animation: spin 1s linear infinite;
}
```

- spin : 회전
- 1s : 한 바퀴에 1초
- linear : 일정한 속도
- infinite : 무한 반복

#### 위아래로 움직이는 Animation

```css
@keyframes float {
  0% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-10px);
  }

  100% {
    transform: translateY(0);
  }
}

.box {
  animation: float 2s ease-in-out infinite;
}
```

- 원래 -> 위로 10px -> 원래 -> 위로 10px -> 무한 반복

```css
@keyframes float {
  from {
    transform: translateY(0);
  }

  to {
    transform: translateY(-10px);
  }
}

.box {
  animation: float 2s ease-in-out infinite alternate;
}
```

- `animation-direction: alternate` 로 더 간단히 만들기 가능
- 0% -> 10px -> 0% -> 10px -> 자동 무한 반복
