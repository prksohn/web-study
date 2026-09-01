## Advanced CSS (7) - Transform

### Transform이란? - 원래 자리에서 시각적으로 변형

요소를 원래 배치된 자리에서 시각적으로 변형시키는 속성

```css
transform: translate();
transform: translateX()
transform: translateY()
transform: scale();
transform: rotate();
transform-origin;
```

### 1. `translate()` - x, y 동시에 이동

x, y 동시에 이동시키는 함수

```css
transform: translate(20px, -10px);
```

- x, y 각각 한 방향만 이동 시키는 함수 사용 빈도가 더 높음

### 2. `translateX()` - x축으로 이동 / 이동 거리

요소를 X축으로 이동

```css
선택자:hover {
  transform: translateX(5px);
}
```

- 선택자에 마우스를 올렸을 때 요소가 살짝 오른쪽으로 움직이는 효과

### 3. `translateY()` - y축으로 이동 / 이동 거리

요소를 Y축으로 이동

```css
선택자:hover {
  transform: translateY(-5px);
}
```

### 4. `scale()` - 배율

크기 확대/축소

```css
선택자:hover {
  transform: scale(0.5);
  transform: scale(1);
  transform: scale(1.05);
  transform: scale(1.1);
}
```

- `scale(0.5)` : 원래 크기의 50%
- `scale(1)` : 원래 크기 100%
- `scale(1.05)` : 원래 크기의 105%
- `scale(1.1)` : 원래 크기의 110% / 버튼, 카드, 이미지 hover 효과에서 주로 사용

### 5. `rotate()` - 각도

아코디언, 드롭다운의 화살표 회전시키는 등의 UI 아이콘 상태 변경

```css
.arrow {
  transform: rotate(0deg); /* 닫힘 */
}

.open .arrow {
  transform: rotate(180deg); /* 열림 */
}
```

- `deg` : degree(도) 약자

### 6. `transform-origin` - 변형 기준

어디를 기준으로 변경할 것인지 지정

```css
선택자 {
  transform-origin: left center;
  transform: rotate(45deg);
}
```

### 6. 여러 transform 함수 조합

Transform 함수 여러 개를 조합하여 적용 가능

```css
선택자 {
  transform: translateY(-5px) scale(1.02);
}
```

- Y축 방향으로 -5px : 위로 5px
- 원래 크기의 102% = 즉 2% 확대
- 여러 개를 조합하여 한번에 적용
- 사용자 입장: 카드가 살짝 떠오르면서 커지는 효과
- transform 을 두 번 선언 시, 동시에 적용 X
- 두 번째가 첫 번째를 덮어쓰기 때문
- 여러 개 사용 시 한 개의 transform에 사용
