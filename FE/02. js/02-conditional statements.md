## 조건문 Conditional Statements

### 1. if - 만약 - 라면

조건이 `true` 일 때 코드 실행

```javascript
변수 선언

if (조건) {
    조건이 맞으면 실행
}


const age = 20;

if (age >= 18) {
  console.log("성인입니다.");
}
```

### 2. else - 그렇지 않다면/아니면

조건이 `false` 일 때 실행

```javascript
변수 선언

if (조건) {
    조건이 맞으면 실행
} else {
  조건이 아니면 실행
}


const age = 15;

if (age >= 18) {
  console.log("성인");
} else {
  console.log("미성년자");
}
```

### 3. else if - 그렇지 않고 만약 - 라면

조건이 여러 개일 때 사용

```javascript
변수 선언

if (조건) {
    조건이 맞으면 실행
} else if {
  조건이 아니면 실행
} else if {
  두번째 조건이 아니면 실행
} else {
  모든 조건이 아니면 실행
}


const score = 85;

if (score >= 90) {
  console.log("A");
} else if (score >= 80) {
  console.log("B");    // B
} else if (score >= 70) {
  console.log("C");
} else {
  console.log("F");
}
```

- 위에서부터 확인하고, 처음으로 `true` 가 된 곳 하나만 실행

### 4. switch - 여러 경우로 나누기

하나의 값을 여러 값과 비교할 때 사용

```javascript
변수 선언

if (조건) {
    조건이 맞으면 실행
} else if {
  조건이 아니면 실행
} else if {
  두번째 조건이 아니면 실행
} else {
  모든 조건이 아니면 실행
}


const status = "success";

switch (status) {
  case "pending":
    console.log("처리 중");
    break;

  case "success":
    console.log("성공");
    break;

  case "error":
    console.log("실패");
    break;

  default:
    console.log("알 수 없는 상태");
}
```

- `case` : - 인 경우
- `break` : 여기서 멈추기, 해당 case를 실행한 후 switch문 종료
- `default` : 아무 경우에도 해당하지 않을 때

### if문과 switch문 차이

- if : 조건 자체를 검사할 때
- switch : 하나의 값이 어떤 값인지 확인할 때
