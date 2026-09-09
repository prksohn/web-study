## 객체 Object

### 1. 객체란?

관련 있는 데이터를 묶어서 하나의 대상으로 표현하는 자료구조

```javascript
// (1) 기본 객체 선언
const 객체이름 = {
  key: value,
  key: value,
};

const users = {
  name: '철수',
  age: 20,
  city: '대구',
};

// (2) 배열 + 객체
const users = [
  {
    name: '철수',
    age: 20,
  },
  {
    name: '영희',
    age: 22,
  },
];

console.log(users[0].name);
```

- 각각의 데이터를 `key : value` 형태로 저장
- `key` : 데이터 이름
- `value` : key에 저장된 실제 데이터
- 관련 있는 데이터를 객체로 묶음으로서 하나의 데이터 덩어리처럼 관리 용이
- API에서 주로 배열과 같이 사용

### 2. 객체 접근

#### `.` 으로 접근

```javascript
console.log(user.name);
```

#### `대괄호 []` 로 접근

```javascript
console.log(user['name']);
```

- `(user.name)`, `(user["name"])` : 결과는 동일

### 3. 객체 수정

이미 존재하는 값 변경 가능

```javascript
const user = {
  name: '철수',
  age: 20,
};

user.age = 21;

console.log(user.age); // 21
```

- const 객체명을 재선언 할 수 없지만,
- const 객체 내부의 값은 변경 가능

### 4. 객체 추가

새로운 `key`, `value` 모두 추가 가능

```javascript
const user = {
  name: '철수',
  age: 20,
};

user.city = '대구';
```

### 5. 객체 삭제 - `delete`

```javascript
const user = {
  name: '철수',
  age: 20,
  city: '대구',
};

delete user.city;
```

### 6. Object.keys() - 객체 key만 가져오기

```javascript
const user = {
  name: '철수',
  age: 20,
  city: '대구',
};

console.log(Object.keys(user)); // name, age, city
```

### 7. Object.values() - 객체 value만 가져오기

```javascript
const user = {
  name: '철수',
  age: 20,
  city: '대구',
};

console.log(Object.values(user)); // 철수, 20, 대구
```

### 8. Object.entries() - key, value 같이 가져오기

```javascript
const user = {
  name: '철수',
  age: 20,
  city: '대구',
};

console.log(Object.entries(user));
```

### 9. 구조 분해 할당 Destructuring - 안에 있는 값을 꺼내는 것

객체에서 필요한 값 꺼내서 변수로 생성

```javascript
const user = {
  name: '철수',
  age: 20,
  city: '대구',
};

// 이렇게 하지 않고
const name = user.name;
const age = user.age;
const city = user.city;

// 이렇게 한 번에 꺼내서 사용
const { name, age, city } = user;

console.log(name); // 철수
console.log(age); // 20
console.log(city); // 대구
```

- const : 변수 선언
- { key1, key2, key3 } : 찾아서 꺼낼 key 목록
- = 객체명 : 해당 객체에서 가져온다

### 10. 전개 연산자 `...` - 안에 있는 값을 펼치는 것

```javascript
const user = {
  name: '철수',
  age: 20,
};

const newUser = {
  ...user,
};
```

- `...객체명` : 새로운 객체 안에 기존 객체 내용을 펼쳐 넣음
- 객체를 복사할 때 사용
- 객체를 복사 후 복사한 객체에서 `value` 수정 가능

#### 객체 복사하면서 값 수정

```javascript
const user = {
  name: '철수',
  age: 20,
};

const newUser = {
  ...user,
  age: 21,
};
```

#### 새로운 데이터 추가

```javascript
const user = {
  name: "철수",
  age: 20
};

const newUser = {
  ...user,
  city: "대구"
};

// 결과
{
  name: "철수",
  age: 20,
  city: "대구"
}
```

- 객체 데이터 수정할 때 사용
