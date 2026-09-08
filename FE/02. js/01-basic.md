## JavaScript Basic

### 1. 변수 Variable - `let`

값을 저장해두는 공간, 값 재할당 가능

```javascript
let age = 20;
age = 21;
console.log(age);
```

### 2. 상수 Constant - `const`

값을 저장해두는 공간, 값 재할당 불가능

```javascript
const name = '철수';
console.log(name);
```

- 기본적으로 `const` 를 사용하고, 값을 변경해야 할 때 `let` 사용

#### 주의점

`const` 여도 무조건 재할당 불가능한 건 아님

```javascript
// 가능
const user = {
  name: '철수',
  age: 20,
};

user.age = 21;
console.log(user.age);

// 불가능
const user = {
  name: '철수',
};

user = {
  name: '영희',
};
```

- `const user` : 객체를 가리키는 연결 자체는 변경 불가
- `name: "철수", age: 20` : 객체 내부 프로퍼티는 변경 가능
- 추후 react에서 중요
- 변수명은 변수가 무엇을 의미하는지 이름만 보고 알 수 있도록 선언

### 3. 자료형 Type

#### 문자열 String

`" "`, `' '`

```javascript
const name = '철수';
const message = '안녕하세요';
```

#### 숫자

JS에서는 기본적으로 정수, 소수 모두 number type

```javascript
const age = 20;
const price = 15000;
```

#### 문자열 + 숫자

문자열 `+` 숫자 = 문자열

```javascript
const age = 20;
console.log('나이: ' + age);
```

#### 템플릿 리터럴 - `${name}`

실무에서 주로 사용 <br>
`${name}`

```javascript
const name = '철수';
const age = 20;

const message = `${name}의 나이는 ${age}살입니다.`;
console.log(message);
```

#### 불리언 Boolean - 참/거짓

주로 조건문에서 사용

```javascript
const isLogin = true;
const isAdmin = false;
```

#### undefined

값이 아직 할당되지 않았거나 존재하지 않는 상태

```javascript
let age;
console.log(age); // 출력: undefined

// 객체에서 없는 프로퍼티
const user = {
  name: '철수',
};

console.log(user.age); // 출력: undefined
```

#### null

의도적으로 값이 없음을 지정

```javascript
let profileImage = null;
```

#### 객체 Object

관련된 데이터(속성/정보)를 하나로 묶어서 표현할 때

```javascript
// (1) 기본 객체 생성
const user = {
  name: '철수',
  age: 20,
  isStudent: true,
};

// (2) 객체에서 값 가져와야 할 때
console.log(user.name); // 출력: 철수
console.log(user.age); // 출력: 20

console.log(user['name']); // 출력: 철수

// (3) 프로퍼티 이름을 변수로 다뤄야 할 때
const key = 'name';

console.log(user[key]); // 출력: 철수

// (4) 객체 값 변경
const user = {
  name: '철수',
  age: 20,
};

user.age = 21; // 내부 프로퍼티만 변경

console.log(user.age); // 출력: 21

// (5) 새로운 프로퍼티 추가
const user = {
  name: '철수',
  age: 20,
};

user.age = 21;
user.city = '대구';

console.log(user); // 출력: name: "철수", age: 21, city: "대구"
```

- 사용 빈도: `console.log(user.name);` > `console.log(user["name"]);`
- 단 프로퍼티 이름을 변수로 다뤄야 할 때는 대괄호 표기법 사용
- `name`, `age`, `isStudent` : 프로퍼티 Property
- 새로운 프로퍼티 추가도 가능

#### 배열 Array

여러 개의 값을 순서대로 저장하는 자료구조

```javascript
// (1) 기본 배열 선언
const fruits = ['사과', '바나나', '포도'];

console.log(fruits.length); // .length : 배열의 데이터 개수

// (2) 배열 + 반복문
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}

// (3) 배열 안에 객체 넣기 - API 응답 데이터 구조
const users = [
  {
    id: 1,
    name: '철수',
    age: 20,
  },
  {
    id: 2,
    name: '영희',
    age: 22,
  },
  {
    id: 3,
    name: '민수',
    age: 25,
  },
];

console.log(users[0].name); // 출력: 철수
```

- 배열 안에는 순서가 있고 그 번호를 Index 라고 한다.
- JS 배열은 0부터 시작
- `.length` : 배열의 데이터 개수, 반복문과 함께 사용
- 배열 안에 객체 넣기도 가능
- `users[0].name` : users -> 0번째 데이터 가져오기 -> 그 안에서 name 가져오기

#### typeof - 값의 타입 확인

값의 타입을 확인할 때 사용 <br>
null, 배열, 객체 타입은 주의

```javascript
const name = '철수';
const age = 20;
const isStudent = true;

console.log(typeof name); // 출력: string
console.log(typeof age); // 출력: number
console.log(typeof isStudent); // 출력: boolean
```

##### 주의점

```javascript
// (1) typeof null
console.log(typeof null); // 출력: object

// (2) 배열의 typeof
const fruits = ['사과', '바나나'];

console.log(typeof fruits); // 출력: object

// (3) 배열 type 검사 후 결과 반환
Array.isArray(fruits); // 출력: true

// (4) 배열 type 결과 콘솔 출력
console.log(Array.isArray(fruits)); // 출력: true
```

- (1) `null` 은 논리적으로 객체가 아닌데도 `typeof null` 의 결과는 `object`
- (2) 배열도 typeof는 `object`
- (3), (4) 배열 타입인지 확인 방법 - 결과값은 항상 boolean

### 4. 비교 연산자 - `===`, `!==`, `>`, `<`, `>=` `<=`

두 값을 비교해서 `true` 또는 `false` 를 만드는 연산자

```javascript
연산자      의미           예시         결과
===       같다        10 === 10      true
!==       같지 않다    10 !== 20      true
>         크다        10 > 5         true
<         작다        10 < 5         false
>=        크거나 작다   10 < 5         true
<=        작거나 같다   10 <= 5        false
```

#### `===` - 완전히 같은지 확인 (값과 타입까지 엄격한 비교)

실무에서 가장 중요, 사용 권장

```javascript
const age = 20;

console.log(age === 20); // true
console.log(age === 30); // false
console.log(20 === '20'); // false
```

- 데이터 타입도 일치 해야 완전히 같다.

#### `!==` - 다른지 확인

```javascript
const age = 20;

console.log(age !== 20); // false
console.log(age !== 30); // true
```

#### `==` - 같은지 확인 (형변환은 비교하지 않음)

```javascript
20 == '20'; // true

20 === '20'; // false
```

### 5. 논리 연산자 - `&&`, `||`, `!`

#### `&&` - AND (둘 다 true여야 true)

```javascript
// (1) 참
const age = 20;
const hasTicket = true;

console.log(age >= 18 && hasTicket); // true

// (2) 거짓
const age = 15;
const hasTicket = true;

console.log(age >= 18 && hasTicket); // false
```

#### `||` - OR (둘 중 하나만 true여도 true)

```javascript
const isAdmin = false;
const isManager = true;

console.log(isAdmin || isManager); // true

if (isAdmin || isManager) {
  console.log('관리자 페이지 접근 가능');
}
```

#### `!` - NOT (true <-> false)

```javascript
const isLogin = true;

console.log(!isLogin); // false

const isLogin = false;

console.log(!isLogin); // true

if (!isLogin) {
  console.log('로그인이 필요합니다.');
}
```

### 6. 조건 연산자 (= 삼항 연산자 ternary operator)

```javascript
조건 ? 참일 때 : 거짓일 때

const age = 20;

const result = age >= 18 ? "성인" : "미성년자";  // 삼항 연산자

console.log(result); // 성인
```

- 간단한 조건: `삼항 연산자` 사용
- 복잡한 조건: `if - else` 사용
