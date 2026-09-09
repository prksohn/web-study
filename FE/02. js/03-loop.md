## 반복문 Loops

### 1. for문 - 정해진 횟수만큼 반복

```javascript
변수 선언

for (초기값; 조건; 증감) {
  // 반복할 코드
}

for (let i = 0; i < 5; i++) {
  console.log(i);  // 0 1 2 3 4
}

const fruits = ["사과", "바나나", "포도"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

- `let i = 0` : 처음 시작할 값
- `i < 5` : 언제까지 반복할지
- `i++` : 한 번 실행할 때마다 1 증가
- 보통 배열을 반복하는 경우가 많음
- .length: 인덱스 직접 다룸

### 2. while문 - 조건이 맞는 동안 반복

```javascript
변수 선언

while (조건) {
  // 반복할 코드
}

let count = 0;

while (count < 5) {
  console.log(count); // 0 1 2 3 4
  count++;
}
```

- 조건이 계속 true면 무한 반복되기 때문에 조건이 언젠가 false가 되도록 만들어야 함

### 3. do while문 - 일단 한 번 실행하고 조건 확인

```javascript
변수 선언

do {
  // 먼저 한번 실행할  코드
} while (조건) {
    // 반복할 코드
}

let count = 0;

do {
  console.log(count);
  count++;
} while (count < 5);
```

### 4. while과 do while 차이

조건이 false일 경우

```javascript
// (1) while
let count = 10;

while (count < 5) {
  console.log('실행'); // 실행 되지 않음
}

// (2) do while
let count = 10;

do {
  console.log('실행'); // 실행
} while (count < 5);
```

### 5. for of - 배열의 값을 하나씩 가져오기 (값)

배열 같은 iterable의 값을 하나씩 가져온다.

```javascript
// (1) 선언 방법
변수 선언

for (const 하나의 값의 변수명 of 위에 선언한 여러개 값의 변수명) {
  // 하나의 값을 사용
}

// (2) 기본 for of
const fruits = ['사과', '바나나', '포도'];

for (const fruit of fruits) {
  console.log(fruit); // 사과 바나나 포도
}

// (3) 객체 배열에서의 사용
const users = [
  { name: '철수', age: 20 },
  { name: '영희', age: 22 },
  { name: '민수', age: 19 },
];

for (const user of users) {
  console.log(user.name); // 철수 영희 민수
}
```

- for문 .length와 다르게 값을 직접 가져옴
- API 데이터 다룰 때 주로 사용
- const이지만 각 반복에서 새로운 변수명이 생성되는 것

### 6. for in - 객체의 key 가져오기 (key/index)

객체의 key(속성 이름)를 하나씩 가져올 때 사용

```javascript
// (1) 객체에서 사용 - key
const user = {
  name: '철수',
  age: 20,
  city: '대구',
};

for (const key in user) {
  console.log(key); // name age city
  console.log(user[key]); // 철수 20 대구
}

// (2) 배열에서 사용 - index
const fruits = ['사과', '바나나', '포도'];

for (const index in fruits) {
  console.log(index); // 0 1 2
}
```

- `console.log(key)` : 속성 이름 가져올 때
- `console.log(user[key])` : 속성 값을 가져올 때

### 7. break - 반복 중단

반복문을 즉시 끝내는 것

```javascript
변수 선언

for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;
  }

  console.log(i); // 0 1 2 3 4
}

// 특정 데이터 찾으면 더 이상 반복할 필요없을 때 사용
const users = ["철수", "영희", "길동"]

for (const user of users) {
  if (user.name === "영희") {
    console.log("영희를 찾았습니다.");
    break;
  }
}
```

- `i === 5` 가 되는 순간 break가 실행돼서 반복문 종료

### 8. continue - 이번 반복만 건너뛰기

현재 반복을 건너뛰고 다음 반복으로 넘어가는 것

```javascript
for (let i = 0; i < 5; i++) {
  if (i === 2) {
    continue;
  }

  console.log(i); // 0 1 3 4
}
```

### break와 continue 차이

- `break` : 반복문 자체를 종료
- `continue` : 이번 반복만 건너뛰고, 다음 반복 계속

### 실무에서 사용 방법

- for : 인덱스가 필요하거나 횟수를 직접 제어해야 할 때
- for of : 배열의 데이터를 하나씩 처리할 때
- for in : 객체의 key를 순회할 때
- while : 조건을 만족되는 동안 계속 반복해야 할 때
- do while : 최소 한번은 실행해야 할 때
