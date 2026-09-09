## 함수 Function

### 1. 함수란?

특정 작업을 하나로 묶어놓은 코드 <br>
여러번 재사용 가능

```javascript
function 함수명(매개변수) {
  // 실행할 코드
}

함수명(); // 함수 밖에서 함수 실행
```

### 2. 매개변수 - parameter

외부에서 값을 전달받기 위해 생성한 변수

```javascript
function sayHello(name) {
  console.log(`안녕하세요 ${name}님`); // name -> 매개변수
}

sayHello('철수'); // 안녕하세요 철수님
```

### 3. 인자 - argument

함수를 호출할 때 전달하는 실제 값

```javascript
function sayHello(name) {
  console.log(`안녕하세요 ${name}님`);
}

sayHello('철수'); // 철수 -> 인자
```

### 4. 여러 매개변수와 인자 사용

```javascript
function add(a, b) {
  console.log(a + b);
}

add(10, 20);
```

### 5. return - 함수 결과를 함수 밖으로 돌려주는 것

```javascript
function add(a, b) {
  return a + b;
}

const result = add(10, 20);

console.log(result);
```

- `console.log` : 화면/콘솔에 결과를 보여주는 것, 단 함수의 결과를 다른 변수에 받을 수 없음
- `return` : 함수의 결과를 밖으로 전달하는 것, return을 만나면 뒤에 다른 선언이 있더라도 함수 종료
- `return` 생략 : 화면에 출력하는 작업만 하고 밖으로 전달할 값이 필요없을 때 생략 가능

### 6. 함수 표현식 Function Expression

함수를 변수에 저장하는 방식

```javascript
// (1) 함수 표현식
const add = function (a, b) {
  // add에 함수 자체를 저장
  return a + b;
};

add(10, 20); // 함수 호출 방식은 동일

// (2) 함수 선언식
function add(a, b) {
  return a + b;
}

add(10, 20); // 함수 호출 방식은 동일
```

### 7. 화살표 함수 Arrow Function

함수를 더 짧게 작성하는 문법

```javascript
// (1) 기존 함수 표현식
const add = function (a, b) {
  return a + b;
};

// (2) 화살표 함수 표현식
const add = (a, b) => {
  return a + b;
};

// (3) 화살표 함수 표현식 - 더 짧게
const add = (a, b) => a + b;

// (4) 매개변수가 하나일 경우
const double = (number) => {
  return number * 2;
};

// 매개변수 괄호 생략
const double = (number) => {
  return number * 2;
};
```

- 화살표 함수에서 보통 return 생략 -> (3)으로 주로 사용, 자동으로 return
- 매개변수 괄호 생략 -> 매개변수가 무조건 하나일 때만 가능
