## 배열 Array

### 1. 배열이란?

여러 개의 데이터를 하나로 묶어서 저장하는 자료형

```javascript
const fruits = ['사과', '바나나', '포도'];

console.log(fruits[0]); // 사과
console.log(fruits[1]); // 바나나
console.log(fruits[2]); // 포도
```

- `Index` : 배열의 위치 번호 (0부터 시작)

## 배열 정보 확인

### 2. `.length` - 배열의 데이터 개수

메서드가 아닌 배열의 속성 (property)

```javascript
const fruits = ['사과', '바나나', '포도'];

console.log(fruits.length); // 3
```

### 3. 배열 메서드란?

어떤 값에 `.` 을 붙여서 사용하는 함수

#### 선언 형태

```javascript
배열.메서드((매개변수) => {
  // 실행할 코드
});
```

## 배열 데이터 추가/삭제

### 4. `.push()` - 배열 맨 뒤에 추가

```javascript
const fruits = ['사과', '바나나'];

fruits.push('포도');

console.log(fruits); // 사과 바나나 포도
```

### 5. `.pop()` - 배열 맨 뒤의 데이터 제거

```javascript
const fruits = ['사과', '바나나', '포도'];

const removed = fruits.pop();

console.log(removed); // 포도
console.log(fruits); // 사과, 바나나
```

- 저게한 데이터를 바로 사용하기 위해서는 -> 제거한 값을 반환 필수
- return은 함수에서 값을 밖으로 반환할 필요가 있을 때만 사용

### 6. `.shift()` - 배열 맨 앞의 데이터 제거

```javascript
const fruits = ['사과', '바나나', '포도'];

const removed = fruits.shift();

console.log(removed); // 사과
console.log(fruits); // 바나나, 포도
```

- 저게한 데이터를 바로 사용하기 위해서는 -> 제거한 값을 반환 필수
- 반환값을 사용하지 않을 때는 -> 반환 불필요- return은 함수에서 값을 밖으로 반환할 필요가 있을 때만 사용

### 7. `.unshift()` - 배열 맨 앞의 데이터 추가

```javascript
const fruits = ['바나나', '포도'];

fruits.unshift('사과');

console.log(fruits); // 사과 바나나 포도
```

## 배열 일부 다루기

### 8. `.slice()` - 배열 일부분을 잘라서 새로운 배열로 가져오기

```javascript
.slice(시작, 끝)

const fruits = ["사과", "바나나", "포도", "딸기"];

const result = fruits.slice(1, 3);

console.log(result); // 바나나 포도
```

- `.slice(시작, 끝)` : 끝은 미포함, 내용을 가져와도 원본 배열 변경 되지 않음

### 9. `.splice()` - 배열 중간 데이터를 추가하거나 제거하거나 교체할 때

```javascript
// (1) 인덱스 제거
.splice(시작 위치, 제거할 개수)

const fruits = ["사과", "바나나", "포도"];

fruits.splice(1, 1); // idex 1부터 1개만 제거

console.log(fruits);  // 사과 포도

// (2) 인덱스 추가
.splice(시작 위치, 제거할 개수, 추가할 내용) // 제거할 개수는 0

const fruits = ["사과", "포도"];

fruits.splice(1, 0, "바나나");

console.log(fruits); // 사과 바나나 포도
```

- `.splice(시작 위치, 제거할 개수)` : 원본 배열 직접 수정

## 배열 데이터 찾기/확인

### 10. `.indexOf()` - 배열에서 특정 데이터가 몇번째 index에 있는지 찾기

```javascript
const fruits = ['사과', '바나나', '포도'];

console.log(fruits.indexOf('바나나')); // 1
console.log(fruits.indexOf('딸기')); // -1
```

- 없는 데이터를 찾을 경우 : -1

### 11. `.includes()` - 배열에 특정 데이터가 존재하는지 확인

```javascript
const fruits = ['사과', '바나나', '포도'];

console.log(fruits.includes('바나나')); // true
```

- 결과값은 항상 boolean

### 12. `.find()` - 조건에 맞는 첫 번째 데이터 하나만 찾기

```javascript
const numbers = [1, 2, 3, 4, 5];

const result = numbers.find((number) => {
  return number >= 3;
});

console.log(result); // 3
```

- 반환 결과 -> 하나의 값

### 13. `.findIndex()` - 조건에 맞는 첫 번째 데이터의 index 찾기

```javascript
const numbers = [10, 20, 30, 40];

const result = numbers.findIndex((number) => {
  return number >= 30;
});

console.log(result); // 2
```

- 반환 결과 -> 하나의 숫자(index)

## 배열 조건 확인

### 14. `.some()` - 조건에 맞는 데이터가 하나라도 있는지 확인

```javascript
const numbers = [1, 2, 3, 4, 5];

const result = numbers.some((number) => {
  return number >= 5;
});

console.log(result); // true
```

- 반환 결과 -> 항상 boolean

### 15. `.every()` - 배열의 모든 데이터가 조건에 만족하는지 확인

```javascript
const numbers = [2, 4, 6, 8];

const result = numbers.every((number) => {
  return number % 2 === 0; // 짝수인지
});

console.log(result); // true
```

- 모든 데이터가 조건에 만족해야 true
- 하나라도 조건에 만족하지 않으면 false
- 반환 결과 -> 항상 boolean

## 배열 가공

### 16. `.map()` - 배열의 각각의 데이터를 변환해서 새로운 배열 생성

```javascript
const numbers = [1, 2, 3];

const result = numbers.map((number) => {
  return number * 2;
});

console.log(result); // 2 4 6
```

- `map()` 함수의 괄호 안에 함수를 하나 넣은 것
- API 데이터 처리에서 사용 빈도 높음
- 반환 결과 -> 새로운 배열

### 17. `.filter()` - 배열에서 조건에 맞는 데이터만 골라서 새로운 배열 생성

```javascript
const numbers = [1, 2, 3, 4, 5];

const result = numbers.filter((number) => {
  return number >= 3;
});

console.log(result); // 3 4 5
```

- 조건에 맞는 것만 남긴다.
- 반환 결과 -> 새로운 배열

### 18. `.reduce()` - 배열 데이터를 하나의 결과값으로 합칠 때

```javascript
.reduce(함수, 초기값)

const numbers = [10, 20, 30];

const result = numbers.reduce((sum, number) => {
  return sum + number;
}, 0);

console.log(result); // 60
```

- sum = 0
- 0 + 10 = 10
- 10 + 20 = 30
- 30 + 30 = 60
- 배열 여러 개를 하나의 값으로 축약 (reduce)
- sum : 지금까지 계산한 결과ㅏ
- number : 현재 배열에서 꺼낸 값
- `초기값 0` : 어떤 값으로 시작할지 정해주는 것
- 곱셈을 누적한다면 -> 1로 초기화
- 반환 결과 -> 하나의 값

## 배열 하나씩 작업

### 19. `.forEach()` - 배열 데이터를 하나씩 꺼내서 어떤 작업 할 때

```javascript
const fruits = ['사과', '바나나', '포도'];

fruits.forEach((fruit) => {
  console.log(fruit); // 사과 바나나 포도 각각 별도로 실행
});
```

- `for ... of` 와 비슷하게 각각의 데이터 처리
- API에서 사용자 목록 데이터 중 원하는 데이터만 출력하고 싶을 떄 사용
- 배열의 각각의 데이터를 가지고 어떤 작업을 실행하기 때문에 별도의 변수 선언 불필요
- 반환 결과 -> 반환값을 활용하는 용도가 아님
