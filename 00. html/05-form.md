## 폼 Form

### Form이란?

사용자가 웹사이트에 정보를 입력하고 제출할 수 있도록 만드는 구조

- 로그인
- 회원가입
- 검색
- 게시글 작성
- 댓글 작성
- 상품 주문
- 문의하기 등

### 1. `<form>` - 입력 영역

사용자가 입력하는 데이터를 하나의 폼으로 묶어 제출하는 영역 <br>
1개의 `form ` 만 사용 가능 (= `form ` 안에 `form ` 불가)

```html
<form>
  <!-- 입력 요소 -->
</form>
```

- `<label>`, `<input>`, `<textarea>`, `<select>`, `<option>`, `<button>` 사용 시 <br>
  상단에 `<form>` 선언 필수, 없을 경우 서버로 데이터 전송 불가

### 2. `<label>` - 입력 요소의 이름

입력 요소가 무엇을 입력하는 곳인지 설명하는 텍스트

```html
<label for="username">아이디</label>

<input type="text" id="username" />
```

- `label` 과 `input` 연결이 중요
- 예시 코드처럼 `for` 와 `id`가 서로 연결되서,
- 사용자가 아이디라는 `label` 클릭 시 해당 `input` 을 선택 가능

### 3. `<input>` - 입력

한 줄 입력, 사용자가 값을 입력하거나 선택할 수 있는 입력 요소 <br>
type에 따라 다른 역할 부여

#### 일반 텍스트

```html
<input type="text" />
```

#### 이메일

```html
<input type="email" />
```

#### 비밀번호

```html
<input type="password" />
```

#### 숫자

```html
<input type="number" />
```

#### 체크박스

```html
<input type="checkbox" />
```

#### 라디오 버튼

```html
<input type="radio" />
```

### 4. `<textarea>` - 여러 줄 입력

여러 줄의 텍스트를 입력할 때, 게시글이나 문의 내용을 작성할 때 사용

```html
<label for="message">문의 내용</label>

<textarea id="message"></textarea>
```

- 자기소개, 문의 내용, 게시글 등

### 5. `<select>` - 선택 목록

여러 선택지 중에서 하나 또는 여러 개를 선택할 수 있는 목록 <br>
사용자가 목록을 열어서 선택 한다.

```html
<select>
  <option>선택1</option>
  <option>선택2</option>
  <option>선택3</option>
  <option>선택4</option>
</select>
```

### 6. `<option>` - 선택 항목

`select` 안에 각각의 선택지

```html
<select>
  <option>선택1</option>
  <option>선택2</option>
  <option>선택3</option>
  <option>선택4</option>
</select>
```

### 7. `<button>` - 버튼

사용자가 클릭해서 어떤 동작을 실행하도록 만들 때

```html
<form>
  <input type="text" />
  <button type="submit">제출</button>
</form>
```

- `input` : 사용자가 입력
- `button` : form 제출

### 버튼의 타입

`button` 의 `type` 지정 가능 <br>
`type="button"` 과 `type="submit"` 구분 중요

#### button - 일반 버튼

```html
<button type="button">클릭</button>
```

#### submit - 폼 제출

```html
<button type="submit">로그인</button>
```

#### reset - 폼 입력값 초기화

```html
<button type="reset">초기화</button>
```

### 8. form과 속성의 연결

#### `label` + `input` 연결

```html
<label for="username">아이디</label>

<input type="text" id="username" name="username" value="lee" />
```

- `id` : `label의 for` 와 연결하기 위한 식별자
- `name` : form 데이터 구분하는 이름
- `value` : 입력 요소 값 (생략 가능)
- `label의 for` = `input의 id` 해야함

#### `select` + `option` + `value` 연결

```html
<select name="city">
  <option value="seoul">서울</option>
  <option value="busan">부산</option>
  <option value="daegu">대구</option>
</select>
```

- 대구 : 사용자에게 보여주는 텍스트
- `"daegu"` : 실제 값
- 서울 선택 시 `name = city value = daegu` 형태로 데이터 구분
