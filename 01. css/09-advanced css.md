## Advanced CSS (2) - Pseudo-class

### Pseudo-class - 의사 클래스

요소의 특정 상태나 조건을 선택하는 방법

### 1. 사용자 상호작용

#### `:hover`

마우스 포인터가 요소 위에 올라갔을 때 적용

```css
.선택자:hover {
  /* 적용할 스타일 */
}
```

- transition과 함께 자주 사용

#### `:active`

요소를 실제로 누르고 있는 상태에 적용

```css
.선택자:active {
  /* 적용할 스타일 */
}
```

#### `:focus`

요소가 focus 된 상태에 적용, 마우스 사용

```css
.선택자:focus {
  /* 적용할 스타일 */
}
```

- `<input>`, `<button>`, `<select>` 같은 폼 요소에 주로 사용
- 마우스 클릭 뿐만 아니라, `tab 키` 를 이용해서 요소를 이동해도 focus 발생
- 접근성에서 매우 중요한 개념

#### `:focus-visible`

사용자에게 Focus 표시가 필요한 상황에 적용, tab 사용

```css
.선택자:focus {
  /* 적용할 스타일 */
}
```

- `:focus` : 요소를 마우스로 클릭 했을 때도 포커스 스타일이 나타날 수 있음
- `:focus-visible` : 브라우저가 사용자에게 포커스 표시가 필요하다고 판단하는 경우에만 표시
- 특히 키보드 사용자에게 포커스를 명확하게 보여주는 데 유용

#### `:focus-within`

자기 자신 또는 자신의 자식 요소 중 하나가 focus 상태에 적용

```html
<div class="form-group">
  <label>이름</label>
  <input type="text" />
</div>
```

```css
.form-group {
  padding: 10px;
  border: 1px solid gray;
}

.form-group:focus-within {
  border: 2px solid blue;
}
```

- `input` 을 클릭해서 Focus가 되면, 부모인 `.form-group` 에 `focus-within` 이 적용
- `input` 주변 전체를 강조 가능

### 2. Form 상태

#### `:checked`

Checkbox나 Radio가 선택된 상태에 적용

```html
<input type="checkbox" id="agree" /> <label for="agree">동의합니다</label>
```

```css
input:checked {
  accent-color: blue;
}
```

- checkbox가 체크되면 체크 표시가 적용

##### `+` - 인접 형태 선택자

바로 다음 형제 요소에만 적용

```css
input:checked + label {
  font-weight: bold;
}
```

- 위의 코드처럼 Label의 스타일도 변경 가능

#### `:disabled`

비활성화된 요소에만 스타일 적용

```html
<button disabled>제출</button>
```

```css
button {
  background: blue;
}

button:disabled {
  background: gray;
}
```

- 기본적으로 활성화된 요소에 일반 스타일을 적용, 비활성화 상태만 따로 처리하는 방식 주로 사용

#### `:enabled`

활성화되어 있는 요소에만 스타일 적용

```html
<button>제출</button> <button disabled>삭제</button>
```

```css
button:enabled {
  background: blue;
}
```

### 3. 구조/조건

#### `:first-child`

부모 안에서 첫번째 자식 요소에만 적용

```html
<div>
  <p>첫 번째</p>
  <p>두 번째</p>
  <p>세 번째</p>
</div>
```

```css
p:first-child {
  color: red;
}
```

- p 중 첫 번째가 아니라,
- 부모의 첫 번째 자식이면서 p인 요소이다.

#### `:last-child`

부모의 마지막 자식 요소에만 적용

```html
<ul>
  <li>첫 번째</li>
  <li>두 번째</li>
  <li>마지막</li>
</ul>
```

```css
li:last-child {
  color: red;
}
```

- 메뉴의 마지막 요소에 Border을 넣지 않는 경우에 자주 사용
- `<ul>` 에 class가 있을 경우, .class명 li:last-child {} 로 사용 해야함

#### `:nth-child()`

첫 번째와 마지막 요소 외에 특정 순서의 자식에만 적용

```css
li:nth-child(2) {
  color: red;
}
```

- `nth` : 몇 번째, ( ) 안에 숫자로 요소 선택
- `nth-child(odd)` : 홀수 번째만 적용
- `nth-child(even)`: 짝수 번째만 적용
- `nth-child(2n)` : 짝수와 같은 의미
- `nth-child(3n)` : 3의 배수에만 적용
- `nth-child(3n + 1)` :
- `nth-child(3(0) + 1)` = 1
- `nth-child(3(1) + 1)` = 4
- `nth-child(3(2) + 1)` = 7
- `nth-child(3(3) + 1)` = 10 처럼 사용 가능

- 테이블이나 리스트의 Zebra Striping에서 많이 사용

#### `:not()`

특정 조건을 제외하고 적용

```html
<button class="primary">제출</button>
<button>취소</button>
<button>삭제</button>
```

```css
button:not(.primary) {
  background: gray;
}
```

- `button` 인데 `.primary` 가 아닌 것에만 적용

##### 여러 조건도 사용 가능

```css
button:not(.primary):not(.danger) {
  background: gray;
}

.item:not(:first-child) {
  margin-top: 10px;
}
```

- `button` 이면서 `.primary` 도 아니고 `.danger` 도 아닌 것에만 적용
- 첫 번째 자식이 아닌 `.item` 에만 적용 : 리스트 간격 만들 수 있음
