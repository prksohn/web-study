## Advanced CSS (10) - Object-fit (Image & Media)

### Object-fit이란?

이미지 카드, 프로필 이미지, 썸네일 만들 때 사용

### 1. `object-fit` - 박스 안에 이미지를 어떻게 넣을지

`<img>`, `<video>` 같은 대체 요소의 콘텐츠를 지정한 크기의 박스 안에 어떻게 맞출 것인지 결정

```css
img {
  width: 300px;
  height: 200px;
  object-fit: cover; /* 사용 빈도 높음 */
  object-fit: contain;
  object-fit: fill;
  object-fit: none;
}
```

- `width`, `height` : 이미지가 들어갈 박스 크기
- `object-fit` : 그 박스 안에 이미지를 어떻게 채울지

#### `object-fit: cover` - 박스 우선

- 이미지의 원래 비율 유지하면서 박스 빈틈없이 꽉 채운다.
- 단 이미지 비율과 박스 비율이 다르면 일부가 잘릴 수 있다.
- 이미지 일부가 잘려도 박스를 꽉 채우고 싶을 때 사용
- 카드 썸네일, 블로그 이미지, 상품 이미지, 프로필 이미지, 갤러리 등

#### `object-fit: contain` - 이미지 우선

- 이미지 전체가 보이도록 박스 안에 맞춘다.
- 원본 비율 유지, 이미지 잘리지 않지만,
- 이미지 비율과 박스 비율이 다르면 빈 공간 생김
- 로고, 상품 전체 이미지, 이미지가 절대 잘리면 안되는 경우 등

#### `object-fit: fill`

- 기본값으로, 이미지를 박스 크기에 강제로 맞춘다.
- 따라서 원본 비율 깨질 수 있음
- 일반적으로 이미지에서는 `cover`, `contain` 주로 사용

#### `object-fit: none`

- 이미지를 확대하거나 축소해서 박스에 맞추지 않고 원래 크기 그대로 유지
- 사용 빈도 낮음

### 2. `object-position` - 이미지를 어느 부분 중심으로 보여줄 지

`object-fit: cover` 사용 시 이미지가 잘릴 경우 : <br>
그때 어느 부분을 보여줄 지 정해주는 것

```css
img {
  width: 300px;
  height: 200px;
  object-position: center; /* default */
  object-position: top;
  object-position: bottom;
  object-position: left;
  object-position: right;
  object-position: 30% 20%;
}
```

- `center` : 기본, 가운데를 기준
- `top` : 위쪽 기준, 인물 사진에서 머리 부분 잘리면 안될 때 사용
- `bottom` : 아래쪽 기준
- `left`, `right` : 왼쪽, 오른쪽 기준
- `object-position: 가로% 세로%` : % 사용 가능, = X Y;

### 3. `object-fit` + `object-position` 활용

#### 인물 사진에서 머리 잘릴 때

```css
.profile img {
  width: 200px;
  height: 200px;
  object-fit: cover;
  object-position: top;
}
```

- `object-fit` : 이미지를 박스에 꽉 채움
- `object-position` : 그 중 위쪽 보여줌

### 4. `aspect-ratio` - 가로 : 세로 비율 설정 (박스 비율)

가로 : 세로 비율

```css
.thumbnail {
  width: 100%;
  aspect-ratio: 16 / 9;
}
```

- 썸네일을 만들 때, width가 바뀌어도 16:9 비율 유지하면서 높이가 자동으로 결정

### 5. `aspect-ratio` + `object-position` 활용

#### 카드 / 썸네일 이미지 생성

```css
.card img {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
}
```

- `width: 100%` : 부모 너비에 맞춘다
- `aspect-ratio: 16 / 9` : 가로세로 비율은 16:9로 만든다
- `object-fit: cover` : 그 16:9 박스 안에 이미지를 꽉 채운다

#### `width/height` 와 `aspect-ration` 차이

```css
/* (1) */
.box {
  width: 400px;
  height: 200px;
}

/* (2) */
.box {
  width: 400px;
  aspect-ratio: 2 / 1;
}
```

- (1) : 직접 정확한 사이즈 지정
- (2) : 높이를 비율에 맞춰 계산, 반응형에서 유용
